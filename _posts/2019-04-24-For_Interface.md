---
layout: post
title: Interface에 관하여
date: 2019-04-24 21:53:00 +0300
description: Grow as a Full Stack Development. This blog always used to keep learning knowledge.
# img: Dark.jpg # Add image post (optional)
tags: [GitHub Blog, C#, Interface]
---

### Interface에 관하여 적어봅니다.

- 인터페이스는 다른 인원들과 협업을 위한 통로가 될 수 있습니다. 가령 정수형 숫자를 입력받아 처리하는 사칙연산 계산기 를 만든다고 합시다. 그럼 계산기에 대한 구조는 어떻게 될까요?


    ```
    1. Input
    2. Output
    3. Operator
        1) Plus
        2) Minus
        3) 곱하기
        4) 나누기
    ```
    위 처럼 기능들을 분할해볼 수 있을겁니다. 그럼 분할한 기능별로 제작을 할 수 있도록 Interface Achitecter를 해보도록 하겠습니다.
    <br><br>

    우선 인터페이스는 크게 두가지로 분류하겠습니다. 

    - 입출력을 받는, User에게 이벤트를 유발할수 있는 부분
        
        >```C#
        >interface IView {
        >    int ChooseMenu(int value);
    
        >    int Input();

        >    void Output(float value);
        >}
        >```

    - 데이터가 계산되는 부분 
        
        ```C#
        interface ICalculator {
            float Add(int fst, int secd);

            float Minus(int fst, int secd);

            float Mulitiply(int fst, int secd);

            float Division(int fst, int secd);
        }
        ```
    두가지로 분리하여 설계가 끝났습니다.

    그럼 구현에 앞서 우선 Interface로 프로그램을 작동해 보겠습니다.

    인터페이스를 사용했을때 장점이 여기서 나옴니다.

    구현 전에 프로그램을 구성해볼수 있다는 점입니다.

    프로그램을 구성하기 전에 인터페이스를 상속받는 클래스를 먼저 생성해야 합니다.

    ```C# 
    class View : IView{
        public int ChooseMenu(int value){

        }

        public int Input(){

        }

        public void Output(float value){

        }
    }
    ```
    IView를 상속받는 View 클래스와

    ```C#
    class Calculator : ICalculator{
        publi float Add(int fstm int secd){

        }

        public Minus(int fst, int secd){

        }

        public Mulitiply(int fst, int secd){

        }

        public float Division(int fst, int secd){

        }
    }
    ```
    ICalculator를 상속받는 Calculator 입니다.
    <br><br>

    그럼 이제 프로그램의 비즈니스 로직을 구현해 보겠습니다.
    ```C#
    class Main : ICalculator, IView {
        public static void Main(stirng args[]){
            IView view = new View();
            ICalcultor cal = new Calculator();

            int oper = view.ChooseMenu(view.input());

            
            switch(oper) {
                case "+":
                    view.Output(cal.Add(1, 2));
                    break;
                case "-":
                    view.Output(cal.Minus(1, 2));
                    break;
                case "*":
                    view.Output(cal.Mulitiply(1, 2));
                    break;
                case "/":
                    view.Output(cal.Division(1, 2));
                    break;
                default:
                    Console.WriteLine("잘못된 명령입니다.");
                    break;
            }
        }
    }
    ```


