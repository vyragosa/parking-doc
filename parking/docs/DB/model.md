---
title: ERD
sidebar_position: 1
---

# Модель данных

import Drawio from '@theme/Drawio'
import diagram from '!!raw-loader!./model.drawio';

<Drawio content={diagram} editable={false} />

# ERD

## Таблицы и их атрибуты

---

### Parking Type

| Название        | Тип     | Описание                               | Примечание          |
| --------------- | ------- | -------------------------------------- | ------------------- |
| parking_type_id | int     | Уникальный идентификатор типа парковки | Первичный ключ (PK) |
| parking_type    | varchar | Название типа парковки                 |                     |

---

### Parking Space

| Название         | Тип     | Описание                                           | Примечание          |
| ---------------- | ------- | -------------------------------------------------- | ------------------- |
| parking_space_id | int     | Уникальный идентификатор парковочного пространства | Первичный ключ (PK) |
| parking_type_id  | int     | Ссылка на тип парковки                             | Внешний ключ (FK)   |
| description      | varchar | Описание парковочного пространства                 |                     |
| location         | varchar | Локация парковочного пространства                  |                     |

---

### Parking Space Status

| Название        | Тип     | Описание                               | Примечание          |
| --------------- | ------- | -------------------------------------- | ------------------- |
| space_status_id | int     | Уникальный идентификатор статуса места | Первичный ключ (PK) |
| space_status    | varchar | Описание статуса (занято, свободно)    |                     |

---

### Parking Zone

| Название         | Тип     | Описание                                  | Примечание          |
| ---------------- | ------- | ----------------------------------------- | ------------------- |
| parking_zone_id  | int     | Уникальный идентификатор парковочной зоны | Первичный ключ (PK) |
| parking_space_id | int     | Ссылка на парковочное пространство        | Внешний ключ (FK)   |
| description      | varchar | Описание зоны                             |                     |
| location         | varchar | Локация парковочной зоны                  |                     |

---

### Parking Spot

| Название          | Тип     | Описание                                    | Примечание          |
| ----------------- | ------- | ------------------------------------------- | ------------------- |
| parking_spot_id   | int     | Уникальный идентификатор парковочного места | Первичный ключ (PK) |
| spot_status_id    | int     | Ссылка на статус парковочного места         | Внешний ключ (FK)   |
| parking_spot_type | int     | Ссылка на тип парковочного места            | Внешний ключ (FK)   |
| name              | varchar | Имя или идентификатор места                 |                     |
| description       | varchar | Описание места                              |                     |

---

### Parking Spot Status

| Название       | Тип     | Описание                                   | Примечание          |
| -------------- | ------- | ------------------------------------------ | ------------------- |
| spot_status_id | int     | Уникальный идентификатор статуса места     | Первичный ключ (PK) |
| spot_status    | varchar | Описание статуса (занято, свободно и т.д.) |                     |

---

### Parking Spot Type

| Название          | Тип     | Описание                               | Примечание          |
| ----------------- | ------- | -------------------------------------- | ------------------- |
| parking_spot_type | int     | Уникальный идентификатор типа места    | Первичный ключ (PK) |
| parking_spot_type | varchar | Тип места (например, стандартное, VIP) |                     |

---

### Reservation

| Название              | Тип      | Описание                                        | Примечание          |
| --------------------- | -------- | ----------------------------------------------- | ------------------- |
| reservation_id        | int      | Уникальный идентификатор бронирования           | Первичный ключ (PK) |
| start_time            | datetime | Время начала бронирования                       |                     |
| end_time              | datetime | Время окончания бронирования                    |                     |
| creation_date         | datetime | Дата создания бронирования                      |                     |
| car_number            | varchar  | Номер машины                                    |                     |
| user_id               | int      | Ссылка на пользователя, сделавшего бронирование | Внешний ключ (FK)   |
| parking_spot_id       | int      | Ссылка на парковочное место                     | Внешний ключ (FK)   |
| reservation_status_id | int      | Ссылка на статус бронирования                   | Внешний ключ (FK)   |

---

### Reservation Status

| Название              | Тип     | Описание                                       | Примечание          |
| --------------------- | ------- | ---------------------------------------------- | ------------------- |
| reservation_status_id | int     | Уникальный идентификатор статуса               | Первичный ключ (PK) |
| status                | varchar | Статус бронирования (активно, отменено и т.д.) |                     |

---

### Notification

| Название        | Тип      | Описание                             | Примечание          |
| --------------- | -------- | ------------------------------------ | ------------------- |
| notification_id | int      | Уникальный идентификатор уведомления | Первичный ключ (PK) |
| reservation_id  | int      | Ссылка на бронирование               | Внешний ключ (FK)   |
| header          | varchar  | Заголовок уведомления                |                     |
| body            | varchar  | Текст уведомления                    |                     |
| send_date       | datetime | Дата и время отправки уведомления    |                     |

---

### User

| Название       | Тип     | Описание                              | Примечание          |
| -------------- | ------- | ------------------------------------- | ------------------- |
| user_id        | int     | Уникальный идентификатор пользователя | Первичный ключ (PK) |
| identifier     | varchar | Идентификатор пользователя            |                     |
| role_id        | int     | Ссылка на роль пользователя           | Внешний ключ (FK)   |
| car_identifier | varchar | Номер машины пользователя             |                     |

---

### Role

| Название      | Тип     | Описание                      | Примечание          |
| ------------- | ------- | ----------------------------- | ------------------- |
| role_id       | int     | Уникальный идентификатор роли | Первичный ключ (PK) |
| permission_id | int     | Ссылка на разрешение          | Внешний ключ (FK)   |
| role_name     | varchar | Название роли                 |                     |
| description   | varchar | Описание роли                 |                     |

---

### Permission

| Название               | Тип     | Описание                            | Примечание          |
| ---------------------- | ------- | ----------------------------------- | ------------------- |
| permission_id          | int     | Уникальный идентификатор разрешения | Первичный ключ (PK) |
| permission_name        | varchar | Название разрешения                 |                     |
| permission_description | varchar | Описание разрешения                 |                     |