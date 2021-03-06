## Телеграм-бот
**Описание**

Телеграм-бот. Данный бот был создан, для того, чтобы пользователи могли следить за своим самочувствием сразу в нескольких удобных для них форматах, ведь для кого-то просто таблица с данными может быть гораздо удобней и информативней, чем построенные графики. Также Телеграм-бот поможет в целом следить за здоровьем абсолютно всем группам лиц, которым это необходимо или просто интересно, также можно следить за своим состоянием после тренировок, если Вы спортсмен. С точки зрения непосредственно работы с данным ботом, то пользователь может с ним общаться исключительно нажатием кнопок, но при большом желании может писать и сам, если пользователю что-то не понятно, то он может это всегда прочитать в инструкции. Бот реализован на языке python.

**Тестирование бота**

Заходя в переписку с ботом, на главном экране, пользователь видит 4 основные кнопки, каждую со своим уникальным функционалом, в соответствии с рисунком 1.
 
 ![image](https://user-images.githubusercontent.com/75118943/178711836-783905e6-75df-429d-8ee9-bb87fa473928.png)

Рисунок 1 – Основные кнопки

Если пользователь первый раз пользуется ботом, то он скорее всего нажмет на кнопку «Инструкция», чтобы узнать зачем нужен этот бот и какие кнопки в какой момент надо нажимать, чтобы добиться необходимого результата в соответствии с рисунком 2.
 
 ![image](https://user-images.githubusercontent.com/75118943/178711763-3bea5009-ea87-4d61-84ae-de8f9f1d3b04.png)

Рисунок 2 – Кнопка «Инструкция»

У пользователя может возникнуть такая ситуация, что нижние кнопки куда-то пропадут и видны не будут, тогда он не будет понимать, что происходит и попробует отправить какое-то сообщение и получит рекомендации к действию в соответствии с рисунком 3.
 
 ![image](https://user-images.githubusercontent.com/75118943/178711483-91ba1275-546d-4991-8fa2-1e61f9c1239b.png)
 
Рисунок 3 – Непонятное сообщение

После того, как пользователь прочитал инструкцию и во всем разобрался, он пытается занести свои данные в таблицу, нажимая на кнопку «Ввести данные». Далее он видит перед собой несколько новых инлайн-кнопок с разными темами и ему необходимо нажать на ту кнопку, о состоянии чего он хочет занести данные в таблицу в соответствии с рисунком 4. После нажатия кнопки пользователь видит еще некоторое количество инлайн-кнопок и нажатием на одну из них определяет конкретное состояние той части тела, которое было выбрано предыдущей кнопкой, после выбора непосредственно состояния данные заносятся в файл в соответствии с рисунком 5. В самом файле формата .csv автоматически определяется время сообщения с датой, а также атмосферное давление и температура в Санкт-Петербурге в соответствии с рисунком 6.
 
 ![image](https://user-images.githubusercontent.com/75118943/178711317-3a412cb1-7b6b-41be-99fb-9c44f077da08.png)
 
Рисунок 4 – Выбор кнопки «Ввести данные»
 
 ![image](https://user-images.githubusercontent.com/75118943/178711272-a527180b-a677-46af-8137-57469c3138eb.png)
 
Рисунок 5 – Непосредственная оценка состояния
 
 ![image](https://user-images.githubusercontent.com/75118943/178709938-7b27f4dc-564e-43c3-9f5f-d0ff32d8572c.png)
 
Рисунок 6 – Файл формата .csv

Заполняя определенное время свои данные и общаясь с ботом, пользователь может узнать отчет по своему состоянию за данный период, для этого, следуя инструкции, ему необходимо нажат на кнопку «Прислать мне отчет», после чего ему придет файл формата .csv и два графика зависимости самочувствия от температуры и от атмосферного давления в соответствии с рисунком 7.

 ![image](https://user-images.githubusercontent.com/75118943/178710166-04f51c1e-3fb1-4b66-a3cb-41a0e2dffeeb.png)
 
Рисунок 7 – Кнопка «Прислать мне отчет»

Также, в случае если, пользователь захочет начать бот заново, заполнять новую таблицу и забыть все старые данные, он должен нажать на кнопку «Сделать таблицу пустой» и тогда файл формата .csv станет пустым и его можно будет заполнять заново в соответствии с рисунком 8.

![image](https://user-images.githubusercontent.com/75118943/178709485-ef13766b-9451-4a67-b556-cb9fcaeac14f.png)

Рисунок 8 – Пустой файл формата .csv
