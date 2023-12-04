### 객체지향프로그래밍 13주차 과제 7조 - 변유빈, 유시연 

##### 문제: 실습문제 10장 16번 - vector<Shape*>v;를 이용하여 간단한 그래픽 편집기를 콘솔 바탕으로 만들어보자.
<details>
<summary>소스코드</summary>

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




### 실행 결과 이미지 

<img width="863" alt="image" src="https://github.com/hiciz/Cpp_07_group/assets/138213248/3e0ba4ab-e611-4c3b-8680-e66b1d89a3b3.png">

