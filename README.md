# Magister_2018_K1-K9
## Частина 1

Спроба пошуку кореляції між коеф. К1-К9 та виділеними бюджетними місцями в магістратуру в 2018 році

Частина 1: https://github.com/SerhiyProtsenko/Magister_2018_K1-K9/blob/master/Mag2018%20%D0%9A-1_%D0%9A-9_v2.ipynb

Згідно наказу МОН №445 “Про затвердження Критеріїв конкурсного відбору виконавців державного замовлення на підготовку магістрів у закладах вищої освіти, які знаходяться у сфері управління МОН” див. http://zakon3.rada.gov.ua/laws/show/z0625-18 . Запроваджується система згідно якої кожен ЗВО (заклад вищої освіти) повинен отримати ту кількість держбюджетних місць в магістратуру в 2018 році на яку він заслуговує згідно критеріїв, які підтверджують якість наукової роботи, диверсифікацію доходів, якість кадрового забезпечення тощо (див. детально наказ).

Кожен ЗВО повинен був надати необхідну інформацію для розрахунку критеріїв К1-К9 за кожного спеціальністю, надати обсяги випуску бакалаврів в 2018 році тощо.

Після перевірки значень коефіцієнтів К1-К9, утворена комісія в МОН знаходить добуток коефіцієнтів К1-К9 та потім підраховує конкурсний бал, як добуток обсягу випуску бакалавра на добуток коефіцієнтів К1-К9 (див. детально наказ п.6).

Конкурсний бал (розраховується для кожної окремої спеціальності ) = К1К2К3К4К5К6К7К8К9*”обсяг випуску бакалаврів за спеціальністю”

І згідно пукту 6 зазначеного наказу : “визначення обсягу державного замовлення проводить Комісія окремо за кожною конкурсною позицією пропорційно конкурсному балу”. В результаті ЗВО, який мав гарні показники К1-К9 повинен був розраховувати на максимальні обсяги держбюджетних місць під всіх або практично під всіх випускників бакалавратури.

Ідея наказу взагалі гарна. Оцінити університети і окремі спеціальності в цих університетах за критеріями і пропорційно ним і обсягу випуску бакалаврів розподіляти держбюджетні місця і надавати держбюджетні місця тільки тим університетам, які на це заслуговують і можуть дійсно забезпечити якісну освіту.

Давайте спробуємо перевірити цей добрий намір. Забігаючи наперед, я побачив, що обсяг виділених держбюджетних місць в магістратуру в 2018 році дуже слабо або взагалі не корелює з коефіцієнтами К1-К9 та їх добутком і як в минулі роки розподіл держбюджетних місць скоріш за все відбувався в “ручному режимі” (дивлячись тільки на обсяги випуску бакалаврів), а можливо я щось не врахував і тому прошу вивчити мої розрахунки, щоб ми всі разом зрозуміли де істина (я вже змарнував весь вихідний на це).

Одна з проблем, яку ми повинні вирішити це те, що необхідна нам інформація знаходиться в трьох різних pdf файлах, яку ми повинні зібрати до купи. Користуватися ми будемо трьома файлами pdf, які розміщені на сайті МОН і є офіційними (https://mon.gov.ua/storage/app/media/vishcha-osvita/vstup-2018/dergavne-zamovlenna/komisia/2-konkursna-komisiya-mon-z-vidboru-vikonavtsiv-dz-130718.rar та https://mon.gov.ua/storage/app/media/vishcha-osvita/vstup-2018/komisiya-mon-z-vidboru-vikonavtsiv-dz-200718.rar )

Перший файл: Критерії К-5_К-9.pdf - тут є необхідна для нас інформація про обсяги випуску бакалаврів. В таблиці більш ніж 3000 записів (по всім ЗВО та спеціальностям в державі). Pdf сформований кривувато і тому пришлось довго чистити мусор.
Другий файл: Коофіцієнти (Наказ 445).pdf - містить в собі інформацію по значенням розрахованих коефіцієнтів К1-К9. В таблиці більш ніж 3000 записів (по всім ЗВО та спеціальностям в державі). Pdf сформований краще, з ним було менше проблем.
Третій файл: Обсяг Магістратура.pdf - містить в собі саме головне: обсяги виділених держбюджетних місць в магістратуру. В таблиці більш ніж 3000 записів (по всім ЗВО та спеціальностям в державі). Pdf сформований краще, з ним було менше проблем.
Перша задача, розпарсити ці три файли та звести докупи. Потім нагенерити додаткових фітч та подивитися на це все очами Data Scientist’a ;)

Для кого слова python, jupyter notebook та ін. незнайомі можна скористатися файлом , який я згенерував - Mag2018_K1_k9_v2.xlsx. https://github.com/SerhiyProtsenko/Magister_2018_K1-K9/blob/master/Mag2018_K1_k9_v2.xlsx

## Частина 2


В другій частині ми проаналізуємо в якому випадку виділення бюджету відбувалося непропорційно добутку коефіцієнтів К1-К9 і саме для яких спеціальностей. Оскільки до першої частини надходили зауваження стосовно того, що не можна рахувати кореляцію по всій виборці (з чим я взагалі не згоден, оскільки немає різниці). В другій частині ми будемо рахувати кореляції окремо для кожної спеціальності. Також були зауваження стосовно того, що необхідно шукати кореляцію між конкурсним балом (добуток між обсягом випуску бакалаврів та добутком коефіцієнтів К1-К9.) але, як ми встановили в першій частині є гарна кореляція між наданими бюджетними місцями в магістратуру та випуском бакалаврів але практично відсутня між добутком коефіцієнтів К1-К9 та відсотком виділеного бюджету магістрів. Оскільки здобутки університетів відображаються саме в коефіцієнтах К1-К9, а не в випуску бакалаврів то це питання нас буде цікавить більше всього.

В третій частині проаналізуємо питання, які університети отримали більший бюджет і за рахунок яких університетів це відбулося. (з'явиться незабаром, коли знайду вільний час)

