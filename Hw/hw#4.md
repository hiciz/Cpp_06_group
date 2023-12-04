### 객체지향프로그래밍 13주차 과제 7조 - 변유빈, 유시연 

##### 문제: 실습문제 11장 12번
<details>
<summary>소스코드</summary>

<div markdown="1">

```c++
#include <iostream>
#include <iomanip>
using namespace std;

class Material {
protected:
    string name;
    int amount;
public:
    string getName() {
        return name;
    }
    int getAmount() {
        return amount;
    }
    void setAmount(int amount) {
        this->amount = amount;
    }
    bool subAmount(int amount) {
        if (this->amount <= 0)
            return false;
        else
            this->amount -= amount;
        return true;
    }
};

class Coffee : public Material {
public:
    Coffee() {
        name = "Coffee";
        amount = 3;
    }
};

class Sugar : public Material {
public:
    Sugar() {
        name = "Sugar";
        amount = 3;
    }
};

class Cream : public Material {
public:
    Cream() {
        name = "Cream";
        amount = 3;
    }
};

class Water : public Material {
public:
    Water() {
        name = "Water";
        amount = 3;
    }
};

class Cup : public Material {
public:
    Cup() {
        name = "Cup";
        amount = 3;
    }
};

class CoffeeMachine {
    Material* mat[];
public:
    CoffeeMachine() {
        cout << "-----명품 커피 자판기 켭니다.-----" << endl;
        mat[0] = new Coffee();
        mat[1] = new Sugar();
        mat[2] = new Cream();
        mat[3] = new Water();
        mat[4] = new Cup();
        showCoffeeMachineState();
        cout << endl;
    }
    void showCoffeeMachineState() {
        for (int i = 0; i < 5; i++) {
            cout << setw(10) << mat[i]->getName();
            for (int j = 0; j < mat[i]->getAmount(); j++)
                cout << "*";
            cout << endl;
        }
    }
    void start() {
        int num;
        while (true) {
            showMenu();
            num = selectMenu();
            if (num == 3) {
                for (int i = 0; i < 5; i++) {
                    mat[i]->setAmount(3);
                }
                cout << "모든 통을 채웁니다~~" << endl;
                showCoffeeMachineState();
                cout << endl;
                continue;
            }
            else if (num == 4) {
                cout << "프로그램을 종료합니다..." << endl;
                exit(0);
            }

            if (mat[0]->subAmount(1) == false) { //커피
                cout << "재료가 부족합니다." << endl;
                showCoffeeMachineState();
                continue;
            }
            if (mat[3]->subAmount(1) == false) { // 물
                cout << "재료가 부족합니다." << endl;
                showCoffeeMachineState();
                continue;
            }
            if (mat[4]->subAmount(1) == false) { // 컵
                cout << "재료가 부족합니다." << endl;
                showCoffeeMachineState();
                continue;
            }
            // 2번 부족하다면 실행 
            switch (num) {
            case 0:
                if (mat[2]->subAmount(1) == false) {
                    cout << "재료가 부족합니다." << endl;
                    showCoffeeMachineState();
                    continue;
                }
                cout << "맛있는 보통 커피 나왔습니다~~" << endl;
                showCoffeeMachineState();
                cout << endl;
                break;
            case 1:
                if (mat[1]->subAmount(1) == false) { //설탕
                    cout << "재료가 부족합니다." << endl;
                    showCoffeeMachineState();
                    continue;
                }
                cout << "맛있는 설탕 커피 나왔습니다~~" << endl;
                showCoffeeMachineState();
                cout << endl;
                break;
            case 2:
                cout << "맛있는 블랙 커피 나왔습니다~~" << endl;
                showCoffeeMachineState();
                break;
            default: //입력을 잘못했을 때
                cout << "잘못 입력 하셨습니다." << endl << endl;
                break;
            }
        }
    }
    void showMenu() {
        cout << "보통 커피:0, 설탕 커피:1, 블랙 커피:2, 채우기:3, 종료:4>> ";
    }
    int selectMenu() {
        int num;
        cin >> num;
        return num;
    }
};

int main() {
    cout.setf(ios::left);
    CoffeeMachine c;
    c.start();
}
```

</div>
</details>




### 실행 결과 이미지 

<img width="863" alt="image" src="https://github.com/hiciz/Cpp_07_group/assets/138213248/693b2964-2e66-4eca-919f-95a0d5f9c955.png">

