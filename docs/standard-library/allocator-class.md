---
title: Allocator — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a6bd8c230f17e3b62d02d724cfd0744c0d335eac
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060549"
---
# <a name="allocator-class"></a>allocator — Klasa

Klasa szablonu opisuje obiekt, który zarządza alokacją pamięci i zwalnianiem dla tablic obiektów typu `Type`. Obiekt klasy `allocator` jest domyślny obiekt alokatora, określone w konstruktory szereg klas szablonu kontenera standardowej biblioteki C++.

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator
```

### <a name="parameters"></a>Parametry

*Typ*<br/>
Typ obiektu, dla którego jest Magazyn przydzielony lub z cofniętą alokacją.

## <a name="remarks"></a>Uwagi

Wszystkie kontenery standardowej biblioteki języka C++ ma parametr szablonu, który domyślnie przyjmuje wartość `allocator`. Konstruowanie kontenera za pomocą niestandardowego zarządcy zapewniają kontrolę nad alokacją i zwalnianiem elementów tego kontenera.

Na przykład obiekt programu przydzielania mogą przydzielić pamięć na stosie prywatnej lub w pamięci współdzielonej, lub może zoptymalizować rozmiary małych lub dużych obiektów. On może również określać, za pośrednictwem definicji typu, który dostarcza mu elementy były dostępne za pośrednictwem obiektów specjalne metody dostępu, które zarządzać pamięci współużytkowanej lub wykonać automatyczne wyrzucanie elementów bezużytecznych. W związku z tym klasa, która przydziela pamięć przy użyciu obiekt programu przydzielania należy te są używane do deklarowania wskaźników i odwołują się do obiektów, tak jak kontenery w standardowej biblioteki języka C++.

**(C_ ++ 98/03)** Po utworzeniu klasy pochodnej z klasy programu przydzielania, musisz podać [ponownie powiązać](#rebind) struktury, których `_Other` typedef odwołuje się do klasy pochodnej nowo.

W efekcie alokatora definiuje następujące typy:

- [wskaźnik](#pointer) zachowuje się jak wskaźnik do `Type`.

- [const_pointer](#const_pointer) zachowuje się jak wskaźnik const `Type`.

- [Odwołanie](#reference) zachowuje się jak odwołanie do `Type`.

- [const_reference —](#const_reference) zachowuje się jak const odwołanie do `Type`.

Te `Type`s określony formularz, który wskaźników i odwołań musi mieć przydzielone elementów. ( [allocator::pointer](#pointer) niekoniecznie jest taka sama jak `Type*` dla wszystkich obiektów programu przydzielania, nawet jeśli ma to oczywiste definicję klasy `allocator`.)

**C ++ 11 i nowszych:** włączyć operacji przenoszenia w swojej alokatora, przy użyciu interfejsu minimalnych i zaimplementować konstruktora kopiującego, == i! = operatory przydzielania i cofnąć jej przydział. Aby uzyskać więcej informacji i obejrzeć przykład, zobacz [buforów](../standard-library/allocators.md)

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[allocator](#allocator)|Konstruktory użyty do utworzenia `allocator` obiektów.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez program przydzielania.|
|[const_reference](#const_reference)|Typ, który zawiera stałe odwołanie do typu obiektu zarządzanego przez program przydzielania.|
|[difference_type](#difference_type)|Podpisany typ całkowity, który może reprezentować różnicy między wartościami wskaźniki do typu obiektu zarządzanego przez program przydzielania.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez program przydzielania.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do typu obiektu zarządzanego przez program przydzielania.|
|[size_type](#size_type)|Sekwencja nieoznaczoną liczbę całkowitą reprezentujące długość każdego obiekt klasy szablonu `allocator` można przydzielić.|
|[value_type](#value_type)|Typ, który jest zarządzany przez program przydzielania.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Adres](#address)|Wyszukuje adres obiektu, którego wartość jest określona.|
|[allocate](#allocate)|Przydziela blok pamięci jest wystarczająco duży, aby zapisać co najmniej określonej liczby elementów.|
|[construct](#construct)|Tworzy określonego typu obiektu pod określony adres, który jest inicjowany z określoną wartością.|
|[Cofnij Przydział](#deallocate)|Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.|
|[destroy](#destroy)|Wywołuje destruktora obiektów bez Trwa cofanie alokacji pamięci, do przechowywania obiektu.|
|[max_size](#max_size)|Zwraca liczbę elementów typu `Type` może zostać przydzielone przez obiekt klasy `allocator` przed wolnej pamięci jest używany w.|
|[ponowne wiązanie](#rebind)|Struktura, która umożliwia alokatora dla obiektów typu jeden do przydzielania pamięci dla obiektów innego typu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje jeden `allocator` obiektu do drugiego `allocator` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<pamięci >

**Namespace:** standardowe

## <a name="address"></a>  Allocator::Address

Wyszukuje adres obiektu, którego wartość jest określona.

```cpp
pointer address(reference val) const;
const_pointer address(const_reference val) const;
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Const lub nonconst wartość obiektu, którego adres są wyszukiwane.

### <a name="return-value"></a>Wartość zwracana

"Const" lub nonconst wskaźnik do obiektu znaleźć wartości, odpowiednio, const lub nonconst.

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zwracają adres *val*na formularz, który wskaźniki należy wykonać dla przydzielone elementów.

### <a name="example"></a>Przykład

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

## <a name="allocate"></a>  Allocator::allocate

Przydziela blok pamięci jest wystarczająco duży, aby zapisać co najmniej określonej liczby elementów.

```cpp
pointer allocate(size_type count, const void* _Hint);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba elementów, dla których ma można przydzielić wystarczającej ilości miejsca.

*_Hint*<br/>
Wskaźnika elementu const, które mogą być pomocne obiekt alokatora który spełnia żądanie dla magazynu, znajdując adres obiektu, przydzielany przed żądania.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do przydzielonego obiektu lub wartość null, jeśli nie została przydzielona pamięć.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego przydziela pamięć dla tablic, liczba elementów typu `Type`, przez nowy operator wywołania (*liczba*). Zwraca wskaźnik do przydzielonego obiektu. Argument wskazówka pomaga niektóre puli buforów w ulepszaniu miejscowość odwołanie; prawidłowy wybór jest adres obiektu wcześniej przydzielonej przez ten sam obiekt programu przydzielania i nie została jeszcze z cofniętą alokacją. Aby przekazać bez wskazówki, zamiast tego użyj argumentów wskaźnika o wartości null.

### <a name="example"></a>Przykład

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

## <a name="allocator"></a>  Allocator::Allocator

Konstruktory używany do tworzenia obiektów programu przydzielania.

```cpp
allocator();
allocator(const allocator<Type>& right);
template <class Other>
allocator(const allocator<Other>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Obiekt alokatora, który ma być skopiowany.

### <a name="remarks"></a>Uwagi

Konstruktor nie działa. Ogólnie rzecz biorąc jednak obiekt programu przydzielania skonstruowany z innego obiektu programu przydzielania powinien porównywane do niego i umożliwić intermixing alokacji obiektów i zwalnianie pomiędzy dwoma obiektami alokatora.

### <a name="example"></a>Przykład

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

## <a name="const_pointer"></a>  Allocator::const_pointer

Typ, który zapewnia stały wskaźnik do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef const value_type *const_pointer;
```

### <a name="remarks"></a>Uwagi

Typ wskaźnika opisuje obiekt `ptr` , wyznaczyć, za pomocą wyrażenia `*ptr`, obiekt const, który można przydzielić obiektu alokatora klasy szablonu.

### <a name="example"></a>Przykład

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

## <a name="const_reference"></a>  Allocator::const_reference

Typ, który zawiera stałe odwołanie do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef const value_type& const_reference;
```

### <a name="remarks"></a>Uwagi

Typ odwołania, opisująca obiekt, który można określić obiekt const, który można przydzielić obiektu alokatora klasy szablonu.

### <a name="example"></a>Przykład

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

## <a name="construct"></a>  Allocator::Construct

Tworzy określonego typu obiektu pod określony adres, który jest inicjowany z określoną wartością.

```cpp
void construct(pointer ptr, const Type& val);
void construct(pointer ptr, Type&& val);
template <class _Other>
void construct(pointer ptr, _Other&&...   val);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik do lokalizacji, w której obiekt ma zostać skonstruowane.

*Val*<br/>
Wartość za pomocą którego generowana jest zainicjowane.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska jest odpowiednikiem **nowe** (( `void` \*) `ptr` ) **typu** ( `val` ).

### <a name="example"></a>Przykład

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

## <a name="deallocate"></a>  Allocator::deallocate

Zwalnia określoną liczbę obiektów z pamięci masowej rozpoczynający się od określonej pozycji.

```cpp
void deallocate(pointer ptr, size_type count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik do pierwszego obiektu można cofnąć przydziału z magazynu.

*Liczba*<br/>
Liczba obiektów, które można cofnąć przydziału z magazynu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwalnia pamięć dla tablicy obiektów typu Liczba `Type` począwszy od *ptr*, wywołując `operator delete(ptr)`. Wskaźnik *ptr* musi zostały zwrócone wcześniej przez wywołanie [przydzielić](#allocate) dla obiekt alokatora, który porównuje równa  **\*to**, przydzielania tablicy obiekt tego samego rozmiaru i typu. `deallocate` nigdy nie zgłasza wyjątek.

### <a name="example"></a>Przykład

Na przykład za pomocą funkcji elementu członkowskiego, zobacz [allocator::allocate](#allocate).

## <a name="destroy"></a>  Allocator::Destroy

Wywołuje destruktora obiektów bez Trwa cofanie alokacji pamięci, do przechowywania obiektu.

```cpp
void destroy(pointer ptr);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik, wyznaczanie adres obiektu, które mają zostać zniszczone.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji niszczy obiekcie wyznaczonym przez *ptr*, przez wywołanie destruktora `ptr->` **typu**::**~ typu**.

### <a name="example"></a>Przykład

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

## <a name="difference_type"></a>  Allocator::difference_type

Podpisany typ całkowity, który może reprezentować różnicy między wartościami wskaźniki do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef ptrdiff_t difference_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej ze znakiem opisuje obiekt, który może reprezentować różnica między adresami dowolne dwa elementy w sekwencji, który można przydzielić obiektu alokatora klasy szablonu.

### <a name="example"></a>Przykład

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

## <a name="max_size"></a>  Allocator::max_size

Zwraca liczbę elementów typu `Type` , może zostać przydzielone przez obiekt alokatora klas, zanim zostaną użyte wolnej pamięci w.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które może zostać przydzielone.

### <a name="example"></a>Przykład

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

## <a name="op_eq"></a>  Allocator::operator =

Przypisuje jeden obiekt alokatora do innego obiektu programu przydzielania.

```cpp
template <class Other>
allocator<Type>& operator=(const allocator<Other>& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Obiekt alokatora, który można przypisać do innego takiego obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu programu przydzielania

### <a name="remarks"></a>Uwagi

Operator przypisania szablonu nic nie robi. Ogólnie rzecz biorąc jednak obiekt programu przydzielania przypisane do innego obiektu programu przydzielania powinien porównywane do niego i umożliwić intermixing alokacji obiektów i zwalnianie pomiędzy dwoma obiektami alokatora.

### <a name="example"></a>Przykład

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

## <a name="pointer"></a>  Allocator::Pointer

Typ, który dostarcza wskaźnik do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef value_type *pointer;
```

### <a name="remarks"></a>Uwagi

Typ wskaźnika opisuje obiekt `ptr` , wyznaczyć, za pomocą wyrażenia  **\*ptr**, dowolnego obiektu, który można przydzielić obiektu alokatora klasy szablonu.

### <a name="example"></a>Przykład

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

## <a name="rebind"></a>  Allocator::rebind

Struktura, która umożliwia alokatora dla obiektów typu jeden do przydzielania pamięci dla obiektów innego typu.
```cpp
struct rebind {    typedef allocator<_Other> other ;    };
```

### <a name="parameters"></a>Parametry

*other*<br/>
Typ elementu, dla którego pamięć została przydzielona.

### <a name="remarks"></a>Uwagi

Ta struktura jest przydatne w przypadku przydzielania pamięci dla typu, który różni się od typu elementu kontenera wdrażane.

Klasa szablonu elementu członkowskiego definiuje typ innych. Jedynym celem jest zapewnienie nazwę typu **alokatora**\<_ **innych**>, otrzymuje nazwę typu **alokatora** \< **typu** >.

Na przykład, biorąc pod uwagę obiekt programu przydzielania `al` typu `A`, można przydzielić obiektu typu `_Other` przy użyciu wyrażenia:

```cpp
A::rebind<Other>::other(al).allocate(1, (Other *)0)
```

Alternatywnie możesz nazwać jego typ wskaźnika, pisząc typu:

```cpp
A::rebind<Other>::other::pointer
```

### <a name="example"></a>Przykład

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

## <a name="reference"></a>  Allocator::Reference

Typ, który zawiera odwołanie do typu obiektu zarządzanego przez program przydzielania.

```cpp
typedef value_type& reference;
```

### <a name="remarks"></a>Uwagi

Typ odwołania, opisująca obiekt, który można wyznaczyć dowolnego obiektu, który można przydzielić obiektu alokatora klasy szablonu.

### <a name="example"></a>Przykład

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

## <a name="size_type"></a>  Allocator::size_type

Niepodpisane integralny typ, który może reprezentować długość dowolnej sekwencji, który można przydzielić obiektu alokatora klasy szablonu.

```cpp
typedef size_t size_type;
```

### <a name="example"></a>Przykład

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

## <a name="value_type"></a>  Allocator::value_type

Typ, który jest zarządzany przez program przydzielania.

```cpp
typedef Type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Type`.

### <a name="example"></a>Przykład

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

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
