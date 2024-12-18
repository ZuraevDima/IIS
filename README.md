<h2 align="center"><i>Первое задание</i></h2>
<h4 align="center">user stories and usecase</h4>

<p align="center"><i>User stories</i></p>
<h6><b>Я, как , хочу иметь возможность </b></h6>
<ol>
    <li>Я, как отец грудного ребенка, хочу воспользоваться услугой деликатной отмывки сидений от различных пятен, чтобы отмыть хорошо машину.</li>
    <li>Я, как астматик, хочу иметь возможность посидеть в отдельной комнате, чтобы не дышать пылью и грязью</li>
    <li>Я, как бедный студент, хочу иметь возможность получения скидки для определенной категории граждан, чтобы сэкономить деньги </li>
    <li>Я, как владелец большой собаки, хочу иметь возможность в отчистке салона от шерсти, чтобы шерсть не прилеплялась к вещам моих пассажиров.</li>
    <li>Я, как пользователь приложения записи на автомойку, хочу чтобы оно было адаптировано под экран моего устройства, независимо от его размера и форм факторов</li>
    <li>Я, как владелец мопеда, хочу иметь возможность выбора типа транспортного средства, чтобы не переплачивать за услугу</li>
    <li>Я, как клиент, хочу иметь возможность получить уведомление о завершении мойки, чтобы знать когда забрать машину</li>
    <li>Я, как иностранный гражданин, хочу иметь возможность выбора нескольких языков в приложении записи на автомойку, чтобы точно не ошибиться при вводе данных</li>
    <li>Я, как не местный житель, хочу видеть в приложении карту с автомойкой, чтобы без проблем до неё добираться</li>
    <li>Я, как предприниматель, хочу иметь доступ к интернету во время мойки, чтобы не отвлекаться от дел в случае плохого соединения.</li>
</ol>

### <p align="center"><i>Usecase</i></p>
<table border="1">
  <tbody>
    <tr>
      <th>Название</th>
      <td>Запись на автомойку</td>
    </tr>
    <tr>
      <th>Описание</th>
      <td>Клиент может выбрать и забронировать услугу мойки машины на нужное ему время, используя онлайн-систему записи</td>
    </tr>
    <tr>
      <th>Акторы</th>
      <td>Клиент</td>
    </tr>
    <tr>
      <th>Предусловия</th>
      <td>Клиент зашёл в приложение по автомойке</td>
    </tr>
    <tr>
      <th>Основной поток событий</th>
      <td>
        <ol>
            <li>Клиент выбирает дату и время на запись</li>
            <li>Система отображает список доступных временных слотов для записи на автомойку</li>
            <li>Клиент выбирает нужный ему слот</li>
            <li>Система запрашивает у клиента информацию о мойке машины</li>
            <li>Клиент вводит информацию о мойке машины</li>
            <li>Система отображает информацию о стоимости мойки</li>
            <li>Клиент подтверждает бронирование и оплачивает</li>
        </ol>
      </td>
    </tr>
    <tr>
      <th>Альтернативный поток событий</th>
      <td>
        <ol>
            <li>На шаге 2 система не отображает список доступных временных слотов</li>
            <li>Клиент изменяет дату записи</li>
            <li>Система отображает новый список доступных слотов</li>
            <li>Клиент продолжает запись</li>
        </ol>
      </td>
    </tr>
    <tr>
      <th>Постусловия</th>
      <td>Клиент успешно забронировал временной слот на мойку и получил подтверждение о записи</td>
    </tr>
    <tr>
      <th>Расширенные атрибуты</th>
      <td>
        <ol>
            <li>Если клиент вводит неверные данные, система сообщает об ошибке и предлагает исправить их</li>
            <li>Клиент не вводит никакой информации о мойке машины, и принимаются данные по умолчанию</li>
        </ol>
      </td>
    </tr>
    <tr>
      <th>Диаграмма usecase</th>
      <td>
      <img src="uc1.PNG" alt="usecase1" width="400">
      <img src="uca.PNG" alt="usecase_new" width="400"></td>
    </tr>
    <tr>
      <th>Рекомендации по реализации</th>
      <td>
        <ol>
            <li>Реализовать удобный и интуитивно понятный интерфейс для ввода данных клиентом.</li>
            <li>Отобразить доступные временные слоты на мойку в удобном для клиента виде</li>
        </ol>
      </td>
    </tr>
  </tbody>
</table>
### <p align="center"><i>ERD</i></p>


```plaintext
Table Clients{
	id integer [primary key]
	full_name varchar
	phone_number varchar
	brand_of_the_car varchar
        dimensions_of_the_machine varchar
}

Table Car_washes{
	id integer [primary key]
	longitude float
	latitude float
	service set
}
Table Records {
       id integer [primary key]
client_id integer
car_washes_id integer
service_id integer
cost decimal
date_time datetime
payment bool
}

Table Services {
id integer [primary key]
title varchar
price decimal
}


```


<img src="erd.PNG" alt="erd" width="700" height="300">
<hr>
### <p align="center"><i>C4 model</i></p>

```plaintext
@startuml
class Clients {
  - id: Integer [PK]
  - full_name: String
  - phone_number: String
  - brand_of_the_car: String
  - dimensions_of_the_machine: String
}

class Car_washes {
  - id: Integer [PK]
  - longitude: Float
  - latitude: Float
    - services: Set<Service>
}

class Records {
  - id: Integer [PK]
  - client_id: Integer [FK]
  - car_washes_id: Integer [FK]
  - service_id: Integer [FK]
  - cost: Decimal
  - date_time: DateTime
  - payment: Boolean
}

class Services {
  - id: Integer [PK]
  - title: String
  - price: Decimal
}

Clients "1" -- "0..*" Records : has records >
Clients "1" *-- "0..*" Records: client (FK: client_id) >
Car_washes "1" -- "0..*" Records : has records >
Car_washes "1" *-- "0..*" Records: car_wash (FK: car_washes_id) >
Services "1" -- "0..*" Records : has records >
Services "1" *-- "0..*" Records: service (FK: service_id) >

Car_washes "1" *-- "0..*" Services : has services>

@enduml
```

<img src="c4.png" alt="c4_model_pic">
