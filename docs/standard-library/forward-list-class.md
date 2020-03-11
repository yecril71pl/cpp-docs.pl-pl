---
title: forward_list — Klasa
ms.date: 11/04/2016
f1_keywords:
- forward_list/std::forward_list
- forward_list/std::forward_list::allocator_type
- forward_list/std::forward_list::const_iterator
- forward_list/std::forward_list::const_pointer
- forward_list/std::forward_list::const_reference
- forward_list/std::forward_list::difference_type
- forward_list/std::forward_list::iterator
- forward_list/std::forward_list::pointer
- forward_list/std::forward_list::reference
- forward_list/std::forward_list::size_type
- forward_list/std::forward_list::value_type
- forward_list/std::forward_list::assign
- forward_list/std::forward_list::before_begin
- forward_list/std::forward_list::begin
- forward_list/std::forward_list::cbefore_begin
- forward_list/std::forward_list::cbegin
- forward_list/std::forward_list::cend
- forward_list/std::forward_list::clear
- forward_list/std::forward_list::emplace_after
- forward_list/std::forward_list::emplace_front
- forward_list/std::forward_list::empty
- forward_list/std::forward_list::end
- forward_list/std::forward_list::erase_after
- forward_list/std::forward_list::front
- forward_list/std::forward_list::get_allocator
- forward_list/std::forward_list::insert_after
- forward_list/std::forward_list::max_size
- forward_list/std::forward_list::merge
- forward_list/std::forward_list::pop_front
- forward_list/std::forward_list::push_front
- forward_list/std::forward_list::remove
- forward_list/std::forward_list::remove_if
- forward_list/std::forward_list::resize
- forward_list/std::forward_list::reverse
- forward_list/std::forward_list::sort
- forward_list/std::forward_list::splice_after
- forward_list/std::forward_list::swap
- forward_list/std::forward_list::unique
helpviewer_keywords:
- std::forward_list
- std::forward_list::allocator_type
- std::forward_list::const_iterator
- std::forward_list::const_pointer
- std::forward_list::const_reference
- std::forward_list::difference_type
- std::forward_list::iterator
- std::forward_list::pointer
- std::forward_list::reference
- std::forward_list::size_type
- std::forward_list::value_type
- std::forward_list::assign
- std::forward_list::before_begin
- std::forward_list::begin
- std::forward_list::cbefore_begin
- std::forward_list::cbegin
- std::forward_list::cend
- std::forward_list::clear
- std::forward_list::emplace_after
- std::forward_list::emplace_front
- std::forward_list::empty
- std::forward_list::end
- std::forward_list::erase_after
- std::forward_list::front
- std::forward_list::get_allocator
- std::forward_list::insert_after
- std::forward_list::max_size
- std::forward_list::merge
- std::forward_list::pop_front
- std::forward_list::push_front
- std::forward_list::remove
- std::forward_list::remove_if
- std::forward_list::resize
- std::forward_list::reverse
- std::forward_list::sort
- std::forward_list::splice_after
- std::forward_list::swap
- std::forward_list::unique
ms.openlocfilehash: e13242aa41cc99cdd01a6f16b607ef568195d659
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78890879"
---
# <a name="forward_list-class"></a>forward_list — Klasa

Opisuje obiekt, który kontroluje różnej długości sekwencji elementów. Sekwencja jest przechowywana jako pojedynczo dołączoną listę węzłów, z których każdy zawiera element członkowski typu `Type`.

## <a name="syntax"></a>Składnia

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Parametry

Typ * \
Typ danych elementu, który ma być przechowywany w forward_list.

\ *alokatora*
Przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące alokacji forward_list i dealokacji pamięci. Ten parametr jest opcjonalny. Wartość domyślna to Alokator <`Type`>.

## <a name="remarks"></a>Uwagi

Obiekt `forward_list` przydziela i zwalnia magazyn dla sekwencji, która kontroluje za pośrednictwem przechowywanego obiektu *alokatora* klas, który jest oparty na [klasie alokatora](../standard-library/allocator-class.md) (często znanej jako `std::allocator)`. Aby uzyskać więcej informacji, zobacz [przydzielanie](../standard-library/allocators.md). Obiekt alokatora musi mieć ten sam interfejs zewnętrzny co obiekt typu `allocator`.

> [!NOTE]
> Przechowywany obiekt alokatora nie jest kopiowany po przypisaniu obiektu kontenera.

Iteratory, wskaźniki i odwołania mogą stać się nieprawidłowe, gdy elementy ich kontrolowanej sekwencji są wymazywane za `forward_list`. Wstawienia i kombinacje wykonywane na kontrolowanej sekwencji za pomocą `forward_list` nie weryfikują iteratorów.

Dodatki do kontrolowanej sekwencji mogą wystąpić przez wywołania do [forward_list:: insert_after](#insert_after), która jest jedyną funkcją członkowską, która wywołuje Konstruktor `Type(const  T&)`. `forward_list` może również wywołać konstruktory przenoszenia. Jeśli takie wyrażenie zgłasza wyjątek, obiekt kontenera nie wstawia żadnych nowych elementów i ponownie generuje wyjątek. W związku z tym obiekt typu `forward_list` pozostały w znanym stanie w przypadku wystąpienia takich wyjątków.

## <a name="members"></a>Elementy członkowskie

### <a name="constructors"></a>Konstruktorów

|||
|-|-|
|[forward_list](#forward_list)|Konstruuje obiekt typu `forward_list`.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę alokatora dla obiektu listy do przodu.|
|[const_iterator](#const_iterator)|Typ, który zapewnia stały iterator dla listy do przodu.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do elementu **const** na liście do przodu.|
|[const_reference](#const_reference)|Typ, który dostarcza stałe odwołanie do elementu na liście do przodu.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów listy do przodu w zakresie między elementami wskazywanymi przez Iteratory.|
|[Iterator](#iterator)|Typ, który dostarcza iterator dla listy do przodu.|
|[przytrzymaj](#pointer)|Typ, który dostarcza wskaźnik do elementu na liście do przodu.|
|[odwoła](#reference)|Typ, który zawiera odwołanie do elementu na liście do przodu.|
|[size_type](#size_type)|Typ, który reprezentuje odległość bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ, który reprezentuje typ elementu przechowywanego na liście do przodu.|

### <a name="functions"></a>Funkcje

|||
|-|-|
|[ponownie](#assign)|Wymazuje elementy z listy do przodu i kopiuje nowy zestaw elementów na listę docelową do przodu.|
|[before_begin](#before_begin)|Zwraca iterator odnoszący się do pozycji przed pierwszym elementem na liście do przodu.|
|[zaczną](#begin)|Zwraca iterator odnoszący się do pierwszego elementu na liście do przodu.|
|[cbefore_begin](#cbefore_begin)|Zwraca iterator const odnoszący się do pozycji przed pierwszym elementem na liście do przodu.|
|[cbegin](#cbegin)|Zwraca iterator const odnoszący się do pierwszego elementu na liście do przodu.|
|[cend](#cend)|Zwraca iterator const, który odnosi się do lokalizacji po ostatnim elemencie na liście do przodu.|
|[Wyczyść](#clear)|Kasuje wszystkie elementy listy do przodu.|
|[emplace_after](#emplace_after)|Przenieś konstruuje nowy element po określonej pozycji.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu na początku listy.|
|[ciągiem](#empty)|Testuje, czy lista do przodu jest pusta.|
|[punktów](#end)|Zwraca iterator, który odnosi się do lokalizacji na końcu ostatniego elementu na liście do przodu.|
|[erase_after](#erase_after)|Usuwa elementy z listy do przodu po określonej pozycji.|
|[FSB](#front)|Zwraca odwołanie do pierwszego elementu na liście do przodu.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu alokatora używanego do konstruowania listy do przodu.|
|[insert_after](#insert_after)|Dodaje elementy do listy do przodu po określonej pozycji.|
|[max_size](#max_size)|Zwraca maksymalną długość listy do przodu.|
|[połączenie](#merge)|Usuwa elementy z listy argumentów, wstawia je do docelowej listy do przodu i porządkuje nowy, połączony zestaw elementów w kolejności rosnącej lub w innej określonej kolejności.|
|[pop_front](#pop_front)|Usuwa element na początku listy do przodu.|
|[push_front](#push_front)|Dodaje element na początku listy do przodu.|
|[remove](#remove)|Usuwa elementy z listy do przodu, które pasują do określonej wartości.|
|[remove_if](#remove_if)|Usuwa elementy z listy do przodu, dla których spełniony jest określony predykat.|
|[Zmień rozmiar](#resize)|Określa nowy rozmiar listy do przodu.|
|[cofnięci](#reverse)|Odwraca kolejność, w jakiej elementy pojawiają się na liście do przodu.|
|[porządku](#sort)|Rozmieszcza elementy w kolejności rosnącej lub z kolejnością określoną przez predykat.|
|[splice_after](#splice_after)|Łączy linki między węzłami.|
|[wymiany](#swap)|Wymienia elementy dwóch list do przodu.|
|[unique](#unique)|Usuwa przylegające elementy, które przechodzą do określonego testu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#op_eq)|Zamienia elementy listy do przodu z kopią innej listy do przodu.|

## <a name="allocator_type"></a>allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu listy do przodu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla alokatora parametrów szablonu.

## <a name="assign"></a>ponownie

Wymazuje elementy z listy do przodu i kopiuje nowy zestaw elementów na listę docelową do przodu.

```cpp
void assign(
    size_type Count,
    const Type& Val);

void assign(
    initializer_list<Type> IList);

template <class InputIterator>
void assign(InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*pierwszy*\
Początek zakresu zastępowania.

*ostatni*\
Koniec zakresu zastępowania.

*liczba*\
Liczba elementów do przypisania.

*val*\
Wartość, aby przypisać każdy element.

*Typ*\
Typ wartości.

\ *IList*
Initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Jeśli forward_list jest typu Integer, Pierwsza funkcja członkowska zachowuje się tak samo jak `assign((size_type)First, (Type)Last)`. W przeciwnym razie Pierwsza funkcja członkowska zastępuje sekwencję, która `*this` z sekwencją [`First, Last)`, która nie może nakładać się na początkową sekwencję sterowaną.

Druga funkcja członkowska zastępuje sekwencję, która jest kontrolowana przez `*this` za pomocą powtarzania `Count` elementów wartości `Val`.

Trzecia funkcja członkowska Kopiuje elementy initializer_list do forward_list.

## <a name="before_begin"></a>before_begin

Zwraca iterator odnoszący się do pozycji przed pierwszym elementem na liście do przodu.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje tuż przed pierwszym elementem sekwencji (lub tuż przed końcem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="begin"></a>zaczną

Zwraca iterator odnoszący się do pierwszego elementu na liście do przodu.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje na pierwszy element sekwencji (lub tuż poza końcem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="cbefore_begin"></a>cbefore_begin

Zwraca iterator const odnoszący się do pozycji przed pierwszym elementem na liście do przodu.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje tuż przed pierwszym elementem sekwencji (lub tuż przed końcem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="cbegin"></a>cbegin

Zwraca iterator **const** , który dotyczy pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator **const** dostęp do przodu, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną `cbegin`nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji składowej `begin()`, aby zagwarantować, że wartość zwracana jest `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, że `Container` być kontenerem modyfikowalnym (innym niż **const**) dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>cend

Zwraca iterator **const** , który odnosi się do lokalizacji jedynie poza ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu do przodu, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` służy do sprawdzania, czy iterator przeszedł koniec zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast funkcji składowej `end()`, aby zagwarantować, że wartość zwracana jest `const_iterator`. Zwykle jest używany w połączeniu z słowem kluczowym odejmowania [autotype,](../cpp/auto-cpp.md) jak pokazano w poniższym przykładzie. W tym przykładzie Rozważmy, że `Container` być kontenerem modyfikowalnym (innym niż **const**) dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Nie należy wywoływać wartości zwracanej przez `cend`.

## <a name="clear"></a>Wyczyść

Kasuje wszystkie elementy listy do przodu.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego wywołuje `erase_after(before_begin(), end()).`

## <a name="const_iterator"></a>const_iterator

Typ, który zapewnia stały iterator dla listy do przodu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

`const_iterator` opisuje obiekt, który może obsłużyć ciągły iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację.

## <a name="const_pointer"></a>const_pointer

Typ, który dostarcza wskaźnik do elementu **const** na liście do przodu.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Uwagi

## <a name="const_reference"></a>const_reference

Typ, który dostarcza stałe odwołanie do elementu na liście do przodu.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

## <a name="difference_type"></a>difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów listy do przodu w zakresie między elementami wskazywanymi przez Iteratory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` opisuje obiekt, który może reprezentować różnicę między adresami wszystkich dwóch elementów w kontrolowanej sekwencji.

## <a name="emplace_after"></a>emplace_after

Przenieś konstruuje nowy element po określonej pozycji.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Pozycja na liście docelowych przekazywania, w której jest konstruowany nowy element.

*val*\
Argument konstruktora.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wyznacza nowo wstawiony element.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska wstawia element z argumentami konstruktora *Val* tuż po elemencie wskazywanym przez *WHERE* w kontrolowanej sekwencji. Jego zachowanie jest takie samo jak [forward_list:: insert_after](#insert_after).

## <a name="emplace_front"></a>emplace_front

Dodaje element skonstruowany w miejscu na początku listy.

```cpp
template <class Type>
    void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*val*\
Element dodany na początku listy do przodu.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska wstawia element z argumentami konstruktora `_ val` na końcu kontrolowanej sekwencji.

Jeśli wyjątek jest zgłaszany, kontener pozostaje niezmienione i wyjątek jest ponownie zgłaszany.

## <a name="empty"></a>ciągiem

Testuje, czy lista do przodu jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli lista przesyłania dalej jest pusta; w przeciwnym razie **false**.

## <a name="end"></a>punktów

Zwraca iterator, który odnosi się do lokalizacji na końcu ostatniego elementu na liście do przodu.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje tuż poza końcem sekwencji.

## <a name="erase_after"></a>erase_after

Usuwa elementy z listy do przodu po określonej pozycji.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Pozycja na liście docelowych przekazywania, w której element jest wymazany.

*pierwszy*\
Początek zakresu do wymazania.

*ostatni*\
Koniec zakresu do wymazania.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wyznacza pierwszy element, który nie został usunięty, lub [forward_list:: end](#end) , jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska usuwa element kontrolowanej sekwencji tuż po *lokalizacji*.

Druga funkcja członkowska usuwa elementy z kontrolowanej sekwencji w zakresie `( first,  last)` (żaden punkt końcowy nie jest uwzględniony).

Wymazywanie `N` elementów powoduje wywołanie `N` destruktora. [Ponowna alokacja](../standard-library/forward-list-class.md) jest wykonywana, dlatego Iteratory i odwołania stają się nieprawidłowe dla wymazanych elementów.

Funkcja członkowska nigdy nie zgłasza wyjątku.

## <a name="forward_list"></a>forward_list

Konstruuje obiekt typu `forward_list`.

```cpp
forward_list();
explicit forward_list(const Allocator& Al);
explicit forward_list(size_type Count);
forward_list(size_type Count, const Type& Val);
forward_list(size_type Count, const Type& Val, const Allocator& Al);
forward_list(const forward_list& Right);
forward_list(const forward_list& Right, const Allocator& Al);
forward_list(forward_list&& Right);
forward_list(forward_list&& Right, const Allocator& Al);
forward_list(initializer_list<Type> IList, const Alloc& Al);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last);
template <class InputIterator>
forward_list(InputIterator First, InputIterator Last, const Allocator& Al);
```

### <a name="parameters"></a>Parametry

*Al*\
Klasa alokatora do wykorzystania z tym obiektem.

*Liczba*\
Liczba elementów na liście skonstruowane.

*Val*\
Wartość elementów na utworzonej liście.

*Prawa*\
Lista, której skonstruowaną listą jest kopia.

*Pierwszy*\
Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.

*Ostatni*\
Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.

\ *IList*
Initializer_list do skopiowania.

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowują [Alokator](../standard-library/allocator-class.md) i inicjują kontrolowaną sekwencję. Obiekt alokatora jest argumentem *Al*, jeśli jest obecny. Dla konstruktora kopiującego jest ` right.get_allocator()`. W przeciwnym razie jest `Allocator()`.

Pierwsze dwa konstruktory określają pustą, początkową sekwencję.

Trzeci konstruktor określa powtarzanie elementów *Count* wartości `Type()`.

Czwarty i piąty konstruktory określają powtórzenia elementów *Count* wartości *Val*.

Szósty konstruktor określa kopię sekwencji kontrolowanej przez *prawo*. Jeśli `InputIterator` jest typem liczb całkowitych, następne dwa konstruktory określają powtarzanie `(size_type)First` elementów wartości `(Type)Last`. W przeciwnym razie dwa następne konstruktory określają sekwencję `[First, Last)`.

"Dziewiąte i dziesiąte" konstruktory są takie same jak szósty, ale z odwołaniem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

Ostatni konstruktor określa początkową kontrolowana sekwencję z obiektem klasy `initializer_list<Type>`.

## <a name="front"></a>FSB

Zwraca odwołanie do pierwszego elementu na liście do przodu.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego elementu kontrolowanej sekwencji, które nie może być puste.

## <a name="get_allocator"></a>get_allocator

Zwraca kopię obiektu alokatora używanego do konstruowania listy do przodu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt [alokatora](../standard-library/allocator-class.md) .

## <a name="insert_after"></a>insert_after

Dodaje elementy do listy do przodu po określonej pozycji.

```cpp
iterator insert_after(const_iterator Where, const Type& Val);
void insert_after(const_iterator Where, size_type Count, const Type& Val);
void insert_after(const iterator Where, initializer_list<Type> IList);
iterator insert_after(const_iterator Where, Type&& Val);
template <class InputIterator>
    void insert_after(const_iterator Where, InputIterator First, InputIterator Last);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Pozycja na liście docelowych przekazywania, w której wstawiany jest pierwszy element.

*Liczba*\
Liczba elementów do wstawienia.

*Pierwszy*\
Początek zakresu wstawiania.

*Ostatni*\
Koniec zakresu wstawiania.

*Val*\
Element dodany do listy do przodu.

\ *IList*
Initializer_list do wstawienia.

### <a name="return-value"></a>Wartość zwracana

Iterator, który wyznacza nowo wstawiony element (tylko funkcje pierwszej i ostatniego elementu członkowskiego).

### <a name="remarks"></a>Uwagi

Każda funkcja członkowska wstawia — tuż po elemencie wskazywanym przez, *gdzie* w kontrolowanej sekwencji — sekwencję, która jest określona przez pozostałe operandy.

Pierwsza funkcja członkowska wstawia element, który ma wartość *Val* i zwraca iterator, który wyznacza nowo wstawiony element.

Druga funkcja członkowska wstawia powtarzające się elementy *Count* wartości *Val*.

Jeśli `InputIterator` jest typu Integer, trzecia funkcja członkowska zachowuje się tak samo jak `insert(it, (size_type)First, (Type)Last)`. W przeciwnym razie wstawia `[First, Last)`sekwencji, która nie może nakładać się na początkową sekwencję.

Czwarta funkcja członkowska wstawia sekwencję, która jest określona przez obiekt klasy `initializer_list<Type>`.

Ostatnia funkcja członkowska jest taka sama jak pierwsza, ale z odwołaniem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

Wstawianie `N` elementów powoduje `N` wywołań konstruktora. [Ponowna alokacja](../standard-library/forward-list-class.md) występuje, ale żadne Iteratory lub odwołania nie staną się nieprawidłowe.

Jeśli wyjątek jest zgłaszany podczas wstawiania jednego lub kilku elementów, kontener pozostaje niezmienione i zostanie ponownie zgłoszony wyjątek.

## <a name="iterator"></a>Iterator

Typ, który dostarcza iterator dla listy do przodu.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

`iterator` opisuje obiekt, który może obsłużyć iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego przez implementację.

## <a name="max_size"></a>max_size

Zwraca maksymalną długość listy do przodu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość najdłuższej sekwencji, którą obiekt może kontrolować.

### <a name="remarks"></a>Uwagi

## <a name="merge"></a>połączenie

Łączy dwie posortowane sekwencje w jedną posortowaną sekwencję w czasie liniowym. Usuwa elementy z listy argumentów i wstawia je do tej `forward_list`. Dwie listy powinny być sortowane według tego samego obiektu funkcji Compare przed wywołaniem do `merge`. Połączona lista będzie sortowana według tego obiektu funkcji porównywania.

```cpp
void merge(forward_list& right);
template <class Predicate>
    void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parametry

*prawa*\
Lista do przodu do scalenia.

\ *zgodności*
Obiekt funkcji Compare, który jest używany do sortowania elementów.

### <a name="remarks"></a>Uwagi

`forward_list::merge` usuwa elementy z `right``forward_list` i wstawia je do tego `forward_list`. Obie sekwencje muszą być uporządkowane według tego samego predykatu, co opisano poniżej. Połączona sekwencja jest również uporządkowana przez ten obiekt funkcji porównywania.

W przypadku iteratorów `Pi` i `Pj` wyznaczania elementów w pozycji `i` i `j`Pierwsza funkcja członkowska nakłada `!(*Pj < *Pi)` zamówienia w przypadku `i < j`. (Elementy są sortowane w kolejności `ascending`). Druga funkcja członkowska nakłada kolejność `! comp(*Pj, *Pi)` za każdym razem, gdy `i < j`.

W wyniku kontrolowanej sekwencji nie są odwrócone żadne pary elementów w oryginalnej kontrolowanej sekwencji. Jeśli para elementów w wyniku kontrolowanej sekwencji porównuje równe (`!(*Pi < *Pj) && !(*Pj < *Pi)`), element z oryginalnej kontrolowanej sekwencji pojawia się przed elementem z sekwencji kontrolowanej przez `right`.

Wyjątek występuje tylko wtedy, gdy `comp` zgłasza wyjątek. W takim przypadku kontrolowana sekwencja pozostanie w nieokreślonej kolejności, a wyjątek jest zgłaszany ponownie.

## <a name="op_eq"></a>operator =

Zamienia elementy listy do przodu z kopią innej listy do przodu.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Lista do przodu jest kopiowana na listę do przodu.

\ *IList*
Lista inicjalizatora w nawiasach klamrowych, która zachowuje się podobnie jak sekwencja elementów typu `Type`.

### <a name="remarks"></a>Uwagi

Pierwszy operator członkowski zastępuje kontrolowaną sekwencję kopią sekwencji kontrolowanej przez *prawo*.

Drugi operator członkowski zastępuje kontrolowaną sekwencję z obiektu klasy `initializer_list<Type>`.

Trzeci operator członkowski jest taki sam jak pierwszy, ale z odwołaniem [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) .

## <a name="pointer"></a>przytrzymaj

Typ, który dostarcza wskaźnik do elementu na liście do przodu.

```cpp
typedef typename Allocator::pointer pointer;
```

## <a name="pop_front"></a>pop_front

Usuwa element na początku listy do przodu.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element listy do przodu nie może być pusty.

Funkcja członkowska nigdy nie zgłasza wyjątku.

## <a name="push_front"></a>push_front

Dodaje element na początku listy do przodu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

*val*\
Element dodany na początku listy do przodu.

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, kontener pozostaje niezmienione i wyjątek jest ponownie zgłaszany.

## <a name="reference"></a>odwoła

Typ, który zawiera odwołanie do elementu na liście do przodu.

```cpp
typedef typename Allocator::reference reference;
```

## <a name="remove"></a>usuwa

Usuwa elementy z listy do przodu, które pasują do określonej wartości.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

*val*\
Wartość, która, jeśli jest przechowywana przez element, spowoduje usunięcie tego elementu z listy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa z kontrolowanej sekwencji wszystkie elementy, wyznaczone przez `P`iteratora, dla którego `*P ==  val`.

Funkcja członkowska nigdy nie zgłasza wyjątku.

## <a name="remove_if"></a>remove_if

Usuwa elementy z listy do przodu, dla których spełniony jest określony predykat.

```cpp
template <class Predicate>
    void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parametry

*pred*\
Predykat jednoargumentowy, który, jeśli jest spełniony przez element, powoduje usunięcie tego elementu z listy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa z kontrolowanej sekwencji wszystkie elementy, wyznaczone przez `P`iteratora, dla których ` pred(*P)` ma wartość true.

Wyjątek występuje tylko wtedy, gdy *pred* zgłasza wyjątek. W takim przypadku kontrolowana sekwencja pozostanie w nieokreślonym stanie, a wyjątek jest zgłaszany ponownie.

## <a name="resize"></a>Zmień rozmiar

Określa nowy rozmiar listy do przodu.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parametry

*_Newsize*\
Liczba elementów na liście o zmienionym rozmiarze.

*val*\
Wartość, która ma zostać użyta do uzupełnienia.

### <a name="remarks"></a>Uwagi

Funkcje składowe gwarantują, że liczba elementów na liście jest odtąd *_Newsize*. Jeśli ta sekwencja musi być większa, funkcja pierwszej składowej dołącza elementy o wartości `Type()`, podczas gdy druga funkcja członkowska dołącza elementy o wartości *Val*. W celu skrócenia kontrolowanej sekwencji obydwa funkcje elementów członkowskich skutecznie wywołują `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a>cofnięci

Odwraca kolejność, w jakiej elementy pojawiają się na liście do przodu.

```cpp
void reverse();
```

## <a name="size_type"></a>size_type

Typ, który reprezentuje odległość bez znaku między dwoma elementami.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ liczby całkowitej bez znaku opisuje obiekt, który może reprezentować długość dowolnej kontrolowanej sekwencji.

## <a name="sort"></a>porządku

Rozmieszcza elementy w kolejności rosnącej lub z kolejnością określoną przez predykat.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parametry

*pred*\
Predykat porządkowania.

### <a name="remarks"></a>Uwagi

Obie funkcje składowe porządkują elementy w kontrolowanej sekwencji według predykatu, opisanego poniżej.

W przypadku iteratorów `Pi` i `Pj` wyznaczania elementów w pozycji `i` i `j`Pierwsza funkcja członkowska nakłada `!(*Pj < *Pi)` zamówienia w przypadku `i < j`. (Elementy są sortowane w kolejności `ascending`). Funkcja szablonu elementu członkowskiego nakłada kolejność `! pred(*Pj, *Pi)` za każdym razem, gdy `i < j`. Brak uporządkowanych par elementów w oryginalnej kontrolowanej sekwencji nie są odwrócone w wyniku kontrolowanej sekwencji. (Sortowanie jest stabilne).

Wyjątek występuje tylko wtedy, gdy *pred* zgłasza wyjątek. W takim przypadku kontrolowana sekwencja pozostanie w nieokreślonej kolejności, a wyjątek jest zgłaszany ponownie.

## <a name="splice_after"></a>splice_after

Usuwa elementy ze źródła forward_list i wstawia je do forward_list docelowej.

```cpp
// insert the entire source forward_list
void splice_after(const_iterator Where, forward_list& Source);
void splice_after(const_iterator Where, forward_list&& Source);

// insert one element of the source forward_list
void splice_after(const_iterator Where, forward_list& Source, const_iterator Iter);
void splice_after(const_iterator Where, forward_list&& Source, const_iterator Iter);

// insert a range of elements from the source forward_list
void splice_after(
    const_iterator Where,
    forward_list& Source,
    const_iterator First,
    const_iterator Last);

void splice_after(
    const_iterator Where,
    forward_list&& Source,
    const_iterator First,
    const_iterator Last);
```

### <a name="parameters"></a>Parametry

*Gdzie*\
Pozycja w forward_list docelowym, która ma zostać wstawiona.

\ *źródłowa*
Forward_list źródłowa, która ma zostać wstawiona do forward_list docelowej.

\ *ITER*
Element, który ma zostać wstawiony ze źródłowego forward_list.

*Pierwszy*\
Pierwszy element z zakresu, który ma zostać wstawiony ze źródłowego forward_list.

*Ostatni*\
Pierwsza pozycja poza zakresem, który ma zostać wstawiony z forward_list źródłowej.

### <a name="remarks"></a>Uwagi

Pierwsza para funkcji Członkowskich wstawia sekwencję sterowaną przez *Źródło* tuż po elemencie w kontrolowanej sekwencji wskazywanym przez *WHERE*. Powoduje również usunięcie wszystkich elementów ze *źródła*. (`&Source` nie może być **taka sama.** )

Druga para funkcji Członkowskich usuwa element tuż po *ITER* w sekwencji kontrolowanej przez *Źródło* i wstawia go tuż po elemencie w kontrolowanej sekwencji wskazywanym przez *WHERE*. (Jeśli `Where == Iter || Where == ++Iter`, nie ma zmian).

Trzecia para funkcji elementów członkowskich (Metoda łączenia z zakresem) wstawia Podzakres wyznaczone przez `(First, Last)` z sekwencji kontrolowanej przez *Źródło* tuż po elemencie w kontrolowanej sekwencji wskazywanym przez *WHERE*. Powoduje również usunięcie oryginalnego podzakresu z sekwencji kontrolowanej przez *Źródło*. (W przypadku `&Source == this`zakres `(First, Last)` nie może zawierać elementu wskazywanego przez *WHERE*.)

Jeśli metoda łączenia w zakresie wstawia `N` elementy, a `&Source != this`, obiekt [iteratora](#iterator) klas jest zwiększany `N` razy.

Żadne Iteratory, wskaźniki lub odwołania, które wyznaczą elementy, są nieprawidłowe.

### <a name="example"></a>Przykład

```cpp
// forward_list_splice_after.cpp
// compile with: /EHsc /W4
#include <forward_list>
#include <iostream>

using namespace std;

template <typename S> void print(const S& s) {
    for (const auto& p : s) {
        cout << "(" << p << ") ";
    }

    cout << endl;
}

int main()
{
    forward_list<int> c1{ 10, 11 };
    forward_list<int> c2{ 20, 21, 22 };
    forward_list<int> c3{ 30, 31 };
    forward_list<int> c4{ 40, 41, 42, 43 };

    forward_list<int>::iterator where_iter;
    forward_list<int>::iterator first_iter;
    forward_list<int>::iterator last_iter;

    cout << "Beginning state of lists:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);
    cout << "c3 = ";
    print(c3);
    cout << "c4 = ";
    print(c4);

    where_iter = c2.begin();
    ++where_iter; // start at second element
    c2.splice_after(where_iter, c1);
    cout << "After splicing c1 into c2:" << endl;
    cout << "c1 = ";
    print(c1);
    cout << "c2 = ";
    print(c2);

    first_iter = c3.begin();
    c2.splice_after(where_iter, c3, first_iter);
    cout << "After splicing the first element of c3 into c2:" << endl;
    cout << "c3 = ";
    print(c3);
    cout << "c2 = ";
    print(c2);

    first_iter = c4.begin();
    last_iter = c4.end();
    // set up to get the middle elements
    ++first_iter;
    c2.splice_after(where_iter, c4, first_iter, last_iter);
    cout << "After splicing a range of c4 into c2:" << endl;
    cout << "c4 = ";
    print(c4);
    cout << "c2 = ";
    print(c2);
}
```

```Output
Beginning state of lists:c1 = (10) (11)c2 = (20) (21) (22)c3 = (30) (31)c4 = (40) (41) (42) (43)After splicing c1 into c2:c1 =c2 = (20) (21) (10) (11) (22)After splicing the first element of c3 into c2:c3 = (30)c2 = (20) (21) (31) (10) (11) (22)After splicing a range of c4 into c2:c4 = (40) (41)c2 = (20) (21) (42) (43) (31) (10) (11) (22)
```

## <a name="swap"></a>wymiany

Wymienia elementy dwóch list do przodu.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parametry

*prawa*\
Lista przesyłania dalej zawierająca elementy, które mają być wymieniane.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowane sekwencje między `*this` i *po prawej*. Jeśli `get_allocator() ==  right.get_allocator()`, robi to w stałym czasie, nie zgłasza wyjątków i unieważnia odwołania, wskaźniki lub Iteratory, które wyznaczają elementy w dwóch kontrolowanej sekwencji. W przeciwnym razie wykonuje wiele przypisań elementów i wywołań konstruktora proporcjonalnie do liczby elementów w dwóch kontrolowanej sekwencji.

## <a name="unique"></a>unikatowy

Eliminuje wszystkie elementy oprócz pierwszego elementu z każdej kolejnej grupy równych elementów.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

\ *zgodności*
Predykat binarny używany do porównywania kolejnych elementów.

### <a name="remarks"></a>Uwagi

Zachowuje pierwszy z każdego unikatowego elementu i usuwa resztę. Elementy muszą być sortowane, tak aby elementy równej wartości były przyległe na liście.

Pierwsza funkcja członkowska usuwa z kontrolowanej sekwencji każdy element, który jest porównywany z poprzednim elementem. W przypadku iteratorów `Pi` i `Pj` wyznaczania elementów w pozycji `i` i `j`Druga funkcja członkowska usuwa każdy element, dla którego `i + 1 == j &&  comp(*Pi, *Pj)`.

Dla kontrolowanej sekwencji `N` (> 0) ` comp(*Pi, *Pj)` predykatu jest oceniane `N - 1` razy.

Wyjątek występuje tylko wtedy, gdy `comp` zgłasza wyjątek. W takim przypadku kontrolowana sekwencja pozostanie w nieokreślonym stanie, a wyjątek jest zgłaszany ponownie.

## <a name="value_type"></a>value_type

Typ, który reprezentuje typ elementu przechowywanego na liście do przodu.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu `Type`.
