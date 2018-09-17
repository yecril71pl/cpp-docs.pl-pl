---
title: '&lt;Pamięć&gt; funkcje | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- memory/std::addressof
- memory/std::align
- memory/std::allocate_shared
- memory/std::const_pointer_cast
- memory/std::declare_no_pointers
- memory/std::declare_reachable
- memory/std::default_delete
- memory/std::dynamic_pointer_cast
- memory/std::get_deleter
- memory/std::get_pointer_safety
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- xmemory/std::return_temporary_buffer
- memory/std::static_pointer_cast
- memory/std::swap
- memory/std::undeclare_no_pointers
- memory/std::undeclare_reachable
- memory/std::uninitialized_copy
- memory/std::uninitialized_copy_n
- memory/std::uninitialized_fill
- memory/std::uninitialized_fill_n
- memory/std::get_temporary_buffer
- memory/std::return_temporary_buffer
dev_langs:
- C++
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::swap [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
- std::addressof [C++]
- std::align [C++]
- std::allocate_shared [C++]
- std::const_pointer_cast [C++]
- std::declare_no_pointers [C++]
- std::declare_reachable [C++]
- std::default_delete [C++]
- std::dynamic_pointer_cast [C++]
- std::get_deleter [C++]
- std::get_pointer_safety [C++]
- std::get_temporary_buffer [C++]
- std::make_shared [C++]
- std::make_unique [C++]
- std::owner_less [C++]
- std::return_temporary_buffer [C++]
- std::static_pointer_cast [C++]
- std::undeclare_no_pointers [C++]
- std::undeclare_reachable [C++]
- std::uninitialized_copy [C++]
- std::uninitialized_copy_n [C++]
- std::uninitialized_fill [C++]
- std::uninitialized_fill_n [C++]
ms.workload:
- cplusplus
ms.openlocfilehash: b740613666c7e4e1b5cc2c1b14c5cbf04b0fe6ef
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702874"
---
# <a name="ltmemorygt-functions"></a>&lt;Pamięć&gt; funkcji

||||
|-|-|-|
|[AddressOf](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared](#make_shared)|
|[make_unique](#make_unique)|[owner_less —](#owner_less)|[return_temporary_buffer](#return_temporary_buffer)|
|[static_pointer_cast](#static_pointer_cast)|[swap (standardowa biblioteka C++)](#swap)|[undeclare_no_pointers](#undeclare_no_pointers)|
|[undeclare_reachable](#undeclare_reachable)|[uninitialized_copy](#uninitialized_copy)|[uninitialized_copy_n](#uninitialized_copy_n)|
|[uninitialized_fill](#uninitialized_fill)|[uninitialized_fill_n](#uninitialized_fill_n)|

## <a name="addressof"></a>  AddressOf

Pobiera prawdziwy adres obiektu.

```cpp
template <class T>
T* addressof(T& Val);
```

### <a name="parameters"></a>Parametry

*Val*<br/>
Obiekt lub funkcja, dla których ma być uzyskany prawdziwy adres.

### <a name="return-value"></a>Wartość zwracana

Rzeczywisty adres obiektu lub funkcji, które odwołuje się *Val*, nawet jeśli przeciążone `operator&()` istnieje.

### <a name="remarks"></a>Uwagi

## <a name="align"></a>  Dopasuj

Pasuje do pamięci o danym rozmiarze — wyrównany przez daną specyfikację wyrównania — do pierwszego możliwego adresu danej pamięci.

```cpp
void* align(
    size_t Alignment, // input
    size_t Size,      // input
    void*& Ptr,        // input/output
    size_t& Space     // input/output
);
```

### <a name="parameters"></a>Parametry

*Wyrównanie*<br/>
Wyrównanie powiązane z próbą.

*Rozmiar*<br/>
Rozmiar w bajtach dla wyrównanej pamięci.

*PTR*<br/>
Adres początkowy dostępnej puli ciągłej pamięci, która ma być użyta. Ten parametr to również parametr wyjściowy, a jest równa zawiera nowy adres początkowy, jeśli wyrównanie zakończy się pomyślnie. Jeśli `align()` się nie powiedzie, ten parametr nie jest modyfikowany.

*miejsce*<br/>
Całkowita ilość miejsca dostępna do `align()` w celu utworzenia wyrównanej pamięci. Ten parametr to również parametr wyjściowy, zawiera skorygowane miejsce pozostawione w buforze pamięci po odjęciu wyrównanej pamięci i wszystkich powiązanych obciążeń.

Jeśli `align()` się nie powiedzie, ten parametr nie jest modyfikowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik zerowy, jeśli żądany wyrównany bufor nie pasuje do dostępnego miejsca; w przeciwnym razie nowa wartość *Ptr*.

### <a name="remarks"></a>Uwagi

Zmodyfikowanego *Ptr* i *miejsca* parametry umożliwiają wywołanie `align()` wielokrotnie na tym samym buforze, ewentualnie z różnymi wartościami dla *wyrównanie* i  *Rozmiar*. Poniższy fragment kodu demonstruje jedno użycie `align()`.

```cpp
#include <type_traits> // std::alignment_of()
#include <memory>
//...
char buffer[256]; // for simplicity
size_t alignment = std::alignment_of<int>::value;
void * ptr = buffer;
std::size_t space = sizeof(buffer); // Be sure this results in the true size of your buffer

while (std::align(alignment, sizeof(MyObj), ptr, space)) {
    // You now have storage the size of MyObj, starting at ptr, aligned on
    // int boundary. Use it here if you like, or save off the starting address
    // contained in ptr for later use.
    // ...
    // Last, move starting pointer and decrease available space before
    // the while loop restarts.
    ptr = reinterpret_cast<char*>(ptr) + sizeof(MyObj);
    space -= sizeof(MyObj);
}
// At this point, align() has returned a null pointer, signaling it is not
// possible to allow more aligned storage in this buffer.
```

## <a name="allocate_shared"></a>  allocate_shared

Tworzy `shared_ptr` do obiektów, które są przydzielane i zbudowane dla danego typu przy użyciu określonego alokatora. Zwraca `shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parametry

*Alokacji*<br/>
Alokator używany do tworzenia obiektów.

*Args*<br/>
Zero lub więcej argumentów, które stają się obiektami.

### <a name="remarks"></a>Uwagi

Funkcja tworzy obiekt `shared_ptr<Type>`, wskaźnik do `Type(Args...)` jako przydzielony i skonstruowany przez *alokacji*.

## <a name="const_pointer_cast"></a>  const_pointer_cast —

Stała ustawiona na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ kontrolowany przez dzielony wskaźnik zwracany.

*Inne*<br/>
Typ kontrolowany przez dzielony wskaźnik argumentu.

*Inne*<br/>
Argument wskaźnika udostępnionego.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca obiekt shared_ptr puste, jeśli `const_cast<Ty*>(sp.get())` zwraca wskaźnik o wartości null; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu, który jest własnością `sp`. Wyrażenie `const_cast<Ty*>(sp.get())` musi być prawidłowy.

### <a name="example"></a>Przykład

```cpp
// std__memory__const_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

int main()
{
    std::shared_ptr<int> sp0(new int);
    std::shared_ptr<const int> sp1 =
        std::const_pointer_cast<const int>(sp0);

*sp0 = 3;
    std::cout << "sp1 == " << *sp1 << std::endl;

    return (0);
}
```

```Output
sp1 == 3
```

## <a name="declare_no_pointers"></a>  declare_no_pointers

Informuje moduł odśmiecający pamięci, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku nie zawiera żadnych wskaźników mogących podlegać śledzeniu.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Adres pierwszy znak, który nie zawiera już wskaźników mogących podlegać śledzeniu.|
|*_Rozmiar*|Rozmiar bloku, który rozpoczyna się od *ptr* który nie zawiera żadnych wskaźników mogących podlegać śledzeniu.|

### <a name="remarks"></a>Uwagi

Funkcja informuje dowolny moduł odśmiecania pamięci, zakres adresów `[ ptr, ptr + _Size)` już nie zawierają wskaźników mogących podlegać śledzeniu. (Wszystkie wskaźniki do przydzielenia pamięci, która musi nie zostać wyłuskany, chyba że wykonane dostępny.)

## <a name="declare_reachable"></a>  declare_reachable

Informuje moduł odśmiecania pamięci, że wskazany adres prowadzi do przydzielonej pamięci i jest osiągalny.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik do obszaru pamięci dostępny, przydzielony prawidłowy.

### <a name="remarks"></a>Uwagi

Jeśli *ptr* nie ma wartości null, funkcja informuje dowolny moduł odśmiecania pamięci, *ptr* poniżej jest osiągalny (wskazuje prawidłowy Magazyn przydzielony).

## <a name="default_delete"></a>  default_delete —

Usuwa obiekty przydzielone za pomocą **nowy operator**. Odpowiedni do użytku z `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

*PTR*<br/>
Wskaźnik do obiektu do usunięcia.

*Inne*<br/>
Typ elementów w tablicy do usunięcia.

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje `deleter` który usuwa skalarne obiekty przydzielone z **nowy operator**, odpowiedni do użytku z szablonu klasy `unique_ptr`. Ma on także jawna specjalizacja `default_delete<Type[]>`.

## <a name="dynamic_pointer_cast"></a>  dynamic_pointer_cast

Rzutowania dynamicznego do shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ kontrolowany przez dzielony wskaźnik zwracany.

*Inne*<br/>
Typ kontrolowany przez dzielony wskaźnik argumentu.

*SP*<br/>
Argument wskaźnika udostępnionego.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca obiekt shared_ptr puste, jeśli `dynamic_cast<Ty*>(sp.get())` zwraca wskaźnik o wartości null; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu, który jest własnością *sp* . Wyrażenie `dynamic_cast<Ty*>(sp.get())` musi być prawidłowy.

### <a name="example"></a>Przykład

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int val;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::dynamic_pointer_cast<derived>(sp0);

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="get_deleter"></a>  get_deleter —

Pobieranie programu usuwającego z shared_ptr.

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

*D*<br/>
Typ deletera.

*Ty*<br/>
Typ kontrolowany przez dzielony wskaźnik.

*SP*<br/>
Wspólny wskaźnik.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wskaźnik do deleter typu *D* należący do [shared_ptr — klasa](../standard-library/shared-ptr-class.md) obiektu *sp*. Jeśli *sp* ma nie deleter lub jego deleter nie jest typu *D* funkcja zwraca 0.

### <a name="example"></a>Przykład

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct deleter
{
    void operator()(base *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->val = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->val = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}

```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>  get_pointer_safety

Zwraca typ bezpieczeństwa wskaźnika założony przez dowolny moduł odśmiecania pamięci.

```cpp
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>Uwagi

Funkcja zwraca typ bezpieczeństwa wskaźnika założony przez dowolny automatyczne moduł odśmiecania pamięci.

## <a name="get_temporary_buffer"></a>  get_temporary_buffer

Przydziela tymczasową pamięć dla sekwencji elementów, która nie przekracza określonej liczby elementów.

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Maksymalną liczbę elementów zażądał, dla którego ma przydzielenia pamięci.

### <a name="return-value"></a>Wartość zwracana

A `pair` którego pierwszy składnik to wskaźnik do pamięci, która została przydzielona i którego składnik sekundy daje rozmiar buforu, wskazującą największą liczbę elementów, które może ona przechowywać.

### <a name="remarks"></a>Uwagi

Funkcja sprawia, że żądanie dotyczące pamięci, a jego może zakończyć się niepowodzeniem. Jeśli bufor nie została przydzielona, funkcja zwraca parę za pomocą drugiego składnika równego zero i pierwszego składnika równego do wskaźnika o wartości null.

Ta funkcja powinna używana tylko w pamięci, która jest tymczasowe.

### <a name="example"></a>Przykład

```cpp
// memory_get_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
   // Create an array of ints
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
   int count = sizeof ( intArray ) / sizeof ( int );
   cout << "The number of integers in the array is: "
      << count << "." << endl;

   pair<int *, ptrdiff_t> resultPair;
   resultPair = get_temporary_buffer<int>( count );

   cout << "The number of elements that the allocated memory\n"
        << "could store is given by: resultPair.second = "
        << resultPair.second << "." << endl;
}
```

```Output
The number of integers in the array is: 9.
The number of elements that the allocated memory
could store is given by: resultPair.second = 9.
```

## <a name="make_shared"></a>  make_shared

Tworzy i zwraca `shared_ptr` wskazującej przydzielone obiekty, które są skonstruowane z zera lub więcej argumentów za pomocą domyślnego alokatora. Przydziela i tworzy zarówno obiekt określonego typu i `shared_ptr` do zarządzania wspólnej własności obiektu i zwraca `shared_ptr`.

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*_Args*|Zero lub więcej argumentów konstruktora. Funkcja wnioskuje przeciążenia konstruktora, który można wywołać na podstawie argumentów, które są dostarczane.|

### <a name="remarks"></a>Uwagi

Użyj `make_shared` jako prosty i bardziej efektywny sposób do utworzenia obiektu i `shared_ptr` Zarządzanie dostępu współdzielonego do obiektu w tym samym czasie. Semantycznie te dwie instrukcje są równoważne:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Jednak pierwszej instrukcji sprawia, że dwa alokacji i, jeśli alokacja `shared_ptr` zakończy się niepowodzeniem po alokacja `Example` obiektu zakończyła się pomyślnie, następnie nienazwane `Example` przeciek obiektu. Instrukcja, która używa `make_shared` jest prostsze, ponieważ jest zaangażowane wywołanie funkcji tylko jeden. Jest bardziej wydajne, ponieważ biblioteka może być pojedynczą alokację inteligentny wskaźnik i obiektu. To jest szybsze i prowadzi do mniej fragmentacji pamięci, i nie ma możliwości wyjątek w jednym alokacji, ale nie drugiej. Znacznie poprawia wydajność lepsze miejscowość dla kodu, który odwołuje się do obiektu i aktualizacje, które liczby odwołań w inteligentnego wskaźnika.

Należy rozważyć użycie [make_unique](../standard-library/memory-functions.md#make_unique) Jeśli nie potrzebujesz dostępu do obiektu. Użyj [allocate_shared](../standard-library/memory-functions.md#allocate_shared) Jeśli trzeba określić niestandardowy alokator dla obiektu. Nie można użyć `make_shared` Jeśli obiekt wymaga niestandardowym narzędziem usuwania, ponieważ nie istnieje żaden sposób przekazać deleter jako argument.

Poniższy przykład pokazuje, jak utworzyć udostępnione wskaźniki do typu za pomocą przeciążenia konstruktora określone.

### <a name="example"></a>Przykład

```cpp
// stl_make_shared.cpp
// Compile by using: cl /W4 /EHsc stl_make_shared.cpp
#include <iostream>
#include <string>
#include <memory>
#include <vector>

class Song {
public:
   std::wstring title_;
   std::wstring artist_;

   Song(std::wstring title, std::wstring artist) : title_(title), artist_(artist) {}
   Song(std::wstring title) : title_(title), artist_(L"Unknown") {}
};

void CreateSharedPointers() {
   // Okay, but less efficient to have separate allocations for
   // Song object and shared_ptr control block.
   auto song = new Song(L"Ode to Joy", L"Beethoven");
   std::shared_ptr<Song> sp0(song);

   // Use make_shared function when possible. Memory for control block
   // and Song object are allocated in the same call:
   auto sp1 = std::make_shared<Song>(L"Yesterday", L"The Beatles");
   auto sp2 = std::make_shared<Song>(L"Blackbird", L"The Beatles");

   // make_shared infers which constructor to use based on the arguments.
   auto sp3 = std::make_shared<Song>(L"Greensleeves");

   // The playlist vector makes copies of the shared_ptr pointers.
   std::vector<std::shared_ptr<Song>> playlist;
   playlist.push_back(sp0);
   playlist.push_back(sp1);
   playlist.push_back(sp2);
   playlist.push_back(sp3);
   playlist.push_back(sp1);
   playlist.push_back(sp2);
   for (auto&& sp : playlist) {
      std::wcout << L"Playing " << sp->title_ <<
         L" by " << sp->artist_ << L", use count: " <<
         sp.use_count() << std::endl;
   }
}

int main() {
   CreateSharedPointers();
}
```

Przykład generuje następujące dane wyjściowe:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>  make_unique

Tworzy i zwraca [unique_ptr](../standard-library/unique-ptr-class.md) do obiektu określonego typu, który jest konstruowany przy użyciu określonych argumentów.

```cpp
// make_unique<T>
template <class T, class... Types>
unique_ptr<T>
make_unique(Types&&... Args)
{
    return (unique_ptr<T>(new T(forward<Types>(Args)...)));
}

// make_unique<T[]>
template <class T>
make_unique(size_t Size)
{
    return (unique_ptr<T>(new Elem[Size]()));
}

// make_unique<T[N]> disallowed
template <class T, class... Types>
typename enable_if<extent<T>::value != 0, void>::type
make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który `unique_ptr` wskaże.

*Typy*<br/>
Typy argumentów konstruktora określone przez *Args*.

*Args*<br/>
Argumenty do przekazania do konstruktora obiektu typu *T*.

*Elem*<br/>
Tablica elementów typu *T*.

*Rozmiar*<br/>
Liczba elementów do przydzielenia miejsca dla w nowej tablicy.

### <a name="remarks"></a>Uwagi

Pierwsze przeciążenie jest wykorzystywane dla pojedynczych obiektów, drugie przeciążenie jest wywoływane dla tablic, a trzecie przeciążenie uniemożliwia uniemożliwia określenie rozmiaru tablicy w argument typu (make_unique\<T [N] >); ta konstrukcja nie jest obsługiwana. przez bieżące normy. Kiedy używasz `make_unique` utworzyć `unique_ptr` do tablicy, musisz oddzielnie zainicjować elementy tablicy. Jeżeli rozważasz to przeciążenie, być może lepszym rozwiązaniem jest użycie [std::vector](../standard-library/vector-class.md).

Ponieważ `make_unique` jest dokładnie zaimplementowano pod kątem bezpieczeństwa wyjątków, firma Microsoft zaleca użycie `make_unique` zamiast bezpośredniego wywoływania `unique_ptr` konstruktorów.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `make_unique`. Aby uzyskać więcej przykładów, zobacz [porady: Tworzenie wystąpień unique_ptr i korzystanie](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Po wyświetleniu błędu C2280 w połączeniu z `unique_ptr`, jest prawie na pewno ponieważ próbujesz wywołać konstruktora kopiującego, który jest funkcją usuniętych.

## <a name="owner_less"></a>  owner_less —

Pozwala na mieszane porównania oparte na własności współdzielonych i słabych wskaźników. Zwraca **true** Jeśli lewy parametr był zamówiony przed odpowiednich parametrów przez funkcję elementu członkowskiego `owner_before`.

```cpp
template <class Type>
struct owner_less; // not defined

template <class Type>
struct owner_less<shared_ptr<Type>> {
    bool operator()(
    const shared_ptr<Type>& left,
    const shared_ptr<Type>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Type>& right);
};

template <class Type>
struct owner_less<weak_ptr<Type>>
    bool operator()(
    const weak_ptr<Type>& left,
    const weak_ptr<Type>& right);

    bool operator()(
    const weak_ptr<Type>& left,
    const shared_ptr<Ty>& right);

    bool operator()(
    const shared_ptr<Type>& left,
    const weak_ptr<Type>& right);
};
```

### <a name="parameters"></a>Parametry

*z _lewej*<br/>
Udostępnione lub słaby wskaźnik.

*right*<br/>
Udostępnione lub słaby wskaźnik.

### <a name="remarks"></a>Uwagi

Klasy szablonów definiowanie ich operatorach składowych powrotu `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a>  return_temporary_buffer

Zwalnia pamięć tymczasową, która została przydzielona za pomocą `get_temporary_buffer` funkcji szablonu.

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parametry

*_Pbuf*<br/>
Wskaźnik do pamięci do przydzielenia.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna używana tylko w pamięci, która jest tymczasowe.

### <a name="example"></a>Przykład

```cpp
// memory_ret_temp_buf.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

int main( )
{
   // Create an array of ints
   int intArray [ ] = { 10, 20, 30, 40, 100, 200, 300 };
   int count = sizeof ( intArray ) / sizeof ( int );
   cout << "The number of integers in the array is: "
         << count << "." << endl;

   pair<int *, ptrdiff_t> resultPair;
   resultPair = get_temporary_buffer<int>( count );

   cout << "The number of elements that the allocated memory\n"
         << " could store is given by: resultPair.second = "
         << resultPair.second << "." << endl;

   int* tempBuffer = resultPair.first;

   // Deallocates memory allocated with get_temporary_buffer
   return_temporary_buffer ( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>  static_pointer_cast —

Rzutowanie statyczne na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ kontrolowany przez dzielony wskaźnik zwracany.

*Inne*<br/>
Typ kontrolowany przez dzielony wskaźnik argumentu.

*Inne*<br/>
Argument wskaźnika udostępnionego.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca obiekt shared_ptr puste, jeśli `sp` jest pustym `shared_ptr` obiektu; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu, który jest własnością `sp`. Wyrażenie `static_cast<Ty*>(sp.get())` musi być prawidłowy.

### <a name="example"></a>Przykład

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int val;
};

struct derived
    : public base
{
};

int main()
{
    std::shared_ptr<base> sp0(new derived);
    std::shared_ptr<derived> sp1 =
        std::static_pointer_cast<derived>(sp0);

    sp0->val = 3;
    std::cout << "sp1->val == " << sp1->val << std::endl;

    return (0);
}
```

```Output
sp1->val == 3
```

## <a name="swap"></a>  swap (standardowa biblioteka C++)

Zamień dwa obiekty shared_ptr lub weak_ptr.

```cpp
template <class Ty, class Other>
void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ kontrolowany przez wskaźnik udostępnione weak po lewej stronie.

*Inne*<br/>
Typ kontrolowany przez wskaźnik udostępnione bezpośrednio/weak.

*left*<br/>
Po lewej stronie wskaźnika udostępnionego słabych.

*right*<br/>
Wskaźnik udostępnione bezpośrednio/weak.

### <a name="remarks"></a>Uwagi

Szablon funkcji wywołanie `left.swap(right)`.

### <a name="example"></a>Przykład

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct deleter
{
    void operator()(int *p)
    {
        delete p;
    }
};

int main()
{
    std::shared_ptr<int> sp1(new int(5));
    std::shared_ptr<int> sp2(new int(10));
    std::cout << "*sp1 == " << *sp1 << std::endl;

    sp1.swap(sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;

    swap(sp1, sp2);
    std::cout << "*sp1 == " << *sp1 << std::endl;
    std::cout << std::endl;

    std::weak_ptr<int> wp1(sp1);
    std::weak_ptr<int> wp2(sp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    wp1.swap(wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    swap(wp1, wp2);
    std::cout << "*wp1 == " << *wp1.lock() << std::endl;

    return (0);
}
```

```Output
*sp1 == 5
*sp1 == 10
*sp1 == 5

*wp1 == 5
*wp1 == 10
*wp1 == 5
```

## <a name="undeclare_no_pointers"></a>  undeclare_no_pointers

Informuje moduł odśmiecający pamięci, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku mogą teraz zawierać wskaźniki mogące podlegać śledzeniu.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="remarks"></a>Uwagi

Funkcja informuje dowolny moduł odśmiecania pamięci, zakres adresów `[ptr, ptr + _Size)` mogą teraz zawierać wskaźniki mogące podlegać śledzeniu.

## <a name="undeclare_reachable"></a>  undeclare_reachable

Odwołuje deklarację osiągalności określona lokalizacja w pamięci.

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do adresu pamięci, aby być nie deklarowane dostępny.|

### <a name="remarks"></a>Uwagi

Jeśli *ptr* nie **nullptr**, funkcja informuje dowolny moduł odśmiecania pamięci, *ptr* nie jest już dostępny. Zwraca wskaźnik bezpiecznie klasy pochodnej, która porównuje w równa *ptr*.

## <a name="uninitialized_copy"></a>  uninitialized_copy

Kopiuje obiekty z określonego zakresu źródłowego do niezainicjowanego zakresu docelowego.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, odnoszący się do pierwszego elementu w zakresie źródłowym.

*ostatni*<br/>
Iterator danych wejściowych, odnoszący się do ostatniego elementu w zakresie źródłowym.

*dest*<br/>
Iterator do przodu, który dotyczy pierwszego elementu w zakresie docelowym.

### <a name="return-value"></a>Wartość zwracana

Iterator postępujący odnosi się do pierwszej pozycji poza zakres docelowy, chyba że zakres źródłowy był pusty.

### <a name="remarks"></a>Uwagi

Ten algorytm umożliwia oddzielenie alokacji pamięci od konstrukcji obiektu.

Funkcja szablonu skutecznie wykonuje:

```cpp
while (first != last) {
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

### <a name="example"></a>Przykład

```cpp
// memory_uninit_copy.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    Integer(int x) : val(x) {}
    int get() { return val; }
private:
    int val;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    int i;
    cout << "The initialized Array contains " << N << " elements: ";
    for (i = 0; i < N; i++)
    {
        cout << " " << Array[i];
    }
    cout << endl;

    Integer* ArrayPtr = (Integer*)malloc(N * sizeof(int));
    Integer* LArrayPtr = uninitialized_copy(
        Array, Array + N, ArrayPtr);  // C4996

    cout << "Address of position after the last element in the array is: "
        << &Array[0] + N << endl;
    cout << "The iterator returned by uninitialized_copy addresses: "
        << (void*)LArrayPtr << endl;
    cout << "The address just beyond the last copied element is: "
        << (void*)(ArrayPtr + N) << endl;

    if ((&Array[0] + N) == (void*)LArrayPtr)
        cout << "The return value is an iterator "
        << "pointing just beyond the original array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the original array." << endl;

    if ((void*)LArrayPtr == (void*)(ArrayPtr + N))
        cout << "The return value is an iterator "
        << "pointing just beyond the copied array." << endl;
    else
        cout << "The return value is an iterator "
        << "not pointing just beyond the copied array." << endl;

    free(ArrayPtr);

    cout << "Note that the exact addresses returned will vary\n"
        << "with the memory allocation in individual computers."
        << endl;
}
```

## <a name="uninitialized_copy_n"></a>  uninitialized_copy_n

Tworzy kopię określonej liczby elementów z iteratora danych wejściowych. Kopie są wprowadzane do iteratora do przodu.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator danych wejściowych, który odwołuje się do obiektu do skopiowania.

*Liczba*<br/>
Typ całkowitoliczbowy ze znakiem lub bez znaku, określający, ile razy obiekt ma być skopiowany.

*dest*<br/>
Iterator do przodu odwołujący się do lokalizacji nowych kopii.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który odnosi się do pierwszej pozycji poza miejscem docelowym. Jeśli zakres źródłowy był pusty, iterator odnosi się do *pierwszy*.

### <a name="remarks"></a>Uwagi

Funkcja szablonu skutecznie wykonuje następujące:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

## <a name="uninitialized_fill"></a>  uninitialized_fill

Kopiuje obiekty z określoną wartością do niezainicjowanego zakresu docelowego.

```cpp
template <class ForwardIterator, class Type>
void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator postępujący odnosi się do pierwszego elementu w zakresie docelowym, który ma zostać zainicjowane.

*ostatni*<br/>
Iterator do przodu, odnoszący się do ostatniego elementu w zakresie docelowym, który ma zostać zainicjowane.

*Val*<br/>
Wartość wykorzystana do zainicjowania zakresu docelowego.

### <a name="remarks"></a>Uwagi

Ten algorytm umożliwia oddzielenie alokacji pamięci od konstrukcji obiektu.

Funkcja szablonu skutecznie wykonuje:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (val);
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

### <a name="example"></a>Przykład

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer {         // No default constructor
   public:
      Integer( int x ) : val( x ) {}
      int get( ) { return val; }
   private:
      int val;
};

int main( )
{
   const int N = 10;
   Integer val ( 25 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill( Array, Array + N, val );
   int i;
   cout << "The initialized Array contains: ";
      for ( i = 0 ; i < N; i++ )
      {
         cout << Array [ i ].get( ) << " ";
      }
   cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>  uninitialized_fill_n

Kopiuje obiekty z określoną wartością do określonej liczby elementów w niezainicjowanym zakresie docelowym.

```cpp
template <class FwdIt, class Size, class Type>
void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>Parametry

*pierwszy*<br/>
Iterator do przodu, odnoszący się do pierwszego elementu w zakresie docelowym, który ma być zainicjowany.

*Liczba*<br/>
Liczba elementów, które mają być zainicjowane.

*Val*<br/>
Wartość wykorzystana do zainicjowania zakresu docelowego.

### <a name="remarks"></a>Uwagi

Ten algorytm umożliwia oddzielenie alokacji pamięci od konstrukcji obiektu.

Funkcja szablonu skutecznie wykonuje:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(val);
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

### <a name="example"></a>Przykład

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer {   // No default constructor
public:
   Integer( int x ) : val( x ) {}
   int get( ) { return val; }
private:
   int val;
};

int main() {
   const int N = 10;
   Integer val ( 60 );
   Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
   uninitialized_fill_n( Array, N, val );  // C4996
   int i;
   cout << "The uninitialized Array contains: ";
   for ( i = 0 ; i < N; i++ )
      cout << Array [ i ].get( ) <<  " ";
}
```

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)<br/>
