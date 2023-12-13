# <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">Вопросы: Неделя 2!<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
# Содержание

- [RecyclerView](#recyclerview)
  - [AV Назначение и ключевые функции Android RecyclerView и почему это важно для разработки современных приложений для Android?](#av)
  - [AV asd](#av_asd)    
  - [Разница от ListView?](#разница)
  - [Чем отличается LinearLayout от RecycleView если оба использовать как отображение списка?](#чем-отличается-linearlayout-от-recycleView-если-оба-использовать-как-отображение-списка?)
  - [Паттерны Adapter и ViewHolder](#Паттерны-Adapter-и-ViewHolder)
  - [diffutil](#diffutil)
  - [delegate RV](#delegate-RV)
  - Server Driven UI
  - 
  
- [Fragments](#fragments)

   - [Q1](#q1) Что такое фрагмент и для чего он нужен?
   - [Q2](#q2) Как создать Fragment?
   - [Q3](#q3) Расскажите что такое `FragmentManager`?
   - [Q4](#q4) Расскажите про способы добавления и переключения фрагментов.
   - [Q5](#q5) Расскажите какие методы есть у класса `FragmentTransaction`.
   - [Q6](#q6) Как работать с бэкстэком?
   - [Q7](#q7) Как отобразить фрагмент на `Activity`?
   - [Q8](#q8) Как получить ссылку на фрагмент из `Activity`?
   - [Q9](#q9) Завершающие методы `FragmentTransaction`.
   - [Q10](#q10) Что за методы `parentFragmentManager`, `childFragmentManager`?
   - [Q11](#q11) Опишите жизненный цикл фрагмента
   - [Q12](#q12) FragmentResultApi
   - [Q13](#q13) Как организовать взаимодействие `Activity` и `Fragment`?
   - [Q14](#q14) Как передать параметры во `Fragment`?
   - [Q15](#q15) 
   - [Q16](#q16)
   - [Q17](#q17)
   - [Q18](#q18) 
   - [Q19](#q19) 
   - [Q20](#q20) Что происходит с фрагментом при повороте экрана?
   - [Q21](#q21) Для чего нужен метод `Fragment.setRetainInstance()`?
 






# RecyclerView<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">

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


# Fragments
 
 ### Q1<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px"> 
 ### Что такое фрагмент и для чего он нужен?

`Fragment` —  используется для отображения части UI на экране. Фрагмент создается внутри активити или внутри другого фрагмента. Фрагмент является модульным компонентом и один и тот же фрагмент можно встроить в две разные активности. Класс-наследник класса Fragment должен иметь дефолтный конструктор без параметров. Система использует этот конструктор при пересоздании фрагмента.

[Содержание](#содержание)

 ### Q2<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Как создать Fragment?
 Чтобы создать `Fragment` необходимо создать класс наследующий `Fragment` и переопределить в нем метод `onCreateView`, или можно создать класс наследующий `Fragment AndroidX` и передать в базовый конструктор (конструктор родителя) ресурс макета (layout).

 ### Q3<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px"> 
 ### Расскажите что такое `FragmentManager`?
 Это класс, отвечающий за выполнение действий над фрагментами нашего приложения, таких как:

 - добавление
 - удаление
 - замена

 А также добавление их в backStack.

 ### Q4<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px"> 
 ### Расскажите про способы добавления и переключения фрагментов.

 Для управления фрагментами используются два класса: `FragmentManager` и `FragmentTransaction`.
 
- `supportFragmentManager` - это метод `Activity` используется для получения фрагмента.

- `getChildFragmentManager` - это метод `Fragment` используется для получения фрагмента.

`FragmentManager` начинает транзакцию и возвращает объект `FragmentTransaction` вызовом метода `beginTransaction()`.


 ### Q5<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Расскажите какие методы есть у класса `FragmentTransaction`.
- `add()`- добавляет фрагмент на активити или другой фрагмент.
- `remove()`- удаляет фрагмент.
- `replace()`- удаляет все фрагменты, добавленные методом `add()` в заданный контейнер, и добавляет переданный аргументом фрагмент в контейнер.
- `hide`- делает фрагмент невидимым.
- `show`- отображает фрагмент.

### Q6<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
### Как работать с бэкстэком?

-для работы с бэкстеком используются следующие методы:
- `addToBackStack`-добавляет транзакцию в Back Stack. Это значит, что когда пользователь нажмет Back, транзакция откатится. Применяется ко всем операциям в транзакции.
- `popBackStack`-удаляет транзакцию с верхушки бэкстэка, возвращает `true`, если бэкстэк хранил хотя бы одну транзакцию.

 ### Q7<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Как отобразить фрагмент на `Activity`?
 Для отображения фрагментов на `Activity`, ее макет должен иметь у себя `FragmentContainerView`, который будет служить контейнером фрагментов.

 В xml файле фрагмента назначаем `id` для нашей Activity:

 ```xml
 <androidx.constraintlayout.widget.ConstraintLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    android:id="@+id/host"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    app:layout_constraintBottom_toBottomOf="parent"
    app:layout_constraintEnd_toEndOf="parent"
    app:layout_constraintStart_toStartOf="parent"
    app:layout_constraintTop_toTopOf="parent"
    />
 ```

В классе `MainActivity` прописываем код для отображения фрагмента:

```kotlin
class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)
        supportFragmentManager
            .beginTransaction().apply {
                replace(R.id.host, MainScreenFragment())
            }.commit()
    }
}
```


- `beginTransaction` - это метод используется для добавления, замены или удаления фрагментов.

 ### Q8<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Как получить ссылку на фрагмент из `Activity`?

 Системное API предоставляет два метода для поиска и получения фрагмента внутри активити:
 - `findFragmentByTag()` принимает параметром тег, который передается в методе `add()` или `replace()` или в XML в элементе `FragmentContainerView`. 
 - `findFragmentById()` принимает параметром `id` фрагмента.

 ### Q9<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Завершающие методы `FragmentTransaction`

 - `commit` - добавляет транзакцию в очередь UI потока и транзакция выполняется при первой возможности. Является асинхронным, т.е. транзакция не выполняется во время вызова метода.
- `commitNow` - противоположность commit. Является синхронным, т.е. транзакция выполняется во время вызова метода. При работе с данным методом нельзя использовать `addToBackStack`.
- `commitAllowingStateLoss` - делает то же, что и метод `commit`, но говорит системе, что мы готовы к потере состояния и исключение бросать не нужно. Замалчивает, а не решает проблему. Является асинхронным. Не рекомендуется использовать.

 ### Q10<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Что за методы `parentFragmentManager`, `childFragmentManager`?

 - `parentFragmentManager` - `FragmentManager` родителя.
- `childFragmentManager` - `FragmentManager` текущего фрагмента.

 ### Q11<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Опишите жизненный цикл фрагмента

- Жизненный цикл Fragment
  - ![Жизненный цикл фрагмента](https://i.stack.imgur.com/fRxIQ.png)


## CREATED
- `onAttach()`–вызывается когда фрагмент присоединяется к активити. С этого момента мы можем получить ссылку на контекст.
- `onCreate()`–вызывается когда фрагмент создается. В этом методе можно получить сохраненное состояние savedInstanceState типа Bundle.
- `onCreateView()`–фрагмент создает представление (View). Устанавливается какой именно визуальный интерфейс будет у фрагмента.
- `onViewCreated()`–вызывается после создания представления фрагмента (view). В этом методе можно работать с элементами view.
- onViewStateRestored()`–позволяет получить состояние фрагмента.
## STARTED
- `onStart()`–вызывается, когда фрагмент становится видим пользователю, после `Activity.onStart()`.
## RESUMED
-`onResume()`–вызывается когда фрагмент становится доступен для взаимодействия с пользователем, после `Activity.onResume()`.
## PAUSED
-`onPause()`–пользователь не может взаимодействовать с фрагментом, но часть фрагмента видима пользователю.
## STOPED
- `onStop()`– фрагмент становится не видим пользователю.
- `onSaveInstanceState()`-позволяет сохранить состояние фрагмента. До API 28 вызывался до onStop, начиная с API 28 после onStop.
## DESTROYED
- `onDestroyView()` – уничтожает представление (view) фрагмента.
- `onDestroy()` – уничтожает фрагмент.
- `onDetach()` – вызывается, когда фрагмент удаляется из FragmentManager и открепляется от активити.

 ### Q12<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px"> 
 ### FragmentResultApi

 Функционал, который позволяет возвращать результат из фрагмента.
 - `setFragmentResult("requestKey",bundleOf("bundleKey" to result))` - метод для отправки результата в другой фрагмент
 - `setFragmentResultListener("requestKey"){_,bundle -> result=bundle.getString("bundleKey")}` - метод для получения результата из другого фрагмента.

Если оба фрагмента находятся в одном и том же FragmentManager, то мы должны использовать `parentFragmentManager`. Если у нас фрагмент вложен в другой фрагмент, то для передачи данных мы используем `childFragmentManager`. Важно понимать, что наш `FragmentResultListener` должен находиться в общем для двух фрагментов `FragmentManager`-е.

Если какой-либо фрагмент подписывается на результат методом `setFragmentResultListener` после того, как отправляющий фрагмент вызовет `setFragmentResult`, то он немедленно получит результат. Каждую связку `"Key+Result(Bundle)"` фрагмент получает только 1 раз. Фрагменты которые находятся в бек стеке получат результат только после того как перейдут в состояние `STARTED`. После того как фрагмент перейдет в состояние `DESTROYED` мы больше не сможем подписываться на `ResultListener`.

 ### Q13<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Multi-backstack
Используется для сохранения `backstack` при переходах между вкладками. Для работы необходимо:
- `setReorderingAllowed(true)`
- `FragmentTransaction.addToBackStack(String?)` - указать уникальные имена.
- под каждый `parentFragment` добавить таб (Tablayout) и при переходе внутри этих фрагментов, будем сохранять и восстанавливать `backstack`-и с помощью методов `saveBackStack(String)` и `restoreBackStack(String)`.
-имена, указанные в `saveBackStack` и `restoreBackStack`, должны совпадать с именами, указанными в `addToBackStack`. При вызове `saveBackStack`, `FragmentManager` проходит по всему своему `backstack`-у и собирает все транзакции по указанному имени, после чего сохраняет их в `HashMap`, используя имя и ключ.


 ### Q14<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Как организовать взаимодействие `Activity` и `Fragment`?
 
    1.При помощи интерфейса. Переменная интерфейсного типа должна быть объявлена внутри фрагмента, а в активити этот интерфейс должент быть реализован. Внутри метода onAttach() можно активити привести к интерфейсному типу и работать с ней.
    
    2. Через ViewModel 

 ### Q15<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Как передать параметры во `Fragment`?

 При помощи объекта `Bundle` и метода `setArguments`

  ### Q16<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
  ### Почему нельзя передавать параметры в конструктор `Fragment`-а?

  Потому что при пересоздании фрагмента будет вызван его конструктор без параметров. Если такого конструктора нет, то приложение упадет, а если есть, то переданные ранее параметры не сохранятся.

  ### Q17<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
  ### Для чего метод requireActivity()?
  Служит для передачи результатов между фрагментами.

 ### Q18<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
 ### Как определить скрыт ли на данный момент фрагмент?

  ### Q19<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
  ### Фрагмент является налседником Context?
  Не является!

   ### Q20<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
   ### Что происходит с фрагментом при повороте экрана?

   При повороте `Activity-host` (Activity которое является родителем для фрагмента) уничтожается. В тот момент когда этот процесс происходит `FragmentManager` отвечает за уничтожение дочернего фрагмента. `FragmentManager` запускает методы угасающего жизненного цикла фрагмента: 
   - `onPause()` 
   - `onStop()` 
   - `onDestroy()`

  При изменении конфигурации `FragmentManager` уничтожает и заново собирает представление фрагментов. Это происходит из соображений что в новой конфигурации могут потребоваться новые ресурсы. На случай, если для нового варианта существуют более подходящие ресурсы, представление строится «с нуля».

  ### Q21<img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExbnluOG4xdGlpeWxwYnFhM3Bjc2Z3dzN5eDhhaThza2N0Ym9wOGUxOCZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/zECASgodRMZ5QAbRao/giphy.gif" width="30px">
  ### Для чего нужен метод `Fragment.setRetainInstance()`?

  Метод `setRetainInstance(boolean)` является частью Fragment API фреймворка Android. Он используется для того, чтобы указать системе, сохранять ли текущий фрагмент при повторном создании `Activity` (например, при изменении конфигурации, таком как поворот).

  Когда вы вызываете `setRetainInstance(true)` для фрагмента, это означает, что фрагмент не будет уничтожен вместе со своей родительской активностью при изменении конфигурации. Вместо этого он будет сохранен и повторно присоединен к новому экземпляру активности после завершения изменения. Это может быть особенно полезно для сохранения состояний асинхронных задач или данных, которые были загружены и которые вы не хотите перезагружать или перевычислять при ротации.

  Однако важно отметить, что setRetainInstance имеет свои ограничения и может привести к утечке памяти, если вы не будете внимательно относиться к управлению ссылками на контекст или другие объекты во фрагменте. Кроме того, он помогает только при изменении конфигурации, а не в тех случаях, когда активность уничтожается по другим причинам, например, когда пользователь нажимает кнопку "назад" или когда система уничтожает активность из-за нехватки памяти.

  Для решения сохранения данных лучше использовать ViewModel и LiveData (из компонентов архитектуры Android) для более чистой и безопасной обработки изменений конфигурации. ViewModel переживает изменения конфигурации, поэтому в ней могут храниться данные, которые в противном случае вы бы сохранили с помощью сохраненного фрагмента.

  Вот базовый пример использования ViewModel для сохранения данных:

  ```kotlin

class MyViewModel : ViewModel() {
    private val data = MutableLiveData<String>()
    fun getData(): LiveData<String> {
        return data
    }
    fun loadData() {
        
    }
}

class MyActivity : AppCompatActivity() {
    private lateinit var viewModel: MyViewModel
    
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        
        viewModel = ViewModelProvider(this).get(MyViewModel::class.java)
        viewModel.getData().observe(this, { data ->
            
        })
        if (savedInstanceState == null) {
            
            viewModel.loadData()
        }
    }
}
  ```

## Другое

- Разница между Serializable и Parcelable
  - В первом используется рефлексия, довольно медленный процесс, однако разработчику нужно писать меньше кода. В Parcelable мы описываем только те вещи, которые нужно сериализовать, из-за чего кода становится больше. 

- Виды Intent-ов
  - **Implicit** (неявный) Вызываете системный интент: отправить СМС, позвонить, открыть карты и так далее
  - **Explicit** (явный) Вызов других активити внутри приложения
  - **Sticky** Интент, который остаётся после завершения бродкаста. Например, при подписке на `ACTION_BATTERY_CHANGED`, мы получим последний посланный интент. Поэтому, если нам нужно только текущее состояние батареи, слушать дальнейшие бродкасты не обязательно. 
  - **Pending** Интент, который может быть исполнен в будущем на правах вашего приложения 

- Может ли приложение работать в разных процессах? Зачем это нужно? Как можно организовать межпроцессорное взаимодействие?
  - Может. Для частей приложения (активити, сервисы, бродкасты и контент провайдеры) надо указать флаг process. 
  - +: Получаем больше памяти. Не всё приложение при недостатке памяти будет убито. 
  - -: Поскольку каждый процесс живёт в отдельном инстансе Дальвика, делиться информацией сложно. Для этого используются AIDL, интенты, handler-ы, messenger-ы

- Из-за чего возникает ошибка Application Not Responding (ANR)
  - Когда UI не отвечает несколько секунд. Случается обычно из-за блокированного главного треда.

- Как обнаружить ANR?
```kotlin
class App : Application() {

    var tick = 0 % Integer.MAX_VALUE

    override fun onCreate() {
        super.onCreate()

        val handler = Handler(mainLooper)

        thread {
            while (true) {
                val lastTick = tick + 1
                handler.post { tick += 1 }
                TimeUnit.SECONDS.sleep(5)

                if (lastTick != tick)
                    Log.d("APP", "ANR")
            }
        }

    }
}
```

## Inline-функции

- Зачем в котлине ключевое слово `inline`
  - В Котлине функции рассматриваются как любые другие значения: они могут быть переданы в и возвращены из методов, сохранены в переменные или в структуры данных. Чтобы поддержать это, Котлин использует семейство функциональных типов. Тогда, чтобы работать с `лямбдами`, Котлин создаёт объекты, реализующие интерфейсы `Function0`, `Function1` и так далее.
  - Когда в лямбде нет замыкания (грубо говоря: из лямбды не вызываются переменные и методы, которые не лежат внутри самой лямбды), для её реализации компилятор создаёт синглтон. Но для лямбды с замыканием компилятор вынужен создавать инстанс для каждого вызова лямбды. Если лямбда вызывается в цикле, это может даже привести к OOM (нехватке памяти).
  - В таком случае на помощь приходит ключевое слово `inline`: оно говорит компилятору, что содержимое лямбды нужно встроить в место её вызова, как будто мы написали код не внутри лямбды, а прямо в теле метода. 

- Для чего нужно ключевое слово `reified`
  - В Java существует такая концепция, как Type Erasure — стирание типов. Коротко говоря, это проблема, возникающая при работе с дженериками. Из-за неё, например, нельзя сделать проверку типа `new ArrayList<String>() instanceof List<String>`: в рантайме джава-машина не знает, какие конкретно типы лежат внутри дженерика. 
  - Поскольку в Андроиде Котлин использует рантайм Джавы, проблема остаётся: мы не можем проверить, что `arrayListOf<String>() is List<String>`. 
  - Но используя `inline` функции, мы можем избежать стирания типов с помощью применения модификатора `reified` к дженерику: 
    ```kotlin
    inline fun <reified T> myGenericFunction(value: T): T {...}
    ```
- `crossinline` и `noinline`
  - Поскольку мы встраиваем код лямбды на место вызова, `return`, написанный в лямбде, закончит выполнение не лямбды, а всей функции. Когда нам это не нужно, мы можем пометить лямбда-параметр функции как `crossinline`, что запретит нелокальные `return`ы.
    ```kotlin
    inline fun function(crossinline nonLocalReturnBlockedLambda: () -> Unit) {...}
    ```
  - Порой в inline функции нам нужно не вызвать лямбду на месте, а передать дальше, в другой метод. Тогда лямбда-параметр можно пометить как `noinline`, и он не будет встраиваться в место вызова. 
    ```kotlin
    inline fun parameterPassedToOtherInlineFunction(lambda1: () -> Unit, noinline lambda2: () -> Boolean) {
        // эта лямбда встроится
        lambda1.invoke()
        // а эта останется лямбдой и будет передана в другой метод
        someNonInlinedLambdaConsumingFunction(lambda2)
    }
    ```

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
