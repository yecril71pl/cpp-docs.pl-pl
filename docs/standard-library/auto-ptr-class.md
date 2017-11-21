---
title: "auto_ptr — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
dev_langs: C++
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
caps.latest.revision: "26"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c7411a11a396627fb01d1dad1d47dc957ce968a7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="autoptr-class"></a>auto_ptr — Klasa
Zawija się wokół zasobów, które zapewnia, że zasób zostanie zniszczony automatycznie, gdy formant opuszcza blok wskaźnika inteligentnego.  
  
 Więcej funkcją `unique_ptr` zastępuje klasy `auto_ptr`. Aby uzyskać więcej informacji, zobacz [unique_ptr — klasa](../standard-library/unique-ptr-class.md).  
  
 Aby uzyskać więcej informacji na temat `throw()` i obsługa wyjątków, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md).  
  
## <a name="syntax"></a>Składnia  
 ```   
class auto_ptr {
public:
    typedef Type element_type;
    explicit auto_ptr(Type* ptr = 0) throw();
    auto_ptr(auto_ptr<Type>& right) throw()
        ;
    template <class Other>
    operator auto_ptr<Other>() throw();
    template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
    template <class Other>
    auto_ptr(auto_ptr<Other>& right);
    auto_ptr<Type>& operator=(auto_ptr<Type>& right);
    ~auto_ptr();
    Type& operator*() const throw();
    Type * operator->()const throw();
    Type *get() const throw();
    Type *release()throw();
    void reset(Type* ptr = 0);
};
```  
#### <a name="parameters"></a>Parametry  
 `right`  
 `auto_ptr` z którego można pobrać istniejący zasób.  
  
 `ptr`  
 Wskaźnik, określić, aby zastąpić przechowywanych wskaźnika.  
  
## <a name="remarks"></a>Uwagi  
 Klasa szablonu opisuje wskaźnika inteligentnego o nazwie `auto_ptr`, do przydzielonego obiektu. Wskaźnik musi być równa albo wartość null lub wyznaczyć przydzielone przez obiekt `new`. `auto_ptr` Przesyła własność, jeśli jego wartość przechowywana jest przypisany do innego obiektu. (Zastępowanego przechowywana wartość po transferu za pomocą wskaźnika null.) Destruktor dla elementu `auto_ptr<Type>` usuwa przydzielonego obiektu. `auto_ptr<Type>` Gwarantuje, że obiekt przydzielony jest automatycznie usuwana, gdy formant opuszcza blok, nawet za pośrednictwem zwrócony wyjątek. Nie należy utworzyć dwa `auto_ptr<Type>` obiekty, które posiadają ten sam obiekt.  
  
 Można przekazać `auto_ptr<Type>` obiektu przez wartość jako argument wywołania funkcji. `auto_ptr` Nie może być elementem każdy kontener standardowa biblioteka. Nie można niezawodnie zarządzać sekwencji `auto_ptr<Type>` obiektów z kontenera standardowa biblioteka C++.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[auto_ptr](#auto_ptr)|Konstruktor dla obiektów typu `auto_ptr`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[ELEMENT_TYPE](#element_type)|Typ jest synonimem parametru szablonu `Type`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Pobierz](#get)|Funkcja członkowska zwraca wskaźnik przechowywanych `myptr`.|  
|[zlecenia](#release)|Element członkowski zastępuje przechowywanych wskaźnika `myptr` za pomocą wskaźnika null i zwraca wskaźnik zapisanych wcześniej.|  
|[Resetowanie](#reset)|Funkcja członkowska oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość wskaźnika przechowywanych `myptr` zmiany w wyniku wywołania funkcji. Następnie zastępuje przechowywanych wskaźnik z `ptr`.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#op_eq)|Operator przypisania przeniesienia własności z jedną `auto_ptr` obiektu do innego.|  
|[operator *](#op_star)|Operator usuwania odwołań dla obiektów typu `auto_ptr`.|  
|[operator ->](#operator-_gt)|Operator umożliwiający dostęp do elementu członkowskiego.|  
|[auto_ptr operatora\<innych >](#op_auto_ptr_lt_other_gt)|Rzutuje z jednego rodzaju `auto_ptr` do innego rodzaju z `auto_ptr`.|  
|[Operator auto_ptr_ref\<innych >](#op_auto_ptr_ref_lt_other_gt)|Rzutuje z `auto_ptr` do `auto_ptr_ref`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<pamięci >  
  
 **Namespace:** Standard  
  
##  <a name="auto_ptr"></a>auto_ptr::auto_ptr  
 Konstruktor dla obiektów typu `auto_ptr`.  
  
```   
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>  
auto _ptr(auto _ptr<Other>& right) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do obiektu który `auto_ptr` hermetyzuje.  
  
 `right`  
 `auto_ptr` Obiektu do skopiowania przez konstruktora.  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy magazynów konstruktora `ptr` w **myptr**, przechowywane wskaźnik do przydzielonego obiektu. Drugi Konstruktor przesyła własność wskaźnika przechowywane w `right`, przechowując `right`. [Zwolnij](#release) w **myptr**.  
  
 Trzeci konstruktora zachowuje się taka sama jak druga Strona, z wyjątkiem tego, że przechowuje **prawo**. `ref`. **Zwolnij** w **myptr**, gdzie `ref` odwołanie znajduje się w `right`.  
  
 Konstruktor szablonu działa tak samo jak drugi Konstruktor, pod warunkiem, że wskaźnik do **innych** można niejawnie przekonwertować na wskaźnik do **typu**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// auto_ptr_auto_ptr.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
class Int   
{  
public:  
   Int(int i)   
   {  
      cout << "Constructing " << ( void* )this  << endl;   
      x = i;  
      bIsConstructed = true;  
   };  
   ~Int( )   
   {  
      cout << "Destructing " << ( void* )this << endl;   
      bIsConstructed = false;  
   };  
   Int &operator++( )   
   {  
      x++;  
      return *this;  
   };  
   int x;  
private:  
   bool bIsConstructed;  
};  
  
void function ( auto_ptr<Int> &pi )  
{  
   ++( *pi );  
   auto_ptr<Int> pi2( pi );  
   ++( *pi2 );  
   pi = pi2;  
}  
  
int main( )   
{  
   auto_ptr<Int> pi ( new Int( 5 ) );  
   cout << pi->x << endl;  
   function( pi );  
   cout << pi->x << endl;  
}  
```  
  
```Output  
Constructing 00311AF8  
5  
7  
Destructing 00311AF8  
```  
  
##  <a name="element_type"></a>auto_ptr::ELEMENT_TYPE  
 Typ jest synonimem parametru szablonu **typu**.  
  
```  
 
typedef Type element  _type;  
```  
  
##  <a name="get"></a>auto_ptr::Get  
 Funkcja członkowska zwraca wskaźnik przechowywanych **myptr**.  
  
```   
Type *get() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik przechowywanych **myptr**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// auto_ptr_get.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
class Int   
{  
public:  
   Int(int i)   
   {  
      x = i;  
      cout << "Constructing " << ( void* )this  << " Value: " << x << endl;   
   };  
   ~Int( )   
   {  
      cout << "Destructing " << ( void* )this << " Value: " << x << endl;   
   };  
  
   int x;  
  
};  
  
int main( )   
{  
   auto_ptr<Int> pi ( new Int( 5 ) );  
   pi.reset( new Int( 6 ) );  
   Int* pi2 = pi.get ( );  
   Int* pi3 = pi.release ( );  
   if (pi2 == pi3)  
      cout << "pi2 == pi3" << endl;  
   delete pi3;  
}  
```  
  
```Output  
Constructing 00311AF8 Value: 5  
Constructing 00311B88 Value: 6  
Destructing 00311AF8 Value: 5  
pi2 == pi3  
Destructing 00311B88 Value: 6  
```  
  
##  <a name="op_eq"></a>auto_ptr::operator =  
 Operator przypisania przeniesienia własności z jedną `auto_ptr` obiektu do innego.  
  
```  
template <class Other>  
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Obiekt typu `auto_ptr`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu typu `auto_ptr` \< **typu**>.  
  
### <a name="remarks"></a>Uwagi  
 Przypisanie oblicza wyrażenie **usunąć myptr**, ale tylko wtedy, gdy wskaźnik przechowywanych **myptr** zmiany wyniku przypisania. Następnie przesyła własność wskaźnika przechowywane w _ *prawej*, przechowując \_ *prawej*. [Zwolnij](#release) w **myptr**. Funkcja zwraca  **\*to**.  
  
### <a name="example"></a>Przykład  
  Na przykład użycie operator członkowski zobacz [auto_ptr::auto_ptr](#auto_ptr).  
  
##  <a name="op_star"></a>auto_ptr::operator *  
 Operator usuwania odwołań dla obiektów typu `auto_ptr`.  
  
```   
Type& operator*() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do obiektu typu **typu** będący właścicielem wskaźnika.  
  
### <a name="remarks"></a>Uwagi  
 Operator pośredni zwraca `*` [uzyskać](#get). W związku z tym przechowywanych wskaźnika nie może mieć wartości null.  
  
### <a name="example"></a>Przykład  
  Na przykład dotyczące używania funkcji członkowskiej zobacz [auto_ptr::auto_ptr](#auto_ptr).  
  
##  <a name="auto_ptr__operator-_gt"></a>auto_ptr::operator-&gt;  
 Operator umożliwiający dostęp do elementu członkowskiego.  
  
```   
Type * operator->() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Element członkowski obiektu, który **auto_ptr** właścicielem.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca operatorem wyboru [uzyskać](#get)`( )`, dzięki czemu wyrażenie *region*-> **elementu członkowskiego** działa tak samo jak ( *region*. **Pobierz**()) -> **elementu członkowskiego**, gdzie *region* jest obiektem klasy `auto_ptr` \< **typu**>. W związku z tym przechowywanych wskaźnika nie może być pusta, i **typu** musi być klasy, struktury lub Unii typu o **elementu członkowskiego** elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
  Na przykład dotyczące używania funkcji członkowskiej zobacz [auto_ptr::auto_ptr](#auto_ptr).  
  
##  <a name="op_auto_ptr_lt_other_gt"></a>auto_ptr::operator auto_ptr&lt;innych&gt;  
 Rzutuje z jednego rodzaju `auto_ptr` do innego rodzaju z `auto_ptr`.  
  
```   
template <class Other>  
operator auto _ptr<Other>() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ rzutowania zwraca operator `auto_ptr` \< **innych**> (  **\*to**).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// auto_ptr_op_auto_ptr.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
int main()  
{  
   auto_ptr<int> pi ( new int( 5 ) );  
   auto_ptr<const int> pc = ( auto_ptr<const int> )pi;  
}  
```  
  
##  <a name="op_auto_ptr_ref_lt_other_gt"></a>auto_ptr::operator auto_ptr_ref&lt;innych&gt;  
 Rzutuje z `auto_ptr` do **auto_ptr_ref**.  
  
```   
template <class Other>  
operator auto _ptr  _ref<Other>() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Typ rzutowania zwraca operator **auto_ptr_ref** \< **innych**> (  **\*to**).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// auto_ptr_op_auto_ptr_ref.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;  
  
class C {
public:
    C(int _i) : m_i(_i) {
    }
    ~C() {
        cout << "~C:  " << m_i << "\n";
    }
    C &operator =(const int &x) {
        m_i = x;
        return *this;
    }
    int m_i;
};
void f(auto_ptr<C> arg) {
};
int main()
{
    const auto_ptr<C> ciap(new C(1));
    auto_ptr<C> iap(new C(2));

    // Error: this implies transfer of ownership of iap's pointer  
    // f(ciap);   
    f(iap); // compiles, but gives up ownership of pointer  

            // here, iap owns a destroyed pointer so the following is bad:  
            // *iap = 5; // BOOM  

    cout << "main exiting\n";
}
```  
  
```Output  
~C:  2  
main exiting  
~C:  1  
```  
  
##  <a name="release"></a>auto_ptr::Release  
 Element członkowski zastępuje przechowywanych wskaźnika **myptr** za pomocą wskaźnika null i zwraca wskaźnik zapisanych wcześniej.  
  
```   
Type *release() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik zapisanych wcześniej.  
  
### <a name="remarks"></a>Uwagi  
 Element członkowski zastępuje przechowywanych wskaźnika **myptr** za pomocą wskaźnika null i zwraca wskaźnik zapisanych wcześniej.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// auto_ptr_release.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
using namespace std;  
  
class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int() {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;

};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```  
  
```Output  
Constructing 00311AF8 Value: 5  
Constructing 00311B88 Value: 6  
Destructing 00311AF8 Value: 5  
pi2 == pi3  
Destructing 00311B88 Value: 6  
```  
  
##  <a name="reset"></a>auto_ptr::reset  
 Funkcji członkowskiej oblicza wyrażenie **usunąć** **myptr**, ale tylko wtedy, gdy wartość wskaźnika przechowywanych **myptr** zmiany w wyniku wywołania funkcji. Następnie zastępuje przechowywanych wskaźnik z **ptr**.  
  
```   
void reset(Type* ptr = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik, określić, aby zastąpić przechowywanych wskaźnika **myptr**.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// auto_ptr_reset.cpp  
// compile with: /EHsc  
#include <memory>  
#include <iostream>  
#include <vector>  
  
using namespace std;

class Int
{
public:
    Int(int i)
    {
        x = i;
        cout << "Constructing " << (void*)this << " Value: " << x << endl;
    };
    ~Int()
    {
        cout << "Destructing " << (void*)this << " Value: " << x << endl;
    };

    int x;
};

int main()
{
    auto_ptr<Int> pi(new Int(5));
    pi.reset(new Int(6));
    Int* pi2 = pi.get();
    Int* pi3 = pi.release();
    if (pi2 == pi3)
        cout << "pi2 == pi3" << endl;
    delete pi3;
}
```  
  
```Output  
Constructing 00311AF8 Value: 5  
Constructing 00311B88 Value: 6  
Destructing 00311AF8 Value: 5  
pi2 == pi3  
Destructing 00311B88 Value: 6  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [unique_ptr — klasa](../standard-library/unique-ptr-class.md)

