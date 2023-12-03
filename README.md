# <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">Вопросы: Неделя 2!<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
# Содержание

- [RecyclerView](#recyclerview)
  - [Разница от ListView?](#разница)
  - [Чем отличается LinearLayout от RecycleView если оба использовать как отображение списка?](#чем-отличается-linearlayout-от-recycleView-если-оба-использовать-как-отображение-списка?)
  - [Паттерны Adapter и ViewHolder](#Паттерны-Adapter-и-ViewHolder)
  - [diffutil](#diffutil)
  - [delegate RV](#delegate-RV)
  - Server Driven UI
- [Fragments](#fragments)
- Что такое фрагмент(фраг может исполь в нескольких фрагмертами)?
- Жизненный цикл фрагмента
- Как передаются параметры между фрагментами через ViewModel? (LifeData получить и запасить) Один отслеживает данные, второй получив эту LifeDat
- Расскажите про способы добавления и переключения фрагментов. Как работать с бэкстэком?
- Как передать параметры в конструктор фрагменты?
- Почему нельзя передавать параметры через конструктор фрагмента?
- Метод FragmentManager.commit() – синхронный или нет?
- обязан ли фрагмент layout?(нет)
- Как получить ссылку на фрагмент из активити?
- Чем отличается tag в методах add() и addToBackStack()?
- Как правильно подписываться на LiveData во фрагментах?
- Как определить скрыт ли на данный момент фрагмент?
- Фрагмент является налседником Context?(не является)
- Для чего нужен метод Fragment.setRetainInstance()?
- Что происходит с фрагментом при повороте экрана?
- что делает метод  popBackStack()?
- Fragment Result Api -
- inLine, crossLine,noinline
- Вместо объектов будет тот код, который мы указали
- Модификатор crossinline используется для указания того, что лямбда-выражение не может содержать операторы return, даже если функция, принимающая лямбда-выражение, инлайновая.
- Модификатор noinline, с другой стороны, указывает на то, что лямбда-выражение может быть сохранено как объект функции, а не выполнено внутри вызывающей функции. Это может быть полезно в случае, когда вы хотите использовать лямбда-выражение где-то ещё, например, как параметр для другой функции.

- @AttrRes
- Стерание типов при компиляции почитать
- Ограничение ЖЦ у фрагмента
- MultiBackStack
- Communication with fragments
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

[Содержание](#содержание)

### Разница от ListView?
RecyclerView и ListView используются в Android для отображения прокручиваемого списка элементов. Однако между ними есть несколько ключевых различий.

+ Переработка представления. RecyclerView использует шаблон держателя представления для переработки и повторного использования представлений, что может повысить производительность и уменьшить объем памяти, используемой приложением. ListView по умолчанию не перерабатывает представления  —  для этого его необходимо настроить вручную.

+ Менеджер макетов. RecyclerView включает гибкий менеджер макетов, который позволяет задать расположение элементов в списке, например сетку и линейный макет. ListView использует фиксированный макет, где все элементы отображаются в виде вертикального списка.

+ Декорирование элементов. RecyclerView включает поддержку добавления художественного оформления к элементам списка, например разделителей и фонов элементов. ListView не обладает встроенной поддержкой художественного оформления.

+ Изменения данных. RecyclerView включает поддержку уведомления адаптера об изменениях данных, что позволяет обновлять список в режиме реального времени. ListView не обладает встроенной поддержкой изменений данных: об изменениях необходимо уведомлять вручную.

Выбор между RecyclerView и ListView зависит от конкретных потребностей приложения и типа списка, который нужно отобразить. RecyclerView обеспечивает большую гибкость и улучшает производительность, но требует больше кода для реализации, в то время как ListView проще в использовании, но имеет меньше возможностей.

[Содержание](#содержание)

### Чем отличается LinearLayout от RecycleView если оба использовать как отображение списка? 
-в LinearLayout можно установить ориентацию содержимого, делая таким образом содержимое статичным. Это означает, что содержимое страницы не перемещается и не прокручивается. 
-RecycleView используется для списков и представлений с прокруткой.

[Содержание](#содержание)

### Как можно прокручивать LinearLayout?
Его необходимо положить в ScrollView.

[Содержание](#содержание)

### Какие минусы такого подхода?
Файд xml не является view элементом, по этому что бы работать с ним из кода, необходимо использовать `LayoutInflater`. Это такой класс, который из макета умеет создавать `view`.
inflate - очень ресурсозатратная операция. Она выполняется долго. А она будет вызываться столько раз, сколько у нас элементов в списке.
findViewById - Вызывается каждый раз для одного элемента. .в результате если у нас несколько View в одном layout, то данный метод будет вызываться дважды. Элементов 10 000, то он 
вызовится 20 000 раз. Нужно вызывать для каждой  View столько раз, сколько у нас есть элементов в списке. В результате образуются задержки во премя скрола, и приложение может 
зависнуть и выйдет ошибка Applicatinon is not responding.
При обнавлении всего одного элемента, придется обнавлть весь список. 
Почему это происходит?
Когда мы получаем новый список у нас создаются view элементы обсалютно для каждого объекта в нашей коллекции. 
```kotlin
private lateinit var llShopList: LinearLaout

private fun showList(list: List(ShopItem>){
  for(shopItem in list){
    val layoutId = shopItem.layoutName
    val view = LayoutInflater.from(this).inflate(layout_Id, llShopList, Boolean(прикреплять ли к родителю)
    val tvName = view.findViewById
    val tvLast_Name = view.findViewById
    llShopList.addView(view)
}
```
[Содержание](#содержание)

###  Как работает RecyclerView?
Решили сделать так. Если пользователь видит 10 элементов, то нет необходимости создавать сразу все view. Достаточно отобразить определенное количество для 
заполнения экрана плюс несколько штук сверху и снизу, для того что бы при скроле небыло видно лагов. При скроле неискользуемые view будут перемещаться вниз 
и им будут установлены новые значения в зависимости от того объекта который появляется на экране. 
По этому для работы с RecyclerView нам нужен объект который скажет
- как нам создавать View
- как устанавливать значения внутри View 
Этим объектом является `Adapter`.

[Содержание](#содержание)


### Жизненный цикл фрагмента
<h3 align="center"><strong>Fragment Lifecycles</strong></h3>
<p align="center">
  <img src="https://developer.android.com/static/images/guide/fragments/fragment-view-lifecycle.png" weight = "20" alt="Preview">
</p>

Часть методов жизненного цикла фрагмента аналогична методам жизненного цикла активити.

Методы жизненного цикла фрагмента в порядке вызова:

`onAttach()` – Вызывается когда фрагмент присоединяется к активити.

`onCreate()` – Вызывается когда фрагмент создается.

`onCreateView()` – Метод, в котором создается иерархия View, связанная с фрагментом.

`onActivityCreated()` – Вызывается после того, как отрабатывает метод Activity.onCreate().

`onViewStateRestored()` – Вызывается, когда состояние иерархии View восстановлено.

`onStart()` – Вызывается, когда фрагмент становится видим пользователю, после Activity.onStart().

`onResume()` – Вызывается перед тем как фрагмент станет доступен для взаимодействия с пользователем, после Activity.onResume().

`onPause()` – Пользователь не может взаимодействовать с фрагментом, но часть фрагмента видима пользователю.

`onStop()` – Фрагмент становится не видим пользователю.

`onDestroyView()` – Метод, в котором фрагмент очищает ресурсы, связанные с иерархией View.

`onDestroy()` – Вызывается перед тем, как фрагмент будет уничтожен системой.

`onDetach()` – Вызывается перед тем, как фрагмент будет отсоединен от активити.

Когда фрагмент удаляется методом `remove()` или `replace()` и транзакция добавляется в back stack, то у удаленного фрагмента вызывается onStop() и не вызывается `onDestroy()`. Если пользователь нажимает Back, то транзакция откатывается и у фрагмента вызывается `onStart()`.
Если же транзакция не добавляется в back stack, то у удаленного фрагмента вызывается `onDestroy()`. 

[Содержание](#содержание)

### Для чего нужен метод Fragment.setRetainInstance()?

Метод `setRetainInstance()` принимает boolean параметр. По умолчанию значение retainInstance фрагмента – false. 
Если retainInstance выставлен в true, то фрагмент переживает пересоздание хост-активити, например при повороте экрана.

Когда активити пересоздается, фрагмент с retainInstance=true отсоединяется от старой активити и присоединяется к новой. Поэтому при пересоздании 
активити у фрагмента не вызываются методы `onDestroy()` и `onCreate()`, но вызываются `onDetach()`, `onAttach()` и `onActivityCreated()`.

`setRetainInstance()` может быть использован только на фрагментах, не добавленных в backstack

[Содержание](#содержание)


### Расскажите про способы добавления и переключения фрагментов. Как работать с бэкстэком?

Для управления фрагментами используются два класса: FragmentManager и FragmentTransaction.

Для получения FragmentManager используются метод активити getSupportFragmentManager() или метод фрагмента getChildFragmentManager().
FragmentManager начинает транзакцию и возвращает объект FragmentTransaction вызовом метода beginTransaction().

Методы класса FragmentTransaction, которые необходимо знать - add(), remove() и replace().

add() добавляет фрагмент на активити или другой фрагмент. Принимает аргументами containerViewId, в который добавляется фрагмент, инстанс фрагмента, тег.
Другой способ добавить фрагмент - определить в лэйауте с помощью тега <fragment>.

remove() - операция, обратная add(). Удаляет фрагмент.

replace() удаляет все фрагменты, добавленные методом add() в заданный контейнер, и добавляет переданный аргументом фрагмент в контейнер. Параметр tag может быть null.

Эти операции не выполняются сразу же после вызова методов. Метод commit() завершает транзакцию и выполняет операции транзакции.

Метод addToBackStack() добавляет транзакцию в Back Stack. Это значит, что когда пользователь нажмет Back транзакция откатится. addToBackStack() применяется ко всем 
операциям в транзакции. Например следующий код добавляет транзакцию из трех операций в бэкстэк:

fragmentTransaction
.add(R.id.fragmentContainer1, fragment1)
.add(R.id.fragmentContainer2, fragment2)
.replace(R.id.fragmentContainer1, fragment3)
.addToBackStack("tag")
.commit()

Метод popBackStack() удаляет транзакцию с верхушки бэкстэка, возвращает true, если бэкстэк хранил хотя бы одну транзакцию.

[Содержание](#содержание)


### Как получить ссылку на фрагмент из активити?

Отвечая на этот вопрос, не рассказывайте, пока не спросят, об использовании в активити объекта List<MyFragment>, в который вы добавляете фрагменты при вызове onAttach() и 
удаляете в onDetach(). Интервьюер хочет услышать знаете ли вы стандартные методы API.

Системное API предоставляет два метода для поиска и получения фрагмента внутри активити: findFragmentByTag() и findFragmentById().

findFragmentByTag() принимает параметром тег, который передается в методе add() или replace() или в XML в элементе <fragment>. Возвращает null, если фрагмент не найден.

findFragmentById() принимает параметром id фрагмента. Если фрагмент добавляется методом add() или replace(), то id фрагмента – это id контейнера, который передается 
первым параметром. В случае добавления фрагмента через XML, id задается в элементе <fragment>. findFragmentById() возвращает null, если фрагмент не найден.

[Содержание](#содержание)

### Отличие fragment от activity?

-  Фрагмент не может запустить приложение, точка входа
-  для отображения нужна активити
-  фрагмент можно создать напрямую, в отличии от activity

[Содержание](#содержание)

###

###
###
###
###
###
###
###
###
###
###
###
###
###
###
