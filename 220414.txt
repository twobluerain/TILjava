1교시

Method Overriding 

 -  슈퍼 클래스와 서브 클래스의 메소드에서 발생합니다.
 -  슈퍼 클래스의 메소드를 서브 클래스에서 재정의하는 것 입니다.
 -  슈퍼 클래스의 메소드 이름, 메소드 인자 타입 및 개수, 리턴 타입 등
       모든 것 동일하게 정의 합니다.
 -  오버라이딩된 메소드의 접근 지정자는 슈퍼 클래스의 메소드의 접근
       지정자 보다 좁아질 수 없습니다. (protected -> public)
 - static, private, 또는 final 메소드는 오버라이딩 될 수 없습니다.
 - return 타입이 다른 경우 오류 납니다.

 -  부모클래스의 메소드는 무시됩니다.

 - 부모클래스가 메소드를 상속해주나 자식 클래스는 자신이 구현한 
  메소드를 우선 하여 이용합니다. 

 - 메신저는 버젼별로 기능이 틀리나 버전이 틀리다고해서 대화를 할 수 
  없는 것은 아닌것과 같이 Overriding 기술은 부모클래스의 구기능을 없애는
  것이 아니라 유지하면서 자식의 새로운 기능으로 교체하는 목적으로 
  사용됩니다. 

- 자식 클래스에서 super.메소드(매개변수); 로 부모클래스를 호출 가능 ?

setname : public 에서 protected으로 ?

static 선언하면 오버라이딩 X

 

객체 형변환

 - 상속 관계에서는 부모자식간에 형변환이 가능합니다. 

 - 상속관계에서는 좌측에 부모클래스가 오고 우측에 자식 클래스가 올수 
  있습니다. 

String str = new Object() XObjiect obj = new String() O

String str = obj; O

 

업캐스팅

 -  프로그램에서 이루어지는 자동 타입 변환 입니다.

 -  자식객체 내에 있는 모든 멤버를 접근할 수 없고 슈퍼 클래스의 멤버만
        접근 가능합니다. 단, 부모에게 오버라이딩 되었다면 접근할 수 있다. ?

다운캐스팅

 -  슈퍼 클래스 레퍼런스를 서브 클래스 타입의 변수에 대입

상속일 때 자식 부모클래스만

상속일 때 업캐스팅 되었다면 부모클래스만 오버라이딩 되었다면 부모/자식클래스

 

객체 형변환

클래스가 다른 클래스로 (상속관계일 때)

오버라이딩 안하면 부모클래스만 접근 가능

오버라이딩 되었다면 자식클래스도 호출 가능

 

 

2교시

상속 관계에서의 생성자

 - 기본 생성자가 명시되지 않은 경우 자동으로 기본 생성자가 생성되어 
     객체가 만들어 집니다 
 - 자식 클래스 객체 생성시 부모클래스의 생성자가 먼저 호출되고 자식 
     클래스의 생성자가 호출됨 

 

메소드 내부 객체 변수 

 - this : 메소드안에서 객체를 나타내는 객체 변수,  
             메소드안에서 메소드를 호출한 객체의 주소(Hash Code)를    
             가지고 있습니다.  
             this.멤버변수   
  - super : 메소드안에서 상위 클래스 객체를 나타내는 객체 변수 
             , super.멤버변수  

             오버라이딩 되어 or 변수가 같아 숨겨진 메소드에 접근할 때

생성자 호출 메소드 

  - 생성자안에서 다른형태의 생성자를 호출 할 수 있습니다. 
  - this() : 현재 클래스의 생성자를 호출합니다. 
  - super() : 부모 클래스의 생성자를 호출합니다. 
  - 생성자 : new를 이용하여 메모리 할당이 끝난 후 메모리를 초기화하는 
   역할을 합니다. 멤버 변수에 초기값을 할당합니다. 

 

 

3교시

this() 생성자

 - 파라미터가 계속 증가해도 기존의 생성자를 이용 활 수 있습니다. 

super() 생성자

 - 자식 클래스는 자신이 가지고 있는 멤버 변수만 초기화하고 나머지는 
     부모클래스의  생성자를 호출해서 부모클래스의 멤버로 초기화 합니다. 

 - 부모클래스의 생성자를 호출할 경우는 반드시 자식 클래스의 생성자
     안에서 가장먼저 선언해야 합니다.  
     이유는 자식 클래스의 모듈이 실행되기전에 부모클래스의 생성자가 먼저 
    실행이 되어야 하는 우선순위의 규칙 때문에 그렇습니다. 

 

4교시

package day07;

class Pay{ //클래스:필드
  private String name;
  private int bonbong;
  
  public Pay() {}
  public Pay(String name, int bonbong) {
    this.name = name;
    this.bonbong = bonbong;
  }
  
  //setter(합법적으로 숨겨진 영역에 접근해서 데이타 저장) 
  public void setName(String name) {
    this.name = name;
  }
  
  //getter(합법적으로 숨겨진 영역의 데이터를 가져온다)
  public String getName() {
    return name;
  }
  
  public void setBonbong(int bonbong) {
    this.bonbong = bonbong;
  }
  
  public int getBonbong() {
    return bonbong;
  }
  
  public int taxCalc() {
    return (int) (bonbong * 0.045 + 0.5);
  }
  
  public int silsuCalc() {
    return bonbong - taxCalc();
  }
  
  public void printCalc() {
    System.out.println("---------------------");
    System.out.println("---- 4월 급여 내역 -----");
    System.out.println("---------------------");
    System.out.println("성명 : "+name);
    System.out.println("본봉 : "+bonbong);
    System.out.println("세금 : "+taxCalc());
    System.out.println("실수령액 : "+silsuCalc());
  }
  
}

class Extra extends Pay{
  private int year;  //근무년수
  private int child; //자녀수
  
  public Extra() {}
  public Extra(String name,int bonbong, int year, int child) {
    super(name,bonbong);
    this.year = year;
    this.child = child;
  }
  
  public void setYear(int year) {
    this.year = year;
  }
  public int getYear() {
    return year;
  }
  
  public void setChild(int child) {
    this.child = child;
  }
  
  public int getChild() {
    return child;
  }
  
  public int calcExtra() {
    int pay = 0;
    if (year == 1) { 
        pay = pay + 200000;         
    }else if(year == 2) { 
        pay = pay + 400000; 
    }else if(year == 3) { 
        pay = pay + 600000; 
    }else if(year == 4) { 
        pay = pay + 800000; 
    }else{ 
        pay = pay + 1500000; 
    } 
     
    //자녀수당을 계산합니다. 
    if ( year >=1){ 
        if (child > 1){ 
            pay = pay + (child * 200000); 
        } 
    } 
    return pay;
  }
  @Override
  public int silsuCalc() {

    return getBonbong() + calcExtra() - taxCalc();
  }
  @Override
  public void printCalc() {
    // TODO Auto-generated method stub
    System.out.println("------------------------");
    System.out.println("---- 4월 급여 내역(수당) -----");
    System.out.println("------------------------");
    System.out.println("성명 : "+getName());
    System.out.println("본봉 : "+getBonbong());
    System.out.println("세금 : "+taxCalc());
    System.out.println("수당 : "+calcExtra());
    System.out.println("실수령액 : "+silsuCalc());

  }
  
}
public class PayCalc2 {

  public static void main(String[] args) {
    Pay p1 = new Pay();
    Pay p2 = new Pay();
    Pay p3 = new Pay();    
    Pay p4 = new Pay("홍길동", 4000000);
    
//    p4.printCalc();
    
    p1.setName("왕눈이");
    p1.setBonbong(2000000);
    p1.printCalc();

    p2.setName("아로미");
    p2.setBonbong(2500000);
    p2.printCalc();
    
    p3.setName("투투");
    p3.setBonbong(1500000);
    p3.printCalc();
    
    Extra e = new Extra();
    e.setName("김길동");
    e.setBonbong(4000000);
    e.setYear(3);
    e.setChild(2);
    e.printCalc();
    
    Extra e2 = new Extra("이길동",4300000,3,1);
    e2.printCalc();
    
  }

}

 

5교시

package day07;

class Score {
  private String name;
  private int math;
  private int eng;
  private int kor;

  public Score() {}
    public Score(String name, int math, int eng, int kor) {
    this.name = name;
    this.math = math;
    this.eng = eng;
    this.kor = kor;
  }

  public void setName(String name) {
    this.name = name;
  }

  public String getName() {
    return name;
  }

  public void setMath(int math) {
    this.math = math;
  }

  public int getMath() {
    return math;
  }

  public void setEng(int eng) {
    this.eng = eng;
  }

  public int getEng() {
    return eng;
  }

  public void setKor(int kor) {
    this.kor = kor;
  }

  public int getKor() {
    return kor;
  }

  public int total() {
    return math + eng + kor;
  }

  public int avg() {
    return total() / 3;
  }

  public void printScore() {
    System.out.println("----------------------");
    System.out.println("---------스코어--------");
    System.out.println("----------------------");
    System.out.println("성명 : " + name);
    System.out.println("수학 점수 : " + math);
    System.out.println("영어 점수 : " + eng);
    System.out.println("국어 점수 : " + kor);
    System.out.println("합계 : " + total());
    System.out.println("평균 : " + avg());
  }
}
class Grade extends Score {
 
  public Grade() {}
  public Grade(String name, int math, int eng, int kor) {
    super(name, math, eng, kor);
  }

  public String calcGrade() {
    String grade = null;
    
    int score = (int)avg()/10;
    switch (score) {
    case 10:
      grade = "A 입니다.";
      break;
    case 9:
      grade = "B 입니다.";
      break;
    case 8:
      grade = "C 입니다.";
      break;
    case 7:
      grade = "D 입니다.";
      break;
    case 6:
      grade = "E 입니다.";
      break;
    default:
      grade = "F 입니다.";
      break;

    }
    return grade;
  }
    @Override
  public void printScore() {
    super.printScore();
    System.out.println("평점 :" +calcGrade());
  }
}
  
  
public class ScoreCalc {

  public static void main(String[] args) {
    Score s1 = new Score ();
    Score s2 = new Score ();
    Score s3 = new Score ();
    Score s4 = new Score ("가", 60,70,80);
    s4.printScore();
        
     s1.setName ("나");
     s1.setKor  (90);
     s1.setEng (100);
     s1.setMath  (80);
     s1.printScore();
     
     s2.setName  ("다");
     s2.setKor  (60);
     s2.setEng (50);
     s2.setMath (100);
     s2.printScore();
     
     s3.setName ("라");
     s3.setKor (90);
     s3.setEng (90);
     s3.setMath  (80);
     s3.printScore();

     
     Grade g = new Grade();
     g.setName("마");
     g.setKor(80);
     g.setEng(80);
     g.setMath(90);
     g.printScore();
     
     Grade g2 = new Grade("바",20,40,60);
     g2.printScore();
  }
}

 

 

6교시

추상클래스 abstract class

 - 추상 메소드 
   기능이 구현되지 않고 stub, 원형만 선언되어 있는 메소드 입니다. 
   중괄호 "{, }"가 생략되어 있습니다.  

   추상 메소드는 서브 클래스에서 오버라이딩하여 구현합니다.

package day07;

abstract class Calculator {
  public abstract int add(int a, int b);

  public abstract int substract(int a, int b);

  public abstract double average(int[] a);

  public abstract double division(int[] a);
  
}

  class GoodCalc extends Calculator {
    
    public int add(int a, int b) {
    return a+b;
 }
  public int substract(int a, int b) {
    return a-b;
 }
  public double average(int[] a) {
    int sum=0;
    for(int i=0 ; i<a.length; i++) {
      sum+=a[i];
    }
    return sum/a.length;
  }
   public double division(int a, int b) {
      return a/b;
   }
  }
 
    
  
public class CalcMain {

  public static void main(String[] args) {
    
    GoodCalc cal = new GoodCalc();
    System.out.println("add():"+cal.add(100, 20));
    System.out.println("sub():"+cal.substract(100, 10));
    int[] a = {90, 100, 90, 99, 46};
    System.out.println("avg():"+cal.average(a));
    System.out.println("div():"+cal.division(100,20));
    
  }

}

 

상수 선언 : public static final int 변수명 = 값; 

 - 고정된 같은 값이 반복해서 쓰이는 경우 상수를 이용한다.
 - public: 누구나 사용할 수 있음 
 - static: 객체를 만들지 않고도 사용 할 수 있음 
 - final: 변수의 값을 변경할 수 없음 
 - int: 정수를 저장함 
 - 상수의 예: 
    . 1년 365, 1주일 7일등 로직상에서 변하지 않는 고정된 값 또한 상수의  
      대상이 됩니다. 
    . 상수 사용이 많은 클래스: Calendar Class 등 

 

 

7교시

오버라이딩 예제

package day07.code;

class Person {
  String phone;

  public String getPhone() {
    return phone;
  }

  public void setPhone(String phone) {
    this.phone = phone;
  }

}

class Professor extends Person {

  @Override
  public String getPhone() {
    return "professor: " + super.getPhone();
  }

}

public class Overriding {

  public static void main(String[] args) {

    Professor a = new Professor();
    a.setPhone("010-1234-5678");
    System.out.println(a.getPhone());
    
    
    Person p = a;
    System.out.println(p.getPhone());
  }

}

 

생성자 예제

package day07.code;

class A {
  public A() {
    System.out.println("생성자A");
  }
}

class B extends A {
  public B() {
    System.out.println("생성자B");
  }
}

class C extends B {
  public C() {
    System.out.println("생성자C");
  }
}

public class ConstructorEx {
  public static void main(String[] args) {
    C c;
    c = new C();
  }
}

 

 

8교시

WrapperClass

Integer i = new Integer(10);   (WrapperClass)

package day07.code;

public class WrapperClassEx {
public static void main(String[] args) {
Integer i = new Integer(10);
char c = '4';
Double d = new Double(3.1234566);
System.out.println(Character.toLowerCase('A')); // 대문자 A를 소문자로 변환
 
if (Character.isDigit(c)) // 문자 c가 숫자를 나타내면 true
System.out.println(Character.getNumericValue(c)); // 문자 c를 숫자로 변환하여 출력
 
System.out.println(Integer.parseInt("-123")); // 문자열 “-123”을 정수로 변환하여 출력
System.out.println(Integer.parseInt("10", 16)); // 16진수로 표현된 문자열 “10”을 정수로 변환하여 출력
System.out.println(Integer.toBinaryString(28)); // 28의 2진수 표현을 나타내는 문자열 출력
System.out.println(Integer.bitCount(28)); // 28의 2진수에서 1의 개수출력
System.out.println(Integer.toHexString(28)); // 28의 16진수 표현을 나타내는 문자열 출력
System.out.println(i.doubleValue()); // i값(=10)을 double로 변환하여 출력
System.out.println(d.toString()); // d값(=3.1234566)을 문자열로 변환하여 출력
System.out.println(Double.parseDouble("44.13e-6")); // 문자열 “44.13e-16"을 double로 변환하여 출력
}
}
 

AutoBoxingUnBoxing

package day07.code;

public class AutoBoxingUnBoxing {
  public static void main(String[] args) {
    int i = 10;
//    StringBuffer str = new StringBuffer("홍");
//    System.out.println(str);
    Integer intObject = i; // auto boxing
    System.out.println("intObject = " + intObject);
    i = intObject + 10; // auto unboxing
    System.out.println("i = " + i);
  }
}

- Wrapper와 기본형 타입에서만 가능하다.

 

String StringBuffer

package day07.code;

public class StringBufferEx {
  public static void main(String[] args) {
    StringBuffer sb = new StringBuffer("This");
    System.out.println(sb.hashCode()); // 생성 후 스트링버퍼 해쉬값 출력
    sb.append(" is pencil"); // 문자열 덧붙이기
    System.out.println(sb);
    sb.insert(7, " my"); // 문자열 삽입
    System.out.println(sb);
    sb.replace(8, 10, "your "); // 문자열 대치
    System.out.println(sb);
    sb.setLength(5); // 스트링 버퍼 내 문자열 길이 설정
    System.out.println(sb);
    System.out.println(sb.hashCode()); // 문자열 조작 후 스트링 버퍼의 해쉬 코드
    
    System.out.println(sb.length());
    System.out.println(sb.hashCode()); // 값이 같으면 같은 객체임을 나타낸다.
  }
}