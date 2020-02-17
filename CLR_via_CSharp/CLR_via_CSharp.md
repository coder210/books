# CLR��ִ��ģ��
**CRL**(������������ʱ)��һ�����ɶ��ֱ������ʹ�õ�**����ʱ**
 
**CTS**(Common Type System ͨ������ϵͳ)�ƶ�һ����ʽ�淶���������͵Ķ������Ϊ

**CLS**(Common Language Specification �������Թ淶)������һ����С���ܼ�,�κα�����ֻ��֧��������ܼ�,���ɵ����Ͳ��ܼ�������������CLS������CLR���������ɵ����

---

## ��4�� ���ͻ���
CRLҪ���������Ͷ���System.Object����, ��������������ĸ��඼��`Object`
```c#
// ��ʽ������Object
class Employee{
	...
}

// ��ʽ������Object
class Employee : System.Object{
	...
}
```

<br>

System.Object�Ĺ�������
- Equals: �ж��������������ͬ��ֵ
- GetHashCode: ���ض����ֵ�Ĺ�ϣ��
- ToString: Ĭ�Ϸ������͵���������
- GetType: ���ش�Type������һ�����͵�ʵ��


new�������ͼ������л������ж��������ʵ���ֶ���Ҫ���ֽ���,�ڶ���ÿһ��������Ҫ�����Ա,�����Ͷ���ָ��(type object pointer)��ͬ��������(sync block index),CLR������Щ�����Ա�����С,ͬ��������ֶ�ҲҪ�����С

CLR�����������ջ���,����newû�ж�Ӧdelete������
  
CLRͨ��GetType������ȡ���������

C#��Ҫ�κι�����﷨���ɽ�����ת���������κθ�����,��ת����**��ʽ��ȫ**.��ת����Ҫ��ʾת��,����**����ȫ**��,�������ͨ����ת��ʧ�ܻ��׳�**InvalidCastException**�쳣
```c#
// ��ʽת��
Object o = new Pserson();
// ��ʾת��
Person p = o as Person;
```
<br/>

**is**�������Ƿ����ָ������,����true����ݶ�false�򲻼���, **��Զ�����׳��쳣**. �������Ϊnull�����Ƿ���false. 
���������������ͼ��,���������Ӱ��
is ��һ�μ���ж�o�Ƿ����Person�������
��oת��Person����,CLR������һ�����ͼ��,����C#�ṩ**as**������
```c#
if (o is Person){
	Person p = (Person)o
	// ��if���ʹ��p
}
```
<br/>

**as**�������Ƿ����ָ������,���ض�����������ݶ�����null�򲻼���, **��Զ�����׳��쳣**.
��������һ�����ͼ��,����asת��ΪPerson����ʱ
```c#
Person p = o as Person
if (p != null){
	// ʹ��p
}
```
<br/>

�����ռ����ص����ͽ��з���,����ͨ�������ռ䶨λ����.��΢��**Microsoft**�����ռ���һ����**Widget**,�����ǵ�**Wintellect**ͬ����**widget**��, ��ͬʱ������������ռ�,�ͻ���ɱ������**CS0140: Widget��Microsoft.Widget��Wintellect.Widget**֮��Ĳ���ȷ����
```c#
using Microsoft;
using Wintellect;

public static viod Main()
{
	// ����ȷ����
	Widget w = new Widget();
}
```

��Ҫȷ�������ռ�

```c#
using Microsoft;
using Wintellect;

// ΪWintellect.Widget�����
using WintellectWidget = Wintellect.Widget;

public static viod Main()
{
	// ����ȷ����
	Widget w = new WintellectWidget();
}
```

<br/>
<br/>

### 4.4����ʱ���໥״̬
![ջͼ](./images/CLR_via_CSharp/4.4_1.png)

1. ���ַ������в�����û��joe����ַ���,�еĻ�ֱ�ӽ�**�ڴ��ַ**��ֵ��name, û�оͳ�ʼ��һ���ڴ�ռ����joe�ַ���,��**�ڴ��ַ**��ֵ��name
2. ��name��ֵѹ��ջ��
3. ����M2����

![ջͼ](./images/CLR_via_CSharp/4.4_2.png)

1. ������length, tally�����ڴ�ռ�, �����߳�ջ��**s**ʵ��,�����ȸ�ֵ��length
2. ִ��M2�����ڵĴ���
3. ����reture, ��Ҫ��**s**ʵ�γ�ջ
4. ͬ��ִ����M1��������ҲҪ��ջ 

������������δ��ʽ��ʼ���ľֲ�����, C#�ᱨ�������Ϣ: **ʹ����δ��ֵ��nn����**

---

## ��5�� ��Ԫ���͡��������ͺ�ֵ����
������ֱ��֧�ֵ��������ͳ�Ϊ**��Ԫ����**����Ԫ����ֱ��ӳ�䵽Framework���(FCL)�д��ڵ����͡���C#��intֱ��ӳ�䵽System.Int32����,���ɵ�IL��ȫ��ͬ
```C#
int				a = 0; // a���
System.Int32			a = 0; // b
int				a =  new int(); // c
System.Int32		        a =  new System.Int32(); //d���
```

<br/>

#### ��Ԫ�������Ӧ��FCL����ͼ

![ͼ��](./images/CLR_via_CSharp/5.1_1.png)
