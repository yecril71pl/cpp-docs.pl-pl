---
title: forward_list — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
dev_langs:
- C++
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
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
caps.latest.revision: 25
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: cb1c470c509c7e09cf53da66d8c9a65d61ba4ea8
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="forwardlist-class"></a>forward_list — Klasa

Opis obiektu, który określa sekwencję zróżnicowanych długość elementów. Sekwencja jest przechowywana lista pojedynczo połączonych węzłów, każdy z nich zawierający element członkowski typu `Type`.

## <a name="syntax"></a>Składnia

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Type`|Typ danych elementu mają być przechowywane w forward_list —.|
|`Allocator`|Obiekt alokatora przechowywane, który hermetyzuje szczegółowe informacje dotyczące alokacji forward_list — i cofania alokacji pamięci. Ten parametr jest opcjonalny. Wartość domyślna to alokatora < `Type`>.|

## <a name="remarks"></a>Uwagi

A `forward_list` obiektu przydziela i zwalnia magazynu na potrzeby sekwencji steruje się za pomocą składowanych obiekt klasy `Allocator` opartego na [Allocator — klasa](../standard-library/allocator-class.md) (powszechnie znane jako `std::allocator)`. Aby uzyskać więcej informacji, zobacz [allocators —](../standard-library/allocators.md). Obiekt alokatora muszą mieć ten sam interfejs zewnętrznych jako obiekt klasy szablonu `allocator`.

> [!NOTE]
> Obiekt alokatora przechowywanych nie skopiowano po przypisaniu obiektu kontenera.

Iteratory, wskaźniki i odwołania mogą być nieprawidłowe po wymazaniu elementy ich kontrolowanej sekwencji za pośrednictwem `forward_list`. Wstawienia i splatane wykonywane w kontrolowanej sekwencji za pośrednictwem `forward_list` unieważnia Iteratory.

Dodatki do kontrolowanej sekwencji mogą wystąpić wywołań [forward_list::insert_after](#insert_after), która jest tylko funkcji członkowskiej, która wywołuje konstruktor `Type(const  T&)`. `forward_list` może również wywołania przenieść konstruktorów. Jeśli takie wyrażenie zgłasza wyjątek, obiektu kontenera wstawia żadnych nowych elementów i ponownie zgłasza wyjątek. W związku z tym obiekt klasy szablonu `forward_list` pozostanie w znanego stanu, gdy występują takie wyjątki.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[forward_list —](#forward_list)|Tworzy obiekt typu `forward_list`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę alokatora dla obiekt do przodu listy.|
|[const_iterator](#const_iterator)|Typ, który zapewnia stałą iteratora listy do przodu.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do `const` element na liście do przodu.|
|[const_reference](#const_reference)|Typ, który zapewnia stałą odwołanie do elementu na liście do przodu.|
|[difference_type](#difference_type)|Typ liczbę całkowitą ze znakiem, który może służyć do reprezentować liczbę elementów listy do przodu w zakresie między elementami wskazywana przez Iteratory.|
|[iterator](#iterator)|Typ, który udostępnia iterację na liście do przodu.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu na liście do przodu.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu na liście do przodu.|
|[size_type](#size_type)|Typ reprezentujący niepodpisane odległość między dwoma elementami.|
|[value_type](#value_type)|Typ, który reprezentuje typ elementu przechowywane na liście do przodu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Przypisz](#assign)|Powoduje usunięcie elementów z listy do przodu, a następnie kopiuje nowy zbiór elementów na listę docelową do przodu.|
|[before_begin](#before_begin)|Zwraca iteratora adresowania pozycji przed pierwszym elementem na liście do przodu.|
|[begin](#begin)|Zwraca iteratora adresowania pierwszy element na liście do przodu.|
|[cbefore_begin](#cbefore_begin)|Zwraca const iteratora adresowania pozycji przed pierwszym elementem na liście do przodu.|
|[cbegin](#cbegin)|Zwraca const iteratora adresowania pierwszy element na liście do przodu.|
|[cend](#cend)|Zwraca iteratora const, który dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście do przodu.|
|[Wyczyść](#clear)|Usuwa wszystkie elementy do przodu listy.|
|[emplace_after](#emplace_after)|Przenieś tworzy nowy element od określonej pozycji.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowane w miejscu na początku listy.|
|[pusty](#empty)|Sprawdza, czy do przodu lista jest pusta.|
|[Koniec](#end)|Zwraca iteratora, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście do przodu.|
|[erase_after](#erase_after)|Usuwa elementy na liście do przodu po określonej pozycji.|
|[Front](#front)|Zwraca odwołanie do pierwszego elementu listy do przodu.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu alokatora użyty do utworzenia listy do przodu.|
|[insert_after](#insert_after)|Dodaje elementy do listy do przodu po określonej pozycji.|
|[max_size](#max_size)|Zwraca maksymalną długość listy do przodu.|
|[merge](#merge)|Usuwa elementy z listy argumentów, wstawia je do listy do przodu docelowej oraz zamówienia nowe, łączny zbiór elementów w kolejności rosnącej lub w określonej kolejności.|
|[pop_front](#pop_front)|Usuwa element na początku listy do przodu.|
|[push_front](#push_front)|Dodaje element na początku listy do przodu.|
|[remove](#remove)|Usuwa elementy na liście do przodu, który spełnia określone wymagania.|
|[remove_if](#remove_if)|Usuwa elementy z listy do przodu, dla których jest spełniony określony predykat.|
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar listy do przodu.|
|[Reverse](#reverse)|Odwraca kolejność, w którym elementy występuje na liście do przodu.|
|[sort](#sort)|Rozmieszcza elementy w kolejności rosnącej lub z kolejnością określoną przez predykat.|
|[splice_after](#splice_after)|Restitches łącza między węzłami.|
|[swap](#swap)|Zamienia elementy dwie listy do przodu.|
|[unique](#unique)|Usuwa elementy sąsiednie przekazujące określonego testu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zamienia elementy do przodu listy kopię innej listy do przodu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<forward_list — >

**Namespace:** Standard

## <a name="allocator_type"></a>  forward_list::allocator_type

Typ, który reprezentuje klasę alokatora dla obiekt do przodu listy.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem parametru szablonu przydzielania.

## <a name="assign"></a>  forward_list::ASSIGN

Powoduje usunięcie elementów z listy do przodu, a następnie kopiuje nowy zbiór elementów na listę docelową do przodu.

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

|Parametr|Opis|
|---------------|-----------------|
|`first`|Początek zakresu zastąpienia.|
|`last`|Koniec zakresu zastąpienia.|
|`count`|Liczba elementów do przypisania.|
|`val`|Wartość do przypisania każdego elementu.|
|`Type`|Typ wartości.|
|`IList`|Initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Forward_list — w przypadku typu integer, pierwszej funkcji Członkowskich działa tak samo jak `assign((size_type)First, (Type)Last)`. W przeciwnym razie pierwszy funkcji członkowskiej zastępuje sekwencji kontrolowane przez `*this` z sekwencją [ `First, Last)`, który musi nie mogą się pokrywać początkowej kontrolowanej sekwencji.

Drugi funkcji członkowskiej zastępuje sekwencji kontrolowane przez `*this` z powtórzenia `Count` elementy wartości `Val`.

Trzeci funkcji członkowskiej kopiuje elementy initializer_list forward_list —.

## <a name="before_begin"></a>  forward_list::before_begin

Zwraca iteratora adresowania pozycji przed pierwszym elementem na liście do przodu.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, wskazujące bezpośrednio przed pierwszym elementem sekwencji (lub bezpośrednio przed zakończeniem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="begin"></a>  forward_list::BEGIN

Zwraca iteratora adresowania pierwszy element na liście do przodu.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iteratora do przodu, który wskazuje na pierwszym elementem sekwencji (lub bezpośrednio po zakończeniu pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="cbefore_begin"></a>  forward_list::cbefore_begin

Zwraca const iteratora adresowania pozycji przed pierwszym elementem na liście do przodu.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, wskazujące bezpośrednio przed pierwszym elementem sekwencji (lub bezpośrednio przed zakończeniem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="cbegin"></a>  forward_list::cbegin

Zwraca `const` iteratora, którego dotyczy pierwszy element w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A `const` iteratora dostępu do przodu, który wskazuje na pierwszym elementem w zakresie lub lokalizacji bezpośrednio po zakończeniu pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Z wartością zwracaną z `cbegin`, elementy w zakresie nie może być modyfikowany.

Można użyć funkcji członkowskiej zamiast `begin()` funkcji członkowskiej, aby zagwarantować, że jest zwracana wartość `const_iterator`. Zazwyczaj jest używany w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowo kluczowe wnioskowanie, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` do można modyfikować (z systemem innym niż `const`) kontenera dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  forward_list::cend

Zwraca `const` iteratora, którego dotyczy lokalizacji bezpośrednio po ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu do przodu, który wskazuje tuż za koniec zakresu.

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

## <a name="clear"></a>  forward_list::Clear

Usuwa wszystkie elementy do przodu listy.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Wywołania funkcji członkowskiej `erase_after(before_begin(), end()).`

## <a name="const_iterator"></a>  forward_list::const_iterator

Typ, który zapewnia stałą iteratora listy do przodu.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

`const_iterator` Opis obiektu, który może służyć jako stałej iteratora do przodu w kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla zdefiniowanego typu.

## <a name="const_pointer"></a>  forward_list::const_pointer

Typ, który dostarcza wskaźnik do `const` element na liście do przodu.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Uwagi

## <a name="const_reference"></a>  forward_list::const_reference

Typ, który zapewnia stałą odwołanie do elementu na liście do przodu.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

## <a name="difference_type"></a>  forward_list::difference_type

Typ liczbę całkowitą ze znakiem, który może służyć do reprezentować liczbę elementów listy do przodu w zakresie między elementami wskazywana przez Iteratory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Opis obiektu, który może reprezentować różnica między adresami dwóch elementów w kontrolowanej sekwencji.

## <a name="emplace_after"></a>  forward_list::emplace_after

Przenieś tworzy nowy element od określonej pozycji.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Where`|Pozycja na liście cel do przodu, w której jest tworzony nowy element.|
|`val`|Argument konstruktora.|

### <a name="return-value"></a>Wartość zwracana

Iterację wyznacza nowo wstawiony element.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska wstawia element z argumentów konstruktora `val` zaraz po elemencie wskazywana przez `Where` w kontrolowanej sekwencji. Jego zachowanie w przeciwnym razie jest taka sama jak [forward_list::insert_after](#insert_after).

## <a name="emplace_front"></a>  forward_list::emplace_front

Dodaje element skonstruowane w miejscu na początku listy.

```cpp
template <class Type>
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`val`|Element na początku listy do przodu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska wstawia element z argumentów konstruktora `_ val` na końcu kontrolowanej sekwencji.

Jeśli wyjątek kontenera pozostaje niezmieniony i jest zgłoszony wyjątek.

## <a name="empty"></a>  forward_list::Empty

Sprawdza, czy do przodu lista jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli do przodu lista jest pusta. w przeciwnym razie `false`.

## <a name="end"></a>  forward_list::end

Zwraca iteratora, którego dotyczy lokalizacji pomyślne wykonanie ostatniego elementu na liście do przodu.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iteratora do przodu, który wskazuje bezpośrednio po zakończeniu sekwencji.

## <a name="erase_after"></a>  forward_list::erase_after

Usuwa elementy na liście do przodu po określonej pozycji.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Where`|Pozycja na liście cel do przodu, gdzie usunięciem elementu.|
|`first`|Początek zakresu na usunięcie.|
|`last`|Koniec przedziału, aby wymazać.|

### <a name="return-value"></a>Wartość zwracana

Iterację wyznacza pierwszy element pozostałych poza wszelkie elementy usunięte, lub [forward_list::end](#end) , jeśli nie zawiera żadnego takiego elementu.

### <a name="remarks"></a>Uwagi

Pierwszej funkcji Członkowskich spowoduje usunięcie elementu w kontrolowanej sekwencji tuż po `Where`.

Drugi funkcji członkowskiej usuwa elementy kontrolowanej sekwencji w zakresie `( first,  last)` (ani punktu końcowego jest dołączony).

Wymazywanie `N` powoduje, że elementy `N` wywołania destruktora. [Ponowne przydzielenie](../standard-library/forward-list-class.md) występuje, więc Iteratory i odwołań staną się nieprawidłowe wymazanej elementów.

Funkcje Członkowskie nigdy nie zgłaszają wyjątków.

## <a name="forward_list"></a>  forward_list::forward_list

Tworzy obiekt typu `forward_list`.

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

|Parametr|Opis|
|---------------|-----------------|
|`Al`|Klasa alokatora do wykorzystania z tym obiektem.|
|`Count`|Liczba elementów na liście skonstruowany.|
|`Val`|Wartość elementów na liście skonstruowany.|
|`Right`|Lista skonstruowane listy ma być kopii.|
|`First`|Pozycja pierwszego elementu w zakresie elementów do skopiowania.|
|`Last`|Pozycja pierwszego elementu poza zakres elementów do skopiowania.|
|`IList`|Initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory przechowywania [alokatora](../standard-library/allocator-class.md) i zainicjuj kontrolowanej sekwencji. Obiekt alokatora jest argument `Al`, jeśli jest obecny. Konstruktor kopiujący jest ` right.get_allocator()`. W przeciwnym razie jest `Allocator()`.

Pierwsze dwa konstruktory Określ pusty początkowej kontrolowanej sekwencji.

Trzeci konstruktora określa powtórzenia `Count` elementy wartości `Type()`.

Konstruktory czwartym i piątym Określ powtórzenia `Count` elementy wartości `Val`.

Konstruktor szóstego Określa kopię sekwencji kontrolowane przez `Right`. Jeśli `InputIterator` jest typu integer następne dwa konstruktory Określ powtórzenia `(size_type)First` elementy wartości `(Type)Last`. W przeciwnym razie następne dwa konstruktory Określ sekwencję `[First, Last)`.

Konstruktory dziewiąty i dziesiątego są takie same jak szóstego, ale z [prawostronnie](../cpp/rvalue-reference-declarator-amp-amp.md) odwołania.

Konstruktor ostatniego Określa początkowy kontrolowanej sekwencji z obiektu klasy `initializer_list<Type>`.

## <a name="front"></a>  forward_list::front

Zwraca odwołanie do pierwszego elementu listy do przodu.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego elementu w kontrolowanej sekwencji musi być niepusta.

## <a name="get_allocator"></a>  forward_list::get_allocator

Zwraca kopię obiektu alokatora użyty do utworzenia listy do przodu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Zapisana [alokatora](../standard-library/allocator-class.md) obiektu.

## <a name="insert_after"></a>  forward_list::insert_after

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

|Parametr|Opis|
|---------------|-----------------|
|`Where`|Pozycja na liście cel do przodu, gdzie dodaje się pierwszym elementem.|
|`Count`|Liczba elementów do wstawienia.|
|`First`|Początek zakresu wstawiania.|
|`Last`|Koniec zakresu wstawiania.|
|`Val`|Element dodany do listy do przodu.|
|`IList`|Initializer_list do wstawienia.|

### <a name="return-value"></a>Wartość zwracana

Iteratora określający element nowo wstawionej (imię i nazwisko funkcje Członkowskie tylko).

### <a name="remarks"></a>Uwagi

Każdy element członkowski funkcji wstawiania — tylko po elemencie wskazywana przez `Where` w kontrolowanej sekwencji — sekwencję który "określony przez pozostałych argumentów.

Pierwszy funkcji członkowskiej wstawia element, który ma wartość `Val` i zwracającą iterator określający nowo wstawiony element.

Drugi funkcji członkowskiej wstawia powtórzenia `Count` elementy wartości `Val`.

Jeśli `InputIterator` jest typu integer trzeci funkcji członkowskiej działa tak samo jak `insert(it, (size_type)First, (Type)Last)`. W przeciwnym razie wstawia sekwencji `[First, Last)`, który musi nie mogą się pokrywać początkowej kontrolowanej sekwencji.

Czwarty funkcji członkowskiej wstawia sekwencji, określonym przez obiekt klasy `initializer_list<Type>`.

Ostatni funkcja członkowska jest taka sama jak pierwszy, ale z [prawostronnie](../cpp/rvalue-reference-declarator-amp-amp.md) odwołania.

Wstawianie `N` powoduje, że elementy `N` wywołania konstruktora. [Ponowne przydzielenie](../standard-library/forward-list-class.md) występuje, ale nie Iteratory lub odwołania staną się nieprawidłowe.

Jeśli wyjątek podczas wstawiania jednego lub więcej elementów, kontener jest niezmieniony po lewej i jest zgłoszony wyjątek.

## <a name="iterator"></a>  forward_list::iterator

Typ, który udostępnia iterację na liście do przodu.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

`iterator` Opis obiektu, który może służyć jako do przodu iteratora w kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla zdefiniowanego typu.

## <a name="max_size"></a>  forward_list::max_size

Zwraca maksymalną długość listy do przodu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość sekwencji najdłuższym, który można kontrolować obiektem.

### <a name="remarks"></a>Uwagi

## <a name="merge"></a>  forward_list::merge

Łączy dwie sekwencje posortowane w jednym sekwencji posortowane w czasie liniowej. Usunięcie elementów z listy argumentów i wstawia je do tego `forward_list`. Dwie listy mają być sortowane według tego samego obiektu Funkcja porównywania przed wywołaniem do `merge`. Połączonej listy będą sortowane według który porównuje obiekt funkcji.

```cpp
void merge(forward_list& right);
template <class Predicate>
void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|Lista do przodu do scalenia.|
|`comp`|Obiekt Funkcja porównywania jest używane do sortowania elementów.|

### <a name="remarks"></a>Uwagi

`forward_list::merge` Usuwa elementy z `forward_list` `right`i wstawia je do tego `forward_list`. Zarówno sekwencji muszą być uporządkowane tego samego predykat opisane poniżej. Łączna sekwencji jest również uporządkowanych według tego obiektu Funkcja porównywania.

Dla Iteratory `Pi` i `Pj` wyznaczenie elementy w pozycji `i` i `j`, pierwszej funkcji Członkowskich nakłada kolejność `!(*Pj < *Pi)` przy każdym `i < j`. (Elementy są sortowane w `ascending` kolejności.) Drugi funkcji członkowskiej nakłada kolejność `! comp(*Pj, *Pi)` przy każdym `i < j`.

Nie pary elementów w oryginalnym kontrolowanej sekwencji są wycofywane w wynikowej kontrolowanej sekwencji. Jeśli dwa elementy w wynikowym kontrolowane sekwencji porównuje równe ( `!(*Pi < *Pj) && !(*Pj < *Pi)`), z oryginalnego kontrolowanej sekwencji jest wyświetlany element przed elementem z sekwencji kontrolowane przez `right`.

Wyjątek występuje tylko wtedy, gdy `comp` zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w nieokreślonej kolejności i jest zgłoszony wyjątek.

## <a name="op_eq"></a>  forward_list::operator =

Zamienia elementy do przodu listy kopię innej listy do przodu.

```cpp
forward_list& operator=(const forward_list& right);
forward_list& operator=(initializer_list<Type> IList);
forward_list& operator=(forward_list&& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|Lista do przodu kopiowane do listy do przodu.|
|`IList`|Listy inicjalizatora w nawiasach klamrowych zachowuje się jak sekwencję elementów typu `Type`.|

### <a name="remarks"></a>Uwagi

Pierwszy operator członkowski zastępuje kopię sekwencji kontrolowane przez kontrolowanej sekwencji `right`.

Drugi operator członkowski zastępuje kontrolowanej sekwencji z obiektu klasy `initializer_list<Type>`.

Trzeci operator członkowski jest taka sama jak pierwszy, ale z [prawostronnie](../cpp/rvalue-reference-declarator-amp-amp.md) odwołania.

## <a name="pointer"></a>  forward_list::Pointer

Typ, który dostarcza wskaźnik do elementu na liście do przodu.

```cpp
typedef typename Allocator::pointer pointer;
```

### <a name="remarks"></a>Uwagi

## <a name="pop_front"></a>  forward_list::pop_front

Usuwa element na początku listy do przodu.

```cpp
void pop_front();
```

### <a name="remarks"></a>Uwagi

Pierwszy element listy do przodu musi być niepusta.

Funkcja członkowska nie zgłasza wyjątek.

## <a name="push_front"></a>  forward_list::push_front

Dodaje element na początku listy do przodu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`val`|Element na początku listy do przodu.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek kontenera pozostaje niezmieniony i jest zgłoszony wyjątek.

## <a name="reference"></a>  forward_list::Reference

Typ, który zawiera odwołanie do elementu na liście do przodu.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="remarks"></a>Uwagi

## <a name="remove"></a>  forward_list::Remove

Usuwa elementy na liście do przodu, który spełnia określone wymagania.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`val`|Wartość, która posiadanych przez element spowoduje usunięcie tego elementu z listy.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa kontrolowanej sekwencji wszystkie elementy wskazywany przez iterator `P`, dla którego `*P ==  val`.

Funkcja członkowska nie zgłasza wyjątek.

## <a name="remove_if"></a>  forward_list::remove_if

Usuwa elementy z listy do przodu, dla których jest spełniony określony predykat.

```cpp
template <class Predicate>
void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pred`|Predykat jednoargumentowe, które, jeśli spełnione przez element, powoduje usunięcie elementu z listy.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa kontrolowanej sekwencji wszystkie elementy wskazywany przez iterator `P`, dla którego ` pred(*P)` ma wartość true.

Wyjątek występuje tylko wtedy, gdy `pred` zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w stanie nieokreślony i jest zgłoszony wyjątek.

## <a name="resize"></a>  forward_list::Resize

Określa nowy rozmiar listy do przodu.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Newsize`|Liczba elementów na liście do przodu po zmianie rozmiaru.|
|`val`|Wartość służących do uzupełniania.|

### <a name="remarks"></a>Uwagi

Funkcje Członkowskie zarówno zapewnienia, że liczba elementów na liście odtąd `_Newsize`. Należy go dłużej kontrolowanej sekwencji, pierwszej funkcji Członkowskich dołącza elementy o wartości `Type()`, podczas gdy druga funkcji członkowskiej dołącza elementy o wartości `val`. Aby kontrolowanej sekwencji krótszy, efektywnie wywołania funkcji obu elementów członkowskich `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a>  forward_list::reverse

Odwraca kolejność, w którym elementy występuje na liście do przodu.

```cpp
void reverse();
```

### <a name="remarks"></a>Uwagi

## <a name="size_type"></a>  forward_list::size_type

Typ reprezentujący niepodpisane odległość między dwoma elementami.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typu Liczba całkowita bez znaku opisuje obiekt, który może reprezentować długość żadnych kontrolowanej sekwencji.

## <a name="sort"></a>  forward_list::sort

Rozmieszcza elementy w kolejności rosnącej lub z kolejnością określoną przez predykat.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`pred`|Predykat porządkowania.|

### <a name="remarks"></a>Uwagi

Obie funkcje Członkowskie kolejność elementów w kontrolowanej sekwencji predykatu, opisane poniżej.

Dla Iteratory `Pi` i `Pj` wyznaczenie elementy w pozycji `i` i `j`, pierwszej funkcji Członkowskich nakłada kolejność `!(*Pj < *Pi)` przy każdym `i < j`. (Elementy są sortowane w `ascending` kolejności.) Funkcja szablonu elementu członkowskiego nakłada kolejność `! pred(*Pj, *Pi)` przy każdym `i < j`. Nie uporządkowanej pary elementów w oryginalnym kontrolowanej sekwencji są wycofywane w wynikowej kontrolowanej sekwencji. (Sortowanie jest stabilna).

Wyjątek występuje tylko wtedy, gdy `pred` zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w nieokreślonej kolejności i jest zgłoszony wyjątek.

## <a name="splice_after"></a>  forward_list::splice_after

Usuwa elementy z forward_list — źródło i wstawia je do forward_list — docelowym.

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

`Where` Pozycja w forward_list docelowy — po upływie którego do wstawienia.

`Source` Forward_list — źródło, to można wstawiać do forward_list — docelowego.

`Iter` Element, który ma zostać wstawiony z forward_list — źródło.

`First` Pierwszym elementem w zakresie ma zostać wstawiony z forward_list — źródło.

`Last` Pierwszą pozycję spoza zakresu, który ma zostać wstawiony z forward_list — źródło.

### <a name="remarks"></a>Uwagi

Pierwszy pary funkcji Członkowskich wstawia sekwencji kontrolowane przez `Source` zaraz po elementu w kontrolowanej sekwencji wskazywana przez `Where`. Usuwa również wszystkie elementy z `Source`. ( `&Source` nie może być równa `this`.)

Druga para funkcji Członkowskich usuwa element tuż po `Iter` w sekwencji kontrolowane przez `Source` i wstawia go tuż po elementu w kontrolowanej sekwencji wskazywana przez `Where`. (Jeśli `Where == Iter || Where == ++Iter`, Brak zmian.)

Trzeci pary funkcji Członkowskich (ranged łączenia) wstawia Podzakres wskazywany przez `(First, Last)` z sekwencji kontrolowane przez `Source` zaraz po elementu w kontrolowanej sekwencji wskazywana przez `Where`. Powoduje usunięcie oryginalnego Podzakres z sekwencji kontrolowane przez `Source`. (Jeśli `&Source == this`, zakres `(First, Last)` nie może zawierać elementu wskazywanego przez `Where`.)

Jeśli wstawia łączenia ranged `N` elementów, i `&Source != this`, obiekt klasy [iterator](#iterator) jest zwiększany `N` razy.

Nie Iteratory, wskaźniki lub odwołania, które określają połączonego elementy staną się nieprawidłowe.

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

## <a name="swap"></a>  forward_list::swap

Zamienia elementy dwie listy do przodu.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`right`|Lista do przodu, zawierająca elementy, aby wymienić.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska zamienia kontrolowanej sekwencji między `*this` i `right`. Jeśli `get_allocator() ==  right.get_allocator()`, robi to w czasie stałej zgłasza bez wyjątków i go unieważnia nie odwołań, wskaźniki lub Iteratory, które określają elementów w dwóch kontrolowanej sekwencji. W przeciwnym razie wykonuje szereg element zadania i wywołania konstruktora proporcjonalny do liczby elementów w dwóch kontrolowanej sekwencji.

## <a name="unique"></a>  forward_list::UNIQUE

Usuwa wszystkie oprócz pierwszego elementu z co grupy kolejnych elementów takie same.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`comp`|Predykat binarne użyty do porównania kolejnych elementów.|

### <a name="remarks"></a>Uwagi

Temu pierwszego dnia każdego elementu unikatowy i usuwa pozostałe. Elementy muszą być posortowane, tak aby elementy takie same wartości znajdują się obok siebie na liście.

Pierwszy funkcji członkowskiej usuwa kontrolowanej sekwencji każdy element, który porównuje równa jej poprzedniego elementu. Dla Iteratory `Pi` i `Pj` wyznaczenie elementy w pozycji `i` i `j`, drugi funkcji członkowskiej Usuwa każdy element, dla którego `i + 1 == j &&  comp(*Pi, *Pj)`.

Kontrolowanej sekwencji długość `N` (> 0), predykat ` comp(*Pi, *Pj)` oceny `N - 1` razy.

Wyjątek występuje tylko wtedy, gdy `comp` zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w stanie nieokreślony i jest zgłoszony wyjątek.

## <a name="value_type"></a>  forward_list::value_type

Typ, który reprezentuje typ elementu przechowywane na liście do przodu.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem _ parametru szablonu `Ty`.

## <a name="see-also"></a>Zobacz także

[<forward_list>](../standard-library/forward-list.md)<br/>
