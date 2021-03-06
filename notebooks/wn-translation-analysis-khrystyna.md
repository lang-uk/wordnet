### Питання від @dchaplinsky:

- Ваші загальні враження від результатів? Чи варто? - **Так. Результати дуже непогані!**
- Чи є ідеї щодо покращення цих результатів? - **Так, див. Аналіз.**
- Чи варто залишати Bing Translate? - **Думаю, так, хоч він і гірше перекладає, ніж Google, але деякі переклади хороші.**
- Чи варто залишати Bing Dictionary? - **Думаю, ні. Я не побачила хороших варіантів перекладу чогось.**
- Чи є ідеї з іншими машиночитними словниками en2uk? - **Так, див. Аналіз.**
- Чи варто намагатися покращити результати Bing Dictionary (наприклад фільтруючи результати за частиною мови або порівнюючі оригінальні леми з backTranslations з відповіді) - **Поки що з тих синсетів, які я проаналізувала, навіть фільтр за частиною мови, не був би дуже помічним.**
- Як фільтрувати мотлох у перекладах? (в мене були думки про використання українських словників синонімів, категоризаторів синонімів, кластеризації по векторах, тощо) - **Див. Аналіз.**


### Аналіз, 15 жовтня

Можна застосовувати такі паттерни для перекладу:

- A <POS> "<synonym 1>" is a synonym to the verb "<synonym 2>"( and "<synonym 3>.")? It means "<definition>." (For example, "<example>.")?

- A <POS> "<synonym 1>" means "<definition>." (For example, "<example>.")?

Де POS - частина мови.

Google і Bing видають здебільшого стандартні переклади: 

- (Іменник|Дієслово|Прикметник|Дієприкметник) "<синонім 1>" - це синонім (іменника|дієслова|прикметника|дієприкметника) "<синонім 2>"( та "<синонім 3>")?. (Це|Воно) означає "<визначення>". Наприклад, "<приклад>."

- (Іменник|Дієслово|Прикметник|Дієприкметник) "<синонім 1>" є синонімом (іменника|дієслова|прикметника|дієприкметника) "<синонім 2>"( та "<синонім 3>")?. (Це|Воно) означає "<визначення>". Наприклад, "<приклад>."

- Bing інколи видає друге речення так: Означає "<визначення>".

- (Іменник|Дієслово|Прикметник|Дієприкметник) "<синонім 1>" означає "<визначення>". Наприклад, "<приклад>."

- NB: Крапка в укр. перекладі зазвичай ставиться після лапок, а в англійському - перед лапками.

- NB: Лапки можуть бути і `" "`, `« »`.

- NB: Все, що з ворднету я брала в лапки.

- NB: в самому визначенні ворднету можуть бути лапки. Див. на `(usually followed by 'to')`: 

```
An adjective "able" means "(usually followed by `to') having the necessary means or skill or know-how or authority to do something." For example, "able to swim"; "she was able to program her computer"; "we were at last able to buy a car"; "able to get a grant for the project."
```

```
Прикметник "здатний" означає "(зазвичай слідує за" до "), що володіє необхідними засобами або навичками, ноу-хау або повноваженнями щось робити". Наприклад, «вміє плавати»; "вона змогла запрограмувати свій комп'ютер"; "ми нарешті змогли купити машину"; "може отримати грант на проект". 
```


### Аналіз, 13 жовтня

##### v: expectorate, cough up, cough out, spit up, spit out

1. Різні префікси: "відпльовувати" та "випльовувати", "вихаркати" та "відхаркати". Поки Bing i Google не дають обидва варіанти. Можна спробувати вирішити через [перекладні словники e2u](https://e2u.org.ua/s?w=expectorate&dicts=all&highlight=on&filter_lines=on): повідшуковувати синонімічні ряди кожного терміна за частиною мови, потім взяти цю множину і позважувати в ній синоніми. Правда, тут виникає питання, якої довжини має бути український синсет порівняно з англ.

2. Док. і недок. вид ("відпльовувати" та "відплюнути"; "відкашлювати" та "відкашляти"). Можна вирішити з векторами.

3. "плювати", "кашляти", "плюнути", != "відкашляти"/"відплюнути". Поганий переклад, це теж можна через перекладні словники: якщо множина синонімів з перекладник словників не містить слова - видалити його з множити.

4. Зворотні дієслова "відкашлятися", "випльовуватися" != "відкашляти"/"відплюнути". Поганий переклад.

5. "мокрота або мокрота". Могло б бути "мокротиння" чи "харкотиння". Треба буде виявляти такі випадки в паттерні <\1 (або|i|та) \1> і або забирати одне слово, або шукати через словники синонімічні.

6. GoogleTranslator. Мав помилку у визначенні (див.5), помилки в перекладі синонімів (див 3.), помилку зі зворотніми дієсл. (див. 4.), одне слово переклав як іменник (але це лише у group_by=1). Тут більше варіантів перекладів синонімів.

7. BingTranslator. Дієслово переклав як дієприкметник (лише у group_by=1); така ж помилка як у 3. і у 4.; Тут менше варіантів синонімів у перекладі.

8. DictionaryBingTranslator без результатів.


##### v: shed, molt, exuviate, moult, slough

1. GoogleTranslator дає кращий переклад визначення, ніж BingTranslator. Переклад визначення BingTranslator'а дивний: "відкидати волосся".

2. "линяти", "лущитися", "вилущуватися" (group_by=3); "скидати" (group_by=1) - найкращі варіанти GoogleTranslate. "хлюпати" - поганий переклад, теоретично його можна з допомогою векторів виключити з синсету. 

3. BingTranslator дає геть погані переклади синсету: "до сльоти", "линька", "линьки", "випрофілювати", "для ексувіату" О_О...

4. group_by=3 для обох перекладачів дає кращі результати, ніж group_by=1.

5. BingDictionary дає геть погані результати: на переклад дієслова дає іменники, ше й в різних відмінках; або дієслова не в початковій формі :) Єдиний хороший переклад - "скинути" - має найнижчий confidence. 

6. Для цього синсету, переклад треба робити з одного на два слова: "скидати шкіру", "скидати шкуру", "міняти шкіру".

7. Синсет дуже специфічний, тому до нього варто додати такі синоніми: "випіритися" (і "випірюватися", "випірятися" - питання про доконаний і недоконаний вид). Це знову можна зробити з допомогою [перекладних словників e2u](https://e2u.org.ua/s?w=molt&dicts=all&highlight=on&filter_lines=on).


##### n: smoke, fastball, heather, bullet, hummer

Дуже специфічний синсет - про бейсбол (про це є примітка у визначенні). Я не знайшла ніяких відповідних перекладів у наших словниках e2u. Навіть Macmillan i Longman не дають нічого про це значення.

Моя пропозиція такі синсети навіть не перекладати на українську (для цього, можна дивитися на примітки, напр., `(baseball)`), бо навіть якщо переклади будуть хороші і зрозумілі ("фастбол", "швидкий м’яч" як дають перекладачі), то для української мови ці терміни непритаманні. 

Натомість виникає питання - які явища притаманні тільки для української культури/мови? І як з них створювати синонімічні ряди? Перша думка - дивитися на векторний простір української мови і знаходити кластери, ще неописані в укр.ворднеті, опрацювувати ці кластери і поступово додавати синряди. Складність проєкту - висока. Можна робити після завершення перекладу ворднету. Або ще можна взяти якісь словники суто українських термінів абощо.


##### a: ill-treated, abused, maltreated, mistreated

1. Геть погані переклади для синонімів. Жоден з синонімів не перекладений як прикметник, перекладені як іменники чи дієслова в різних формах (і чомусь деякі з великої букви?). Те ж саме з визначенням: воно не погане, але там не хватає "той, хто/з ким": "піддається жорстокому поводженню".

2. Я би переклала так: "ображений", "зневажений", "той, кого зневажають", "той, з ким погано жорстоко поводяться", "той, з ким погано поводяться". Останні три - це вже ціла фраза. Я не думаю, що у ворднет варто додавати такі цілі фрази. Але це питання треба дослідити в інших перекладних ворднетах.

3. Це прикметники, похідні від дієслів, тому такі синсети можна пробувати виявляти і мати для них окремий алгоритм опрацювання. Наприклад, до перекладу додавати на початок "той, хто" тощо. А потім перевіряти їхні ймовірності. Наприклад:

```
той, хто + жорстоке поводження [-]
той, хто + зловживання [-]
той, хто + зловживають [-]
той, хто + жорстоко поводяться [-]
той, хто + погано поводяться [-]

той, з ким + жорстоке поводження [-] 
той, з ким + зловживання [-] 
той, з ким + зловживають [-]
той, з ким + жорстоко поводяться [+]
той, з ким + погано поводяться [+]
```


### Роздуми

Для різних частин мови можна застосовувати різні алгоритми перекладу синсетів.

Для дієслів, наприклад, такий: 
- доповнення синсету синонімами (і ширшими синонімічними фразами, як у "скидати шкіру") через перекладні словники.
- фільтрування синсету з допомогою векторів.

Для віддієслівних прикметників такий як у `a: ill-treated, ...`.

Не всі синсети треба перекладати, див. `n: smoke, ...`

Треба опрацювати ще рашту перекладів для загальнішої картини, тому далі буде...

