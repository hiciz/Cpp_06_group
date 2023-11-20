
### 실행 결과 이미지 

<img width="863" alt="image" src="https://user-images.githubusercontent.com/138213248/284153357-fc37ac41-c595-46ae-9405-d536529b42c1.png">




### 소스코드
<details>
<summary>헤더 파일</summary>

<div markdown="1">

```
// Circle.h
#ifndef CIRCLE_H
#define CIRCLE_H

#include "Shape.h"

class Circle : public Shape {
protected:
    virtual void draw();
};

#endif // CIRCLE_H
#pragma once

```
```
//Shape.h
#ifndef SHAPE_H
#define SHAPE_H

class Shape {
    Shape* next;

protected:
    virtual void draw() = 0;

public:
    Shape();
    virtual ~Shape();
    Shape* add(Shape* p);
    void paint();
    Shape* getNext();
};

#endif // SHAPE_H
```
```
// Rectangle.h
#ifndef RECTANGLE_H
#define RECTANGLE_H

#include "Shape.h"

class Rectangle : public Shape {
protected:
    virtual void draw();
};

#endif // RECTANGLE_H
#pragma once

```

```
//Line.h
#ifndef LINE_H
#define LINE_H

#include "Shape.h"

class Line : public Shape {
protected:
    virtual void draw();
};

#endif // LINE_H
#pragma once

```
```
//UI.h
#ifndef UI_H
#define UI_H

class UI {
public:
    static int getMenu();
    static int getShapeTypeToInsert();
    static int getShapeIndexToDelete();
};

#endif // UI_H
#pragma once

```

```
//GraphicEditor.h
#ifndef GRAPHICEDITOR_H
#define GRAPHICEDITOR_H

#include "Shape.h"

class GraphicEditor {
    Shape* pStart;
    Shape* pLast;

public:
    GraphicEditor();
    void insertItem(int type);
    void deleteItem(int index);
    void show();
    void run();
};

#endif // GRAPHICEDITOR_H
#pragma once

```


</div>
</details>


<details>
<summary>cpp 파일</summary>

<div markdown="1">

</div>
</details>
