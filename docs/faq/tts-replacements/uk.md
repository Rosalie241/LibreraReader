---
layout: main
---

# Заміна TTS

> Заміни тексту в мовлення використовуються, щоб змінити спосіб вимовляння певних слів, щоб пропустити певні символи під час читання або встановити правильні позначки наголосу.

*Увімкнути заміни TTS
*Показати уривок із результатами заміни
*Діалогове вікно **Заміни** для встановлення правил заміни

|1|2|3|
|-|-|-|
|![](1.png)|![](2.png)|![](3.png)|

Підтримуються класичні заміни (проста зміна одного рядка іншим), або ви можете використовувати регулярні вирази (RegExp).

## Вирази

*&quot;текст&quot; – простий текст
*&quot;*text&quot; – *Правило RexExp
*&quot;#text&quot; – вимкнене правило
*&quot;text256&quot; - вимкнене правило

## Приклади

*&quot;Lib.&quot; -&gt; &quot;Librera&quot; - замінити Lib. з Librera
*&quot;Librera&quot; -&gt; &quot;Libréra&quot; - додайте правильну позначку наголосу
*&quot;#Lib.&quot; -&gt; &quot;Librera&quot; - використовуйте &quot;#&quot;, щоб вимкнути правило
*&quot;*(L|l)ib.&quot; -&gt; &quot;$1ibrera&quot; - замінити Lib. з Librera і lib. з librera
*&quot;*[()&quot;«»*”“/[]&quot; -&gt; &quot;&quot; - пропускати символи
*&quot;*[?!:;–|—|―]&quot; -&gt; &quot;,&quot; - замінити символи на паузу (,)

## Команди TTS

*&quot;text&quot; -&gt; ttsPAUSE - Додати паузу після &quot;text&quot;
*&quot;text&quot; -&gt; ttsSTOP - Зупинити TTS, якщо знайти &quot;текст&quot; у реченні
*&quot;текст&quot; -&gt; ttsNEXT - Перейти до наступної сторінки, якщо знайти &quot;текст&quot; у реченні
*&quot;текст&quot; -&gt; ttsSKIP - пропустити читання речення, якщо знайти &quot;текст&quot; у реченні

## Додайте файл-правило

**Librera** підтримує файли правил RegExp із **@Voice Reader**
Перегляньте цей зразок **demo-replaces.txt** нижче:

```
" живого " "живо́ва"
" как глаза " " как глаза́ "
" мне глаза" " мне глаза́"
" наклоняющая головы" "наклоня́ющая го́ловы"
" никакого стрелка" "никако́во стрелка́"
" ПОЖАРОБЕЗОПАСНУЮ СРЕДУ" "пожарабезопа́сную среду́."
" Стрелки!" "Стрелки́!"
" стрелки?" "стрелки́?"
", все так," ", всё так,"
"Зачем, стрелок?" "Зачем, стрело́к?"
"стрелок?" "стрело́к?"
*"(?i)\b\Q душа в душу\E\b" "душа́ в ду́шу"
*"(?i)\b\Q подогнулись\E\b" "падагну́лись"
*"(?i)\b\Q стрелки почувствовали\E\b" "стрелки́ почувствовали"
*"(?i)\b\Q стрелки продолжили\E\b" "стрелки́ продолжили"
*"(?i)\b\Q стрелку из\E\b" "стрелку́ из"
*"(?i)\b\Q стрелок\E\b" "стрело́к"
*"(?i)\b\Q стрелы\E\b" "стре́лы"
*"(?i)\b\Q*\E\b" "сно́ска"
*"(?i)\b\Q1 курса\E\b" "1-го курса"
*"(?i)\b\Q171 группы\E\b" "171-ой группы"
*"(?i)\b\Q1977\E\b" "1977-ой"
*"(?i)\b\QAcapela\E\b" "Акапэ́'ла"
*"(?i)\b\QBIOS\E\b" "БИ́“О́С"

*"(^| )(Д|д)-р" " доктор"
"(^| )(Г|г)-н" " господин"
*"(\d+)\s?-\s?я\b(?# ""я"" на границе слова)" "$1-я "
```
## Пропускати обрізані області в документах PDF
> Дуже часто сторінки в PDF-файлах (книги, статті в журналах, підручники тощо) мають верхні та нижні колонтитули, які проходять по всьому документу. Ви можете обрізати головки, що бігають, щипком двома пальцями, що перейде на наступні (і попередні) сторінки. Але ваш двигун TTS не має уявлення про ваші маніпуляції. Отже, вам потрібно сказати йому, що робити (Пропустіть дратівливу річ!), читаючи документ вголос.

У **Librera** ми ввели спеціальні заміни (команди), які дозволять вам ігнорувати обрізані ділянки та забезпечувати безперервне безперервне читання.
*У вікні **Заміни** введіть слово або послідовність слів у лівому стовпці та _ttsSKIP_ як його заміну. Ця заміна скаже двигуну пропустити речення з цією послідовністю слів/слів
*Введіть слово або послідовність слів у лівий стовпець і _ttsNEXT_ як його заміну. Заміна скаже двигуну пропустити речення з цією послідовністю слів/слів і негайно перейти до наступної сторінки
*Не забудьте натиснути кнопку _APPLY_, щоб заміни залишилися в силі

|4|5|
|-|-|
|![](4.png)|![](5.png)|

> **Перевірте зміни кілька разів, щоб переконатися, що все працює належним чином!**

## Прочитайте абревіатуру як вона є

Іноді абревіатура TTS читається неправильно, ми можемо допомогти їй читати як є.
```
"*(\w). (\p{javaLowerCase})" "$1 $2"
```
