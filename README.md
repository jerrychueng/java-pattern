#设计模式的基本原则（设置对应的功能模块，框架设置中会使用到对应的设计模式，对应的是一种规范操作。已达到对应的代码的重用性，解耦操作。）
1.对应的..

#设计模式对应的设计原则（）
1.单一职责原则（Simple Responsibility Principle）
对应的类的责任是单一性的，设计之初对应的不能把多个功能的操作耦合在一起，后面维护和添加新功能时，会出现功能性耦合操作。
将对应的类粒度化，在设计时把对应的功能拆分成对应的单独功能类操作。（在特殊情况下，如果当前的类的功能性比较简单和操行性较少，可以从下的方面出发，从函数的方面的来分化对应的职责单一性，也确保对应的单一性操作，必须保证特定的条件下来确认对应使用对应的函数单一性原则）；
提高类的可读性，提高系统的可维护性；
可以降低类的复杂度，
>> 实例： 
//交通工具
public class Vehicle{
   public void run(String way){
      //如果单一完成对应的功能则，当需要新的方式时，则对应的不符合对应的要求。所有需要新，客户端得不到自己的要求结果。
      System.out.println(way +"run... road"); //在功能性上讲对应的way不能使用所有的方式来确认交通工具用法，
                                              //如果在对应的方法中添加逻辑处理，当添加的新的方式需求时，则对应的函数也需要做对应的修改处理，
                                              //甚至将对应的函数名称接口改变等，这样对客户端要重新改变对应的接口才能完成对应的功能。这样的方式 
                                              //对客户端是不允许的。
       if（bus）{
         //todo bus bussniss...  Q1: 添加多种方式操作性，扩充了对应的耦合性，甚至后期会修改新的需求而修改对应的函数。
       }else if(air){
         // todo air bussniss...
       }else if(car){
         //....
       }...
       //Q2: 如果添加新的需求，将对应的做限制操作，则需要修改对应已经实现过得功能，而添加新的业务逻辑
       else if(boat){
         //...TODO
         //new
         if(time >10 && time<15){
           //TODO new operation...
         }
       }
   }
}

public class Test{
   public static void main(String [] args){
       Vehicle vehicle = new Vehicle();
       vehicle.run(air);
       vehicle.run(boat);
       //Q3. 如果对应的没有rocket的接口处理操作，则对应的客户端使用的方式会出现得不到对应的结果.返回来需要重新设置对应的类接口的操作，添加新的业务。
       vehicle.run(rocket);
       .....
   }
}


//重新设计的方式
public class AirVehicle{
    public void run(String run){
      //todo ...
    }
}

public class BusVehicle{
   public void run(String run){
     //TODO....
   }
}

public class CarVehicle{
   public void run(String run){
     //todo...
   }
}
//A:扩展性如果对应有新的方式了，不用在以前的类上做修改操作， 
...

public class Test{
    public static void main(String [] args){
         //指定特定的功能类来完成对应的业务，如果有新的，不用在原来的基础上做的对应的业务修改。
         AirVehicle airVehicle = new AirVehicle();
         airVehicle.run(air);
         CarVehicle carVehicle = new CarVehicle();
         carVehicle.run(car);
         //...如有新的方式可以完成对应
    }
}
//添加新的方式不用做其他修改来完成
public class BoatVehicle{
    public void run(String boat){
      //TODO...
    }
}

==> BoatVehicle boatVehicle = new BoatVehicle();
    boatVehicle.run(boat);
    
    
扩展说明，如果对应的类中的函数也需要有单一职责操作，不能做过多的业务功能，可将对应的拆分，这样便于可读性和维护操作。

public class NewVehicle{
    //该函数根据对应的函数名，来确认对应的功能，如果要需要新的业务功能操作，值需要添加对应的函数功能来扩展，或者外部类扩展的方式来完成对应的功能。
    public void run(String newVehicle){
       //TODO...
       //A:新的功能，限制对应的时间操作,调用对应的新的处理功能即可
       checkVehicle(newVehicle);
       limitTime(newVehicle);//...完成新功能。不影响对应的原来的调用接口完成对应的功能。
    }
    
    public void checkVehicle(String newVehicel){
      //check the vehicle .... 
    }
   
    public void limitTime(String newVehicle){
       if(time >10 && time<20){
         //....
       }
       ///....
    }
}
------------------------------------------------------------------------------------------------------------------------------
2.接口隔离原则（interface  Segregation Principle）
依据是面向接口编程，而是面向对应的实现类来完成对应的功能，如果需要扩充对应的，需要新填对应的功能，或则实现方式。所以前提面向接口和抽象编程。对于接口和抽象，我们需要将对应的接口最小化关系业务，接口功能单一化，确认性，不能讲重复的功能添加到一个接口中，而对应的接口不会产生业务功能冲突。(一个类对另外一个类的依赖性应当是建立在最小的接口上的。)
>>降低耦合关系，是类直接的职责更加明确。
实例：
//一个接口提供多个操作方式
public interface Interface{
   void operation1();
   void operation2();
   void operation3();
   void operation4();
   void operation5();
}

public class A implements Interface{
   public void operation1(){
      //TODO...
   }
   
   public void operation2(){
      //TODO...
   }
   public void operation3(){
      //TODO...
   }
   
   public void operation4(){
      //TODO...
   }
   
   public void operation5(){
      //TODO...
   }
}
//具体的实现类来实现对应的有多种功能的接口操作
public class B implements Interface{
  public void operation1(){
      //TODO...
   }
   
   public void operation2(){
      //TODO...
   }
   public void operation3(){
      //TODO...
   }
   
   public void operation4(){
      //TODO...
   }
   
   public void operation5(){
      //TODO...
   }

}

public class C{
   public void doOperation1(Interface a){
      //todo...
      a.opeartion1();
      //...
   }
   public void doOpeartion3(Interface a){
      //todo....
      a.operation3();
   }
}

//有对应的类依赖接口时，对应但是对应的实现类完成了所有的功能，已经对应的接口只有部分执行调用接口的方式。而对应的产生具体实现类的依赖的接口有明确的职责关系来完成对应的，需要将对应的接口隔离开来。是调用的方式更加明确。
public class D{
    public void doOperation2(Interface a){
      //todo...
      a.operation2();
    }
    
    public void doOperation4(Interface a){
      //TODO...
      a.operation4();
    }
}

public interface Interface1{
   void operation1();
   void operation3();
}

public interface Interface2{
   void operation2();
   void operation4();
}
//使接口功能职责分隔开来，而不是而合并在一起时对应的耦合性增强。
public interface Interface3{
   void operation5();
}

public class A implements Interface1 ,Interface3{
   public void operation1(){
      //TODO...
   }
   
   public void operation3(){
      //TODO...
   }
   
   public void operation5(){
      //TODO...
   }
}

public class B implements Interface2,Interface5{
    public void operation2(){
      //TODO...
    }
      
    public void operation4(){
      //TODO...
    }
    
    public void operation5(){
      //TODO...
    }
}

public class C {

   public void doOperation1(Interface1 a){
      //todo...
      a.operation1();
   }
   
   public void doOperation3(Interface1 a){
      //TODO...
      a.operation3();
   }
  
}

public class D{
   public void doOperation2(Interface2 a){
      //TODO...
      a.operation2();
   }
   
   public void doOperation4(Interface4 a){
      //TODO...
      a.operation4();
   }
}

public class Test{
   public static void main(String [] args){
         D d = new D();
         d.operation2(new B()); 
         //...
   }
}
客户端不要使用它不需要的接口,设计之初应该保证类不被对应的接口的污染，这个接口类对应的抽象定义太复制，抽象定义的功能在耦合，后期在依赖对应的接口时或关联关系时，就会有过多的不必要的抽象做对应的实现。
------------------------------------------------------------------------------------------------------------------------------
3.依赖倒置原则：（dependence inversion principle）
依赖倒置原则的核心就是面向抽象(抽象类或者接口)编程, 在对应的类与类之间的关系，有之一种依赖关系，而在对应的处理这中关系时，我们应该保证面对抽象，而不依赖具体编程的方式，这个保证在后面客户端（上层调用）时有对应的新功能或则方式时，则需要从结构到调用的方式可能都发生修改，而增加了开发的时间以及可维护性差。 从抽象的本质来切入，抽象是对实现的约束，是对依赖者的一种契约，不仅仅约束自己，同时约束自己与外部的关系，保证了抽象知己和具体外部的依赖的关系。
抽象不应该依赖细节
细节应该依赖抽象
实例
public class Driver{
   public void run(Benz b){
      b.driver();
      //TODO...
   }
}
public class Benz{
   public void drive{
      //todo...
   }
}
public class Client{
   
   public static void main(String [] args){
      Driver driver = new Driver();
      Benz b = new Benz();
      driver.run(b);// 当前这个客户端使用的方式比较固定，对细节实现，而不便于扩展，
   }

}

public class BWM{
   public void drive{
      //todo...
   }
}

对是细节依赖，没有对应的抽象性
public class BWNDriver {
   //
   public void run(BWM bmw){
      bmw.drive(); //...只能被动的扩展对应的如果是底层架构，则需要实现新的方式来提供给客户端来完成对应的功能，如果一个接口的比较多，则可能需要更复杂的实现方式，或则架构重构的方式了。
   }
}



public interface IDriver{
   public void run(ICar car);
}

public interface ICar{
   public void drive();
}

//方式1.
public class Benz implements ICar{
   public void drive(){
      //todo benz drive....
   } 
}

public class Driver implements IDriver {

   public void run(ICar car){
      //driver todo something
      car.drive();///...
   }
}


public class Client {

   public static void main(String [] args){
      Driver driver = new Driver();
      Benz benz = new Benz();
      
      driver.run(benz);
      
      BMW bmw = new BMW();
      driver.run(bmw);//直接扩展对应的新的实现方式，而不需要构建新的抽象方式来完成对应的功能。
      
   }
}

public class BMW  implements ICar{
   public void drive(){
      //todo ...
   }
}

也可以扩展新的
public class NewDriver implements IDriver{
   public void run(ICar car){
      //新的实现方式...
   }
}

------------------------------------------------------------------------------------------------------------------------------
4.里式替换原则（Liskov Substitution Principle）
继承的优点：（定义了一个基本的规范，而且提供了给对应的继承者，可也用于扩展性）
● 代码共享，减少创建类的工作量，每个子类都拥有父类的方法和属性；
● 提高代码的重用性；
● 子类可以形似父类，但又异于父类；
● 提高代码的可扩展性，很多开源框架的扩展接口都是通过继承父类来完成的；
● 提高产品或项目的开放性。

继承的缺点：（被动性增强，主动拥有对应父类的特性，如依赖父类功能时，可能带来一定的耦合性）
● 继承是侵入性的。只要继承，就必须拥有父类的所有属性和方法；
● 降低代码的灵活性。子类必须拥有父类的属性和方法；
● 增强了耦合性。当父类的常量、变量和方法被修改时，需要考虑子类的修改，而且在缺乏规范的环境下，这种修改可能带来非常糟糕的结果—— 大段的代码需要重构。

>>在子类尽量不重写父类的方法，如没有特殊的定义中。继承实际上让两个类耦合性增强，在适当的情况下，可通过聚合，组合，依赖的关系完成。

实例：
public class Parent{
    public int operation(int a,int b){
         return a+b;
    }
}

public class Child extends Parent{
      public void newOperation(){
         //todo...
      }
      //重写了对应的父类的函数，重新定制了对应的操作，当来一定的耦合性
      public int operation(int a, int b){
         //TODO
         return a-b;
      }
}

public class Client{
   public static void main(String [] args){
        Child child = new Child();
        child.operation(1,2);//如果没有特定的调用方式，想使用父类的方式来完成，但是对应的子类重写对应的功能模块，则对应会有不同的实现方式来得到结果。 所有对应的继承带来了耦合性。
   }
}


public class Child {
   private Parent parent = new Parent();//使用组合的方式来完成
   
   public void newOperation(){
      //todo...
   }
   public int operation(int a, int b){
      return parent.operation(a,b);//直接使用对应组合的对象来完成功能。
   }
}




#java的设计模式大体上分为三大类：

 1.   创建型模式（5种）：工厂方法模式，抽象工厂模式，单例模式，建造者模式，原型模式。
 2.   结构型模式（7种）：适配器模式，装饰器模式，代理模式，外观模式，桥接模式，组合模式，享元模式。
 3.   行为型模式（11种）：策略模式、模板方法模式、观察者模式、迭代子模式、责任链模式、命令模式、备忘录模式、状态模式、访问者模式、中介者模式、解释器模式。

设计模式遵循的原则有6个：
1、开闭原则（Open Close Principle）
　　对扩展开放，对修改关闭。
2、里氏代换原则（Liskov Substitution Principle）
　　只有当衍生类可以替换掉基类，软件单位的功能不受到影响时，基类才能真正被复用，而衍生类也能够在基类的基础上增加新的行为。
3、依赖倒转原则（Dependence Inversion Principle）
　　这个是开闭原则的基础，对接口编程，依赖于抽象而不依赖于具体。
4、接口隔离原则（Interface Segregation Principle）
　　使用多个隔离的借口来降低耦合度。
5、迪米特法则（最少知道原则）（Demeter Principle）
　　一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。
6、合成复用原则（Composite Reuse Principle）
　　原则是尽量使用合成/聚合的方式，而不是使用继承。继承实际上破坏了类的封装性，超类的方法可能会被子类修改。
  
  相对与框架级别的设计模型，对应基本设计模式相对应的注重基本元素之间的结构待机，而不是相对与大系统的庞然大雾是细分成子系统，模块，组建等来设计。而基本设计模型可以用来设计成这些小模块之间的内联关系。相对与软件设计模式而言，本人感觉软件本来就是抽象出来层次，首先有了概念然后可能会产生对应的实现关系。所以如何让这个抽象的设计模式有所领悟，也需要去类比其他的行业或则领域的结构关系，相对于在建造行业一样，设计模式是从建造行业应运而生的，所有在很多时候可以使用比较的方式将对应的软件设计模式产生关联关系，而且人的记忆力对于相关有关联的事物记忆和理解达到事半功倍的效果。比如，在原始的时候，人去建造一个房子，可能直接使用原始的石头去建筑，可能去打磨对应的石头形状，然后堆砌在一起，形成了对应的房子。后来然后使用上了泥，将对应的泥土烧制成对应的砖块。使用对应的水泥将对应的砖块粘连在一起即可完成对应房屋建造过程，到现在人的效率性更高，直接将对应的房子拼凑而成，将对应的钢筋，玻璃，螺丝等等原材料直接拼层对应一所高楼大厦，所以软件的设计模式也是一致的。我们使用工厂来帮我创建对象的产生，而不用等到需要的时候去来拿的思想，而是直接找对应的人。当然任何都是没有确定的好，使用设计模式也是相对的，对象在软件中如何达到一定的高效性，及时性等要求，都是需要相对与什么样的环境而定的。而且对应不同的软件设计语言，他们之间的规范不同，也有动态的特性不同，所有相对应java而言，变形使用和扩展的的设计原则是通用的。所以理解好对应的原则会很好帮我们梳理对应的流程分析。
