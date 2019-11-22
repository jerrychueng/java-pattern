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
