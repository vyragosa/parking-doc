---
title: UC
sidebar_position: 1
---

# Сценарий бронирования парковочного места

```plantuml
@startuml
actor Сотрудник
package "Информационная система управления офисной парковкой"  {
  usecase "Забронировать парковочное место" as UC1
  usecase "Посмотреть карту парковочных мест" as UC2
  usecase "Представить места в виде списка" as UC3
  usecase "Посмотреть только свободные парковочные места" as UC4
  usecase "Посмотреть информацию о периоде занятости места" as UC5
  usecase "Осуществить поиск по месту" as UC6
  usecase "Указать время парковки" as UC7
  usecase "Указать парковочное место" as UC8
}
Сотрудник --> UC1
Сотрудник --> UC2

UC1 --> UC7 : <<include>>
UC1 --> UC8 : <<include>>
UC1 <-- UC5 : <<extend>>

UC2 <-- UC3 : <<extend>>
UC2 <-- UC6 : <<extend>>
UC3 <-- UC4 : <<extend>>

@enduml
```

---

1. Сотрудник начинает процесс бронирования через интерфейс системы.
2. Система предоставляет доступ к следующим функциям:
   - Просмотр карты парковочных мест.
   - Фильтрация мест (свободные, занятые).
   - Указание временных интервалов.
3. Система проверяет доступность выбранного места.
4. Если место доступно:
   - Система подтверждает бронирование.
   - Сотруднику отправляется подтверждение.
5. Если место недоступно:
   - Система сообщает об отсутствии доступного места.