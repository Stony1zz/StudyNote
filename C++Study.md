```c++
#include<iostream>
#include<string>
 using namespace std;
 #define N  50
 
 class Animal//动物类
 {
 public:
 	Animal();
 	~Animal();
 	void Animal::eat();
     virtual void Animal::show();
 
 private:
 
 
 protected:
 string name;
 };
 Animal::Animal()
 {
 	name = "animal";
 }
 Animal::~Animal()
 {
 
 }
 void Animal::eat()
 {
 	cout<<"我能吃东西"<<endl;
 }
 void Animal::show()
 {
 	cout<<name<<endl;
	cout<<"我来自动物类。"<<endl;
 }
 
 class Cat : public Animal//猫类
 {
 public:
 	Cat();
 	~Cat();
 	void Cat::eat();
 	virtual void Cat::show();
 	//friend ostream &operator <<(ostream &,const Cat &);
 
 private:
 
 };
 Cat::Cat()
 {
 	name = "cat";
 
 }
 Cat::~Cat()
 {
 
 }
 void Cat::eat()
 {
 	cout<<"我能吃东西"<<endl;
 }
 void Cat::show()
 {
 	cout<<name<<endl;
    cout<<"我来自猫类。"<<endl;
 }
 
 class Garfield : public Cat //加菲猫类
 {
 public:
 Garfield();
 ~Garfield();
 void Garfield::eat();
 void Garfield::show();

 private:
 
 };
 Garfield::Garfield()
 {
 	 name = "Garfield";
 }
 Garfield::~Garfield()
 {
 
 }
 void Garfield::eat()
 {
 	cout<<"我能吃东西"<<endl;
 
 }
 void Garfield::show()
 {
 	cout<<name<<endl;
 	cout<<"我来自加菲猫类。"<<endl;
 }
 
 
 class Father
 {
 public:
 	Father();
 	~Father();
   void Father::show();
 
 protected:
 	string name;
 };
 Father::Father()
 {
 	name="father";
 
 }
 Father::~Father()
 {
 
 }
 void Father::show()
 {
 	cout<<name<<endl;
 }
 
 class Mather
 {
 public:
 	Mather();
 	~Mather();
 	void Mather::show();
 
 protected:
 	string name;
 };
 Mather::Mather()
 {
 	name="mather";
 
 }
 Mather::~Mather()
 {
 
 }
 void Mather::show()
 {
 	cout<<name<<endl;
 }
 
 class Me :public Father ,public Mather
 {
 public:
 	Me();
	~Me();
	void Me::show();
 
 protected:
 	string name;
 };
 Me::Me()
 {
 	name="me";

 }
 Me::~Me()
 {
 
 }
 void Me::show()
 {
 	cout<<name<<endl;
 }
 
 void fmlily()
 {
 	Father f1;
	Mather m1;
 	Me m;
 	f1.show();
 	m1.show();
    m.show();
 }
 
 
 template <class T> //类模板
 void ptd(T a)//类模板调用函数
 {
 	T  *ballisticmissile= &a;
 	ballisticmissile->show();
 
 }
 void main()
 {
  
 	Cat    d;
 	Animal a;
	Garfield w;
 	ptd(d);
 	ptd(a);
 	ptd(w);
 
 	cout<<"--------------------------------------------------"<<endl;
 	fmlily();
 }
 ```