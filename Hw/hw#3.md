### 객체지향프로그래밍 11주차 과제 7조 - 변유빈, 유시연 

##### 문제: 실습문제 10장 16번 - vector<Shape*>v;를 이용하여 간단한 그래픽 편집기를 콘솔 바탕으로 만들어보자.
### 소스코드
<details>
<summary>헤더 파일</summary>

<div markdown="1">

```c++
//Circle.h
class Circle : public Shape {
protected:
    virtual void draw();
};
```

```c++
//Rect.h
class Rect : public Shape {
protected:
    virtual void draw();
};
```

```c++
//Line.h
class Line : public Shape {
protected:
    virtual void draw();
};
```

```c++
//Shape.h
#ifndef SHAPE_H
#define SHAPE_H
class Shape {
protected:
    virtual void draw() = 0;
public:
    void paint();
};
#endif
```

</div>
</details>


<details>
<summary>cpp 파일</summary>

<div markdown="1">

``` c++
//Circle.cpp
#include <iostream>
using namespace std;
#include "Shape.h"
#include "Circle.h"
void Circle::draw() {
    cout << "Circle" << endl;
}
```

``` c++
//Rect.cpp
#include <iostream>
using namespace std;
#include "Shape.h"
#include "Rect.h"
void Rect::draw() {
    cout << "Rectangle" << endl;
}
```

``` c++
//Line.cpp
#include <iostream>
using namespace std;
#include "Shape.h"
#include "Line.h"
void Line::draw() {
    cout << "Line" << endl;
}
```

``` c++
//Shape.cpp
#include <iostream>
#include "Shape.h"
using namespace std;
void Shape::paint() {
    draw();
}
```

``` c++
//main.cpp
#include <iostream>
#include <string>
#include <vector>
#include "Shape.h"
#include "Circle.h"
#include "Rect.h"
#include "Line.h"
using namespace std;

int main()
{
    vector<Shape*> v;
    vector<Shape*>::iterator it;
    int num;
    int sNum;
    cout << "그래픽 에디터입니다." << endl;
    while (true)
    {
        cout << "삽입:1, 삭제:2, 모두보기:3, 종료:4 >> ";
        cin >> num;
        if (num == 4)
            break;
        if (num == 1)
        {
            cout << "선:1, 원:2, 사각형:3 >> ";
            cin >> sNum;
            if (sNum == 1)
            {
                v.push_back(new Line);
            }
            if (sNum == 2)
            {
                v.push_back(new Circle);
            }
            if (sNum == 3)
            {
                v.push_back(new Rect);
            }
        }
        if (num == 2)
        {
            cout << "삭제하고자 하는 도형의 인덱스 >> ";
            cin >> sNum;
            it = v.begin();
            int i = 0;
            while (it != v.end())
            {
                if (i == sNum)
                {
                    it = v.erase(it);
                    break;
                }
                else
                {
                    it++;
                    i++;
                }
            }
        }
        if (num == 3)
        {
            int i;
            for (it = v.begin(), i = 0; it != v.end(); it++, i++)
            {
                Shape* temp = *it;
                cout << i << ": ";
                temp->paint();
            }
        }
    }
}
``` 

</div>
</details>




### 실행 결과 이미지 

<img width="863" alt="image" src="https://github.com/hiciz/Cpp_07_group/assets/138213248/3e0ba4ab-e611-4c3b-8680-e66b1d89a3b3.png">

