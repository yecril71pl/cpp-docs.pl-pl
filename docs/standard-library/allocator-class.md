---
title: allocator — Klasa
ms.date: 11/04/2016
f1_keywords:
- memory/std::allocator
- memory/std::allocator::const_pointer
- memory/std::allocator::const_reference
- memory/std::allocator::difference_type
- memory/std::allocator::pointer
- memory/std::allocator::reference
- memory/std::allocator::size_type
- memory/std::allocator::value_type
- memory/std::allocator::address
- memory/std::allocator::allocate
- memory/std::allocator::construct
- memory/std::allocator::deallocate
- memory/std::allocator::destroy
- memory/std::allocator::max_size
- memory/std::allocator::rebind
helpviewer_keywords:
- std::allocator [C++]
- std::allocator [C++], const_pointer
- std::allocator [C++], const_reference
- std::allocator [C++], difference_type
- std::allocator [C++], pointer
- std::allocator [C++], reference
- std::allocator [C++], size_type
- std::allocator [C++], value_type
- std::allocator [C++], address
- std::allocator [C++], allocate
- std::allocator [C++], construct
- std::allocator [C++], deallocate
- std::allocator [C++], destroy
- std::allocator [C++], max_size
- std::allocator [C++], rebind
ms.assetid: 3fd58076-56cc-43bb-ad58-b4b7c9c6b410
ms.openlocfilehash: 09c30eb58655113ef3daa8338829ad43b37bc415
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456406"
---
# <a name="allocator-class"></a>allocator — Klasa

Klasa szablonu opisuje obiekt zarządzający alokacją i zwalnianiem magazynu dla tablic obiektów typu `Type`. Obiekt klasy `allocator` jest domyślnym obiektem alokatora określonym w konstruktorach dla kilku klas szablonu kontenera w C++ standardowej bibliotece.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>Parametry

*Wprowadź*\
Typ obiektu, dla którego magazyn jest przydzielony lub cofnięty przydział.

## <a name="remarks"></a>Uwagi

Wszystkie kontenery biblioteki C++ standardowej mają parametr szablonu, który ma wartość `allocator`domyślną. Konstruowanie kontenera z niestandardowym alokatorem zapewnia kontrolę nad alokacją i zwalnianiem elementów tego kontenera.

Na przykład obiekt alokatora może przydzielić magazyn na stercie prywatnym lub w pamięci współdzielonej, lub może zoptymalizować w przypadku małych lub dużych rozmiarów obiektów. Może również określać, za pomocą dostarczonych przez niego definicji typów, do elementów, do których można uzyskać dostęp za pomocą obiektów specjalnych akcesorów, które zarządzają współdzieloną pamięcią lub wykonują automatyczne odzyskiwanie pamięci. W związku z tym Klasa, która przydziela magazyn przy użyciu obiektu alokatora, powinna używać tych typów do deklarowania wskaźników i obiektów odniesienia, jak C++ kontenery w bibliotece standardowej.

<strong>(Tylko C++ 98/03)</strong> Gdy dziedziczysz z klasy alokatora, musisz podać strukturę rebind, której [](#rebind) `_Other` element typedef odwołuje się do nowo klasy pochodnej.

W ten sposób Alokator definiuje następujące typy:

- [wskaźnik](#pointer) zachowuje się jak wskaźnik do `Type`.

- [const_pointer](#const_pointer) zachowuje się jak stała wskaźnik do `Type`.

- [odwołanie](#reference) zachowuje się jak odwołanie do `Type`.

- [const_reference](#const_reference) zachowuje się jak odwołanie const do `Type`.

Te `Type`s określają formularz, którego wskaźniki i odwołania muszą przyjmować dla przyznanych elementów. ( [Alokator::p ointer](#pointer) nie musi być taki sam jak `Type*` dla wszystkich obiektów alokatora, nawet jeśli ma tę oczywistą definicję klasy `allocator`.)

**C++ 11 i nowsze:**  Aby włączyć operacje przenoszenia w programie przydzielania, należy użyć minimalnego interfejsu alokatora i zaimplementować konstruktora kopiującego, = = i! = operatory, przydzielanie i cofanie alokacji. Aby uzyskać więcej informacji i zapoznać się z [](../standard-library/allocators.md) przykładem, zobacz przydzielanie

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[allocator](#allocator)|Konstruktory używane do `allocator` tworzenia obiektów.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[const_pointer](#const_pointer)|Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez Alokator.|
|[const_reference](#const_reference)|Typ, który dostarcza stałe odwołanie do typu obiektu zarządzanego przez Alokator.|
|[difference_type](#difference_type)|Typ całkowity ze znakiem, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez Alokator.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez Alokator.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do typu obiektu zarządzanego przez Alokator.|
|[size_type](#size_type)|Typ całkowity bez znaku, który może reprezentować długość dowolnej sekwencji, która może być przydzielona przez obiekt klasy `allocator` szablonu.|
|[value_type](#value_type)|Typ, który jest zarządzany przez program przydzielający.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[address](#address)|Znajduje adres obiektu, którego wartość jest określona.|
|[allocate](#allocate)|Przydziela blok pamięci wystarczająco duży, aby można było przechowywać co najmniej określoną liczbę elementów.|
|[construct](#construct)|Konstruuje określony typ obiektu pod określonym adresem, który jest zainicjowany z określoną wartością.|
|[alokowany](#deallocate)|Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.|
|[destroy](#destroy)|Wywołuje destruktor obiektów bez cofania przydziału pamięci, w której zapisano obiekt.|
|[max_size](#max_size)|Zwraca liczbę elementów typu `Type` , które mogą być przydzielone przez obiekt klasy `allocator` przed użyciem wolnej pamięci.|
|[rebind](#rebind)|Struktura, która umożliwia Alokator dla obiektów jednego typu do przydzielania magazynu dla obiektów innego typu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator=](#op_eq)|Przypisuje `allocator` jeden obiekt do `allocator` innego obiektu.|

### <a name="address"></a>Ulica

Znajduje adres obiektu, którego wartość jest określona.

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

#### <a name="parameters"></a>Parametry

*użyte*\
Wartość const lub niestała obiektu, którego adres jest wyszukiwany.

#### <a name="return-value"></a>Wartość zwracana

Stała lub nadana nadana nieodpowiedniemu wskaźnikowi do obiektu, który znajduje się odpowiednio, stała lub nierówna wartość.

#### <a name="remarks"></a>Uwagi

Funkcje członkowskie zwracają adres *Val*, w formie, którą wskaźniki muszą wykonać w celu przydzielenia elementów.

#### <a name="example"></a>Przykład

```cpp
// allocator_address.cpp
// compile with: /EHsc
#include <memory>
#include <algorithm>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 8;
   v1Ptr = v1Alloc.address( *find(v1.begin( ), v1.end( ), k) );
   // v1Ptr = v1Alloc.address( k );
   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 8.
```

### <a name="allocate"></a>alokacji

Przydziela blok pamięci wystarczająco duży, aby można było przechowywać co najmniej określoną liczbę elementów.

```cpp
pointer allocate(size_type count, const void* _Hint);
```

#### <a name="parameters"></a>Parametry

*liczbą*\
Liczba elementów, dla których należy przydzielyć wystarczającą ilość miejsca do magazynowania.

*_Hint*\
Stała wskaźnikiem, który może pomóc obiektowi alokatora, spełnia żądanie dotyczące magazynu przez lokalizowanie adresu obiektu przydzielonego przed żądaniem.

#### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielnego obiektu lub wartości null, jeśli pamięć nie została przypisana.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska przydziela magazyn dla tablicy elementów count typu `Type`przez wywoływanie operatora new (*Count*). Zwraca wskaźnik do przydzielony obiekt. Argument wskazówki pomaga niektórym przydziałom w ulepszaniu lokalizacji odniesienia; prawidłowy wybór to adres obiektu wcześniej przydzielonego przez ten sam obiekt alokatora, który nie został jeszcze cofnięty. Aby nie podawać żadnej wskazówki, zamiast tego użyj argumentu wskaźnika o wartości null.

#### <a name="example"></a>Przykład

```cpp
// allocator_allocate.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   allocator<int> v1Alloc;
   allocator<int>::pointer v1aPtr;
   v1aPtr = v1Alloc.allocate ( 10 );

   int i;
   for ( i = 0 ; i < 10 ; i++ )
   {
      v1aPtr[ i ] = i;
   }

   for ( i = 0 ; i < 10 ; i++ )
   {
      cout << v1aPtr[ i ] << " ";
   }
   cout << endl;
   v1Alloc.deallocate( v1aPtr, 10 );
}
```

```Output
0 1 2 3 4 5 6 7 8 9
```

### <a name="allocator"></a>Alokator

Konstruktory używane do tworzenia obiektów alokatora.

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
    allocator(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt alokatora, który ma zostać skopiowany.

#### <a name="remarks"></a>Uwagi

Konstruktor niczego nie robi. Ogólnie rzecz biorąc, obiekt alokatora zbudowany z innego obiektu alokatora powinien porównać go z nim i umożliwiać Rozmieszanie alokacji obiektów i zwalnianie między dwoma obiektami alokatora.

#### <a name="example"></a>Przykład

```cpp
// allocator_allocator.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int( int i )
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

int main( )
{
   allocator<double> Alloc;
   vector <Int>:: allocator_type v1Alloc;

   allocator<double> cAlloc(Alloc);
   allocator<Int> cv1Alloc(v1Alloc);

   if ( cv1Alloc == v1Alloc )
      cout << "The allocator objects cv1Alloc & v1Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cv1Alloc & v1Alloc are not equal."
           << endl;

   if ( cAlloc == Alloc )
      cout << "The allocator objects cAlloc & Alloc are equal."
           << endl;
   else
      cout << "The allocator objects cAlloc & Alloc are not equal."
           << endl;
}
```

```Output
The allocator objects cv1Alloc & v1Alloc are equal.
The allocator objects cAlloc & Alloc are equal.
```

### <a name="const_pointer"></a>const_pointer

Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez Alokator.

```cpp
typedef const value_type *const_pointer;
```

#### <a name="remarks"></a>Uwagi

Typ wskaźnika opisuje obiekt `ptr` , który może wyznaczyć, za pomocą wyrażenia `*ptr`, dowolnego obiektu const, który obiekt alokatora klas szablonu może przydzielić.

#### <a name="example"></a>Przykład

```cpp
// allocator_const_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 10;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer's address found has a value of: "
        << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The integer's address found has a value of: 10.
```

### <a name="const_reference"></a>const_reference

Typ, który dostarcza stałe odwołanie do typu obiektu zarządzanego przez Alokator.

```cpp
typedef const value_type& const_reference;
```

#### <a name="remarks"></a>Uwagi

Typ referencyjny opisuje obiekt, który może wyznaczyć dowolny obiekt const, który obiekt alokatora klas szablonu może przydzielić.

#### <a name="example"></a>Przykład

```cpp
// allocator_const_ref.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::const_reference vcref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vcref << ",\n the first element in the vector." << endl;

   // const references can have their elements modified,
   // so the following would generate an error:
   // vcref = 150;
   // but the value of the first element could be modified through
   // its nonconst iterator and the const reference would remain valid
*vfIter = 175;
   cout << "The value of the element referred to by vcref,"
        <<"\n after nofication through its nonconst iterator, is: "
        << vcref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The value of the element referred to by vcref,
after nofication through its nonconst iterator, is: 175.
```

### <a name="construct"></a>Konstruuj

Konstruuje określony typ obiektu pod określonym adresem, który jest zainicjowany z określoną wartością.

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
    void construct(pointer ptr, _Other&&... val);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowany.

*użyte*\
Wartość, za pomocą której tworzony jest obiekt, ma zostać zainicjowany.

#### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska jest równoważna **z nowym** (`void` ( `ptr` \*)) **typem** (`val`).

#### <a name="example"></a>Przykład

```cpp
// allocator_construct.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 6, kB = 7;
   v1PtrA = v1Alloc.address( *find( v1.begin( ), v1.end( ), kA ) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The modified vector v1 is:
( 3 7 9 12 15 18 21 ).
```

### <a name="deallocate"></a>alokowany

Zwalnia określoną liczbę obiektów z magazynu, zaczynając od określonej pozycji.

```cpp
void deallocate(pointer ptr, size_type count);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do pierwszego obiektu do cofnięcia przydziału z magazynu.

*liczbą*\
Liczba obiektów do cofnięcia przydziału z magazynu.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska zwalnia magazyn dla tablicy obiektów Count typu `Type` rozpoczynającego się o *PTR*, wywołując `operator delete(ptr)`metodę. Wskaźnik *PTR* musi zostać zwrócony wcześniej przez wywołanie przydzielenia obiektu [](#allocate) alokatora, który porównuje równe z  **\*tym**, przydzielanie obiektu tablicy o tym samym rozmiarze i typie. `deallocate`nigdy nie zgłasza wyjątku.

#### <a name="example"></a>Przykład

Aby zapoznać się z przykładem przy użyciu funkcji członkowskiej, zobacz [Alokator:: Allocate](#allocate).

### <a name="destroy"></a>usunięcie

Wywołuje destruktor obiektów bez cofania przydziału pamięci, w której zapisano obiekt.

```cpp
void destroy(pointer ptr);
```

#### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik wyznaczający adres obiektu, który ma zostać zniszczony.

#### <a name="remarks"></a>Uwagi

Funkcja członkowska niszczy obiekt wyznaczył wartość *PTR*, wywołując `ptr->` **Typ**destruktora:: **~** .

#### <a name="example"></a>Przykład

```cpp
// allocator_destroy.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 2 * i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::pointer v1PtrA;
   int kA = 12, kB = -99;
   v1PtrA = v1Alloc.address( *find(v1.begin( ), v1.end( ), kA) );
   v1Alloc.destroy ( v1PtrA );
   v1Alloc.construct ( v1PtrA , kB );

   cout << "The modified vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v1 is:
( 2 4 6 8 10 12 14 ).
The modified vector v1 is:
( 2 4 6 8 10 -99 14 ).
```

### <a name="difference_type"></a>difference_type

Typ całkowity ze znakiem, który może reprezentować różnicę między wartościami wskaźników do typu obiektu zarządzanego przez Alokator.

```cpp
typedef ptrdiff_t difference_type;
```

#### <a name="remarks"></a>Uwagi

Typ Liczba całkowita ze znakiem zawiera opis obiektu, który może reprezentować różnicę między adresami każdego z dwóch elementów w sekwencji, które obiekt alokatora klas szablonu może przydzielić.

#### <a name="example"></a>Przykład

```cpp
// allocator_diff_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 0 ; i <= 7 ; i++ )
   {
      v1.push_back( i * 2 );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1PtrA, v1PtrB;
   const int kA = 4, kB =12;
   v1PtrA = v1Alloc.address( kA );
   v1PtrB = v1Alloc.address( kB );
   allocator<int>::difference_type v1diff = *v1PtrB - *v1PtrA;

   cout << "Pointer v1PtrA addresses " << *v1PtrA << "." << endl;
   cout << "Pointer v1PtrB addresses " << *v1PtrB <<  "." << endl;
   cout << "The difference between the integer's addresses is: "
        << v1diff << "." << endl;
}
```

```Output
The original vector v1 is:
( 0 2 4 6 8 10 12 14 ).
Pointer v1PtrA addresses 4.
Pointer v1PtrB addresses 12.
The difference between the integer's addresses is: 8.
```

### <a name="max_size"></a>max_size

Zwraca liczbę elementów typu `Type` , które mogą zostać przydzielone przez obiekt alokatora klasy przed użyciem wolnej pamięci.

```cpp
size_type max_size() const;
```

#### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które można przydzielić.

#### <a name="example"></a>Przykład

```cpp
// allocator_max_size.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( i );
   }

   cout << "The original vector v1 is:\n ( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   vector <double> v2;
   vector <double> ::iterator v2Iter;
   vector <double> :: allocator_type v2Alloc;
   allocator<int>::size_type v1size;
   v1size = v1Alloc.max_size( );

   cout << "The number of integers that can be allocated before\n"
        << " the free memory in the vector v1 is used up is: "
        << v1size << "." << endl;

   int ii;
   for ( ii = 1 ; ii <= 7 ; ii++ )
   {
      v2.push_back( ii * 10.0 );
   }

   cout << "The original vector v2 is:\n ( " ;
   for ( v2Iter = v2.begin( ) ; v2Iter != v2.end( ) ; v2Iter++ )
      cout << *v2Iter << " ";
   cout << ")." << endl;
   allocator<double>::size_type v2size;
   v2size = v2Alloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v2 is used up is: "
        << v2size << "." << endl;
}
```

### <a name="op_eq"></a>operator =

Przypisuje jednemu obiektowi alokatora do innego obiektu alokatora.

```cpp
template <class Other>
    allocator<Type>& operator=(const allocator<Other>& right);
```

#### <a name="parameters"></a>Parametry

*Kliknij*\
Obiekt alokatora, który ma zostać przypisany do innego obiektu.

#### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu alokatora

#### <a name="remarks"></a>Uwagi

Operator przypisania szablonu nic nie robi. Ogólnie rzecz biorąc, obiekt alokatora przypisany do innego obiektu alokatora powinien być porównywany z nim i umożliwiać wzajemną mieszanie alokacji obiektów i zwalnianie między dwoma obiektami alokatora.

#### <a name="example"></a>Przykład

```cpp
// allocator_op_assign.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

class Int {
public:
   Int(int i)
   {
      cout << "Constructing " << ( void* )this  << endl;
      x = i;
      bIsConstructed = true;
   };
   ~Int( ) {
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

int main( )
{
   allocator<Int> Alloc;
   allocator<Int> cAlloc ;
   cAlloc = Alloc;
}
```

### <a name="pointer"></a>przytrzymaj

Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez Alokator.

```cpp
typedef value_type *pointer;
```

#### <a name="remarks"></a>Uwagi

Typ wskaźnika opisuje obiekt `ptr` , który może wyznaczyć, za pomocą wyrażenia  **\*PTR**, każdy obiekt, który obiekt alokatora klas szablonów może przydzielić.

#### <a name="example"></a>Przykład

```cpp
// allocator_ptr.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <int> v1;
   vector <int>::iterator v1Iter;
   vector <int>:: allocator_type v1Alloc;

   int i;
   for ( i = 1 ; i <= 7 ; i++ )
   {
      v1.push_back( 3 * i );
   }

   cout << "The original vector v1 is:\n( " ;
   for ( v1Iter = v1.begin( ) ; v1Iter != v1.end( ) ; v1Iter++ )
      cout << *v1Iter << " ";
   cout << ")." << endl;

   allocator<int>::const_pointer v1Ptr;
   const int k = 12;
   v1Ptr = v1Alloc.address( k );

   cout << "The integer addressed by v1Ptr has a value of: "
        << "*v1Ptr = " << *v1Ptr << "." << endl;
}
```

```Output
The original vector v1 is:
( 3 6 9 12 15 18 21 ).
The integer addressed by v1Ptr has a value of: *v1Ptr = 12.
```

### <a name="rebind"></a>rebind

Struktura, która umożliwia Alokator dla obiektów jednego typu do przydzielania magazynu dla obiektów innego typu.

```cpp
struct rebind { typedef allocator<_Other> other; };
```

#### <a name="parameters"></a>Parametry

*różnych*\
Typ elementu, dla którego przydzielono pamięć.

#### <a name="remarks"></a>Uwagi

Ta struktura jest przydatna do przydzielania pamięci dla typu, który różni się od typu elementu implementowanego kontenera.

Klasa szablonu elementu członkowskiego definiuje typ inny. Jego jedynym celem jest zapewnienie, że **Alokator**\<nazw typów _ **inne**>, z uwzględnieniem typu **alokatora** \< nazwy **typu >.**

Na przykład, dany obiekt `al` alokatora typu `A`, można przydzielić obiekt typu `_Other` za pomocą wyrażenia:

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

Możesz też nazwać typ wskaźnika, pisząc typ:

```cpp
A::rebind<Other>::other::pointer
```

#### <a name="example"></a>Przykład

```cpp
// allocator_rebind.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <algorithm>
#include <vector>

using namespace std;

typedef vector<int>::allocator_type IntAlloc;
int main( )
{
   IntAlloc v1Iter;
   vector<int> v1;

   IntAlloc::rebind<char>::other::pointer pszC =
      IntAlloc::rebind<char>::other(v1.get_allocator()).allocate(1, (void *)0);

   int * pInt = v1Iter.allocate(10);
}
```

### <a name="reference"></a>odwoła

Typ, który zawiera odwołanie do typu obiektu zarządzanego przez Alokator.

```cpp
typedef value_type& reference;
```

#### <a name="remarks"></a>Uwagi

Typ referencyjny opisuje obiekt, który może wyznaczyć dowolny obiekt, który obiekt przydzielania klas szablonów może przydzielić.

#### <a name="example"></a>Przykład

```cpp
// allocator_reference.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::reference vref =*vfIter;
   cout << "The value of the element referred to by vref is: "
        << vref << ",\n the first element in the vector." << endl;

   // nonconst references can have their elements modified
   vref = 150;
   cout << "The element referred to by vref after being modified is: "
        << vref << "." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element referred to by vref is: 100,
the first element in the vector.
The element referred to by vref after being modified is: 150.
```

### <a name="size_type"></a>size_type

Typ całkowity bez znaku, który może reprezentować długość dowolnej sekwencji, która może być przydzielona przez obiekt alokatora klas szablonów.

```cpp
typedef size_t size_type;
```

#### <a name="example"></a>Przykład

```cpp
// allocator_size_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>

using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   allocator<double>::size_type vsize;
   vsize = vAlloc.max_size( );

   cout << "The number of doubles that can be allocated before\n"
        << " the free memory in the vector v is used up is: "
        << vsize << "." << endl;
}
```

### <a name="value_type"></a>value_type

Typ, który jest zarządzany przez program przydzielający.

```cpp
typedef Type value_type;
```

#### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru `Type`szablonu.

#### <a name="example"></a>Przykład

```cpp
// allocator_value_type.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>
#include <vector>
using namespace std;

int main( )
{
   vector <double> v;
   vector <double> ::iterator vIter, vfIter;
   vector <double> :: allocator_type vAlloc;

   int j;
   for ( j = 1 ; j <= 7 ; j++ )
   {
      v.push_back( 100.0 * j );
   }

   cout << "The original vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;

   vfIter = v.begin( );
   allocator<double>::value_type vecVal = 150.0;
*vfIter = vecVal;
   cout << "The value of the element addressed by vfIter is: "
        << *vfIter << ",\n the first element in the vector." << endl;

   cout << "The modified vector v is:\n ( " ;
   for ( vIter = v.begin( ) ; vIter != v.end( ) ; vIter++ )
      cout << *vIter << " ";
   cout << ")." << endl;
}
```

```Output
The original vector v is:
( 100 200 300 400 500 600 700 ).
The value of the element addressed by vfIter is: 150,
the first element in the vector.
The modified vector v is:
( 150 200 300 400 500 600 700 ).
```

## <a name="helpers"></a>Pomocnicy

### <a name="allocator_arg_t"></a>allocator_arg_t

```cpp
struct allocator_arg_t { explicit allocator_arg_t() = default; };
inline constexpr allocator_arg_t allocator_arg{};
```

### <a name="uses_allocator"></a>uses_allocator

```cpp
template <class T, class Alloc> struct uses_allocator;
```
