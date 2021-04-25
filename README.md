# Restuarent-Management-System
package restaurantmanagementsystem;

public class Restaurantmanagementsystem {

    public static void main(String[] args) {
        FoodItem fi1= new FoodItem("101","Chainish",100,500.00);
		Restaurant r1= new Restaurant("kotumBari","Sylhet");
		System.out.println("Restaurant name:"+r1.getName());
		System.out.println("Restaurant location:"+r1.getLocation());
		fi1.showDetails();
		
		Employee e1 = new Employee();
		e1.setEmpId(101);
		e1.setName("joy");
		e1.setSalary(500.00);
		System.out.println("Employee id:"+e1.getEmpId());
		System.out.println("Employee Name:"+e1.getName());
		System.out.println("Employee Salary:"+e1.getSalary());
		
		FoodCourt fc1= new FoodCourt();
		fc1.insertEmployee(e1);
		fc1.showAllEmployees();
		
		fc1.insertRestaurant(r1);
		fc1.showAllRestaurants();
		
	    MainDish m1= new MainDish("101","Chainish",10,500,"Pizza");
		m1.showDetails();
		
		Appetiziers a1= new Appetiziers("101","Chainish",10,500,"large");
		a1.showDetails();
		
		
	}
}
    package restaurantmanagementsystem;
public class Restaurant implements FoodItemOperations{
	
	private String name;
	private String location;
	FoodItem fooditems[];
	public Restaurant()
	{
		
	}
	public Restaurant(String name,String location)
	{
		this.name=name;
		this.location=location;
		
	}
	public void setName(String name)
	{
		this.name=name;
	}
	public void setLocation(String location)
	{
		this.location=location;
	}
	
    public String getName()
    {
        return this.name;
    }
	public String getLocation()
    {
        return this.location;
    }
	
    public void insertFoodItem(FoodItem f)
    {
        int flag = 0;
        for(int i =0; i<fooditems.length;i++)
        {
            if(fooditems[i]==null)
            {
                fooditems[i] =f;
                flag = 1;
                break;
            }
        }
        if(flag == 1)
        {
            System.out.println("Food Items added");
        }
        else
        {
            System.out.println("Food Items not added");
        }
    }
    public void removeFoodItem(FoodItem f)
    {
        int flag = 0;
        for(int i = 0; i<fooditems.length; i++)
        {
            if(fooditems[i] ==f)
            {
                fooditems[i] = null;
                flag = 1;
                break;
            }
        }
        if(flag == 1)
        {
            System.out.println("food items remove");
        }
        else
        {
            System.out.println("food items remove");
        }
    }
	public FoodItem getFoodItem(String fid)
	{
		return null;
	}
    public void showAllFoodItems()
    {
        for(int i = 0; i<fooditems.length; i++)
        {
			
		
			System.out.println("food id is: "+fooditems[i].getFid());
            System.out.println("food name is: "+fooditems[i].getName());
            System.out.println(" available quantity:"+fooditems[i].getAvailableQuantity());
			System.out.println("food price: "+fooditems[i].getPrice());
			
        }
    }
}
package restaurantmanagementsystem;

public class MainDish extends FoodItem{
	private String category;
	public MainDish(String fid,String name,int availableQuantity,double price,String category)
	{
		super(fid,name,availableQuantity,price);
		this.category=category;
		
	}
	public void setCategory(String category)
	{
		this.category=category;
	}
	public String getCategory()
	{
		return this.category;
	}
	public void showDetails()
	{
		System.out.println("Method Override");
	}
	
}
package restaurantmanagementsystem;
public class FoodItem{
	private String fid;
	private String name;
	private int availableQuantity;
	private double price;
	
	public FoodItem()
	{
	}
	public FoodItem( String fid,String name,int availableQuantity,double price)
	{
		this.fid=fid;
		this.name=name;
		this.availableQuantity=availableQuantity;
		this.price=price;
	}
	public void setFid(String fid)
	{
		this.fid=fid;
	}
	public void setName(String name)
	{
		this.name=name;
	}
	public void setAvailableQuantity(int availableQuantity)
	{
		this.availableQuantity=availableQuantity;
	}
	public void setPrice(double price)
	{
		this.price=price;
	}
	
	public String getFid()
	{
		return this.fid;
	}
	public String getName()
	{
		return this.name;
	}
	public int getAvailableQuantity()
	{
		return this.availableQuantity;
	}
	public double getPrice()
	{
		return this.price;
	}
	public void showDetails()
	{
		System.out.println( "Food id :"+getFid());
		System.out.println( "Food Name:"+getName());
		System.out.println( "Food ability:"+getAvailableQuantity());
		System.out.println( "Food price:"+getPrice());
		
		
	}
	
}
package restaurantmanagementsystem;

public class FoodCourt implements EmployeeOperations,RestaurantOperations{
	
	Employee employees[];
	Restaurant restaurants[];
	public FoodCourt()
	
	{
		
	}
	public void insertEmployee(Employee employee)
    {
        int flag = 0;
        for(int i =0; i<employees.length;i++)
        {
            if(employees[i]==null)
            {
                employees[i] = employee;
                flag = 1;
                break;
            }
        }
        if(flag == 1)
        {
            System.out.println("Employee inserted");
        }
        else
        {
            System.out.println("employee can not inserted");
        }
    }
    public void removeEmployee(Employee employee)
    {
        int flag = 0;
        for(int i = 0; i<employees.length; i++)
        {
            if(employees[i] ==employee)
            {
                employees[i] = null;
                flag = 1;
                break;
            }
        }
        if(flag == 1)
        {
            System.out.println("employee remove");
        }
        else
        {
            System.out.println("employee not remove");
        }
    }
   public void showAllEmployees()
    {
        for(int i = 0; i<employees.length; i++)
        {
            System.out.println("employee name is: "+employees[i].getName());
            System.out.println("emplpoyee ID is "+employees[i].getEmpId());
			System.out.println("employee salary is: "+employees[i]. getSalary());
        }
	}
		public void insertRestaurant(Restaurant restaurant)
    {
        int flag = 0;
        for(int i =0; i<restaurants.length;i++)
        {
            if(restaurants[i]==null)
            {
                restaurants[i] = restaurant;
                flag = 1;
                break;
            }
        }
        if(flag == 1)
        {
            System.out.println("restaurants added");
        }
        else
        {
            System.out.println("restaurants not added");
        }
    }
    public void removeRestaurant(Restaurant restaurant)
    {
        int flag = 0;
        for(int i = 0; i<restaurants.length; i++)
        {
            if(restaurants[i] ==restaurant)
            {
               restaurants[i] = null;
                flag = 1;
                break;
            }
        }
        if(flag == 1)
        {
            System.out.println("restaurants remove");
        }
        else
        {
            System.out.println("restaurants not remove");
        }
	}
	public Employee getEmployee(int empId){
		return null;
	}
    
    public void showAllRestaurants()
    {
        for(int i = 0; i<restaurants.length; i++)
        {
            System.out.println("restaurant name is: "+restaurants[i].getName());
            System.out.println("restaurant location "+restaurants[i].getLocation());
	    }
    }
	}
	package restaurantmanagementsystem;


public class Employee
{
	private int empId;
	private String name;
	private double salary;

	public Employee()
	{
		
	}
	public void Employee(int empId,String name,double salary)
	{     
	     this.empId=empId;
		 this.name = name;
		 this.salary=salary;
	}
	public void setEmpId(int empId)
    {
        this.empId =empId;
    }
	 public void setName(String name)
    {
        this.name = name;
    }
	public void setSalary(double salary)
	{
		this.salary=salary;
	}
    public int getEmpId()
    {
        return empId;
    }
    public String getName()
    {
        return name;
    }
	public double getSalary()
    {
        return salary;
    }
}
package restaurantmanagementsystem;


public class Appetiziers extends FoodItem{
	private String size;
	public Appetiziers(String fid,String name,int availableQuantity,double price,String size)
	{
		super(fid,name,availableQuantity,price);
		this.size=size;
		
	}
	public void setSize(String size)
	{
		this.size=size;
	}
	public String getSize()
	{
		return this.size;
	}
	public void showDetails()
	{
		System.out.println("Method overriding");
		
	}
	
	
}
package restaurantmanagementsystem;


public interface RestaurantOperations
{
	public void insertRestaurant (Restaurant r);
	public void removeRestaurant(Restaurant r);
	public void showAllRestaurants();
}
package restaurantmanagementsystem;


public interface FoodItemOperations
{
	void insertFoodItem (FoodItem f);
	void removeFoodItem(FoodItem f);
	public FoodItem getFoodItem(String fid);
	void showAllFoodItems();
}
package restaurantmanagementsystem;


public interface EmployeeOperations
{
    public void insertEmployee(Employee e);
	public void removeEmployee(Employee e);
	public Employee getEmployee(int empId);
	public void showAllEmployees();
}

	 

