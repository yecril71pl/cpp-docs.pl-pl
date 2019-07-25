---
title: auto_ptr — Klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::auto_ptr
- memory/std::auto_ptr::element_type
- memory/std::auto_ptr::get
- memory/std::auto_ptr::release
- memory/std::auto_ptr::reset
helpviewer_keywords:
- std::auto_ptr [C++]
- std::auto_ptr [C++], element_type
- std::auto_ptr [C++], get
- std::auto_ptr [C++], release
- std::auto_ptr [C++], reset
ms.assetid: 7f9108b6-9eb3-4634-b615-cf7aa814f23b
ms.openlocfilehash: 14841662235f075d74120673208dd54531763c09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456709"
---
# <a name="autoptr-class"></a>auto_ptr — Klasa

Otacza inteligentny wskaźnik wokół zasobu, który zapewnia, że zasób jest niszczony automatycznie, gdy kontrolka opuszcza blok.

`unique_ptr` Klasa`auto_ptr`o większej obsłuży. Aby uzyskać więcej informacji, zobacz [Klasa unique_ptr](../standard-library/unique-ptr-class.md).

Aby uzyskać więcej informacji `throw()` na temat obsługi wyjątków, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Składnia

```cpp
class auto_ptr {
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

### <a name="parameters"></a>Parametry

*Kliknij*\
`auto_ptr` Z którego ma zostać pobrany istniejący zasób.

*PTR*\
Wskaźnik określony do zastępowania przechowywanego wskaźnika.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje inteligentny wskaźnik o nazwie `auto_ptr`do przydzielnego obiektu. Wskaźnik musi mieć wartość null lub być obiektem przydzielonym przez **Nowy**. Przenosi `auto_ptr` własność, jeśli jej przechowywana wartość jest przypisana do innego obiektu. (Zastępuje wartość przechowywaną po przeniesieniu ze wskaźnikiem o wartości null). Destruktor dla `auto_ptr<Type>` usuwa przydzielony obiekt. `auto_ptr<Type>` Zapewnia, że przydzielony obiekt jest automatycznie usuwany, gdy kontrolka opuszcza blok, nawet przez zgłoszony wyjątek. Nie należy tworzyć dwóch `auto_ptr<Type>` obiektów, które są właścicielami tego samego obiektu.

Można przekazać `auto_ptr<Type>` obiekt według wartości jako argumentu wywołania funkcji. `auto_ptr` Nie może być elementem żadnego kontenera biblioteki standardowej. Nie można w sposób `auto_ptr<Type>` C++ niezawodny zarządzać sekwencją obiektów przy użyciu kontenera biblioteki standardowej.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[auto_ptr](#auto_ptr)|Konstruktor dla obiektów typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ jest synonimem dla parametru `Type`szablonu.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[get](#get)|Funkcja członkowska zwraca przechowywany wskaźnik `myptr`.|
|[Usuwanie](#release)|Element członkowski zastępuje przechowywany wskaźnik `myptr` wskaźnikiem o wartości null i zwraca poprzednio przechowywany wskaźnik.|
|[zresetować](#reset)|Funkcja członkowska oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość `myptr` przechowywanego wskaźnika zmienia się w wyniku wywołania funkcji. Następnie zamieni zapisany wskaźnik na *PTR*.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_eq)|Operator przypisania, który przenosi własność z jednego `auto_ptr` obiektu do drugiego.|
|[zakład](#op_star)|Operator dereferencji dla obiektów typu `auto_ptr`.|
|[operator — >](#op_arrow)|Operator zezwalający na dostęp do elementu członkowskiego.|
|[Operator auto_ptr\<inne >](#op_auto_ptr_lt_other_gt)|Rzutuje z jednego rodzaju `auto_ptr` do innego `auto_ptr`rodzaju.|
|[operator auto_ptr_ref\<inne >](#op_auto_ptr_ref_lt_other_gt)|Rzutuje od elementu `auto_ptr` `auto_ptr_ref`do.|

### <a name="auto_ptr"></a>auto_ptr

Konstruktor dla obiektów typu `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do obiektu, który `auto_ptr` hermetyzuje.

*Kliknij*\
`auto_ptr` Obiekt, który ma zostać skopiowany przez Konstruktor.

#### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wartość *PTR* w `myptr`, przechowywany wskaźnik do przydzielony obiekt. Drugi Konstruktor przenosi własność wskaźnika przechowywanego *po prawej stronie*, przechowując *prawo*. [wydanie](#release) w `myptr`.

Trzeci Konstruktor zachowuje się tak samo, jak w drugim, z tą różnicą `right`, że są przechowywane. `ref`. `release`w `myptr`, gdzie `ref` to odwołanie przechowywane w `right`.

Konstruktor szablonów działa tak samo jak drugi Konstruktor, pod warunkiem, że wskaźnik `Other` może być niejawnie konwertowany na wskaźnik do. `Type`

#### <a name="example"></a>Przykład

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

### <a name="element_type"></a>element_type

Typ jest synonimem dla parametru `Type`szablonu.

```cpp
typedef Type element  _type;
```

### <a name="get"></a>Pobierz

Funkcja członkowska zwraca przechowywany wskaźnik `myptr`.

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>Wartość zwracana

Przechowywany wskaźnik `myptr`.

#### <a name="example"></a>Przykład

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

### <a name="op_eq"></a>operator =

Operator przypisania, który przenosi własność z jednego `auto_ptr` obiektu do drugiego.

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt typu `auto_ptr`.

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `auto_ptr<Type>`.

#### <a name="remarks"></a>Uwagi

Przypisanie oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy przechowywany wskaźnik `myptr` zmienia się w wyniku przypisania. Następnie przenosi własność wskaźnika przechowywanego *po prawej stronie*, przechowując *prawo*. [wydanie](#release) w `myptr`. Funkcja zwraca  __\*ten__wynik.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem użycia operatora elementu członkowskiego, zobacz [auto_ptr](#auto_ptr).

### <a name="op_star"></a>zakład

Operator dereferencji dla obiektów typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `Type` , którego właścicielem jest wskaźnik.

#### <a name="remarks"></a>Uwagi

Operator pośredni zwraca wartość `*` [Get](#get). W związku z tym, składowany wskaźnik nie może mieć wartości null.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem korzystania z funkcji składowej, zobacz [auto_ptr](#auto_ptr).

### <a name="op_arrow"></a>zakład&gt;

Operator zezwalający na dostęp do elementu członkowskiego.

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>Wartość zwracana

Element członkowski obiektu, `auto_ptr` do którego należy.

#### <a name="remarks"></a>Uwagi

Operator wyboru zwraca wartość [Get](#get)`( )`, dzięki czemu**element członkowski** *AP*-> wyrażenia zachowuje się tak samo jak ( *AP*). **Pobierz** ())-> **element członkowski**, gdzie *AP* jest obiektem `auto_ptr` **typu**klasy \< >. W związku z tym, składowany wskaźnik nie może mieć `Type` wartości null i musi być klasą, strukturą lub typem `member` Unii z elementem członkowskim.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem korzystania z funkcji składowej, zobacz [auto_ptr](#auto_ptr).

### <a name="op_auto_ptr_lt_other_gt"></a>auto_ptr&lt;innych operatorów&gt;

Rzutuje z jednego rodzaju `auto_ptr` do innego `auto_ptr`rodzaju.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Operator rzutowania typu zwraca `auto_ptr` \< **inne**> (  **\*this**).

#### <a name="example"></a>Przykład

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

### <a name="op_auto_ptr_ref_lt_other_gt"></a>auto_ptr_ref&lt;innych operatorów&gt;

Rzutuje od elementu `auto_ptr` `auto_ptr_ref`do.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Operator rzutowania typu zwraca **auto_ptr_ref** \< **inne**> (  **\*this**).

#### <a name="example"></a>Przykład

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

### <a name="release"></a>Usuwanie

Element członkowski zastępuje przechowywany wskaźnik `myptr` wskaźnikiem o wartości null i zwraca poprzednio przechowywany wskaźnik.

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Poprzednio przechowywany wskaźnik.

#### <a name="remarks"></a>Uwagi

Element członkowski zastępuje przechowywany wskaźnik `myptr` wskaźnikiem o wartości null i zwraca poprzednio przechowywany wskaźnik.

#### <a name="example"></a>Przykład

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

### <a name="reset"></a>zresetować

Funkcja członkowska oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość `myptr` przechowywanego wskaźnika zmienia się w wyniku wywołania funkcji. Następnie zastąpi przechowywany wskaźnik `ptr`.

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik określony do zastępowania przechowywanego wskaźnika `myptr`.

#### <a name="example"></a>Przykład

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

## <a name="see-also"></a>Zobacz także

[unique_ptr, klasa](../standard-library/unique-ptr-class.md)
