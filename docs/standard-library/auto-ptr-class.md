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
ms.openlocfilehash: 6b429b0e5c734f81216c988e372c02021528cffd
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2019
ms.locfileid: "72690029"
---
# <a name="auto_ptr-class"></a>auto_ptr — Klasa

Otacza inteligentny wskaźnik wokół zasobu, który zapewnia, że zasób jest niszczony automatycznie, gdy kontrolka opuszcza blok.

Większa `unique_ptr` Klasa zastępuje `auto_ptr`. Aby uzyskać więcej informacji, zobacz [Klasa unique_ptr](../standard-library/unique-ptr-class.md).

Aby uzyskać więcej informacji o `throw()` i obsłudze wyjątków, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md).

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

*prawa* \
@No__t_0, z którego ma zostać pobrany istniejący zasób.

\ *PTR*
Wskaźnik określony do zastępowania przechowywanego wskaźnika.

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje inteligentny wskaźnik o nazwie `auto_ptr` do przydzielnego obiektu. Wskaźnik musi mieć wartość null lub być obiektem przydzielonym przez **Nowy**. @No__t_0 przenosi własność, jeśli jej przechowywana wartość jest przypisana do innego obiektu. (Zastępuje wartość przechowywaną po przeniesieniu ze wskaźnikiem o wartości null). Destruktor dla `auto_ptr<Type>` usuwa przydzielony obiekt. @No__t_0 zapewnia, że przydzielony obiekt jest automatycznie usuwany, gdy kontrolka opuszcza blok, nawet przez zgłoszony wyjątek. Nie należy tworzyć dwóch `auto_ptr<Type>` obiektów, które są właścicielami tego samego obiektu.

Obiekt `auto_ptr<Type>` można przekazać według wartości jako argumentu wywołania funkcji. @No__t_0 nie może być elementem żadnego kontenera biblioteki standardowej. Nie można w sposób niezawodny zarządzać sekwencją `auto_ptr<Type>` obiektów przy użyciu C++ kontenera biblioteki standardowej.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[auto_ptr](#auto_ptr)|Konstruktor dla obiektów typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[element_type](#element_type)|Typ jest synonimem dla parametru szablonu `Type`.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[get](#get)|Funkcja członkowska zwraca przechowywany `myptr` wskaźnika.|
|[Usuwanie](#release)|Element członkowski zastępuje przechowywany wskaźnik `myptr` ze wskaźnikiem o wartości null i zwraca poprzednio przechowywany wskaźnik.|
|[zresetować](#reset)|Funkcja członkowska oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość przechowywanego wskaźnika `myptr` zmiany w wyniku wywołania funkcji. Następnie zamieni zapisany wskaźnik na *PTR*.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_eq)|Operator przypisania, który przenosi własność z jednego `auto_ptr` obiektu do innego.|
|[zakład](#op_star)|Operator dereferencji dla obiektów typu `auto_ptr`.|
|[operator — >](#op_arrow)|Operator zezwalający na dostęp do elementu członkowskiego.|
|[Operator auto_ptr \<Other >](#op_auto_ptr_lt_other_gt)|Rzutuje z jednego rodzaju `auto_ptr` na inny rodzaj `auto_ptr`.|
|[operator auto_ptr_ref \<Other >](#op_auto_ptr_ref_lt_other_gt)|Rzutuje z `auto_ptr` na `auto_ptr_ref`.|

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

\ *PTR*
Wskaźnik do obiektu, który `auto_ptr` hermetyzuje.

*prawa* \
Obiekt `auto_ptr`, który ma zostać skopiowany przez Konstruktor.

#### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wartość *PTR* w `myptr`, zapisany wskaźnik do przydzielnego obiektu. Drugi Konstruktor przenosi własność wskaźnika przechowywanego *po prawej stronie*, przechowując *prawo*. [wydanie](#release) w `myptr`.

Trzeci Konstruktor zachowuje się tak samo, jak w drugim, z tą różnicą, że przechowuje `right`. `ref`., `release` w `myptr`, gdzie `ref` jest odwołaniem przechowywanym w `right`.

Konstruktor szablonów działa tak samo jak drugi Konstruktor, pod warunkiem, że wskaźnik do `Other` może być niejawnie konwertowany na wskaźnik do `Type`.

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

Typ jest synonimem dla parametru szablonu `Type`.

```cpp
typedef Type element  _type;
```

### <a name="get"></a>Pobierz

Funkcja członkowska zwraca przechowywany `myptr` wskaźnika.

```cpp
Type *get() const throw();
```

#### <a name="return-value"></a>Wartość zwracana

@No__t_0 magazynowany wskaźnik.

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

Operator przypisania, który przenosi własność z jednego `auto_ptr` obiektu do innego.

```cpp
template <class Other>
    auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

#### <a name="parameters"></a>Parametry

*prawa* \
Obiekt typu `auto_ptr`.

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `auto_ptr<Type>`.

#### <a name="remarks"></a>Uwagi

Przypisanie oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy przechowywany wskaźnik `myptr` zmiany w wyniku przypisania. Następnie przenosi własność wskaźnika przechowywanego *po prawej stronie*, przechowując *prawo*. [wydanie](#release) w `myptr`. Funkcja zwraca __\*this__.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem użycia operatora elementu członkowskiego, zobacz [auto_ptr](#auto_ptr).

### <a name="op_star"></a>zakład

Operator dereferencji dla obiektów typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `Type`, do którego należy wskaźnik.

#### <a name="remarks"></a>Uwagi

Operator pośredni zwraca `*`[Get](#get). W związku z tym, składowany wskaźnik nie może mieć wartości null.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem korzystania z funkcji składowej, zobacz [auto_ptr](#auto_ptr).

### <a name="op_arrow"></a>operator — &gt;

Operator zezwalający na dostęp do elementu członkowskiego.

```cpp
Type * operator->() const throw();
```

#### <a name="return-value"></a>Wartość zwracana

Element członkowski obiektu, który `auto_ptr` właścicielem.

#### <a name="remarks"></a>Uwagi

Operator [wyboru zwraca `( )`](#get) , tak aby *AP* -> **element członkowski** nie działał tak samo jak ( *AP*). **Get**()) — > **element członkowski**, gdzie *ap* jest obiektem klasy **`auto_ptr` \< >** . W związku z tym, składowany wskaźnik nie może mieć wartości null, a `Type` musi być klasą, strukturą lub typem Unii z składową `member`.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem korzystania z funkcji składowej, zobacz [auto_ptr](#auto_ptr).

### <a name="op_auto_ptr_lt_other_gt"></a>Operator auto_ptr &lt;Other &gt;

Rzutuje z jednego rodzaju `auto_ptr` na inny rodzaj `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Operator rzutowania typu zwraca `auto_ptr` \< **innych**> ( **\*this**).

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

### <a name="op_auto_ptr_ref_lt_other_gt"></a>operator auto_ptr_ref &lt;Other &gt;

Rzutuje z `auto_ptr` na `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Operator rzutowania typu zwraca **auto_ptr_ref** \< **inne**> ( **\*this**).

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

Element członkowski zastępuje przechowywany wskaźnik `myptr` ze wskaźnikiem o wartości null i zwraca poprzednio przechowywany wskaźnik.

```cpp
Type *release() throw();
```

#### <a name="return-value"></a>Wartość zwracana

Poprzednio przechowywany wskaźnik.

#### <a name="remarks"></a>Uwagi

Element członkowski zastępuje przechowywany wskaźnik `myptr` ze wskaźnikiem o wartości null i zwraca poprzednio przechowywany wskaźnik.

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

Funkcja członkowska oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość przechowywanego wskaźnika `myptr` zmiany w wyniku wywołania funkcji. Następnie zastąpi przechowywany wskaźnik `ptr`.

```cpp
void reset(Type* ptr = 0);
```

#### <a name="parameters"></a>Parametry

\ *PTR*
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
