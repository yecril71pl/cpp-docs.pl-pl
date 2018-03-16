---
title: "deque — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- deque/std::deque
- deque/std::deque::allocator_type
- deque/std::deque::const_iterator
- deque/std::deque::const_pointer
- deque/std::deque::const_reference
- deque/std::deque::const_reverse_iterator
- deque/std::deque::difference_type
- deque/std::deque::iterator
- deque/std::deque::pointer
- deque/std::deque::reference
- deque/std::deque::reverse_iterator
- deque/std::deque::size_type
- deque/std::deque::value_type
- deque/std::deque::assign
- deque/std::deque::at
- deque/std::deque::back
- deque/std::deque::begin
- deque/std::deque::cbegin
- deque/std::deque::cend
- deque/std::deque::clear
- deque/std::deque::crbegin
- deque/std::deque::crend
- deque/std::deque::emplace
- deque/std::deque::emplace_back
- deque/std::deque::emplace_front
- deque/std::deque::empty
- deque/std::deque::end
- deque/std::deque::erase
- deque/std::deque::front
- deque/std::deque::get_allocator
- deque/std::deque::insert
- deque/std::deque::max_size
- deque/std::deque::pop_back
- deque/std::deque::pop_front
- deque/std::deque::push_back
- deque/std::deque::push_front
- deque/std::deque::rbegin
- deque/std::deque::rend
- deque/std::deque::resize
- deque/std::deque::shrink_to_fit
- deque/std::deque::size
- deque/std::deque::swap
dev_langs:
- C++
helpviewer_keywords:
- std::deque [C++]
- std::deque [C++], allocator_type
- std::deque [C++], const_iterator
- std::deque [C++], const_pointer
- std::deque [C++], const_reference
- std::deque [C++], const_reverse_iterator
- std::deque [C++], difference_type
- std::deque [C++], iterator
- std::deque [C++], pointer
- std::deque [C++], reference
- std::deque [C++], reverse_iterator
- std::deque [C++], size_type
- std::deque [C++], value_type
- std::deque [C++], assign
- std::deque [C++], at
- std::deque [C++], back
- std::deque [C++], begin
- std::deque [C++], cbegin
- std::deque [C++], cend
- std::deque [C++], clear
- std::deque [C++], crbegin
- std::deque [C++], crend
- std::deque [C++], emplace
- std::deque [C++], emplace_back
- std::deque [C++], emplace_front
- std::deque [C++], empty
- std::deque [C++], end
- std::deque [C++], erase
- std::deque [C++], front
- std::deque [C++], get_allocator
- std::deque [C++], insert
- std::deque [C++], max_size
- std::deque [C++], pop_back
- std::deque [C++], pop_front
- std::deque [C++], push_back
- std::deque [C++], push_front
- std::deque [C++], rbegin
- std::deque [C++], rend
- std::deque [C++], resize
- std::deque [C++], shrink_to_fit
- std::deque [C++], size
- std::deque [C++], swap
ms.assetid: 64842ee5-057a-4063-8c16-4267a0332584
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 88ce199617f0628ccb7e022581cd52d83d82e2ac
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="deque-class"></a>deque — Klasa
Rozmieszcza elementy danego typu w układzie liniowej i, takich jak wektorowa umożliwia szybkiego losowego dostępu do elementu i wydajne wstawiania i usuwania tyłu kontenera. Jednak w przeciwieństwie do wektora `deque` klasa obsługuje również wydajne Wstawianie i usuwanie z przodu kontenera.  
  
## <a name="syntax"></a>Składnia  
  
```unstlib  
template <class Type, class Allocator =allocator<Type>>  
class deque  
```  
  
#### <a name="parameters"></a>Parametry  
 `Type`  
 Typ danych elementu mają być przechowywane w deque —.  
  
 `Allocator`  
 Typ reprezentujący obiekt alokatora przechowywane, który hermetyzuje informacje szczegółowe o alokacji i cofania alokacji pamięci deque —. Ten argument jest opcjonalny, a wartość domyślna to **alokatora\<typu > ***.*  
  
## <a name="remarks"></a>Uwagi  
 Wybór typu kontenera powinien ogólnie być oparty o typ wyszukiwania i wstawiania wymagany przez aplikację. [Wektory](../standard-library/vector-class.md) powinna być preferowanych kontenera zarządzania sekwencję, gdy jest dostępie do dowolnych i wstawiania lub usuwania elementów są tylko wymagane na końcu sekwencji. Działanie kontenera listy jest wstawienia wyższego poziomu, gdy wydajne i jest usunięć (w czasie stałej) w dowolnej lokalizacji w sekwencji. Takich operacji w trakcie wykonywania sekwencji wymagają kopii elementu i przydziały proporcjonalny do liczby elementów w sekwencji (czas liniowej).  
  
 Deque —; Ponowna alokacja występuje, gdy funkcji członkowskiej musi Wstaw lub wymazać elementy sekwencji:  
  
-   Jeśli element znajduje się w wyniku pustą sekwencję, lub jeśli element jest staną się pozostaw pustą sekwencją, następnie Iteratory wcześniej zwróconych przez [rozpocząć](#begin) i [zakończenia](#end) staną się nieprawidłowe.  
  
-   Jeśli element jest wstawiany na pierwszym miejscu deque —, a następnie wszystkie Iteratory, ale żadnych odwołań, które określają istniejące elementy staną się nieprawidłowe.  
  
-   Jeśli jest wstawić element na końcu deque —, następnie [zakończenia](#end) i wszystkie Iteratory, ale żadnych odwołań, które określają istniejące elementy staną się nieprawidłowe.  
  
-   Jeśli element zostanie wymazane z przodu deque —, tylko że iteratora i odwołań do elementu wymazanej staną się nieprawidłowe.  
  
-   Jeśli usunięciem ostatnim elementem od końca deque —, tylko że iteratora ostatniego elementu i odwołań do elementu wymazanej staną się nieprawidłowe.  
  
 W przeciwnym razie Wstawianie lub wymazywanie elementu unieważnia wszystkie Iteratory i odwołań.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[deque —](#deque)|Konstruuje `deque.` kilka konstruktorów są dostarczane do skonfigurowania nowej zawartości `deque` na różne sposoby: pusty; załadowany z określoną liczbę elementów pusty; zawartości przenoszone lub kopiowane z innego `deque`; zawartość jest kopiowana lub przeniesione przy użyciu iteratora; i jeden element kopiowane do `deque` `count` razy. Niektóre z konstruktorów Włącz przy użyciu niestandardowego `allocator` do tworzenia elementów.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[allocator_type](#allocator_type)|Typ reprezentujący `allocator` klasy dla `deque` obiektu.|  
|[const_iterator](#const_iterator)|Typ, który udostępnia iteratora dostępie swobodnym, które i są dostępne elementy do odczytu `deque` jako `const`|  
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu `deque` jako `const.`|  
|[const_reference](#const_reference)|Typ, który zawiera odwołanie do elementu w `deque` do odczytu i inne operacje jako `const.`|  
|[const_reverse_iterator](#const_reverse_iterator)|Typ, który udostępnia iteratora dostępie swobodnym, które i są dostępne elementy do odczytu `deque` jako `const`. Deque — są wyświetlane w odwrotnej. Aby uzyskać więcej informacji, zobacz [reverse_iterator — klasa](../standard-library/reverse-iterator-class.md)|  
|[difference_type](#difference_type)|Typ, który zawiera różnicę między dwoma Iteratory dostępie swobodnym odwołujące się do elementów w tym samym `deque`.|  
|[iterator](#iterator)|Typ, który udostępnia iteratora dostępie swobodnym, które mogą odczytywać lub modyfikować dowolny element w `deque`.|  
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu `deque`.|  
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu przechowywane w `deque`.|  
|[reverse_iterator](#reverse_iterator)|Typ, który udostępnia iteratora dostępie swobodnym, które mogą odczytywać lub modyfikować element `deque`. Deque — zostanie wyświetlony w odwrotnej kolejności.|  
|[size_type](#size_type)|Typ, który oblicza liczbę elementów w `deque`.|  
|[value_type](#value_type)|Typ reprezentujący typ danych przechowywanych w `deque`.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Przypisz](#assign)|Usuwa elementy z `deque` i kopiuje nową sekwencję elementów do obiektu docelowego `deque`.|  
|[at](#at)|Zwraca odwołanie do elementu w określonej lokalizacji w `deque`.|  
|[back](#back)|Zwraca odwołanie do ostatniego elementu `deque`.|  
|[begin](#begin)|Zwraca iteratora dostępie swobodnym adresowania pierwszym elementem w `deque`.|  
|[cbegin](#cbegin)|Zwraca pierwszy element w const iteratora `deque`.|  
|[cend](#cend)|Zwraca losowe dostępu `const` iterator, który wskazuje poza koniec `deque`.|  
|[Wyczyść](#clear)|Usuwa wszystkie elementy `deque`.|  
|[crbegin](#crbegin)|Zwraca pierwszy element w dostępie swobodnym iteratora const `deque` wyświetlane w odwrotnej kolejności.|  
|[crend](#crend)|Zwraca pierwszy element w dostępie swobodnym iteratora const `deque` wyświetlane w odwrotnej kolejności.|  
|[emplace](#emplace)|Wstawia element w miejscu do skonstruować `deque` na określonej pozycji.|  
|[emplace_back](#emplace_back)|Dodaje element skonstruowane w miejscu do końca `deque`.|  
|[emplace_front](#emplace_front)|Dodaje element utworzone w celu uruchomienia `deque`.|  
|[empty](#empty)|Zwraca `true` Jeśli `deque` nie zawiera zero elementów i `false` zawiera co najmniej jeden element.|  
|[Koniec](#end)|Zwraca iteratora dostępie swobodnym tego punkty poza koniec `deque`.|  
|[wymazywanie](#erase)|Usuwa element lub zakresu elementów `deque` z określonych pozycji.|  
|[Front](#front)|Zwraca odwołanie do pierwszego elementu w `deque`.|  
|[get_allocator](#get_allocator)|Zwraca kopię `allocator` obiekt, który jest używany do tworzenia `deque`.|  
|[insert](#insert)|Wstawia element, wiele elementów lub zakres elementów do `deque` na określonej pozycji.|  
|[max_size](#max_size)|Zwraca maksymalną długość możliwe `deque`.|  
|[pop_back](#pop_back)|Usuwa element na końcu `deque`.|  
|[pop_front](#pop_front)|Usuwa element na początku `deque`.|  
|[push_back](#push_back)|Dodaje element do końca `deque`.|  
|[push_front](#push_front)|Dodaje element do początku `deque`.|  
|[rbegin](#rbegin)|Zwraca pierwszy element w odwróconej iteratora dostępie swobodnym `deque`.|  
|[rend](#rend)|Zwraca iteratora dostępie swobodnym tego punkty tuż za ostatnim elementem w odwróconej `deque`.|  
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar `deque`.|  
|[shrink_to_fit](#shrink_to_fit)|Odrzucenia nadmiarowej pojemności.|  
|[Rozmiar](#size)|Zwraca liczbę elementów w `deque`.|  
|[swap](#swap)|Zamienia elementy dwóch `deque`s.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator&#91;&#93;](#op_at)|Zwraca odwołanie do `deque` elementu w określonej pozycji.|  
|[operator=](#op_eq)|Zastępuje elementy `deque` z kopią innego `deque`.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek**: \<deque — >  
  
##  <a name="allocator_type"></a>  deque::allocator_type  
 Typ, który reprezentuje klasę alokatora dla obiekt deque —.  
  
```  
typedef Allocator allocator_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 **allocator_type** jest synonimem parametru szablonu **alokatora**.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [get_allocator](#get_allocator).  
  
##  <a name="assign"></a>  deque::ASSIGN  
 Usuwa elementy z deque — i kopiuje nowy zbiór elementów na deque — docelowy.  
  
```  
template <class InputIterator>  
void assign(
    InputIterator First,  
    InputIterator Last);

void assign(
    size_type Count,  
    const Type& Val);

void assign(initializer_list<Type> IList);
```  
  
### <a name="parameters"></a>Parametry  
 `First`  
 Pozycja pierwszego elementu w zakresie elementów do skopiowania z deque — argument.  
  
 `Last`  
 Pozycja pierwszego elementu poza zakres elementów do skopiowania z deque — argument.  
  
 `Count`  
 Liczba kopii elementu wstawiane do deque —.  
  
 `Val`  
 Wartość wstawiana do deque — element.  
  
 `IList`  
 Initializer_list, wstawiane do deque —.  
  
### <a name="remarks"></a>Uwagi  
 Po usuwane są wszystkie istniejące elementy w deque — docelowej, `assign` Wstawia określony zakres elementów z oryginalnego deque — lub innych deque — do deque — docelowy albo wstawia kopie nowego elementu określoną wartość do deque — docelowej.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_assign.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <initializer_list>  
  
int main()  
{  
    using namespace std;  
    deque <int> c1, c2;  
    deque <int>::const_iterator cIter;  
  
    c1.push_back(10);  
    c1.push_back(20);  
    c1.push_back(30);  
    c2.push_back(40);  
    c2.push_back(50);  
    c2.push_back(60);  
  
    deque<int> d1{ 1, 2, 3, 4 };  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    d1.assign(iList);  
  
    cout << "d1 = ";  
    for (int i : d1)  
        cout << i;  
    cout << endl;  
  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(++c2.begin(), c2.end());  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
    c1.assign(7, 4);  
    cout << "c1 =";  
    for (int i : c1)  
        cout << i;  
    cout << endl;  
  
}  
  
```  
  
```Output  
d1 = 5678c1 =102030c1 =5060c1 =4444444  
```  
  
##  <a name="at"></a>  deque::AT  
 Deque — zwraca odwołanie do elementu w określonej lokalizacji.  
  
```  
reference at(size_type pos);

const_reference at(size_type pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Indeks dolny lub numer pozycji elementu do odwołania w deque —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli `pos` jest większy niż rozmiar deque —, **na** zgłasza wyjątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli wartość zwracana **w** jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana **w** jest przypisany do **odwołania**, obiekt deque — może być modyfikowany.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_at.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int& i = c1.at( 0 );  
   int& j = c1.at( 1 );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="back"></a>  deque::back  
 Zwraca odwołanie do ostatniego elementu deque —.  
  
```  
reference back();
const_reference back() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Ostatnim elementem deque —. Jeśli deque — jest pusta, zwracana wartość jest niezdefiniowana.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **ponownie** jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana **ponownie** jest przypisany do **odwołania**, obiektu deque — może być modyfikowany.  
  
 Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu w pustym deque —.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.back( );  
   const int& ii = c1.front( );  
  
   cout << "The last integer of c1 is " << i << endl;  
   i--;  
   cout << "The next-to-last integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The last integer of c1 is 11  
The next-to-last integer of c1 is 10  
```  
  
##  <a name="begin"></a>  deque::BEGIN  
 Zwraca adresowania pierwszym elementem w deque — iteratora.  
  
```  
const_iterator begin() const;
iterator begin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Adresowanie pierwszym elementem w deque — lub do lokalizacji pomyślne pusty deque — iteratora dostępie swobodnym.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana **rozpocząć** jest przypisany do `const_iterator`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana **rozpocząć** jest przypisany do **iteratora**, obiekt deque — może być modyfikowany.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// deque_begin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::const_iterator c1_cIter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is " << *c1_Iter << endl;  
  
 *c1_Iter = 20;  
   c1_Iter = c1.begin( );  
   cout << "The first element of c1 is now " << *c1_Iter << endl;  
  
   // The following line would be an error because iterator is const  
   // *c1_cIter = 200;  
}  
```  
  
```Output  
The first element of c1 is 1  
The first element of c1 is now 20  
```  
  
##  <a name="cbegin"></a>  deque::cbegin  
 Zwraca `const` iteratora, którego dotyczy pierwszy element w zakresie.  
  
```  
const_iterator cbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 A `const` iteratora dostępie swobodnym, który wskazuje na pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.  
  
 Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.  
  
```cpp  
auto i1 = Container.begin();
// i1 is Container<T>::iterator   
auto i2 = Container.cbegin();

// i2 is Container<T>::const_iterator  
```  
  
##  <a name="cend"></a>  deque::cend  
 Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.  
  
```  
const_iterator cend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dostępu swobodnego, który wskazuje tuż za koniec zakresu.  
  
### <a name="remarks"></a>Uwagi  
 `cend` Służy do sprawdzenia, czy iteratora osiągnęła koniec zakresu.  
  
 Można użyć funkcji członkowskiej zamiast `end()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `end()` i `cend()`.  
  
```cpp  
auto i1 = Container.end();
// i1 is Container<T>::iterator   
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator  
```  
  
 Wartość zwrócona przez `cend` nie powinny być wyłuskiwany.  
  
##  <a name="clear"></a>  deque::Clear  
 Usuwa wszystkie elementy deque —.  
  
```  
void clear();
```  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_clear.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   cout << "The size of the deque is initially " << c1.size( ) << endl;  
   c1.clear( );  
   cout << "The size of the deque after clearing is " << c1.size( ) << endl;  
}  
```  
  
```Output  
The size of the deque is initially 3  
The size of the deque after clearing is 0  
```  
  
##  <a name="const_iterator"></a>  deque::const_iterator  
 Typem udostępniający iteratora dostęp losowy i są dostępne do odczytu **const** element deque —.  
  
```  
typedef implementation-defined const_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_iterator` nie może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [ponownie](#back).  
  
##  <a name="const_pointer"></a>  deque::const_pointer  
 Udostępnia wskaźnik do `const` element deque —.  
  
```
typedef typename Allocator::const_pointer const_pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_pointer` nie może służyć do modyfikowania wartości elementu. [Iterator](#iterator) częściej umożliwia dostęp do elementu deque —.  
  
##  <a name="const_reference"></a>  deque::const_reference  
 Typ, który zawiera odwołanie do **const** element przechowywane w deque — do odczytu i wykonywania **const** operacji.  
  
```  
typedef typename Allocator::const_reference const_reference;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reference` nie może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// deque_const_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const deque <int> c2 = c1;  
   const int &i = c2.front( );  
   const int &j = c2.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
  
   // The following line would cause an error as c2 is const  
   // c2.push_back( 30 );  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="const_reverse_iterator"></a>  deque::const_reverse_iterator  
 Typ, który udostępnia iteratora dostępie swobodnym, który może odczytać **const** element deque —.  
  
```  
typedef std::reverse_iterator<const_iterator> const_reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `const_reverse_iterator` nie można zmodyfikować wartości elementu i jest używany do iterowania po deque — odwrotnie.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rbegin](#rbegin) przykład sposobu deklarowanie i użycie iteratora.  
  
##  <a name="crbegin"></a>  deque::crbegin  
 Pierwszym elementem w odwróconej deque — zwraca const iteratora.  
  
```  
const_reverse_iterator crbegin() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dostępie swobodnym adresowania pierwszym elementem w odwróconej [deque —](../standard-library/deque-class.md) lub adresowania co była ostatnim elementem w stałe `deque`.  
  
### <a name="remarks"></a>Uwagi  
 Z wartością zwracaną z `crbegin`, `deque` obiektu nie może być modyfikowany.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_crbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator v1_Iter;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   v1_Iter = v1.begin( );  
   cout << "The first element of deque is "  
        << *v1_Iter << "." << endl;  
  
   v1_rIter = v1.crbegin( );  
   cout << "The first element of the reversed deque is "  
        << *v1_rIter << "." << endl;  
}  
```  
  
```Output  
The first element of deque is 1.  
The first element of the reversed deque is 2.  
```  
  
##  <a name="crend"></a>  deque::crend  
 Zwraca iteratora const, który dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej deque —.  
  
```  
const_reverse_iterator crend() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Stała wstecznego iteratora dostępie swobodnym, który dotyczy lokalizacji pomyślne ostatnim elementem w odwrotnej [deque —](../standard-library/deque-class.md) (lokalizacja miał przed pierwszym elementem w stałe deque —).  
  
### <a name="remarks"></a>Uwagi  
 `crend` jest używany z odwróconej `deque` podobnie jak [array::cend](../standard-library/array-class-stl.md#cend) jest używany z `deque`.  
  
 Z wartością zwracaną z `crend` (odpowiednio zmniejszany) `deque` obiektu nie może być modyfikowany.  
  
 `crend` można sprawdzać, czy odwrotnej iteratora osiągnął koniec jego deque —.  
  
 Wartość zwrócona przez `crend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_crend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::const_reverse_iterator v1_rIter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
  
   for ( v1_rIter = v1.rbegin( ) ; v1_rIter != v1.rend( ) ; v1_rIter++ )  
      cout << *v1_rIter << endl;  
}  
```  
  
```Output  
2  
1  
```  
  
##  <a name="deque"></a>  deque::deque  
 Tworzy deque — o określonym rozmiarze lub z elementami określonej wartości, lub z określonego programu przydzielania lub jako kopii całości lub części innych deque —.  
  
```  
deque();

explicit deque(const Allocator& Al);
explicit deque(size_type Count);
deque(size_type Count, const Type& Val);

deque(
    size_type Count,  
    const Type& Val,  
    const Allocator& Al);

deque(const deque& Right);

template <class InputIterator>  
deque(InputIterator First,  InputIterator Last);

template <class InputIterator>  
deque(
   InputIterator First,  
   InputIterator Last,  
   const Allocator& Al);

deque(initializer_list<value_type> IList, const Allocator& Al);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Al`|Klasa alokatora do wykorzystania z tym obiektem.|  
|`Count`|Liczba elementów w skonstruowane deque —.|  
|`Val`|Wartość elementów w skonstruowane deque —.|  
|`Right`|Deque — skonstruowane deque — ma być kopii.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|  
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|  
|`IList`|Initializer_list do skopiowania.|  
  
### <a name="remarks"></a>Uwagi  
 Wszystkie konstruktory zapisania obiektu alokatora ( `Al`) i zainicjuj deque —.  
  
 Pierwsze dwa konstruktory Określ pusty deque — początkowej; drugi określa również typ alokatora ( `_Al`) do użycia.  
  
 Trzeci konstruktora określa powtórzenia określonej liczby ( `count`) elementów wartości domyślnej dla klasy `Type`.  
  
 Konstruktory czwartym i piątym Określ powtórzenia ( `Count`) elementy wartości `val`.  
  
 Konstruktor szóstego Określa kopię deque — `Right`.  
  
 Konstruktory siódmego i ósmego skopiuj zakres `[First, Last)` z deque —.  
  
 Konstruktor siódmego przenosi deque — `Right`.  
  
 Konstruktor ósmego kopiuje zawartość initializer_list.  
  
 Żaden z konstruktorów wykonania wszelkich przeniesień tymczasowe.  
  
### <a name="example"></a>Przykład  
  
```cpp 
/ compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <forward_list>  
  
int main()  
{  
    using namespace std;  
  
    forward_list<int> f1{ 1, 2, 3, 4 };  
  
    f1.insert_after(f1.begin(), { 5, 6, 7, 8 });  
  
    deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1(3);  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2(5, 2);  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3(3, 1, c2.get_allocator());  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4(c2);  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5(c4.begin(), c4_Iter);  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin();  
    c4_Iter++;  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c6(c4.begin(), c4_Iter, c2.get_allocator());  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
    initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for (int i : c1)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for (int i : c2)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for (int i : c3)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for (int i : c4)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for (int i : c5)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for (int i : c6)  
        cout << i << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7(move(c6));  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =";  
    for (int i : c7)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    for (int i : c9)  
        cout << i << " ";  
    cout << endl;  
  
    int x = 3;  
}  
// deque_deque.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
    using namespace std;  
   deque <int>::iterator c1_Iter, c2_Iter, c3_Iter, c4_Iter, c5_Iter, c6_Iter;  
  
    // Create an empty deque c0  
    deque <int> c0;  
  
    // Create a deque c1 with 3 elements of default value 0  
    deque <int> c1( 3 );  
  
    // Create a deque c2 with 5 elements of value 2  
    deque <int> c2( 5, 2 );  
  
    // Create a deque c3 with 3 elements of value 1 and with the   
    // allocator of deque c2  
    deque <int> c3( 3, 1, c2.get_allocator( ) );  
  
    // Create a copy, deque c4, of deque c2  
    deque <int> c4( c2 );  
  
    // Create a deque c5 by copying the range c4[ first,  last)  
    c4_Iter = c4.begin( );  
    c4_Iter++;  
    c4_Iter++;  
    deque <int> c5( c4.begin( ), c4_Iter );  
  
    // Create a deque c6 by copying the range c4[ first,  last) and   
    // c2 with the allocator of deque  
    c4_Iter = c4.begin( );  
   c4_Iter++;  
   c4_Iter++;  
   c4_Iter++;  
   deque <int> c6( c4.begin( ), c4_Iter, c2.get_allocator( ) );  
  
    // Create a deque c8 by copying the contents of an initializer_list  
    // using brace initialization  
    deque<int> c8({ 1, 2, 3, 4 });  
  
        initializer_list<int> iList{ 5, 6, 7, 8 };  
    deque<int> c9( iList);  
  
    cout << "c1 = ";  
    for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
        cout << *c1_Iter << " ";  
    cout << endl;  
  
    cout << "c2 = ";  
    for ( c2_Iter = c2.begin( ); c2_Iter != c2.end( ); c2_Iter++ )  
        cout << *c2_Iter << " ";  
    cout << endl;  
  
    cout << "c3 = ";  
    for ( c3_Iter = c3.begin( ); c3_Iter != c3.end( ); c3_Iter++ )  
        cout << *c3_Iter << " ";  
    cout << endl;  
  
    cout << "c4 = ";  
    for ( c4_Iter = c4.begin( ); c4_Iter != c4.end( ); c4_Iter++ )  
        cout << *c4_Iter << " ";  
    cout << endl;  
  
    cout << "c5 = ";  
    for ( c5_Iter = c5.begin( ); c5_Iter != c5.end( ); c5_Iter++ )  
        cout << *c5_Iter << " ";  
    cout << endl;  
  
    cout << "c6 = ";  
    for ( c6_Iter = c6.begin( ); c6_Iter != c6.end( ); c6_Iter++ )  
        cout << *c6_Iter << " ";  
    cout << endl;  
  
    // Move deque c6 to deque c7  
    deque <int> c7( move(c6) );  
    deque <int>::iterator c7_Iter;  
  
    cout << "c7 =" ;  
    for ( c7_Iter = c7.begin( ) ; c7_Iter != c7.end( ) ; c7_Iter++ )  
        cout << " " << *c7_Iter;  
    cout << endl;  
  
    cout << "c8 = ";  
    for (int i : c8)  
        cout << i << " ";  
    cout << endl;  
  
    cout << "c9 = ";  
    or (int i : c9)  
        cout << i << " ";  
    cout << endl;  
}  
```  
  
##  <a name="difference_type"></a>  deque::difference_type  
 Typ, który zawiera różnicę między dwoma Iteratory, które odwołują się do elementów w obrębie tego samego deque —.  
  
```  
typedef typename Allocator::difference_type difference_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 A `difference_type` można również określić jako liczbę elementów od dwóch wskaźników.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_diff_type.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <deque>  
#include <algorithm>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter, c2_Iter;  
  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 10 );  
   c1.push_back( 30 );  
   c1.push_back( 20 );  
  
   c1_Iter = c1.begin( );  
   c2_Iter = c1.end( );  
  
   deque <int>::difference_type df_typ1, df_typ2, df_typ3;  
  
   df_typ1 = count( c1_Iter, c2_Iter, 10 );  
   df_typ2 = count( c1_Iter, c2_Iter, 20 );  
   df_typ3 = count( c1_Iter, c2_Iter, 30 );  
   cout << "The number '10' is in c1 collection " << df_typ1 << " times.\n";  
   cout << "The number '20' is in c1 collection " << df_typ2 << " times.\n";  
   cout << "The number '30' is in c1 collection " << df_typ3 << " times.\n";  
}  
```  
  
```Output  
The number '10' is in c1 collection 1 times.  
The number '20' is in c1 collection 2 times.  
The number '30' is in c1 collection 3 times.  
```  
  
##  <a name="emplace"></a>  deque::emplace  
 Wstawia element zbudowane w miejscu do deque — od określonej pozycji.  
  
```  
iterator emplace(
    const_iterator _Where,  
    Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`_Where`|Pozycja w [deque —](../standard-library/deque-class.md) gdzie dodaje się pierwszym elementem.|  
|`val`|Wartość elementu wstawiane do `deque`.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Funkcja zwraca iteratora wskazującą położenie, w którym wstawiono nowy element do deque —.  
  
### <a name="remarks"></a>Uwagi  
 Wszelkie operacje wstawiania może być kosztowne, zobacz `deque` omówienie `deque` wydajności.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_emplace.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   deque <int>::iterator Iter;  
  
   v1.push_back( 10 );  
   v1.push_back( 20 );  
   v1.push_back( 30 );  
  
   cout << "v1 =" ;  
   for ( Iter = v1.begin( ) ; Iter != v1.end( ) ; Iter++ )  
      cout << " " << *Iter;  
   cout << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace( vv1.begin(), move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      {  
      cout << "vv1[0] =";  
      for (Iter = vv1[0].begin( ); Iter != vv1[0].end( ); Iter++ )  
         cout << " " << *Iter;  
      cout << endl;  
      }  
}  
```  
  
```Output  
v1 = 10 20 30  
vv1[0] = 10 20 30  
```  
  
##  <a name="emplace_back"></a>  deque::emplace_back  
 Dodaje element skonstruowane w miejscu do końca deque —.  
  
```  
void emplace_back(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element dodany na końcu [deque —](../standard-library/deque-class.md).|  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_emplace_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_back( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="emplace_front"></a>  deque::emplace_front  
 Dodaje element skonstruowane w miejscu do końca deque —.  
  
```  
void emplace_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element dodany do początku [deque —](../standard-library/deque-class.md).|  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_emplace_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
  
   v1.push_back( 1 );  
   if ( v1.size( ) != 0 )  
      cout << "Last element: " << v1.back( ) << endl;  
  
   v1.push_back( 2 );  
   if ( v1.size( ) != 0 )  
      cout << "New last element: " << v1.back( ) << endl;  
  
// initialize a deque of deques by moving v1  
   deque < deque <int> > vv1;  
  
   vv1.emplace_front( move( v1 ) );  
   if ( vv1.size( ) != 0 && vv1[0].size( ) != 0 )  
      cout << "Moved last element: " << vv1[0].back( ) << endl;  
}  
```  
  
```Output  
Last element: 1  
New last element: 2  
Moved last element: 2  
```  
  
##  <a name="empty"></a>  deque::Empty  
 Testy, jeśli deque — jest pusta.  
  
```  
bool empty() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 **wartość true,** Jeśli deque — jest pusta. **false** Jeśli deque — nie jest pusty.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_empty.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   if ( c1.empty( ) )  
      cout << "The deque is empty." << endl;  
   else  
      cout << "The deque is not empty." << endl;  
}  
```  
  
```Output  
The deque is not empty.  
```  
  
##  <a name="end"></a>  deque::end  
 Zwraca, którego dotyczy lokalizacji pomyślne ostatnim elementem w deque — iteratora.  
  
```  
const_iterator end() const;

iterator end();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dostępie swobodnym, którego dotyczy lokalizacji pomyślne ostatnim elementem w deque —. Jeśli deque — jest pusty, a następnie deque::end == deque::begin.  
  
### <a name="remarks"></a>Uwagi  
 **końcowy** używany do sprawdzania, czy iteratora osiągnął koniec jego deque —.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_end.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_Iter = c1.end( );  
   c1_Iter--;  
   cout << "The last integer of c1 is " << *c1_Iter << endl;  
  
   c1_Iter--;  
 *c1_Iter = 400;  
   cout << "The new next-to-last integer of c1 is " << *c1_Iter << endl;  
  
   // If a const iterator had been declared instead with the line:  
   // deque <int>::const_iterator c1_Iter;  
   // an error would have resulted when inserting the 400  
  
   cout << "The deque is now:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
}  
```  
  
```Output  
The last integer of c1 is 30  
The new next-to-last integer of c1 is 400  
The deque is now: 10 400 30  
```  
  
##  <a name="erase"></a>  deque::ERASE  
 Usuwa element lub zakres elementów deque — od określonej pozycji.  
  
```  
iterator erase(iterator _Where);

iterator erase(iterator first, iterator last);
```  
  
### <a name="parameters"></a>Parametry  
 `_Where`  
 Położenie elementu do usunięcia z deque —.  
  
 `first`  
 Pozycja pierwszego elementu usunięte z deque —.  
  
 `last`  
 Pozycja poza ostatni element usunięty z deque —.  
  
### <a name="return-value"></a>Wartość zwracana  
 Iterator dostępie swobodnym, który wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte lub wskaźnik do końca deque — Jeśli nie zawiera żadnego takiego elementu.  
  
### <a name="remarks"></a>Uwagi  
 **ERASE** nigdy nie zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_erase.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator Iter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
   c1.push_back( 40 );  
   c1.push_back( 50 );  
   cout << "The initial deque is: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   c1.erase( c1.begin( ) );  
   cout << "After erasing the first element, the deque becomes:  ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
   Iter = c1.begin( );  
   Iter++;  
   c1.erase( Iter, c1.end( ) );  
   cout << "After erasing all elements but the first, deque becomes: ";  
   for ( Iter = c1.begin( ); Iter != c1.end( ); Iter++ )  
      cout << *Iter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The initial deque is: 10 20 30 40 50   
After erasing the first element, the deque becomes:  20 30 40 50   
After erasing all elements but the first, deque becomes: 20   
```  
  
##  <a name="front"></a>  deque::front  
 Deque — zwraca odwołanie do pierwszego elementu.  
  
```  
reference front();

const_reference front() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli deque — jest pusta, zwracany jest niezdefiniowany.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana `front` jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana `front` jest przypisany do **odwołania**, obiekt deque — może być modyfikowany.  
  
 Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu w pustym deque —.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 11 );  
  
   int& i = c1.front( );  
   const int& ii = c1.front( );  
  
   cout << "The first integer of c1 is " << i << endl;  
   i++;  
   cout << "The second integer of c1 is " << ii << endl;  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 11  
```  
  
##  <a name="get_allocator"></a>  deque::get_allocator  
 Zwraca kopię obiektu alokatora użyta do skonstruowania deque —.  
  
```  
Allocator get_allocator() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Allocator — używane przez deque —.  
  
### <a name="remarks"></a>Uwagi  
 Allocators — dla klasy deque — Określ zarządzaniu klasę magazynu. Allocators — domyślna dostarczony wraz z klasy kontenerów standardowa biblioteka C++ są wystarczające dla większości potrzeb programowania. Pisanie i przy użyciu klasy alokatora jest temat zaawansowany C++.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_get_allocator.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   // The following lines declare objects that use the default allocator.  
   deque <int> c1;  
   deque <int, allocator<int> > c2 = deque <int, allocator<int> >( allocator<int>( ) );  
  
   // c3 will use the same allocator class as c1  
   deque <int> c3( c1.get_allocator( ) );  
  
   deque <int>::allocator_type xlst = c1.get_allocator( );  
   // You can now call functions on the allocator class used by c1  
}  
```  
  
##  <a name="insert"></a>  deque::INSERT  
 Wstawia element lub liczba elementów lub zakres elementów do deque — od określonej pozycji.  
  
```  
iterator insert(
    const_iterator Where,  
    const Type& Val);

iterator insert(
    const_iterator Where,  
    Type&& Val);

void insert(
    iterator Where,  
    size_type Count,  
    const Type& Val);

template <class InputIterator>  
void insert(
    iterator Where,  
    InputIterator First,  
    InputIterator Last);

iterator insert(
    iterator Where,initializer_list<Type>  
IList);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`Where`|Pozycja deque — docelowy, w którym dodaje się pierwszym elementem.|  
|`Val`|Wartość wstawiana do deque — element.|  
|`Count`|Liczba elementów wstawiane do deque —.|  
|`First`|Pozycja pierwszego elementu w zakresie elementów w deque — argument do skopiowania.|  
|`Last`|Pozycja pierwszego elementu spoza zakresu elementów deque — argument do skopiowania.|  
|`IList`|Initializer_list elementów do wstawienia.|  
  
### <a name="return-value"></a>Wartość zwracana  
 Wstaw dwa pierwsze zwracają iteratora wskazującą położenie, w którym wstawiono nowy element do deque —.  
  
### <a name="remarks"></a>Uwagi  
 Może być kosztowne żadnej operacji wstawiania.  
  
##  <a name="iterator"></a>  deque::iterator  
 Typ, który udostępnia iteratora dostępie swobodnym, które mogą odczytywać lub modyfikować dowolny element w deque —.  
  
```  
typedef implementation-defined iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **iterator** może służyć do modyfikowania wartości elementu.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozpocząć](#begin).  
  
##  <a name="max_size"></a>  deque::max_size  
 Zwraca maksymalną długość deque —.  
  
```  
size_type max_size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Maksymalna długość możliwe deque —.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_max_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   i = c1.max_size( );  
   cout << "The maximum possible length of the deque is " << i << "." << endl;  
}  
```  
  
##  <a name="op_at"></a>  deque::operator]  
 Zwraca odwołanie do elementu deque — od określonej pozycji.  
  
```  
reference operator[](size_type pos);

const_reference operator[](size_type pos) const;
```  
  
### <a name="parameters"></a>Parametry  
 `pos`  
 Położenie elementu deque — powstanie odwołania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwołanie do elementu, którego pozycja jest określona w argumencie. Jeśli pozycja określona jest większy niż rozmiar deque —, wynikiem jest niezdefiniowany.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wartość zwracana `operator[]` jest przypisany do `const_reference`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana `operator[]` jest przypisany do **odwołania**, obiekt deque — może być modyfikowany.  
  
 Podczas kompilacji za pomocą [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) zdefiniowany jako 1 lub 2, błąd środowiska uruchomieniowego nastąpi próba uzyskania dostępu do elementu poza granicami deque —.  Zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md) Aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_op_ref.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   cout << "The first integer of c1 is " << c1[0] << endl;  
   int& i = c1[1];  
   cout << "The second integer of c1 is " << i << endl;  
  
}  
```  
  
```Output  
The first integer of c1 is 10  
The second integer of c1 is 20  
```  
  
##  <a name="op_eq"></a>  deque::operator =  
 Zastępuje elementy tego deque — za pomocą elementów z innego deque —.  
  
```  
deque& operator=(const deque& right);

deque& operator=(deque&& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`right`|Deque — udostępnia nową zawartość.|  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy zastąpienie kopiuje elementy do tej deque — od `right`, źródłem przypisania. Drugi zastąpienie przenosi elementy do tej deque — z `right`.  
  
 Elementy, które są zawarte w tym deque — przed wykonaniem operator zostaną usunięte.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_operator_as.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
using namespace std;  
  
typedef deque<int> MyDeque;  
  
template<typename MyDeque> struct S;  
  
template<typename MyDeque> struct S<MyDeque&> {  
  static void show( MyDeque& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
    cout << endl;  
  }  
};  
  
template<typename MyDeque> struct S<MyDeque&&> {  
  static void show( MyDeque&& d ) {  
    MyDeque::const_iterator iter;  
    for (iter = d.cbegin(); iter != d.cend(); iter++)  
       cout << *iter << " ";  
cout << " via unnamed rvalue reference " << endl;  
  }  
};  
  
int main( )  
{  
   MyDeque d1, d2;  
  
   d1.push_back(10);  
   d1.push_back(20);  
   d1.push_back(30);  
   d1.push_back(40);  
   d1.push_back(50);  
  
   cout << "d1 = " ;  
   S<MyDeque&>::show( d1 );  
  
   d2 = d1;  
   cout << "d2 = ";  
   S<MyDeque&>::show( d2 );  
  
   cout << "     ";  
   S<MyDeque&&>::show ( move< MyDeque& > (d1) );  
 }  
```  
  
##  <a name="pointer"></a>  deque::Pointer  
 Udostępnia wskaźnik do elementu [deque —](../standard-library/deque-class.md).  
  
```unstlib  
typedef typename Allocator::pointer pointer;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ **wskaźnika** może służyć do modyfikowania wartości elementu. [Iterator](#iterator) częściej umożliwia dostęp do elementu deque —.  
  
##  <a name="pop_back"></a>  deque::pop_back  
 Usuwa element w końcu deque —.  
  
```  
void pop_back();
```  
  
### <a name="remarks"></a>Uwagi  
 Ostatni element nie może być pusta. `pop_back` nigdy nie zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_pop_back.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The last element is: " << c1.back( ) << endl;  
  
   c1.pop_back( );  
   cout << "After deleting the element at the end of the deque, the "  
      "last element is: " << c1.back( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The last element is: 2  
After deleting the element at the end of the deque, the last element is: 1  
```  
  
##  <a name="pop_front"></a>  deque::pop_front  
 Usuwa element na początku deque —.  
  
```  
void pop_front();
```  
  
### <a name="remarks"></a>Uwagi  
 Pierwszy element nie może być pusta. `pop_front` nigdy nie zgłasza wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_pop_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   cout << "The first element is: " << c1.front( ) << endl;  
   cout << "The second element is: " << c1.back( ) << endl;  
  
   c1.pop_front( );  
   cout << "After deleting the element at the beginning of the "  
      "deque, the first element is: " << c1.front( ) << endl;  
}  
```  
  
```Output  
The first element is: 1  
The second element is: 2  
After deleting the element at the beginning of the deque, the first element is: 2  
```  
  
##  <a name="push_back"></a>  deque::push_back  
 Dodaje element do końca deque —.  
  
```  
void push_back(const Type& val);

void push_back(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element dodany na końcu deque —.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek pozostanie deque — niezmieniony i jest zgłoszony wyjątek.  
  
##  <a name="push_front"></a>  deque::push_front  
 Dodaje element do początku deque —.  
  
```  
    void push_front(const Type& val);

void push_front(Type&& val);
```  
  
### <a name="parameters"></a>Parametry  
  
|||  
|-|-|  
|Parametr|Opis|  
|`val`|Element na początku deque —.|  
  
### <a name="remarks"></a>Uwagi  
 Jeśli wyjątek pozostanie deque — niezmieniony i jest zgłoszony wyjątek.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_push_front.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
#include <string>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_front( 1 );  
   if ( c1.size( ) != 0 )  
      cout << "First element: " << c1.front( ) << endl;  
  
   c1.push_front( 2 );  
   if ( c1.size( ) != 0 )  
      cout << "New first element: " << c1.front( ) << endl;  
  
// move initialize a deque of strings  
   deque <string> c2;  
   string str("a");  
  
   c2.push_front( move( str ) );  
   cout << "Moved first element: " << c2.front( ) << endl;  
}  
```  
  
```Output  
First element: 1  
New first element: 2  
Moved first element: a  
```  
  
##  <a name="rbegin"></a>  deque::rbegin  
 Zwraca pierwszy element w odwróconej deque — iteratora.  
  
```  
const_reverse_iterator rbegin() const;

reverse_iterator rbegin();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwrotnej iteratora dostępie swobodnym adresowania pierwszym elementem w odwróconej deque — lub adresowania co była ostatnim elementem w stałe deque —.  
  
### <a name="remarks"></a>Uwagi  
 `rbegin` jest używany z odwróconej deque — podobnie jak [rozpocząć](#begin) jest używany z deque —.  
  
 Jeśli wartość zwracana `rbegin` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana `rbegin` jest przypisany do `reverse_iterator`, obiekt deque — może być modyfikowany.  
  
 `rbegin` może służyć do iterowania po deque — Wstecz.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_rbegin.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
  
   // If the following line had replaced the line above, an error   
   // would have resulted in the line modifying an element   
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rbegin( );  
   cout << "Last element in the deque is " << *c1_rIter << "." << endl;  
  
   cout << "The deque contains the elements: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << "in that order.";  
   cout << endl;  
  
   // rbegin can be used to iterate through a deque in reverse order  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rbegin( );  
 *c1_rIter = 40;  // This would have caused an error if a   
                    // const_reverse iterator had been declared as   
                    // noted above  
   cout << "Last element in deque is now " << *c1_rIter << "." << endl;  
}  
```  
  
```Output  
Last element in the deque is 30.  
The deque contains the elements: 10 20 30 in that order.  
The reversed deque is: 30 20 10   
Last element in deque is now 40.  
```  
  
##  <a name="reference"></a>  deque::Reference  
 Typ, który zawiera odwołanie do elementu przechowywane w deque —.  
  
```  
typedef typename Allocator::reference reference;  
```  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_reference.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
  
   const int &i = c1.front( );  
   int &j = c1.back( );  
   cout << "The first element is " << i << endl;  
   cout << "The second element is " << j << endl;  
}  
```  
  
```Output  
The first element is 10  
The second element is 20  
```  
  
##  <a name="rend"></a>  deque::rend  
 Zwraca iteratora, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej deque —.  
  
```  
const_reverse_iterator rend() const;

reverse_iterator rend();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Odwrotnej iteratora dostępie swobodnym, którego dotyczy lokalizacji pomyślne ostatnim elementem w odwróconej deque — (lokalizacja miał przed pierwszym elementem w stałe deque —).  
  
### <a name="remarks"></a>Uwagi  
 `rend` jest używany z odwróconej deque — podobnie jak [zakończenia](#end) jest używany z deque —.  
  
 Jeśli wartość zwracana `rend` jest przypisany do `const_reverse_iterator`, nie można zmodyfikować obiektu deque —. Jeśli wartość zwracana `rend` jest przypisany do `reverse_iterator`, obiekt deque — może być modyfikowany.  
  
 `rend` może służyć do sprawdzenia, czy odwrotnej iteratora osiągnął koniec jego deque —.  
  
 Wartość zwrócona przez `rend` nie powinny być wyłuskiwany.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_rend.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
  
   deque <int> c1;  
   deque <int>::iterator c1_Iter;  
   deque <int>::reverse_iterator c1_rIter;  
   // If the following line had replaced the line above, an error  
   // would have resulted in the line modifying an element  
   // (commented below) because the iterator would have been const  
   // deque <int>::const_reverse_iterator c1_rIter;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1_rIter = c1.rend( );  
   c1_rIter --; // Decrementing a reverse iterator moves it forward   
                // in the deque (to point to the first element here)  
   cout << "The first element in the deque is: " << *c1_rIter << endl;  
  
   cout << "The deque is: ";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << *c1_Iter << " ";  
   cout << endl;  
  
   // rend can be used to test if an iteration is through all of   
   // the elements of a reversed deque  
   cout << "The reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
  
   c1_rIter = c1.rend( );  
   c1_rIter--; // Decrementing the reverse iterator moves it backward   
               // in the reversed deque (to the last element here)  
 *c1_rIter = 40; // This modification of the last element would   
                   // have caused an error if a const_reverse   
                   // iterator had been declared (as noted above)  
   cout << "The modified reversed deque is: ";  
   for ( c1_rIter = c1.rbegin( ); c1_rIter != c1.rend( ); c1_rIter++ )  
      cout << *c1_rIter << " ";  
   cout << endl;  
}  
```  
  
```Output  
The first element in the deque is: 10  
The deque is: 10 20 30   
The reversed deque is: 30 20 10   
The modified reversed deque is: 30 20 40   
```  
  
##  <a name="resize"></a>  deque::Resize  
 Określa nowy rozmiar deque —.  
  
```  
void resize(size_type _Newsize);

void resize(size_type _Newsize, Type val);
```  
  
### <a name="parameters"></a>Parametry  
 `_Newsize`  
 Nowy rozmiar deque —.  
  
 `val`  
 Wartość nowych elementów do dodania do deque — nowy rozmiar jest większy który oryginalny rozmiar. W przypadku pominięcia wartości nowe elementy są przypisane wartości domyślne dla klasy.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli deque — rozmiar jest mniejszy niż rozmiar żądanej `_Newsize`, elementy są dodawane do deque —, dopóki nie osiągnie żądanego rozmiaru.  
  
 Jeśli deque — rozmiar jest większy niż rozmiar żądanej, najbliżej końca deque — elementy są usuwane, dopóki nie osiągnie rozmiar deque — `_Newsize`.  
  
 Jeśli występuje rozmiar deque — jest taki sam jak żądany rozmiar, nie podjęto żadnej akcji.  
  
 [rozmiar](#size) odzwierciedla bieżący rozmiar deque —.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_resize.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{   
   using namespace std;  
   deque <int> c1;  
  
   c1.push_back( 10 );  
   c1.push_back( 20 );  
   c1.push_back( 30 );  
  
   c1.resize( 4,40 );  
   cout << "The size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is " << c1.back( ) << endl;  
  
   c1.resize( 5 );  
   cout << "The size of c1 is now: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
  
   c1.resize( 2 );  
   cout << "The reduced size of c1 is: " << c1.size( ) << endl;  
   cout << "The value of the last element is now " << c1.back( ) << endl;  
}  
```  
  
```Output  
The size of c1 is: 4  
The value of the last element is 40  
The size of c1 is now: 5  
The value of the last element is now 0  
The reduced size of c1 is: 2  
The value of the last element is now 20  
```  
  
##  <a name="reverse_iterator"></a>  deque::reverse_iterator  
 Typ, który udostępnia iteratora dostępie swobodnym, które mogą odczytywać lub modyfikować elementu w odwróconej deque —.  
  
```  
typedef std::reverse_iterator<iterator> reverse_iterator;  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ `reverse_iterator` umożliwia iterację deque —.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład rbegin.  
  
##  <a name="shrink_to_fit"></a>  deque::shrink_to_fit  
 Odrzucenia nadmiarowej pojemności.  
  
```  
void shrink_to_fit();
```  
  
### <a name="remarks"></a>Uwagi  
 Nie istnieje sposób przenośne można określić, czy `shrink_to_fit` zmniejsza Magazyn używany przez [deque —](../standard-library/deque-class.md).  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_shrink_to_fit.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )  
{  
   using namespace std;     
   deque <int> v1;  
   //deque <int>::iterator Iter;  
  
   v1.push_back( 1 );  
   v1.push_back( 2 );  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
   v1.shrink_to_fit();  
   cout << "Current size of v1 = "   
      << v1.size( ) << endl;  
}  
```  
  
```Output  
Current size of v1 = 1  
Current size of v1 = 1  
```  
  
##  <a name="size"></a>  deque::size  
 Zwraca liczbę elementów w deque —.  
  
```  
size_type size() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżąca długość deque —.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_size.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1;  
   deque <int>::size_type i;  
  
   c1.push_back( 1 );  
   i = c1.size( );  
   cout << "The deque length is " << i << "." << endl;  
  
   c1.push_back( 2 );  
   i = c1.size( );  
   cout << "The deque length is now " << i << "." << endl;  
}  
```  
  
```Output  
The deque length is 1.  
The deque length is now 2.  
```  
  
##  <a name="size_type"></a>  deque::size_type  
 Typ, który oblicza liczbę elementów w deque —.  
  
```  
typedef typename Allocator::size_type size_type;  
```  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [rozmiar](#size).  
  
##  <a name="swap"></a>  deque::swap  
 Zamienia deques dwa elementy.  
  
```  
void swap(deque<Type, Allocator>& right);

friend void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right) template <class Type, class Allocator>  
void swap(deque<Type, Allocator>& left, deque<Type, Allocator>& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Deque —, zapewniając elementy zamianę lub deque —, której elementy są wymienianych z tymi deque — `left`.  
  
 `left`  
 Deque —, której elementy są wymienianych z tymi deque — `right`.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_swap.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   deque <int> c1, c2, c3;  
   deque <int>::iterator c1_Iter;  
  
   c1.push_back( 1 );  
   c1.push_back( 2 );  
   c1.push_back( 3 );  
   c2.push_back( 10 );  
   c2.push_back( 20 );  
   c3.push_back( 100 );  
  
   cout << "The original deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   c1.swap( c2 );  
  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap( c1,c3 );  
  
   cout << "After swapping with c3, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
  
   swap<>(c1, c2);  
   cout << "After swapping with c2, deque c1 is:";  
   for ( c1_Iter = c1.begin( ); c1_Iter != c1.end( ); c1_Iter++ )  
      cout << " " << *c1_Iter;  
   cout << endl;  
}  
```  
  
```Output  
The original deque c1 is: 1 2 3  
After swapping with c2, deque c1 is: 10 20  
After swapping with c3, deque c1 is: 100  
After swapping with c2, deque c1 is: 1 2 3  
```  
  
##  <a name="value_type"></a>  deque::value_type  
 Typ, który reprezentuje typ danych przechowywanych w deque —.  
  
```  
typedef typename Allocator::value_type value_type;  
```  
  
### <a name="remarks"></a>Uwagi  
 `value_type` synonim parametru szablonu jest **typu**.  
  
### <a name="example"></a>Przykład  
  
```cpp 
// deque_value_type.cpp  
// compile with: /EHsc  
#include <deque>  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   deque<int>::value_type AnInt;  
   AnInt = 44;  
   cout << AnInt << endl;  
}  
```  
  
```Output  
44  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)

