Сейчас скелетон еще разрабатывается, поэтому нет никаких гарантий, что в следующих коммитах сохранится интерфейс.
**Актуально для версии 0.0.2**. Проверить версию можно посмотреть так: ```Plotter.version```

```Plotter``` -- основной объект.
Для создания графика нужно передать в конструктор ```Plotter``` id DOM-элемента, где дальше будет отрисовываться график. Затем нужно вызвать метод ```Plotter.draw()```
```javascript
var plotter = new Plotter("plot", options);
plotter.draw();
```


Дальше методы указываются в формате:

```
    ВозвращаемыйТип названиеМетода(аргумент1, аргумент2, ...)
```

# Методы Plotter

```
    Point addPoint(x, y, options)
```

```
    Line addLine(x1, y1, x2, y2, options)
```

```
    ParametricArray addArea(array, options)
```

```
    Func addFunc(Function, options)
```

```
    void removePoint(Point)
```

```
    void removeLine(Line)
```

```
    void removeArea(ParametricArray)
```

```
    void removeFunc(Func)
```

```
    String getID()
```

```
    Plotter draw()  //возвращает this для возможности chaning'а
```

# Работа с объектами скелетона
В текущей версии методы каждого из объектов скелетона, таких как Point, Func, Area, Line, предназначены для внутреннего использования. Для работы с объектами достаточно менять их опции. Также все указанные для объекта опции можно передать в качестве последних аргументов методов addLine, addFunc и т.д.
Дальше для каждой опции каждого из объектов указано значение по-умолчанию.

# Опции Func
```Func.accuracy = 800      // точность прорисовки графика```

```Func.strokeWidth = 2     //толщина линии```

```Func.color = colors(0)   //цвет берется из внутреннего набора цветов```

```Func.breaks = []         // множество точек разрыва функции```

```Func.left = null //ограничение функции слева```

```Func.right = null```

# Опции Line
```Line.strokeWidth = 2     //толщина линии```

```Line.color = colors(0)```

# Методы Line
```Line.setX1() // устанавливает координату x1```

```Line.setX2()```

```Line.setY1()```

```Line.setY2()```

#Опции Point
```movable = false      //можно ли двигать мышкой```

```color = colors(6)```

```size = 3```

#Опции ParametricArray

```
  color: colors(20) //цвет границы
```

```
  fillOpacity: 0.2  //прозрачность. 0 - прозрачно полностью, 1 - непрозрачно вообще.
```

```
  strokeWidth: 0    //толщина границы
```

```
  fill: colors(1)   //цвет заливки
```


# Опции Plot
```left = -10 //левая граница```

```right = 10```

```bottom = -5```

```top = 5```

```width = 800```

```height = 600```

```ticks = 10   //количество линий координатной сетки```

# PlotContainer, несколько графиков на одной странице
Как и Plotter, PlotContainer является глобальным объектом. Он служит для того, чтобы DOM-элемент с указанным ID работал
в качестве контейнера для других DOM-элементов, которые, в свою очередь могут содержать либо графики, либо произвольный
html-код.

```
Plotter PlotContainer.addPlot(options)   //добавляет в DOM-контейнер график и возвращает его. Возвращает то же самое,
что и конструктор Plotter.
```

```
DOM_ID PlotContainer.addEmptyDiv()       //создает в контейнере пустой <div> и возвращает его ID. Можно использовать,
например, для дальнейшей работы с Controls.
```

Инициализация контейнера и создание графика в нем:

```javascript
    var container = new PlotContainer("plot");

    var plotter = container.addPlot();
    plotter.draw();
```

Второй график можно создать также, как и первый:

```javascript
    var plotter2 = container.addPlot();
    plotter2.draw();
```

Также для создания графика можно использовать более короткий синтаксис:

```javascript
    var plotter3 = container.addPlot().draw();
```

#Примеры
Их можно посмотреть в папке scripts. В index.html можно менять имя подключаемого файла, чтобы смотреть разные примеры.
