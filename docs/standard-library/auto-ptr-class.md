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
ms.openlocfilehash: f0c8e0c1f4dc2e1082d5df230c74efafcae24f29
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377984"
---
# <a name="autoptr-class"></a>auto_ptr — Klasa

Otacza inteligentny wskaźnik wokół zasobów, które zapewnia, że zasób zostanie zniszczony automatycznie, kiedy formant opuszcza blok.

Więcej z możliwością `unique_ptr` zastępuje klasy `auto_ptr`. Aby uzyskać więcej informacji, zobacz [unique_ptr — klasa](../standard-library/unique-ptr-class.md).

Aby uzyskać więcej informacji na temat `throw()` i obsługa wyjątków, zobacz [specyfikacje wyjątków (throw)](../cpp/exception-specifications-throw-cpp.md).

## <a name="syntax"></a>Składnia

```cpp
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

### <a name="parameters"></a>Parametry

*right*<br/>
`auto_ptr` z którego można pobrać istniejącego zasobu.

*ptr*<br/>
Wskaźnik, określić, aby zastąpić przechowywany wskaźnik.

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje inteligentny wskaźnik, wywołuje `auto_ptr`, do przydzielonego obiektu. Wskaźnik musi mieć wartość null albo wyznaczenie przydzielonej przez obiekt **nowe**. `auto_ptr` Przeniesienie własności, jeśli jego przechowywanej wartości jest przypisany do innego obiektu. (Jego zastępuje przechowywana wartość po przeniesieniu ze wskaźnikiem typu null). Destruktor dla `auto_ptr<Type>` usuwa przydzielonego obiektu. `auto_ptr<Type>` Gwarantuje, że przydzielony obiekt jest automatycznie usuwany kiedy formant opuszcza blok, nawet za pośrednictwem wyrzuconego wyjątku. Nie należy utworzyć dwa `auto_ptr<Type>` obiekty, które są właścicielami tego samego obiektu.

Możesz przekazać `auto_ptr<Type>` obiekt przez wartość jako argument wywołania funkcji. `auto_ptr` Nie może być elementem dowolnego kontenera standardowej biblioteki. Niezawodne nie da się zarządzać sekwencji `auto_ptr<Type>` obiektów za pomocą kontenera standardowej biblioteki języka C++.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[auto_ptr](#auto_ptr)|Konstruktor dla obiektów typu `auto_ptr`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[element_type](#element_type)|Typ jest synonimem dla parametru szablonu `Type`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[get](#get)|Funkcja elementu członkowskiego zwraca przechowywany wskaźnik `myptr`.|
|[Wydania](#release)|Element członkowski zastępuje przechowywany wskaźnik `myptr` za pomocą wskaźnika o wartości null i zwraca wskaźnik do poprzednio zapisanego.|
|[Resetuj](#reset)|Funkcja elementu członkowskiego oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość przechowywany wskaźnik `myptr` zmiany w wyniku wywołania funkcji. Następnie zastępuje przechowywany wskaźnik przy użyciu *ptr*.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Operator przypisania przeniesienia własności z jedną `auto_ptr` obiektu do drugiego.|
|[operator*](#op_star)|Operator dereferencji dla obiektów typu `auto_ptr`.|
|[operator->](#op_arrow)|Operator umożliwiające dostęp do elementu członkowskiego.|
|[Operator auto_ptr\<innych >](#op_auto_ptr_lt_other_gt)|Rzutuje z jednego rodzaju `auto_ptr` do innego rodzaju elementu `auto_ptr`.|
|[Operator auto_ptr_ref\<innych >](#op_auto_ptr_ref_lt_other_gt)|Rzutuje z `auto_ptr` do `auto_ptr_ref`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="auto_ptr"></a>  auto_ptr::auto_ptr

Konstruktor dla obiektów typu `auto_ptr`.

```cpp
explicit auto_ptr(Type* ptr  = 0) throw();

auto_ptr(auto_ptr<Type>& right) throw();

auto_ptr(auto _ptr_ref<Type> right) throw();

template <class Other>
auto _ptr(auto _ptr<Other>& right) throw();
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik do obiektu, `auto_ptr` hermetyzuje.

*right*<br/>
`auto_ptr` Obiektu do skopiowania przez konstruktora.

### <a name="remarks"></a>Uwagi

Pierwszy magazynów Konstruktor *ptr* w `myptr`, przechowywany wskaźnik do przydzielonego obiektu. Drugi Konstruktor przenosi własność wskaźnika przechowywania w *prawo*, przechowując *prawo*. [Zwolnij](#release) w `myptr`.

Trzeci Konstruktor zachowuje się taka sama jak druga Strona, z tą różnicą, że przechowuje `right`. `ref`. `release` w `myptr`, gdzie `ref` odwołanie znajduje się w `right`.

Konstruktor szablon działa tak samo jak drugi Konstruktor, pod warunkiem, że wskaźnik do `Other` można niejawnie przekonwertować na wskaźnik do `Type`.

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

## <a name="element_type"></a>  auto_ptr::ELEMENT_TYPE

Typ jest synonimem dla parametru szablonu `Type`.

```cpp

typedef Type element  _type;
```

## <a name="get"></a>  auto_ptr::Get

Funkcja elementu członkowskiego zwraca przechowywany wskaźnik `myptr`.

```cpp
Type *get() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany wskaźnik `myptr`.

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

## <a name="op_eq"></a>  auto_ptr::operator =

Operator przypisania przeniesienia własności z jedną `auto_ptr` obiektu do drugiego.

```cpp
template <class Other>
auto_ptr<Type>& operator=(auto_ptr<Other>& right) throw();
auto_ptr<Type>& operator=(auto_ptr<Type>& right) throw();
auto_ptr<Type>& operator=(auto_ptr_ref<Type> right) throw();
```

### <a name="parameters"></a>Parametry

*right*<br/>
Obiekt typu `auto_ptr`.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `auto_ptr<Type>`.

### <a name="remarks"></a>Uwagi

Przypisanie oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy przechowywany wskaźnik `myptr` zmiany wyniku przypisania. Następnie przekazuje własność wskaźnika przechowywania w *prawo*, przechowując *prawo*.[ Zwolnij](#release) w `myptr`. Funkcja zwraca  __\*to__.

### <a name="example"></a>Przykład

Na przykład użycie operatora składowej zobacz [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_star"></a>  auto_ptr::operator *

Operator dereferencji dla obiektów typu `auto_ptr`.

```cpp
Type& operator*() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `Type` będący właścicielem wskaźnika.

### <a name="remarks"></a>Uwagi

Zwraca operatora pośredniego `*` [uzyskać](#get). Dzięki temu przechowywany wskaźnik nie może być zerowy.

### <a name="example"></a>Przykład

Na przykład jak używać funkcji składowej zobacz [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_arrow"></a>  auto_ptr::operator-&gt;

Operator umożliwiające dostęp do elementu członkowskiego.

```cpp
Type * operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Element członkowski obiektu, `auto_ptr` jest właścicielem.

### <a name="remarks"></a>Uwagi

Zwraca operatora wyboru [uzyskać](#get)`( )`, dzięki czemu wyrażenie *ap*-> **elementu członkowskiego** działa tak samo jak ( *ap*. **Pobierz**()) -> **elementu członkowskiego**, gdzie *ap* jest obiektem klasy `auto_ptr` \< **typu**>. Dzięki temu przechowywany wskaźnik nie może być null, i `Type` musi być klasy, struktury lub Unii typu z `member` elementu członkowskiego.

### <a name="example"></a>Przykład

Na przykład jak używać funkcji składowej zobacz [auto_ptr::auto_ptr](#auto_ptr).

## <a name="op_auto_ptr_lt_other_gt"></a>  auto_ptr::operator auto_ptr&lt;innych&gt;

Rzutuje z jednego rodzaju `auto_ptr` do innego rodzaju elementu `auto_ptr`.

```cpp
template <class Other>
operator auto _ptr<Other>() throw();
```

### <a name="return-value"></a>Wartość zwracana

Typ rzutowania operator zwraca `auto_ptr` \< **innych**> (  **\*to**).

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

## <a name="op_auto_ptr_ref_lt_other_gt"></a>  auto_ptr::operator auto_ptr_ref&lt;innych&gt;

Rzutuje z `auto_ptr` do `auto_ptr_ref`.

```cpp
template <class Other>
operator auto _ptr  _ref<Other>() throw();
```

### <a name="return-value"></a>Wartość zwracana

Typ rzutowania operator zwraca **auto_ptr_ref** \< **innych**> (  **\*to**).

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

## <a name="release"></a>  auto_ptr::Release

Element członkowski zastępuje przechowywany wskaźnik `myptr` za pomocą wskaźnika o wartości null i zwraca wskaźnik do poprzednio zapisanego.

```cpp
Type *release() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wcześniej przechowywany wskaźnik.

### <a name="remarks"></a>Uwagi

Element członkowski zastępuje przechowywany wskaźnik `myptr` za pomocą wskaźnika o wartości null i zwraca wskaźnik do poprzednio zapisanego.

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

## <a name="reset"></a>  auto_ptr::reset

Funkcja elementu członkowskiego oblicza wyrażenie `delete myptr`, ale tylko wtedy, gdy wartość przechowywany wskaźnik `myptr` zmiany w wyniku wywołania funkcji. Następnie zastępuje przechowywany wskaźnik przy użyciu `ptr`.

```cpp
void reset(Type* ptr = 0);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik, określić, aby zastąpić przechowywany wskaźnik `myptr`.

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[unique_ptr, klasa](../standard-library/unique-ptr-class.md)<br/>
