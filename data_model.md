```
@prefix src: <https://lang.org.ua/wn/src/> .
@prefix w: <https://lang.org.ua/wn/word/> .
@prefix wf: <https://lang.org.ua/wn/wordform/> .
@prefix lemma: <https://lang.org.ua/wn/lemma/> .
@prefix : <https://lang.org.ua/wn/> .

src:wikt/uk {
  w:мати :form wf:мати/N .
  wf:мати/N :lemma l:мати/N.1 , l:мати/N.2 .
  l:мати/N.1 :hypernym l:родич/N.1 ;
             :synonym l:матір/N.1 , wf:ненька/N , wf:неня/N , wf:мама/N ;
             :def "жінка щодо дитини, яку вона народила" ;
             :def#2 "жінка, що має або мала дитину" ;
             :def#3 "(перен) про що-небудь дуже близьке, дороге, рідне" ;
             :def#4 "самиця, стосовно своїх малят" .
  l:мати/N.2 :synonym w:Батьківщина ;
             :def "місце походження" .
}
```

1. Основний вузол, до якого прив'язані ієрархічні та групові зв'язки — лема (наприклад: l:мати/N.1).
2. Дані з кожного джерела поміщаються у відповідний граф (наприклад: src:wikt/uk).
3. Еталонні дані, які створює наша система, поміщаються у дефолтний граф
4. Що робити, коли в різних джерелах одна лема має різні значення? Приклад:

```
src:wikt/uk {
  l:мати/N.1 :def "жінка щодо дитини, яку вона народила" ;
             :synonym l:матір/N.1 , wf:ненька/N , wf:неня/N , wf:мама/N .
}
src:ulif {
  l:мати/N.1 :def "місце походження" ;
             :synonym w:Батьківщина .
  l:мати/N.2 :def "сорт чаю" ;
             :synonym w:мате .
}
```

Відповідь наступна:

1. Ми не хочемо плодити зайвих сутностей. Тому ми використовуємо стандартні зв'язки (`:synonym`, а не `:wnSynonym` та `:ulifSynonym`), але прив'язані до конкретного графу-джерела. Так само ми не хочемо створювати вузли `wn-мати/N.1` та `ulif-мати/N.1`, бо вся інформація вже є у перерізу конкретного графу.
2. Загалом, при отриманні інформації з декількох джерел можливі наступні ситуації:
   - набір лем збігається
   - перетин лем не нульовий, але в кожному джерелі є додаткові леми
   - порядок лем переплутаний (як у цьому прикладі)

Так чи інакше, на виході (у дефолтному графі) має бути сформований набір еталонних вузлів і зв'язків. Вони будуть виглядати наступним чином:

```
  l:мати/N.1 :def "жінка щодо дитини, яку вона народила" ;
             :synonym l:матір/N.1 , l:ненька/N.1 , l:неня/N.1 , l:мама/N.1 .
  l:мати/N.2 :def "місце походження" ;
             :synonym l:Батьківщина/N.1 .
  l:мати/N.3 :def "сорт чаю" ;
             :synonym l:мате/N.1 .
```

Те, який порядок лем буде обрано, залежить від алгоритму відбору еталонних вузлів, а не від їх порядку у тому чи іншому джерелі. Загалом, ми не можемо мати якісь гарантії щодо того, що леми в різних джерелах будуть збігатись, мати однаковий набір синонімів або ж хоча б не взаємоперетинаючийся, або що всі зв'язки (такі як синоніми чи гірепніми) будуть використовувати саме леми. Іншими словами, варіант "перехресних" лем — це тільки одна з багатьох можливих неоднозначностей, з якими ми матимимо справу, і ми не можемо для кожної неоднозначності вигадувати особливий спосіб обробки.

Втім, якщо ми зможемо достовірно виявити випадок, коли лема.1 у одному джерелі відповідає лема.2 у іншому, ми зможемо відмітити це окремим зв'язком, наприклад так:

```
src:wikt/uk {
  l:мати/N.1 owl:sameAs _:foo .
  _:foo :graph src:ulif ;
        :lemma :l:мати/N.2 .
}
```

(Де `_:foo` — це т.зв. анонімний вузол).

Хоча, як на мене, це не є принциповим. Загалом, в нашій графовій моделі даних ми застосовуємо наступний підхід:

- кожен вузол має певний набір "сирих" властивостей, на основі яких ми робимо висновки щодо властивостей, які включаємо до нашого ворднету
- застосування графів (4-й елемент кваду) дає можливість бачити "вигляд" всіх даних з певного джерела