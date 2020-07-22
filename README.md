# DesignPatterns26
package behaviouralStrategyPattern;

public class Addition implements Strategy {
	 public float calculation(float a, float b) {  
	        return a+b;  
	    }  
}

package behaviouralStrategyPattern;

public class Context {
   private Strategy strat;  

       public Context(Strategy strat){  
          this.strat = strat;  
       }  

       public float executeStrategy(float num1, float num2){  
          return strategy.calculation(num1, num2);  
       }  
}
package behaviouralStrategyPattern;

public class Multiplication implements Strategy {
	 public float calculation(float a, float b){  
	        return a*b;  
	    }  
}
 
package behaviouralStrategyPattern;
import java.io.BufferedReader;  
import java.io.IOException;  
import java.io.InputStreamReader;  
public class StratPatternDemo {
	 public static void main(String[] args) throws NumberFormatException, IOException {  

         BufferedReader br=new BufferedReader(new InputStreamReader(System.in));  
         System.out.print("Enter first value: ");  
         float value1=Float.parseFloat(br.readLine());  
         System.out.print("Enter  second value: ");  
         float value2=Float.parseFloat(br.readLine());  
         Context context = new Context(new Addition());          
         System.out.println("Add = " + context.executeStrategy(value1, value2));  

         context = new Context(new Subtraction());       
         System.out.println("Sub = " + context.executeStrategy(value1, value2));  

         context = new Context(new Multiplication());        
         System.out.println("Mul = " + context.executeStrategy(value1, value2));  
      }  
}
 
package behaviouralStrategyPattern;

public interface Strategy {
	  public float calculation(float a, float b);  
}
package behaviouralStrategyPattern;

public class Subtraction implements Strategy {
	 public float calculation(float a, float b) {  
	        return a-b;  
	    }  
}
 
package behavioural;

public class CollectionofNames implements Container {
	public String name[]={"Manjula", "SriRamulu","Shyam","Kranthi","Kiranmai"};   

	public Iterator getIterator() {  
	        return new CollectionofNamesIterate() ;  
	    }  
	    private class CollectionofNamesIterate implements Iterator{  
	        int i;  
	        public boolean hasNext() {  
	            if (i<name.length){  
	                return true;  
	            }  
	            return false;  
	        }  
	        public Object next() {  
	            if(this.hasNext()){  
	                return name[i++];  
	            }  
	            return null;      
	        }  
	    }  
	}  

package behavioural;

public interface Container {
	 public Iterator getIterator();  
}

package behavioural;

public interface Iterator {
	public boolean hasNext();  
    public Object next();  
}
 

package behavioural;

public class IteratorPattern {

	public static void main(String[] args) {
		 CollectionofNames coRepository = new CollectionofNames();  

         for(Iterator iter = coRepository.getIterator(); iter.hasNext();){  
             String name = (String)iter.next();  
             System.out.println("Name : " + name);  
          }      
	}

}
 
package BuilderPattern;

public class Mobilephone 
{
 private String os;
 private int ram;
 private String processors;
 private double screenshot;
 private int battery;
public Phone(String os, int ram, String processors, double screenshot, int battery) {
	super();
	this.os = os;
	this.ram = ram;
	this.processors = processors;
	this.screenshot = screenshot;
	this.battery = battery;
}
@Override
public String toString() {
	return "Mobilephone [os=" + os + ", ram=" + ram + ", processors=" + processors + ", screenshot=" + screenshot
			+ ", battery=" + battery + "]";
}


}

package BuilderPattern;

public class PhoneBuilder {
	 private String os;
	 private int ram;
	 private String processors;
	 private double screenshot;
	 private int battery;
	public PhoneBuilder setOs(String os) {
		this.os = os;
		return this;
	}
	public PhoneBuilder setRam(int ram) {
		this.ram = ram;
		return this;
	}
	public PhoneBuilder setProcessors(String processors) {
		this.processors = processors;
		return this;
	}
	public PhoneBuilder setScreenshot(double screenshot) {
		this.screenshot = screenshot;
		return this;
	}
	public PhoneBuilder setBattery(int battery) {
		this.battery = battery;
		return this;
	}
	public Phone get Mobilephone()
	{
		return new Mobilephone(os, ram, processors, screenshot, battery);
	}

}
 
package BuilderPattern;

public class Shop 
{
	public static void main(String args[])
	{
		Mobilephone p = new PhoneBuilder().setOs("Android").setRam(2).setProcessors("i5").getMobilephone();
	    System.out.println(p);
	}

}
 
package factorydesign;

public class Android implements OS {

	public void spec() {

			 System.out.println("Most powerful OS");
		}
	}


package factorydesign;

public class FactoryMain {

	public static void main(String[] args) {
		OperatingSystemFactory osf = new  OperatingSystemFactory();
		OS obj = osf.getInstance("Open");
		obj.spec();
	}

}    



package factorydesign;

public class IOS implements OS {

	public void spec() {
		System.out.println("Most secure OS");

	}


}
 

package factorydesign;

public interface OS {
   void spec();
}
   


package factorydesign;

public class OperatingSystemFactory 
{
  public OS getInstance(String str)
  {
	  if(str.equals("Open"))
	  {
		  return new Android();
	  }
	  else if(str.equals("Closed"))
	  {
		  return new IOS();
	  }
	  else
		  return new MAC();
  }
}
 
package factorydesign;

public class Windows implements OS {

	public void spec() {
	System.out.println("Popular operating system");
	}


package Adapterdesignpattern;

import com.Android.PilotPen;

public class AssignmentWork {
	private Pen p;

public Pen getP() {
		return p;
	}

	public void setP(Pen p) {
		this.p = p;
	}

public void writeAssignment(String str)
{
	p.write(str);
}
}
 


package Adapterdesignpattern;

public interface Pen 
{
	void write(String str);

}
 

package Adapterdesignpattern;

import com.Android.PilotPen;

public class PenAdapter implements Pen
{
	PilotPen pp = new PilotPen();

	public void write(String str) {

		pp.mark(str);
	}

}
 
package Adapterdesignpattern;

import com.Arbind.PilotPen;

public class School {

	public static void main(String[] args) {
		//PilotPen pp = new PilotPen();
		Pen p = new PenAdapter(); 
		AssignmentWork aw = new AssignmentWork();
		aw.setP(p);
		aw.writeAssignment("I like to write assignment");

	}

}
 
package CompositeDesignpattern;

import java.util.*;

public interface Component {
void showPrice();

}


class Leaf implements Component
{
    int price;
    String name;

    public Leaf(int price, String name) {
		super();
		this.price = price;
		this.name = name;
	}


	public void showPrice() 
	{
		System.out.println(name + ":" + price);

	}

}

class Composite implements Component
{
    String name;
    List<Component> components = new ArrayList<Component>();

     public Composite(String name) {
		super();
		this.name = name;
	}
	public void addComponent(Component com)
    {
    	components.add(com);
    }
	public void viewPrice() 
	{
       System.out.println(name);
       for(Component c : components)
       {
    	   c.viewPrice();
       }

	}

}
package CompositeDesignpattern;

public class CompositeTest {

	public static void main(String[] args) 
	{
		Component hd = new Leaf(3000,"Harddiskdrive");
		Component mouse = new Leaf(700,"Mouse");
		Component monitor = new Leaf(10000,"Monitor");
		Component ram = new Leaf(4500,"Memory");
		Component cpu = new Leaf(15000,"CPU");



		Composite ph = new Composite("peripheral:");
		Composite cabinet = new Composite("Cabinet");
		Composite mb = new Composite("Motherboard");
		Composite computer = new Composite("Computer:");

		mb.addComponent(cpu);
		mb.addComponent(ram);

		ph.addComponent(mouse);
		ph.addComponent(monitor);
		cabinet.addComponent(hd);
		cabinet.addComponent(mb);

		computer.addComponent(ph);
		computer.addComponent(cabinet);

		ph.viewPrice();
		System.out.println("\n******************\n");
		computer.viewPrice();


	}

}
package com.Arbind;

public class PilotPen {
public void mark(String str)
{
	//
	//
	//
	//
	//
	System.out.println(str);
}
}


<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.dp</groupId>
  <artifactId>designp</artifactId>
  <version>0.0.1-SNAPSHOT</version>
  <packaging>jar</packaging>

  <name>designp</name>
  <url>http://maven.apache.org</url>

  <properties>
    <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
  </properties>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>3.8.1</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
 
package com.dp.designp;

/**
 * Hello world!
 *
 */
public class App 
{
    public static void main( String[] args )
    {
        System.out.println( "Hello World!" );
    }
}

package com.dp.designpatterns;

import junit.framework.Test;
import junit.framework.TestCase;
import junit.framework.TestSuite;

/**
 * Unit test for simple App.
 */
public class AppTest 
    extends TestCase
{
    /**
     * Create the test case
     *
     * 
     */
    public AppTest( String testName )
    {
        super( testName );
    }

    /**
     * @returns to test
     */
    public static Test suite()
    {
        return new TestSuite( AppTest.class );
    }

    /**
     * Rigourous Test :-)
     */
    public void testApp()
    {
        assertTrue( true );
    }
