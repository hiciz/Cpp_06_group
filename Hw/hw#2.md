
### 실행 결과 이미지 

<img width="863" alt="image" src="https://user-images.githubusercontent.com/138213248/284153357-fc37ac41-c595-46ae-9405-d536529b42c1.png">




### 소스코드
<details>
<summary>헤더 파일</summary>

<div markdown="1">

``` c++
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

```c++
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

```c++
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

```c++
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

```c++
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

```c++
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

``` c++
//Shape.cpp
#include "Shape.h"
#include <iostream>

using namespace std;

Shape::Shape() {
    next = NULL;
}

Shape::~Shape() {}

Shape* Shape::add(Shape* p) {
    this->next = p;
    return p;
}

void Shape::paint() {
    draw();
}

Shape* Shape::getNext() {
    return next;
}
```

```c++
//Circle.cpp
#include "Circle.h"
#include <iostream>

using namespace std;

void Circle::draw() {
    cout << "Circle" << endl;
}

```

```c++
// Rectangle.cpp
#include "Rectangle.h"
#include <iostream>

using namespace std;

void Rectangle::draw() {
    cout << "Rectangle" << endl;
}

```

```c++
//Line.cpp
#include "Line.h"
#include <iostream>

using namespace std;

void Line::draw() {
    cout << "Line" << endl;
}

```

```c++
//UI.cpp
#include "UI.h"
#include <iostream>

using namespace std;

int UI::getMenu() {
    int key;
    cout << "삽입:1, 삭제:2, 모두보기:3, 종료:4 >>";
    cin >> key;
    return key;
}

int UI::getShapeTypeToInsert() {
    int key;
    cout << "선:1, 원:2, 사각형:3 >>";
    cin >> key;
    return key;
}

int UI::getShapeIndexToDelete() {
    int key;
    cout << "삭제하고자 하는 도형의 인덱스 >>";
    cin >> key;
    return key;
}
```

```c++
//GraphicEditor.cpp
#include "GraphicEditor.h"
#include "UI.h"
#include "Line.h"
#include "Circle.h"
#include "Rectangle.h"
#include <iostream>

using namespace std;

GraphicEditor::GraphicEditor() {
    pStart = pLast = NULL;
}

void GraphicEditor::insertItem(int type) {
    Shape* p = NULL;
    switch (type) {
    case 1:
        p = new Line();
        break;
    case 2:
        p = new Circle();
        break;
    case 3:
        p = new Rectangle();
        break;
    default:
        break;
    }
    if (pStart == NULL) {
        pStart = p;
        pLast = p;
        return;
    }
    pLast->add(p);
    pLast = pLast->getNext();
}

void GraphicEditor::deleteItem(int index) {
    Shape* pre = pStart;
    Shape* tmp = pStart;
    if (pStart == NULL) {
        cout << "도형이 없습니다!" << endl;
        return;
    }
    for (int i = 1; i < index; i++) {
        pre = tmp;
        tmp = tmp->getNext();
    }
    if (tmp == pStart) { //첫번째 도형을 삭제하는 경우
        pStart = tmp->getNext();
        delete tmp;
    }
    else {
        pre->add(tmp->getNext());
        delete tmp;
    }
}

void GraphicEditor::show() {
    Shape* tmp = pStart;
    int i = 1;
    while (tmp != NULL) {
        cout << i++ << ": ";
        tmp->paint();
        tmp = tmp->getNext();
    }
}

void GraphicEditor::run() {
    cout << "그래픽 에디터입니다." << endl;
    int menu, index, type;
    while (true) {
        menu = UI::getMenu();
        switch (menu) {
        case 1:
            type = UI::getShapeTypeToInsert();
            insertItem(type);
            break;
        case 2:
            index = UI::getShapeIndexToDelete();
            deleteItem(index);
            break;
        case 3:
            show();
            break;
        default:
            return;
        }
    }
}
```

```c++
//main.cpp
#include "GraphicEditor.h"

int main() {
    GraphicEditor graphicEditor;
    graphicEditor.run();

    return 0;
}

```

</div>
</details>
