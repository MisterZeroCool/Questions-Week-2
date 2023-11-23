# <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">Вопросы: Неделя 2!<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
- [RecyclerView](#recyclerview)
  - [Разница от ListVist?](#разница-от-listview?)
  - [Чем отличается LinearLayout от RecycleView если оба использовать как отображение списка?](#чем-отличается-linearlayout-от-recycleView-если-оба-использовать-как-отображение-списка?)
  - [Паттерны Adapter и ViewHolder](#Паттерны-Adapter-и-ViewHolder)
  - [diffutil](#diffutil)
  - [delegate RV](#delegate-RV)
- [Fragments](#fragments)
- [FragmentManager](#FragmentManager)


# RecyclerView<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
### Назначение и ключевые функции Android RecyclerView и почему это важно для разработки современных приложений для Android??

Android RecyclerView — это компонент пользовательского интерфейса, предназначенный для эффективного отображения больших наборов данных. Он повышает производительность за счет повторного использования представлений, уменьшения использования памяти и увеличения скорости прокрутки.


### Основные компоненты RecyclerView?
Для корректной работы RecyclerView необходимо реализовать следующие компоненты:

+ RecyclerView, который необходимо добавить в макет нашего Activity;

+ Adapter, который содержит, обрабатывает и связывает данные со списком;

+ ViewHolder, который служит для оптимизации ресурсов и является своеобразным контейнером для всех элементов, входящих в список;

+ ItemDecorator, который позволяет отрисовать весь декор;

+ ItemAnimator, который отвечает за анимацию элементов при добавлении, редактировании и других операций;

+ DiffUtil, который служит для оптимизации списка и добавления стандартных анимаций.

### Разница от ListView?
RecyclerView и ListView используются в Android для отображения прокручиваемого списка элементов. Однако между ними есть несколько ключевых различий.

+ Переработка представления. RecyclerView использует шаблон держателя представления для переработки и повторного использования представлений, что может повысить производительность и уменьшить объем памяти, используемой приложением. ListView по умолчанию не перерабатывает представления  —  для этого его необходимо настроить вручную.

+ Менеджер макетов. RecyclerView включает гибкий менеджер макетов, который позволяет задать расположение элементов в списке, например сетку и линейный макет. ListView использует фиксированный макет, где все элементы отображаются в виде вертикального списка.

+ Декорирование элементов. RecyclerView включает поддержку добавления художественного оформления к элементам списка, например разделителей и фонов элементов. ListView не обладает встроенной поддержкой художественного оформления.

+ Изменения данных. RecyclerView включает поддержку уведомления адаптера об изменениях данных, что позволяет обновлять список в режиме реального времени. ListView не обладает встроенной поддержкой изменений данных: об изменениях необходимо уведомлять вручную.

Выбор между RecyclerView и ListView зависит от конкретных потребностей приложения и типа списка, который нужно отобразить. RecyclerView обеспечивает большую гибкость и улучшает производительность, но требует больше кода для реализации, в то время как ListView проще в использовании, но имеет меньше возможностей.

### Чем отличается LinearLayout от RecycleView если оба использовать как отображение списка? 
-в LinearLayout можно установить ориентацию содержимого, делая таким образом содержимое статичным. Это означает, что содержимое страницы не перемещается и не прокручивается. 
-RecycleView используется для списков и представлений с прокруткой.
