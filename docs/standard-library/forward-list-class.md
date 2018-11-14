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
ms.assetid: 89a3b805-ab60-4858-b772-5855130c11b1
ms.openlocfilehash: 5eaa8eba1904dc0a729fb66b280b8d3fa4bb78f1
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524550"
---
# <a name="forwardlist-class"></a>forward_list — Klasa

Opisuje obiekt, który kontroluje różnej długości sekwencje elementów. Sekwencja jest przechowywany jako pojedynczo połączoną listę węzłów, każdy z nich zawierający składowej typu `Type`.

## <a name="syntax"></a>Składnia

```cpp
template <class Type,
    class Allocator = allocator<Type>>
class forward_list
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Typ*|Typ danych elementu, który ma być przechowywany w forward_list.|
|*Allocator*|Przechowywany obiekt alokatora, który hermetyzuje szczegóły dotyczące forward_list alokacji i dezalokacji pamięci. Ten parametr jest opcjonalny. Wartość domyślna to alokatora < `Type`>.|

## <a name="remarks"></a>Uwagi

A `forward_list` obiekt przydziela i zwalnia pamięć dla sekwencję którą kontroluje, przez przechowywany obiekt klasy *alokatora* opartego na [alokatora klasy](../standard-library/allocator-class.md) (powszechnie znane jako `std::allocator)`. Aby uzyskać więcej informacji, zobacz [buforów](../standard-library/allocators.md). Obiekt alokatora musi mieć ten sam interfejs zewnętrzny co obiekt klasy szablonu `allocator`.

> [!NOTE]
> Przechowywany obiekt alokatora nie jest kopiowany po przypisaniu obiektu kontenera.

Iteratory, wskaźniki i odwołania mogą stać się nieprawidłowe po ich kontrolowanej sekwencji elementów są usuwane przez `forward_list`. Liczba operacji wstawienia i splatane wykonywane w kontrolowanej sekwencji za pośrednictwem `forward_list` nie unieważnia iteratorów.

Dodatki do kontrolowanej sekwencji mogą wystąpić przez wywołania [forward_list::insert_after](#insert_after), który jest tylko funkcji składowej, która wywołuje konstruktor `Type(const  T&)`. `forward_list` może także wywołania konstruktorów przenoszenia. Jeżeli takie wyrażenie zgłasza wyjątek, obiekt kontenera wstawia nie nowe elementy i ponownie zgłasza wyjątek. W związku z tym, obiekt klasy szablonu `forward_list` pozostanie w znanym stanie, gdy występują takie wyjątki.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[forward_list —](#forward_list)|Tworzy obiekt typu `forward_list`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ, który reprezentuje klasę alokatora dla obiektu listy do przodu.|
|[const_iterator](#const_iterator)|Typ, który zapewnia stały iterator do przodu listy.|
|[const_pointer](#const_pointer)|Typ, który dostarcza wskaźnik do **const** elementu listy do przodu.|
|[const_reference](#const_reference)|Typ, który zawiera stałe odwołanie do elementu na liście do przodu.|
|[difference_type](#difference_type)|Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów listy do przodu w zakresie pomiędzy elementami wskazywanymi przez Iteratory.|
|[iterator](#iterator)|Typ, który zapewnia iterator do przodu listy.|
|[pointer](#pointer)|Typ, który dostarcza wskaźnik do elementu na liście do przodu.|
|[Odwołanie](#reference)|Typ, który zawiera odwołanie do elementu na liście do przodu.|
|[size_type](#size_type)|Typ, który reprezentuje odległości bez znaku między dwoma elementami.|
|[value_type](#value_type)|Typ, który reprezentuje typ elementu przechowywanego na liście do przodu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przypisz](#assign)|Usuwa elementy z listy do przodu i kopiuje nowy zbiór elementów do listy docelowej do przodu.|
|[before_begin](#before_begin)|Zwraca iterator odnoszący się do pozycji przed pierwszym elementem na liście do przodu.|
|[begin](#begin)|Zwraca iterator adresujący pierwszy element na liście do przodu.|
|[cbefore_begin](#cbefore_begin)|Zwraca stały iterator odnoszący się do pozycji przed pierwszym elementem na liście do przodu.|
|[cbegin](#cbegin)|Zwraca iterator stałych adresujący pierwszy element na liście do przodu.|
|[cend](#cend)|Zwraca iterator const, który dotyczy lokalizacji następującej po ostatnim elemencie na liście do przodu.|
|[Usuń zaznaczenie](#clear)|Usuwa wszystkie elementy listy do przodu.|
|[emplace_after](#emplace_after)|Przenieś tworzy nowy element, po określonej pozycji.|
|[emplace_front](#emplace_front)|Dodaje element skonstruowany w miejscu na początku listy.|
|[pusty](#empty)|Sprawdza, czy do przodu lista jest pusta.|
|[koniec](#end)|Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie na liście do przodu.|
|[erase_after](#erase_after)|Usuwa elementy z listy do przodu, po określonej pozycji.|
|[Frontonu](#front)|Zwraca odwołanie do pierwszego elementu na liście do przodu.|
|[get_allocator](#get_allocator)|Zwraca kopię obiektu programu przydzielania, używany do utworzenia listy do przodu.|
|[insert_after](#insert_after)|Dodaje elementy do listy do przodu, po określonej pozycji.|
|[max_size](#max_size)|Zwraca maksymalną długość listy do przodu.|
|[merge](#merge)|Usuwa elementy z listy argumentów, wstawia je do listy do przodu docelowej i porządkuje nowe, połączone zbiór elementów w kolejności rosnącej lub w określonej kolejności.|
|[pop_front](#pop_front)|Usuwa element na początku listy do przodu.|
|[push_front](#push_front)|Dodaje element do początku listy do przodu.|
|[remove](#remove)|Usuwa elementy na liście do przodu, który odpowiada określonej wartości.|
|[remove_if](#remove_if)|Usuwa elementy z listy do przodu, dla których jest spełniony określony predykat.|
|[Zmiana rozmiaru](#resize)|Określa nowy rozmiar dla listy do przodu.|
|[zwrotny](#reverse)|Odwraca kolejność, w której elementy występują na liście do przodu.|
|[sort](#sort)|Rozmieszcza elementy w kolejności rosnącej lub z kolejnością określone przez predykat.|
|[splice_after](#splice_after)|Restitches łącza między węzłami.|
|[swap](#swap)|Zamienia elementy z dwóch list do przodu.|
|[unique](#unique)|Usuwa sąsiadujące elementy, które przekazać określonego testu.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Zamienia elementy do przodu listy kopię innej listy do przodu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<forward_list >

**Namespace:** standardowe

## <a name="allocator_type"></a>  forward_list::allocator_type

Typ, który reprezentuje klasę alokatora dla obiektu listy do przodu.

```cpp
typedef Allocator allocator_type;
```

### <a name="remarks"></a>Uwagi

`allocator_type` jest synonimem dla parametru szablonu programu przydzielania.

## <a name="assign"></a>  forward_list::ASSIGN

Usuwa elementy z listy do przodu i kopiuje nowy zbiór elementów do listy docelowej do przodu.

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
|*pierwszy*|Początek zakresu zastępczy.|
|*ostatni*|Koniec zakresu zastępczy.|
|*Liczba*|Liczba elementów, które można przypisać.|
|*Val*|Wartość do przypisania z każdego elementu.|
|*Typ*|Typ wartości.|
|* IList "|Lista initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Forward_list — w przypadku typu całkowitego, pierwsza funkcja elementu członkowskiego działa tak samo jak `assign((size_type)First, (Type)Last)`. W przeciwnym razie pierwszy element członkowski funkcji zastępuje sekwencji kontrolowanej przez `*this` z sekwencją [ `First, Last)`, który nie może nakładać początkowej kontrolowanej sekwencji.

Funkcja drugiego członka zastępuje sekwencji kontrolowanej przez `*this` z powtórzenia `Count` elementów wartości `Val`.

Trzecia funkcja członkowska kopiuje elementy lista initializer_list do forward_list.

## <a name="before_begin"></a>  forward_list::before_begin

Zwraca iterator odnoszący się do pozycji przed pierwszym elementem na liście do przodu.

```cpp
const_iterator before_begin() const;
iterator before_begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje tuż przed pierwszym elementem sekwencji (lub bezpośrednio przed zakończeniem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="begin"></a>  forward_list::BEGIN

Zwraca iterator adresujący pierwszy element na liście do przodu.

```cpp
const_iterator begin() const;
iterator begin();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje na pierwszy element w sekwencji (lub tuż za koniec pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="cbefore_begin"></a>  forward_list::cbefore_begin

Zwraca stały iterator odnoszący się do pozycji przed pierwszym elementem na liście do przodu.

```cpp
const_iterator cbefore_begin() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje tuż przed pierwszym elementem sekwencji (lub bezpośrednio przed zakończeniem pustej sekwencji).

### <a name="remarks"></a>Uwagi

## <a name="cbegin"></a>  forward_list::cbegin

Zwraca **const** iterator odnoszący się do pierwszego elementu w zakresie.

```cpp
const_iterator cbegin() const;
```

### <a name="return-value"></a>Wartość zwracana

A **const** iterator dostępu do przodu, który wskazuje na pierwszy element zakresu lub lokalizację tuż poza końcem pustego zakresu (dla pustego zakresu, `cbegin() == cend()`).

### <a name="remarks"></a>Uwagi

Wartością zwracaną `cbegin`, nie można modyfikować elementów w zakresie.

Można użyć tej funkcji elementu członkowskiego zamiast `begin()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `begin()` i `cbegin()`.

```cpp
auto i1 = Container.begin();
// i1 is Container<T>::iterator
auto i2 = Container.cbegin();
// i2 is Container<T>::const_iterator
```

## <a name="cend"></a>  forward_list::cend

Zwraca **const** iterator adresujący lokalizację tuż za ostatnim elementem w zakresie.

```cpp
const_iterator cend() const;
```

### <a name="return-value"></a>Wartość zwracana

Iterator dostępu do przodu, który wskazuje tuż za koniec zakresu.

### <a name="remarks"></a>Uwagi

`cend` Służy do sprawdzenia, czy iterator minął koniec swojego zakresu.

Można użyć tej funkcji elementu członkowskiego zamiast `end()` funkcja elementu członkowskiego w celu zagwarantowania, że wartość zwracana jest `const_iterator`. Zazwyczaj jest używana w połączeniu z [automatycznie](../cpp/auto-cpp.md) wpisz słowem kluczowym dedukcji, jak pokazano w poniższym przykładzie. W tym przykładzie należy wziąć pod uwagę `Container` jako modyfikowalny (nie - **const**) kontener dowolnego rodzaju, który obsługuje `end()` i `cend()`.

```cpp
auto i1 = Container.end();
// i1 is Container<T>::iterator
auto i2 = Container.cend();

// i2 is Container<T>::const_iterator
```

Wartość zwrócona przez obiekt `cend` nie należy usuwać odwołania.

## <a name="clear"></a>  forward_list::Clear

Usuwa wszystkie elementy listy do przodu.

```cpp
void clear();
```

### <a name="remarks"></a>Uwagi

Wywołania tej funkcji elementu członkowskiego `erase_after(before_begin(), end()).`

## <a name="const_iterator"></a>  forward_list::const_iterator

Typ, który zapewnia stały iterator do przodu listy.

```cpp
typedef implementation-defined const_iterator;
```

### <a name="remarks"></a>Uwagi

`const_iterator` Opisuje obiekt, który może służyć jako stały iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego w implementacji.

## <a name="const_pointer"></a>  forward_list::const_pointer

Typ, który dostarcza wskaźnik do **const** elementu listy do przodu.

```cpp
typedef typename Allocator::const_pointer
    const_pointer;
```

### <a name="remarks"></a>Uwagi

## <a name="const_reference"></a>  forward_list::const_reference

Typ, który zawiera stałe odwołanie do elementu na liście do przodu.

```cpp
typedef typename Allocator::const_reference const_reference;
```

### <a name="remarks"></a>Uwagi

## <a name="difference_type"></a>  forward_list::difference_type

Typ liczby całkowitej ze znakiem, który może służyć do reprezentowania liczby elementów listy do przodu w zakresie pomiędzy elementami wskazywanymi przez Iteratory.

```cpp
typedef typename Allocator::difference_type difference_type;
```

### <a name="remarks"></a>Uwagi

`difference_type` Opisuje obiekt, który może reprezentować różnica między adresami którychkolwiek dwóch elementów w kontrolowanej sekwencji.

## <a name="emplace_after"></a>  forward_list::emplace_after

Przenieś tworzy nowy element, po określonej pozycji.

```cpp
template <class T>
iterator emplace_after(const_iterator Where, Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Where*|Pozycja na liście do przodu, w której jest tworzony nowy element.|
|*Val*|Argument konstruktora.|

### <a name="return-value"></a>Wartość zwracana

Iterator, który wyznacza nowo wstawionego elementu.

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego wstawia element z argumentów konstruktora *val* zaraz po element wskazane przez *gdzie* w kontrolowanej sekwencji. Jego zachowanie w przeciwnym razie jest taka sama jak [forward_list::insert_after](#insert_after).

## <a name="emplace_front"></a>  forward_list::emplace_front

Dodaje element skonstruowany w miejscu na początku listy.

```cpp
template <class Type>
void emplace_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Val*|Element dodany na początku listy do przodu.|

### <a name="remarks"></a>Uwagi

Ta funkcja elementu członkowskiego wstawia element z argumentów konstruktora `_ val` na koniec kontrolowanej sekwencji.

Jeśli wyjątek jest zgłaszany, kontener pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

## <a name="empty"></a>  forward_list::Empty

Sprawdza, czy do przodu lista jest pusta.

```cpp
bool empty() const;
```

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli do przodu lista jest pusta; w przeciwnym razie **false**.

## <a name="end"></a>  forward_list::end

Zwraca iterator adresujący lokalizację następującą po ostatnim elemencie na liście do przodu.

```cpp
const_iterator end() const;
iterator end();
```

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który wskazuje tuż za koniec sekwencji.

## <a name="erase_after"></a>  forward_list::erase_after

Usuwa elementy z listy do przodu, po określonej pozycji.

```cpp
iterator erase_after(const_iterator Where);
iterator erase_after(const_iterator first, const_iterator last);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Where*|Pozycja na liście do przodu, gdzie elementu są usuwane.|
|*pierwszy*|Początek zakresu, aby wymazać.|
|*ostatni*|Koniec zakresu do wymazania.|

### <a name="return-value"></a>Wartość zwracana

Iterator opisujący pierwszy element pozostający poza wszelkimi elementami usuniętymi lub [forward_list::end](#end) jeśli taki element nie istnieje.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkostwa usuwa element kontrolowanej sekwencji tuż za *gdzie*.

Funkcja drugiego członka usuwa elementy kontrolowanej sekwencji w zakresie `( first,  last)` (ani punktu końcowego jest dołączony).

Wymazywanie `N` powoduje, że elementy `N` wywołania destruktora. [Ponowne przydzielenie](../standard-library/forward-list-class.md) występuje, więc Iteratory i odwołania stają się nieprawidłowe wymazane elementów.

Funkcje elementów członkowskich nigdy nie zgłasza wyjątku.

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
|*Al*|Klasa alokatora do wykorzystania z tym obiektem.|
|*Liczba*|Liczba elementów na utworzonej liście.|
|*Val*|Wartość elementów na utworzonej liście.|
|*po prawej stronie*|Lista, z której kopią jest lista skonstruowana.|
|*pierwszy*|Pozycja pierwszego elementu w zakresie elementów, które mają zostać skopiowane.|
|*ostatni*|Pozycja pierwszego elementu poza zakresem elementów, które mają zostać skopiowane.|
|*IList*|Lista initializer_list do skopiowania.|

### <a name="remarks"></a>Uwagi

Wszystkie konstruktory zapisują [alokatora](../standard-library/allocator-class.md) i zainicjuj kontrolowanej sekwencji. Obiekt alokatora jest argumentem *Al*, jeśli jest obecny. Konstruktor kopiujący jest ` right.get_allocator()`. W przeciwnym razie jest `Allocator()`.

Dwa pierwsze konstruktory określają pustą kontrolowaną sekwencję początkowej.

Trzeci Konstruktor określa powtórzenia *liczba* elementów wartości `Type()`.

Czwarty i piąty Konstruktor określają powtórzenia *liczba* elementów wartości *Val*.

Szósty Konstruktor Określa kopię sekwencji kontrolowanej przez *po prawej stronie*. Jeśli `InputIterator` typu liczby całkowitej, następne dwa konstruktory określają powtórzenia `(size_type)First` elementów wartości `(Type)Last`. W przeciwnym razie Określ sekwencję przez następne dwa konstruktory `[First, Last)`.

Konstruktory dziewiątego i dziesiąty różnią się od szóstego, ale z [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odwołania.

Ostatni Konstruktor Określa początkowy kontrolowanej sekwencji za pomocą obiektu klasy `initializer_list<Type>`.

## <a name="front"></a>  forward_list::front

Zwraca odwołanie do pierwszego elementu na liście do przodu.

```cpp
reference front();
const_reference front() const;
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do pierwszego elementu w kontrolowanej sekwencji, która musi być niepusta.

## <a name="get_allocator"></a>  forward_list::get_allocator

Zwraca kopię obiektu programu przydzielania, używany do utworzenia listy do przodu.

```cpp
allocator_type get_allocator() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany [alokatora](../standard-library/allocator-class.md) obiektu.

## <a name="insert_after"></a>  forward_list::insert_after

Dodaje elementy do listy do przodu, po określonej pozycji.

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
|*Where*|Pozycja na liście do przodu polegający na wstawieniu pierwszego elementu.|
|*Liczba*|Liczba elementów do wstawienia.|
|*pierwszy*|Początek zakresu wstawiania.|
|*ostatni*|Koniec zakresu wstawiania.|
|*Val*|Element dodany do listy do przodu.|
|*IList*|Lista initializer_list do wstawienia.|

### <a name="return-value"></a>Wartość zwracana

Iterator, który wyznacza nowo wstawionego elementu (tylko w pierwszy i ostatni element członkowski funkcji).

### <a name="remarks"></a>Uwagi

Każdy element członkowski funkcji wstawia — tylko po elemencie, do których prowadzą *gdzie* w kontrolowanej sekwencji — sekwencji, "określone przez pozostałe argumenty operacji.

Pierwsza funkcja elementu członkowskiego wstawia element, który ma wartość *Val* i zwraca iterator, który wyznacza nowo wstawionego elementu.

Funkcja drugiego członka wstawia powtórzenia *liczba* elementów wartości *Val*.

Jeśli `InputIterator` typu liczby całkowitej, trzecia funkcji członkowska, działa tak samo jak `insert(it, (size_type)First, (Type)Last)`. W przeciwnym razie wstawia sekwencję `[First, Last)`, który nie może nakładać początkowej kontrolowanej sekwencji.

Czwarty funkcja elementu członkowskiego wstawia sekwencję, która jest określona przez obiekt klasy `initializer_list<Type>`.

Ostatni element członkowski funkcji jest taka sama jak pierwszy, ale z [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odwołania.

Wstawianie `N` powoduje, że elementy `N` wywołania konstruktora. [Ponowne przydzielenie](../standard-library/forward-list-class.md) problem wystąpi, ale nie Iteratory lub odwołania stają się nieprawidłowe.

Jeśli wyjątek jest generowany podczas wstawiania jednego lub więcej elementów, kontener niezmieniony po lewej stronie, a wyjątek jest zgłaszany ponownie.

## <a name="iterator"></a>  forward_list::iterator

Typ, który zapewnia iterator do przodu listy.

```cpp
typedef implementation-defined iterator;
```

### <a name="remarks"></a>Uwagi

`iterator` Opisuje obiekt, który może służyć jako iterator do przodu dla kontrolowanej sekwencji. Jest on opisany tutaj jako synonim dla typu zdefiniowanego w implementacji.

## <a name="max_size"></a>  forward_list::max_size

Zwraca maksymalną długość listy do przodu.

```cpp
size_type max_size() const;
```

### <a name="return-value"></a>Wartość zwracana

Długość najdłuższej sekwencji, która może kontrolować obiekt.

### <a name="remarks"></a>Uwagi

## <a name="merge"></a>  forward_list::merge

Łączy dwie sekwencje posortowanych w pojedynczy posortowany sekwencji liniowo. Usuwa elementy z listy argumentów i wstawia je do tego `forward_list`. Dwie listy powinny być sortowane według tego samego obiektu funkcji porównywania przed wywołaniem do `merge`. Połączonej listy zostaną posortowane według, obiekt funkcji porównywania.

```cpp
void merge(forward_list& right);
template <class Predicate>
void merge(forward_list& right, Predicate comp);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Na liście do przodu, aby Scal z.|
|*Comp*|Obiekt funkcji porównywania jest używana do sortowania elementów.|

### <a name="remarks"></a>Uwagi

`forward_list::merge` Usuwa elementy z `forward_list` `right`i wstawia je do tego `forward_list`. Zarówno sekwencji muszą być uporządkowane według tych samych predykat opisane poniżej. Połączone sekwencji również są uporządkowane według tego obiektu funkcji porównywania.

Dla iteratorów `Pi` i `Pj` wyznaczanie elementów w pozycjach `i` i `j`, pierwsza funkcja elementu członkowskiego nakłada zamówienie `!(*Pj < *Pi)` zawsze wtedy, gdy `i < j`. (Elementy są sortowane w `ascending` zamówienia.) Funkcja drugiego członka nakłada zamówienie `! comp(*Pj, *Pi)` zawsze wtedy, gdy `i < j`.

Nie pary elementów w oryginalnej sekwencji kontrolowanej są wycofywane w wynikowej kontrolowanej sekwencji. Jeśli pary elementów w wynikowym kontrolowane sekwencji porównuje równe ( `!(*Pi < *Pj) && !(*Pj < *Pi)`), element z oryginalnej sekwencji kontrolowanej jest umieszczany przed elementem z sekwencji kontrolowanej przez `right`.

Wyjątek występuje tylko wtedy, gdy `comp` zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w nieokreślonej kolejności, a wyjątek jest zgłaszany ponownie.

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
|*right*|Lista do przodu, są kopiowane do listy do przodu.|
|*IList*|Listy inicjalizatora w nawiasach nawiasów klamrowych zachowuje się jak sekwencji elementów typu `Type`.|

### <a name="remarks"></a>Uwagi

Pierwszy operator członkowski zastępuje kontrolowanej sekwencji kopię sekwencji kontrolowanej przez *prawo*.

Drugi operator składowej zastępuje kontrolowanej sekwencji z obiektu klasy `initializer_list<Type>`.

Trzeci operator składowy jest taki sam jak pierwszy, ale z [rvalue](../cpp/rvalue-reference-declarator-amp-amp.md) odwołania.

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

Funkcja elementu członkowskiego nigdy nie zgłasza wyjątku.

## <a name="push_front"></a>  forward_list::push_front

Dodaje element do początku listy do przodu.

```cpp
void push_front(const Type& val);
void push_front(Type&& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Val*|Element dodany na początku listy do przodu.|

### <a name="remarks"></a>Uwagi

Jeśli wyjątek jest zgłaszany, kontener pozostanie niezmieniony, a wyjątek jest zgłaszany ponownie.

## <a name="reference"></a>  forward_list::Reference

Typ, który zawiera odwołanie do elementu na liście do przodu.

```cpp
typedef typename Allocator::reference reference;
```

### <a name="remarks"></a>Uwagi

## <a name="remove"></a>  forward_list::Remove

Usuwa elementy na liście do przodu, który odpowiada określonej wartości.

```cpp
void remove(const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Val*|Wartość, która posiadaniu elementu, spowoduje usunięcie tego elementu z listy.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa w kontrolowanej sekwencji wszystkie elementy, wyznaczony przez iterator `P`, dla którego `*P ==  val`.

Funkcja elementu członkowskiego nigdy nie zgłasza wyjątku.

## <a name="remove_if"></a>  forward_list::remove_if

Usuwa elementy z listy do przodu, dla których jest spełniony określony predykat.

```cpp
template <class Predicate>
void remove_if(Predicate pred);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*P.*|Predykat jednoelementowy, który, jeżeli zostanie spełniony przez element, powoduje usunięcie tego elementu z listy.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska usuwa w kontrolowanej sekwencji wszystkie elementy, wyznaczony przez iterator `P`, dla którego ` pred(*P)` ma wartość true.

Wyjątek występuje tylko wtedy, gdy *pred* zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w stanie nieokreślony, a wyjątek jest zgłaszany ponownie.

## <a name="resize"></a>  forward_list::Resize

Określa nowy rozmiar dla listy do przodu.

```cpp
void resize(size_type _Newsize);
void resize(size_type _Newsize, const Type& val);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Newsize*|Liczba elementów na liście do przodu o zmienionym rozmiarze.|
|*Val*|Wartość do użytku dopełnienia.|

### <a name="remarks"></a>Uwagi

Funkcje elementów członkowskich zarówno upewnij się, że liczba elementów na liście odtąd *_Newsize*. Jeśli musi stworzyć kontrolowanej sekwencji dłużej, pierwsza funkcja elementu członkowskiego dołącza elementy z wartością `Type()`, natomiast funkcja drugiego członka dołącza elementy z wartością *val*. Aby kontrolowanej sekwencji krótszy, efektywnie wywołać oba funkcje Członkowskie `erase_after(begin() + _Newsize - 1, end())`.

## <a name="reverse"></a>  forward_list::reverse

Odwraca kolejność, w której elementy występują na liście do przodu.

```cpp
void reverse();
```

### <a name="remarks"></a>Uwagi

## <a name="size_type"></a>  forward_list::size_type

Typ, który reprezentuje odległości bez znaku między dwoma elementami.

```cpp
typedef typename Allocator::size_type size_type;
```

### <a name="remarks"></a>Uwagi

Typ całkowitoliczbowy bez znaku, opisująca obiekt, który może reprezentować długość wszelkie kontrolowanej sekwencji.

## <a name="sort"></a>  forward_list::sort

Rozmieszcza elementy w kolejności rosnącej lub z kolejnością określone przez predykat.

```cpp
void sort();
template <class Predicate>
void sort(Predicate pred);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*P.*|Predykat szeregowania.|

### <a name="remarks"></a>Uwagi

Obie funkcje Członkowskie kolejność elementów w kontrolowanej sekwencji predykat, opisane poniżej.

Dla iteratorów `Pi` i `Pj` wyznaczanie elementów w pozycjach `i` i `j`, pierwsza funkcja elementu członkowskiego nakłada zamówienie `!(*Pj < *Pi)` zawsze wtedy, gdy `i < j`. (Elementy są sortowane w `ascending` zamówienia.) Funkcję szablonu członka nakłada zamówienie `! pred(*Pj, *Pi)` zawsze wtedy, gdy `i < j`. Nie uporządkowane pary elementów w oryginalnej sekwencji kontrolowanej są wycofywane w wynikowej kontrolowanej sekwencji. (Sortowania jest stabilna).

Wyjątek występuje tylko wtedy, gdy *pred* zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w nieokreślonej kolejności, a wyjątek jest zgłaszany ponownie.

## <a name="splice_after"></a>  forward_list::splice_after

Usuwa elementy z forward_list źródłowy i wstawia je do forward_list docelowego.

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

*Where*<br/>
Pozycja w forward_list miejsce docelowe, po upływie którego do wstawienia.

*Źródło*<br/>
Forward_list — źródłowy, który ma zostać wstawiony do forward_list docelowego.

*ITER*<br/>
Element, który ma zostać wstawiony z forward_list źródła.

*pierwszy*<br/>
Pierwszy element w zakresie, który ma zostać wstawiony z forward_list źródła.

*ostatni*<br/>
Pierwszej pozycji poza zakres, który ma zostać wstawiony z forward_list źródła.

### <a name="remarks"></a>Uwagi

Pierwszy pary elementów członkowskich wstawia sekwencji kontrolowanej przez *źródła* zaraz po elementu w kontrolowanej sekwencji wskazywany przez *gdzie*. Powoduje ono także usunięcie wszystkich elementów z *źródła*. (`&Source` nie musi być równa **to**.)

Druga para elementów członkowskich usuwa element tuż za *Iter* w sekwencji kontrolowanej przez *źródła* i wstawia go po elementu w kontrolowanej sekwencji wskazywany przez *Gdzie*. (Jeśli `Where == Iter || Where == ++Iter`, nie zmienią.)

Trzecia para elementów członkowskich (w granicach splice) wstawia Podzakres wyznaczonym przez `(First, Last)` z sekwencji kontrolowanej przez *źródła* zaraz po elementu w kontrolowanej sekwencji wskazywany przez *gdzie*. Również usunięcie oryginalnego Podzakres z sekwencji kontrolowanej przez *źródła*. (Jeśli `&Source == this`, zakres `(First, Last)` nie może zawierać element wskazane przez *gdzie*.)

Jeśli ranged splice wstawia `N` elementów, a `&Source != this`, obiekt klasy [iteratora](#iterator) jest zwiększany `N` razy.

Nie Iteratory, wskaźników lub odwołań, które wyznaczają elementy spliced stają się nieprawidłowe.

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

Zamienia elementy z dwóch list do przodu.

```cpp
void swap(forward_list& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Do przodu lista zawierająca elementy, które wymieniane.|

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zamienia kontrolowanej sekwencji między `*this` i *prawo*. Jeśli `get_allocator() ==  right.get_allocator()`, robi to w stałym czasie, wyniku weryfikacji zgłasza wyjątek bez wyjątków i jego unieważnienie nie odwołania wskaźniki i Iteratory, które wyznaczają elementy dwóch sekwencji kontrolowanej. W przeciwnym razie wykonuje szereg element zadania i Konstruktor wywołuje proporcjonalna do liczby elementów w dwóch kontrolowanej sekwencji.

## <a name="unique"></a>  forward_list::UNIQUE

Eliminuje wszystkie oprócz pierwszego elementu z każdej grupy kolejnych elementów równe.

```cpp
void unique();
template <class BinaryPredicate>
void unique(BinaryPredicate comp);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Comp*|Jeśli predykat binarny jest użyty do porównania kolejne elementy.|

### <a name="remarks"></a>Uwagi

Przechowuje pierwszego dnia każdego elementu unikatowe i usuwa pozostałe. Elementy muszą być sortowane, tak, aby elementy równy wartości znajdują się obok siebie na liście.

Pierwsza funkcja członkostwa usuwa z kontrolowanej sekwencji każdy element, który porównuje równa jego poprzedzający element. Dla iteratorów `Pi` i `Pj` wyznaczanie elementów w pozycjach `i` i `j`, funkcja drugiego członka usuwa każdego elementu, dla którego `i + 1 == j &&  comp(*Pi, *Pj)`.

Dla kontrolowanej sekwencji długości `N` (> 0), predykat ` comp(*Pi, *Pj)` jest oceniany `N - 1` razy.

Wyjątek występuje tylko wtedy, gdy `comp` zgłasza wyjątek. W takim przypadku kontrolowanej sekwencji pozostanie w stanie nieokreślony, a wyjątek jest zgłaszany ponownie.

## <a name="value_type"></a>  forward_list::value_type

Typ, który reprezentuje typ elementu przechowywanego na liście do przodu.

```cpp
typedef typename Allocator::value_type value_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla _ parametru szablonu `Ty`.

## <a name="see-also"></a>Zobacz także

[<forward_list>](../standard-library/forward-list.md)<br/>
