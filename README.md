# Учим слова с ботов

### Логика

У бота есть словарик по которому пользователь учит слова. <br>
Проверяет слова бот не просто так, а при помощи рандома с весами
<code>word = (random.choices(words, weights=weight))</code>
То есть значение весов <code> weight</code> для каждого слова это не что иное как процентная вероятность, с которым бот покажет это слово.
Чем труднее слово запоминается - тем чаще показываем.

### Линейная регрессия

Для определения вероятности выдачи слова я выделил факторы<br>
x1 - сложность слова <br>
x2 - правильных ответов подряд<br>
x3 - время ответа (перевода)<br>
x4 - процент правильно отвеченных<br>

Получается <code> weight = w0 + w1x1 + w2*x2 + w3*x3 + w4*x4</code><br><br>

Сложность слова <code>x1</code> я также считал при помощи линейной регрессии <br>
<code>hard_value = v0 + v1*y1 + v2*y2</code> <br>
y1 - длина слова<br>
y2 - наличие сложных "буквосочетаний"<br>

Есть идея добавить произведение этих параметров и также добавить параметр y3 - частота употребления слова
