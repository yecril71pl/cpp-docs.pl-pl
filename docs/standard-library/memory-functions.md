---
title: funkcje&gt; pamięci &lt;
ms.date: 08/05/2019
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
- memory/std::get_temporary_buffer
- xmemory/std::get_temporary_buffer
- memory/std::make_shared
- memory/std::make_unique
- memory/std::owner_less
- memory/std::reinterpret_pointer_cast
- memory/std::return_temporary_buffer
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
ms.assetid: 3e1898c2-44b7-4626-87ce-84962e4c6f1a
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
ms.openlocfilehash: 2aceb96fcda49df8a1fd40a1bd8011170dccd8ef
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79419939"
---
# <a name="ltmemorygt-functions"></a>funkcje&gt; pamięci &lt;

## <a name="addressof"></a>AddressOf

Pobiera prawdziwy adres obiektu.

```cpp
template <class T>
T* addressof(
    T& value) noexcept;    // before C++17

template <class T>
constexpr T* addressof(
    T& value) noexcept;    // C++17

template <class T>
const T* addressof(
    const T&& value) = delete;   // C++17
```

### <a name="parameters"></a>Parametry

\ *wartości*
Obiekt lub funkcja, dla których ma być uzyskany prawdziwy adres.

### <a name="return-value"></a>Wartość zwrócona

Rzeczywisty adres obiektu lub funkcji, do której odwołuje się *wartość*, nawet jeśli przeciążone `operator&()` istnieje.

### <a name="remarks"></a>Uwagi

## <a name="align"></a>dostosowania

Pasuje do magazynu o danym rozmiarze wyrównanym przez daną specyfikację wyrównania do pierwszego możliwego adresu danego magazynu.

```cpp
void* align(
    size_t alignment, // input
    size_t size,      // input
    void*& ptr,       // input/output
    size_t& space     // input/output
);
```

### <a name="parameters"></a>Parametry

\ *wyrównania*
Wyrównanie powiązane z próbą.

\ *rozmiaru*
Rozmiar w bajtach dla wyrównanej pamięci.

\ *PTR*
Adres początkowy dostępnej puli ciągłej pamięci, która ma być użyta. Ten parametr jest również parametrem wyjściowym i jest ustawiony tak, aby zawierał nowy adres początkowy w przypadku pomyślnego wyrównania. Jeśli `align()` nie powiedzie się, ten parametr nie jest modyfikowany.

\ *miejsca*
Łączne miejsce dostępne do `align()` do użycia podczas tworzenia wyrównanego magazynu. Ten parametr to również parametr wyjściowy, zawiera skorygowane miejsce pozostawione w buforze pamięci po odjęciu wyrównanej pamięci i wszystkich powiązanych obciążeń.

Jeśli `align()` nie powiedzie się, ten parametr nie jest modyfikowany.

### <a name="return-value"></a>Wartość zwrócona

Wskaźnik o wartości null, jeśli żądany rozmiar buforu nie mieści się w dostępnym miejscu; w przeciwnym razie nowa wartość *PTR*.

### <a name="remarks"></a>Uwagi

Zmodyfikowane parametry *PTR* i *Space* umożliwiają wielokrotne wywoływanie `align()` w tym samym buforze, prawdopodobnie z różnymi wartościami do *wyrównania* i *rozmiaru*. Poniższy fragment kodu przedstawia jedno użycie `align()`.

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

## <a name="allocate_shared"></a>allocate_shared

Tworzy [shared_ptr](shared-ptr-class.md) do obiektów, które są przydzielane i skonstruowane dla danego typu przy użyciu określonego alokatora. Zwraca `shared_ptr`.

```cpp
template <class T, class Allocator, class... Args>
shared_ptr<T> allocate_shared(
    Allocator alloc,
    Args&&... args);
```

### <a name="parameters"></a>Parametry

\ *alokacji*
Alokator używany do tworzenia obiektów.

*argumenty*\
Zero lub więcej argumentów, które stają się obiektami.

### <a name="remarks"></a>Uwagi

Funkcja tworzy obiekt `shared_ptr<T>`, wskaźnik do `T(args...)` jako przydzielone i skonstruowane przez *Alloc*.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
bool atomic_compare_exchange_strong(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
bool atomic_compare_exchange_weak(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
bool atomic_compare_exchange_strong_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
bool atomic_compare_exchange_weak_explicit(
    shared_ptr<T>* u,
    shared_ptr<T>* v,
    shared_ptr<T> w,
    memory_order success,
    memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
shared_ptr<T> atomic_exchange(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
shared_ptr<T> atomic_exchange_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
bool atomic_is_lock_free(
    const shared_ptr<T>* u);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
shared_ptr<T> atomic_load(
    const shared_ptr<T>* u);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
shared_ptr<T> atomic_load_explicit(
    const shared_ptr<T>* u,
    memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
void atomic_store(
    shared_ptr<T>* u,
    shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
void atomic_store_explicit(
    shared_ptr<T>* u,
    shared_ptr<T> r,
    memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Rzutowanie const na [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> const_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*T*\
Typ kontrolowany przez zwracany wskaźnik udostępniony.

*Inne*\
Typ kontrolowany przez wspólny wskaźnik argumentu.

\ *SP*
Wspólny wskaźnik argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca pusty obiekt `shared_ptr`, jeśli `const_cast<T*>(sp.get())` zwraca wskaźnik o wartości null; w przeciwnym razie zwraca obiekt `shared_ptr<T>`, który jest właścicielem zasobu, który jest własnością *SP*. Wyrażenie `const_cast<T*>(sp.get())` musi być prawidłowe.

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

## <a name="declare_no_pointers"></a>declare_no_pointers

Informuje moduł wyrzucania elementów bezużytecznych, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku nie zawierają wskaźników do śledzenia.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Adres pierwszego znaku, który nie zawiera już wskaźników śledzonych.

\ *rozmiaru*
Rozmiar bloku, który zaczyna się od wartości *PTR* , która nie zawiera wskaźników do śledzenia.

### <a name="remarks"></a>Uwagi

Funkcja informuje dowolny moduł wyrzucania elementów bezużytecznych, że adresy w zakresie `[ ptr, ptr + size)` nie zawierają już wskaźników do śledzenia. (Nie można usunąć odwołania do żadnych wskaźników do przydzielnego magazynu, chyba że jest on dostępny).

## <a name="declare_reachable"></a>declare_reachable

Informuje moduł odśmiecania pamięci, że wskazany adres prowadzi do przydzielonej pamięci i jest osiągalny.

```cpp
void declare_reachable(
    void* ptr);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik do dostępnego, przydzielenia prawidłowego obszaru magazynowania.

### <a name="remarks"></a>Uwagi

Jeśli *PTR* nie ma wartości null, funkcja informuje każdy moduł wyrzucania elementów bezużytecznych, że *PTR* jest teraz osiągalny, czyli wskazuje na prawidłowy przydzieloną pamięć masową.

## <a name="default_delete"></a>default_delete

Usuwa obiekty przydzielono do **operatora new**. Odpowiednie do użycia z [unique_ptr](unique-ptr-class.md).

```cpp
struct default_delete
{
    constexpr default_delete() noexcept = default;

    template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
    default_delete(const default_delete<Other>&) noexcept;

    void operator()(T* ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik do obiektu do usunięcia.

*Inne*\
Typ elementów w tablicy, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

Szablon klasy opisuje obiekt usuwający, który usuwa obiekty skalarne przydzielono z **operatorem New**, odpowiednie do użycia z szablonem klasy `unique_ptr`. Ma także jawną specjalizację `default_delete<T[]>`.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
void destroy_at(
    T* location);
```

Taki sam jak `location->~T()`.

## <a name="destroy"></a>usunięcie

```cpp
template <class ForwardIterator>
void destroy(
    ForwardIterator first,
    ForwardIterator last);
```

Analogicznie jak:

```cpp
for (; first != last; ++first)
    destroy_at(addressof(*first));
```

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
ForwardIterator destroy_n(
    ForwardIterator first,
    Size count);
```

Analogicznie jak:

```cpp
for (; count > 0; (void)++first, --count)
    destroy_at(addressof(*first));
return first;
```

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Dynamiczne rzutowanie na [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> dynamic_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*T*\
Typ kontrolowany przez zwracany wskaźnik udostępniony.

*Inne*\
Typ kontrolowany przez wspólny wskaźnik argumentu.

\ *SP*
Wspólny wskaźnik argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca pusty obiekt `shared_ptr`, jeśli `dynamic_cast<T*>(sp.get())` zwraca wskaźnik o wartości null; w przeciwnym razie zwraca obiekt `shared_ptr<T>`, który jest właścicielem zasobu, który jest własnością *SP*. Wyrażenie `dynamic_cast<T*>(sp.get())` musi być prawidłowe.

### <a name="example"></a>Przykład

```cpp
// std__memory__dynamic_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    virtual ~base() {}
    int value;
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

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="get_deleter"></a>get_deleter

Pobierz obiekt do usunięcia z [shared_ptr](shared-ptr-class.md).

```cpp
template <class Deleter, class T>
Deleter* get_deleter(
    const shared_ptr<T>& sp) noexcept;
```

### <a name="parameters"></a>Parametry

\ *usuwania*
Typ obiektu do usuwania.

*T*\
Typ kontrolowany przez wspólny wskaźnik.

\ *SP*
Udostępniony wskaźnik.

### <a name="remarks"></a>Uwagi

Funkcja Template zwraca wskaźnik do *elementu usuwającego typu,* który należy do obiektu `shared_ptr` *SP*. Jeśli w programie *SP* nie ma żadnego elementu DELETE lub nie jest *on typu Delete*, funkcja zwróci wartość 0.

### <a name="example"></a>Przykład

```cpp
// std__memory__get_deleter.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
};

struct deleter
{
    void operator()(base *pb)
    {
        delete pb;
    }
};

int main()
{
    std::shared_ptr<base> sp0(new base);

    sp0->value = 3;
    std::cout << "get_deleter(sp0) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp0) != 0) << std::endl;

    std::shared_ptr<base> sp1(new base, deleter());

    sp0->value = 3;
    std::cout << "get_deleter(sp1) != 0 == " << std::boolalpha
        << (std::get_deleter<deleter>(sp1) != 0) << std::endl;

    return (0);
}
```

```Output
get_deleter(sp0) != 0 == false
get_deleter(sp1) != 0 == true
```

## <a name="get_pointer_safety"></a>get_pointer_safety

Zwraca typ bezpieczeństwa wskaźnika założony przez dowolny moduł odśmiecania pamięci.

```cpp
pointer_safety get_pointer_safety() noexcept;
```

### <a name="remarks"></a>Uwagi

Funkcja zwraca typ bezpieczeństwa wskaźnika przyjęty przez jakikolwiek automatyczny moduł wyrzucania elementów bezużytecznych.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Przydziela tymczasowy magazyn dla sekwencji elementów, które nie przekraczają określonej liczby elementów.

```cpp
template <class T>
pair<T *, ptrdiff_t> get_temporary_buffer(
    ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

*liczba*\
Maksymalna liczba elementów żądanych do przydzielenia pamięci.

### <a name="return-value"></a>Wartość zwrócona

`pair`, którego pierwszy składnik jest wskaźnikiem do pamięci, która została przypisana, a drugi składnik uzyskuje rozmiar buforu, wskazując największą liczbę elementów, które mogą być przechowywane.

### <a name="remarks"></a>Uwagi

Funkcja wysyła żądanie dotyczące pamięci i może się nie powieść. Jeśli bufor nie zostanie przydzielony, funkcja zwraca parę, z drugim składnikiem równym zero, a pierwszy składnik równy wskaźnikowi o wartości null.

Tej funkcji należy używać tylko w przypadku pamięci, która jest tymczasowa.

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
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300, 1000, 2000 };
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

## <a name="make_shared"></a>make_shared

Tworzy i zwraca [shared_ptr](shared-ptr-class.md) wskazujący przydzielone obiekty, które są zbudowane z zero lub więcej argumentów przy użyciu domyślnego alokatora. Przydziela i konstruuje zarówno obiekt określonego typu, jak i `shared_ptr` do zarządzania współużytkowaną własność obiektu i zwraca `shared_ptr`.

```cpp
template <class T, class... Args>
shared_ptr<T> make_shared(
    Args&&... args);
```

### <a name="parameters"></a>Parametry

*argumenty*\
Zero lub więcej argumentów konstruktora. Funkcja wnioskuje, jakie przeciążenie konstruktora ma zostać wywołane na podstawie podanych argumentów.

### <a name="remarks"></a>Uwagi

Użyj `make_shared` jako prostego i wydajniejszego sposobu tworzenia obiektu i `shared_ptr` do zarządzania dostępem współdzielonym do obiektu w tym samym czasie. Semantycznie te dwie instrukcje są równoważne:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Jednak Pierwsza instrukcja wykonuje dwa alokacje i jeśli alokacja `shared_ptr` nie powiedzie się po pomyślnym wykonaniu przydziału obiektu `Example`, nienazwany obiekt `Example` jest wycieka. Instrukcja, która używa `make_shared` jest prostsza, ponieważ istnieje tylko jedno wywołanie funkcji. Jest to bardziej wydajne, ponieważ biblioteka może wykonać pojedyncze alokacje dla obiektu i wskaźnika inteligentnego. Ta funkcja jest jednocześnie szybsza i prowadzi do mniejszej fragmentacji pamięci i nie ma możliwości wystąpienia wyjątku w jednej alokacji, ale nie w drugim. Wydajność jest ulepszona dzięki lepszej lokalizacji w kodzie, który odwołuje się do obiektu i aktualizuje liczbę odwołań w inteligentnym wskaźniku.

Rozważ użycie [make_unique](memory-functions.md#make_unique) , jeśli nie potrzebujesz dostępu współdzielonego do obiektu. Użyj [allocate_shared](memory-functions.md#allocate_shared) , jeśli musisz określić niestandardowy Alokator dla obiektu. Nie można użyć `make_shared`, jeśli obiekt wymaga niestandardowego obiektu do usuwania, ponieważ nie istnieje sposób przekazania elementu usuwania jako argumentu.

Poniższy przykład pokazuje, jak utworzyć udostępnione wskaźniki do typu przez wywoływanie określonych przeciążeń konstruktora.

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

void CreateSharedPointers()
{
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
    for (auto&& sp : playlist)
    {
        std::wcout << L"Playing " << sp->title_ <<
            L" by " << sp->artist_ << L", use count: " <<
            sp.use_count() << std::endl;
    }
}

int main()
{
    CreateSharedPointers();
}
```

Przykład generuje te dane wyjściowe:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>make_unique

Tworzy i zwraca [unique_ptr](unique-ptr-class.md) do obiektu określonego typu, który jest zbudowany przy użyciu określonych argumentów.

```cpp
// make_unique<T>
template <class T, class... Args>
unique_ptr<T> make_unique(Args&&... args);

// make_unique<T[]>
template <class T>
unique_ptr<T> make_unique(size_t size);

// make_unique<T[N]> disallowed
template <class T, class... Args>
/* unspecified */ make_unique(Args&&...) = delete;
```

### <a name="parameters"></a>Parametry

*T*\
Typ obiektu wskazywanego przez `unique_ptr`.

*Argumenty*\
Typy argumentów konstruktora określonych przez *argumenty*.

*argumenty*\
Argumenty, które mają zostać przekazane do konstruktora obiektu typu *T*.

*elementy*\
Tablica elementów typu *T*.

\ *rozmiaru*
Liczba elementów do przydzielenia miejsca dla nowej tablicy.

### <a name="remarks"></a>Uwagi

Pierwsze przeciążenie jest używane dla pojedynczych obiektów. Drugie Przeciążenie jest wywoływane dla tablic. Trzecie Przeciążenie uniemożliwia określenie rozmiaru tablicy w argumencie typu (make_unique\<T [N] >). Ta konstrukcja nie jest obsługiwana przez bieżący Standard. Gdy używasz `make_unique` do tworzenia `unique_ptr` do tablicy, musisz zainicjować elementy tablicy osobno. Zamiast korzystać z tego przeciążenia, być może lepszym wyborem jest użycie [std:: Vector](vector-class.md).

Ponieważ `make_unique` jest starannie zaimplementowany pod kątem bezpieczeństwa wyjątków, zalecamy użycie `make_unique` zamiast bezpośredniego wywoływania konstruktorów `unique_ptr`.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `make_unique`. Aby uzyskać więcej przykładów, zobacz [How to: Create and Use Unique_ptr Instances](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Gdy zobaczysz błąd C2280 w połączeniu z `unique_ptr`, prawie jest to spowodowane tym, że podjęto próbę wywołania konstruktora kopiującego, który jest funkcją usuniętą.

## <a name="owner_less"></a>owner_less

Pozwala na mieszane porównania oparte na własności współdzielonych i słabych wskaźników. Zwraca **wartość true** , jeśli lewy parametr jest uporządkowany przed prawidłowym parametrem przez funkcję członkowską `owner_before`.

```cpp
template <class T>
    struct owner_less; // not defined

template <class T>
struct owner_less<shared_ptr<T>>
{
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;
};

template <class T>
struct owner_less<weak_ptr<T>>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;

    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<T>& right) const noexcept;

    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<T>& right) const noexcept;
};

template<> struct owner_less<void>
{
    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const shared_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const shared_ptr<U>& right) const noexcept;

    template<class T, class U>
    bool operator()(
        const weak_ptr<T>& left,
        const weak_ptr<U>& right) const noexcept;
};
```

### <a name="parameters"></a>Parametry

\ *lewo*
Udostępniony lub słaby wskaźnik.

*prawa*\
Udostępniony lub słaby wskaźnik.

### <a name="remarks"></a>Uwagi

Szablony klas definiują wszystkie ich operatory składowe jako zwracające `left.owner_before(right)`.

## <a name="reinterpret_pointer_cast"></a>reinterpret_pointer_cast

Tworzy nowy `shared_ptr` na podstawie istniejącego udostępnionego wskaźnika przy użyciu rzutowania.

```cpp
template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    const shared_ptr<U>& ptr) noexcept;

template<class T, class U>
shared_ptr<T> reinterpret_pointer_cast(
    shared_ptr<U>&& ptr) noexcept;
```

### <a name="parameters"></a>Parametry

\ *PTR*
Odwołanie do `shared_ptr<U>`.

### <a name="remarks"></a>Uwagi

Jeśli *PTR* jest puste, nowy `shared_ptr` jest również pusty, w przeciwnym razie współdzieli własność z *PTR*. Nowy wspólny wskaźnik jest wynikiem oceny `reinterpret_cast<Y*>(ptr.get())`, gdzie `Y` jest `typename std::shared_ptr<T>::element_type`. Zachowanie jest niezdefiniowane, jeśli `reinterpret_cast<T*>((U*)nullptr)` nie jest poprawnie sformułowane.

Funkcja szablonu, która przyjmuje odwołanie lvalue, jest nowa w języku C++ 17. Funkcja szablonu, która przyjmuje odwołanie rvalue, jest nowa w języku C++ 20.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Zwalnia pamięć tymczasową, która została przydzielona za pomocą funkcji szablonu `get_temporary_buffer`.

```cpp
template <class T>
void return_temporary_buffer(
    T* buffer);
```

### <a name="parameters"></a>Parametry

*bufor*\
Wskaźnik do pamięci, która ma zostać cofnięta alokacja.

### <a name="remarks"></a>Uwagi

Tej funkcji należy używać tylko w przypadku pamięci, która jest tymczasowa.

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
    int intArray [] = { 10, 20, 30, 40, 100, 200, 300 };
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
    return_temporary_buffer( tempBuffer );
}
```

```Output
The number of integers in the array is: 7.
The number of elements that the allocated memory
could store is given by: resultPair.second = 7.
```

## <a name="static_pointer_cast"></a>static_pointer_cast

Statyczne rzutowanie na [shared_ptr](shared-ptr-class.md).

```cpp
template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    const shared_ptr<Other>& sp) noexcept;

template <class T, class Other>
shared_ptr<T> static_pointer_cast(
    shared_ptr<Other>&& sp) noexcept;
```

### <a name="parameters"></a>Parametry

*T*\
Typ kontrolowany przez zwracany wskaźnik udostępniony.

*Inne*\
Typ kontrolowany przez wspólny wskaźnik argumentu.

\ *SP*
Wspólny wskaźnik argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca pusty obiekt `shared_ptr`, jeśli *SP* jest pustym obiektem `shared_ptr`; w przeciwnym razie zwraca obiekt `shared_ptr<T>`, który jest właścicielem zasobu, który jest własnością *SP*. Wyrażenie `static_cast<T*>(sp.get())` musi być prawidłowe.

### <a name="example"></a>Przykład

```cpp
// std__memory__static_pointer_cast.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

struct base
{
    int value;
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

    sp0->value = 3;
    std::cout << "sp1->value == " << sp1->value << std::endl;

    return (0);
}
```

```Output
sp1->value == 3
```

## <a name="swap"></a>wymiany

Zamień dwa [shared_ptr](shared-ptr-class.md), [unique_ptr](unique-ptr-class.md)lub [weak_ptr](weak-ptr-class.md) obiektów.

```cpp
template <class T>
void swap(
    shared_ptr<T>& left,
    shared_ptr<T>& right) noexcept;

template <class T, class Deleter>
void swap(
    unique_ptr<T, Deleter>& left,
    unique_ptr<T, Deleter>& right) noexcept;

template <class T>
void swap(
    weak_ptr<T>& left,
    weak_ptr<T>& right) noexcept;

```

### <a name="parameters"></a>Parametry

*T*\
Typ kontrolowany przez wskaźnik argumentu.

\ *usuwania*
Usuwanie unikatowego typu wskaźnika.

\ *lewo*
Lewy wskaźnik.

*prawa*\
Prawy wskaźnik.

### <a name="remarks"></a>Uwagi

Wywołania funkcji szablonu `left.swap(right)`.

### <a name="example"></a>Przykład

```cpp
// std__memory__swap.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

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

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

Informuje moduł odśmiecający pamięci, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku mogą teraz zawierać wskaźniki mogące podlegać śledzeniu.

```cpp
void undeclare_no_pointers(
    char* ptr,
    size_t size);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik do adresu pamięci, który został wcześniej oznaczony przy użyciu [declare_no_pointers](#declare_no_pointers).

\ *rozmiaru*
Liczba bajtów w zakresie pamięci. Ta wartość musi być równa liczbie użytej w wywołaniu `declare_no_pointers`.

### <a name="remarks"></a>Uwagi

Funkcja informuje każdy moduł wyrzucania elementów bezużytecznych, że zakres adresów `[ptr, ptr + size)` może teraz zawierać wskaźniki możliwe do śledzenia.

## <a name="undeclare_reachable"></a>undeclare_reachable

Odwołuje deklarację osiągalności dla określonej lokalizacji pamięci.

```cpp
template <class T>
T *undeclare_reachable(
    T* ptr);
```

### <a name="parameters"></a>Parametry

\ *PTR*
Wskaźnik do adresu pamięci, który został wcześniej oznaczony przy użyciu [declare_reachable](#declare_reachable).

### <a name="remarks"></a>Uwagi

Jeśli *PTR* nie jest **nullptr**, funkcja informuje wszystkie Moduł wyrzucania elementów bezużytecznych, że *PTR* nie jest już osiągalny. Zwraca bezpieczny wskaźnik pochodny, który jest porównywany z równy *PTR*.

## <a name="uninitialized_copy"></a>uninitialized_copy

Kopiuje obiekty z określonego zakresu źródłowego do niezainicjowanego zakresu docelowego.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, odnoszący się do pierwszego elementu w zakresie źródłowym.

*ostatni*\
Iterator danych wejściowych, odnoszący się do ostatniego elementu w zakresie źródłowym.

\ miejsca *docelowego*
Iterator do przodu, który dotyczy pierwszego elementu w zakresie docelowym.

### <a name="return-value"></a>Wartość zwrócona

Iterator do przodu, odnoszący się do pierwszej pozycji poza zakresem docelowym, chyba że zakres źródłowy był pusty.

### <a name="remarks"></a>Uwagi

Ten algorytm umożliwia oddzielenie alokacji pamięci od konstrukcji obiektu.

Funkcja szablonu skutecznie wykonuje:

```cpp
while (first != last)
{
    new (static_cast<void*>(&* dest++))
        typename iterator_traits<InputIterator>::value_type(*first++);
}
return dest;
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

Przeciążenie przy użyciu zasad wykonywania jest nowe w języku C++ 17.

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
    Integer(int x) : value(x) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    int Array[] = { 10, 20, 30, 40 };
    const int N = sizeof(Array) / sizeof(int);

    cout << "The initialized Array contains " << N << " elements: ";
    for (int i = 0; i < N; i++)
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

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

Tworzy kopię określonej liczby elementów z iteratora danych wejściowych. Kopie są wprowadzane do iteratora do przodu.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych, który odwołuje się do obiektu do skopiowania.

*liczba*\
Typ całkowitoliczbowy ze znakiem lub bez znaku, określający, ile razy obiekt ma być skopiowany.

\ miejsca *docelowego*
Iterator do przodu odwołujący się do lokalizacji nowych kopii.

### <a name="return-value"></a>Wartość zwrócona

Iterator do przodu, który odnosi się do pierwszej pozycji poza miejscem docelowym. Jeśli zakres źródłowy był pusty, *najpierw*adresy iteratora.

### <a name="remarks"></a>Uwagi

Funkcja Template efektywnie wykonuje następujący kod:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

Przeciążenie przy użyciu zasad wykonywania jest nowe w języku C++ 17.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

Domyślne obiekty konstrukcji iteratorów `value_type` w określonym zakresie.

```cpp
template <class ForwardIterator>
void uninitialized_default_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_default_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator odnoszący się do pierwszego elementu w zakresie, który ma zostać skonstruowany.

*ostatni*\
Iterator odnoszący się do jednego ostatniego elementu w zakresie, który ma zostać skonstruowany.

### <a name="remarks"></a>Uwagi

Wersja bez zasad wykonywania jest efektywnie taka sama jak w przypadku:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

Jeśli wystąpi wyjątek, wcześniej skonstruowane obiekty są niszczone w nieokreślonej kolejności.

Wersja z zasadami wykonywania ma ten sam wynik, ale jest wykonywana zgodnie z określonymi *zasadami*.

Te funkcje są nowe w języku C++ 17.

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

Domyślnie konstruuje określoną liczbę obiektów `value_type`iteratora, rozpoczynając od określonej lokalizacji.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_default_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator odnoszący się do pierwszego elementu w zakresie docelowym do konstruowania.

*liczba*\
Liczba elementów w zakresie docelowym do skonstruowania.

### <a name="return-value"></a>Wartość zwrócona

Iterator do przodu, odnoszący się do pierwszej pozycji poza zakresem docelowym, chyba że zakres źródłowy był pusty.

### <a name="remarks"></a>Uwagi

Wersja bez zasad wykonywania jest efektywnie taka sama jak w przypadku:

```cpp
for (; count>0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
return first;
```

Jeśli wystąpi wyjątek, wcześniej skonstruowane obiekty są niszczone w nieokreślonej kolejności.

Wersja z zasadami wykonywania ma ten sam wynik, ale jest wykonywana zgodnie z określonymi *zasadami*.

Te funkcje są nowe w języku C++ 17.

## <a name="uninitialized_fill"></a>uninitialized_fill

Kopiuje obiekty z określoną wartością do niezainicjowanego zakresu docelowego.

```cpp
template <class ForwardIterator, class T>
void uninitialized_fill(
    ForwardIterator first,
    ForwardIterator last,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class T>
void uninitialized_fill(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last,
    const T& value);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pierwszego elementu w zakresie docelowym, który ma zostać zainicjowany.

*ostatni*\
Iterator do przodu, odnoszący się do ostatniego elementu w zakresie docelowym, który ma zostać zainicjowany.

\ *wartości*
Wartość wykorzystana do zainicjowania zakresu docelowego.

### <a name="remarks"></a>Uwagi

Ten algorytm umożliwia oddzielenie alokacji pamięci od konstrukcji obiektu.

Funkcja szablonu skutecznie wykonuje:

```cpp
while (first != last)
    new (static_cast<void*>(&* first ++))
        typename iterator_traits<ForwardIterator>::value_type (value);
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

Przeciążenie przy użyciu zasad wykonywania jest nowe w języku C++ 17.

### <a name="example"></a>Przykład

```cpp
// memory_uninit_fill.cpp
// compile with: /EHsc
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value ( 25 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill( Array, Array + N, value );
    cout << "The initialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        {
            cout << Array[ i ].get() << " ";
        }
    cout << endl;
}
```

```Output
The initialized Array contains: 25 25 25 25 25 25 25 25 25 25
```

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Kopiuje obiekty z określoną wartością do określonej liczby elementów niezainicjowanego zakresu docelowego.

```cpp
template <class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ForwardIterator first,
    Size count,
    const T& value);

template <class ExecutionPolicy, class ForwardIterator, class Size, class T>
ForwardIterator uninitialized_fill_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count,
    const T& value);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator do przodu, odnoszący się do pierwszego elementu w zakresie docelowym, który ma zostać zainicjowany.

*liczba*\
Liczba elementów do zainicjowania.

\ *wartości*
Wartość, która ma zostać użyta do zainicjowania zakresu docelowego.

### <a name="remarks"></a>Uwagi

Ten algorytm umożliwia oddzielenie alokacji pamięci od konstrukcji obiektu.

Funkcja szablonu skutecznie wykonuje:

```cpp
while (0 < count--)
    new (static_cast<void*>(&* first++))
        typename iterator_traits<ForwardIterator>::value_type(value);
return first;
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

Przeciążenie przy użyciu zasad wykonywania jest nowe w języku C++ 17.

### <a name="example"></a>Przykład

```cpp
// memory_uninit_fill_n.cpp
// compile with: /EHsc /W3
#include <memory>
#include <iostream>

using namespace std;

class Integer
{
public:
    // No default constructor
    Integer( int x ) : value( x ) {}
    int get() { return value; }
private:
    int value;
};

int main()
{
    const int N = 10;
    Integer value( 60 );
    Integer* Array = ( Integer* ) malloc( N * sizeof( int ) );
    uninitialized_fill_n( Array, N, value );  // C4996
    cout << "The uninitialized Array contains: ";
    for ( int i = 0; i < N; i++ )
        cout << Array[ i ].get() <<  " ";
}
```

## <a name="uninitialized_move"></a>uninitialized_move

Przenosi elementy z zakresu źródłowego do niezainicjowanego obszaru pamięci docelowej.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_move(
    ExecutionPolicy&& policy,
    InputIterator first,
    InputIterator last,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie źródłowym, który ma zostać przeniesiony.

*ostatni*\
Iterator danych wejściowych odnoszący się do jednego z ostatnich elementów w zakresie źródłowym, który ma zostać przeniesiony.

\ miejsca *docelowego*
Początek zakresu docelowego.

### <a name="remarks"></a>Uwagi

Wersja bez zasad wykonywania jest efektywnie taka sama jak w przypadku:

```cpp
for (; first != last; (void)++dest, ++first)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return dest;
```

Jeśli wyjątek jest zgłaszany, niektóre obiekty w zakresie źródłowym mogą pozostać w prawidłowym, ale nieokreślonym stanie. Wcześniej skonstruowane obiekty są niszczone w nieokreślonej kolejności.

Wersja z zasadami wykonywania ma ten sam wynik, ale jest wykonywana zgodnie z określonymi *zasadami*.

Te funkcje są nowe w języku C++ 17.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

Przenosi określoną liczbę elementów z zakresu źródłowego do niezainicjowanego obszaru pamięci docelowej.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);

template <class ExecutionPolicy, class InputIterator, class Size, class ForwardIterator>
pair<InputIterator, ForwardIterator> uninitialized_move_n(
    ExecutionPolicy&& policy,
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator danych wejściowych odnoszący się do pierwszego elementu w zakresie źródłowym, który ma zostać przeniesiony.

*liczba*\
Liczba elementów w zakresie źródłowym, które mają zostać przeniesione.

\ miejsca *docelowego*
Początek zakresu docelowego.

### <a name="remarks"></a>Uwagi

Wersja bez zasad wykonywania jest efektywnie taka sama jak w przypadku:

```cpp
for (; count > 0; ++dest, (void) ++first, --count)
    ::new (static_cast<void*>(addressof(*dest)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first));
return {first, dest};
```

Jeśli wyjątek jest zgłaszany, niektóre obiekty w zakresie źródłowym mogą pozostać w prawidłowym, ale nieokreślonym stanie. Wcześniej skonstruowane obiekty są niszczone w nieokreślonej kolejności.

Wersja z zasadami wykonywania ma ten sam wynik, ale jest wykonywana zgodnie z określonymi *zasadami*.

Te funkcje są nowe w języku C++ 17.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

Tworzy obiekty iteratorów `value_type` przez inicjalizację wartości w określonym zakresie.

```cpp
template <class ForwardIterator>
void uninitialized_value_construct(
    ForwardIterator first,
    ForwardIterator last);

template <class ExecutionPolicy, class ForwardIterator>
void uninitialized_value_construct(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    ForwardIterator last);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator odnoszący się do pierwszego elementu w konstrukcji zakresu do wartości.

*ostatni*\
Iterator odnoszący się do jednej poza ostatnim elementem w konstrukcji zakresu do wartości.

### <a name="remarks"></a>Uwagi

Wersja bez zasad wykonywania jest efektywnie taka sama jak w przypadku:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

Jeśli wystąpi wyjątek, wcześniej skonstruowane obiekty są niszczone w nieokreślonej kolejności.

Wersja z zasadami wykonywania ma ten sam wynik, ale jest wykonywana zgodnie z określonymi *zasadami*.

Jeśli wystąpi błąd alokacji pamięci, zostanie zgłoszony wyjątek `std::bad_alloc`.

Te funkcje są nowe w języku C++ 17.

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

Tworzy określoną liczbę obiektów `value_type` iteratora przez inicjalizację wartości, rozpoczynając od określonej lokalizacji.

```cpp
template <class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ForwardIterator first,
    Size count);

template <class ExecutionPolicy, class ForwardIterator, class Size>
ForwardIterator uninitialized_value_construct_n(
    ExecutionPolicy&& policy,
    ForwardIterator first,
    Size count);
```

### <a name="parameters"></a>Parametry

\ *zasad*
Zasady wykonywania, które mają być używane.

*pierwszy*\
Iterator odnoszący się do pierwszego elementu w zakresie docelowym do konstruowania.

*liczba*\
Liczba elementów w zakresie docelowym do skonstruowania.

### <a name="remarks"></a>Uwagi

Wersja bez zasad wykonywania jest efektywnie taka sama jak w przypadku:

```cpp
for (; count > 0; (void)++first, --count)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
return first;
```

Jeśli wystąpi wyjątek, wcześniej skonstruowane obiekty są niszczone w nieokreślonej kolejności.

Wersja z zasadami wykonywania ma ten sam wynik, ale jest wykonywana zgodnie z określonymi *zasadami*.

Jeśli wystąpi błąd alokacji pamięci, zostanie zgłoszony wyjątek `std::bad_alloc`.

Te funkcje są nowe w języku C++ 17.

## <a name="uses_allocator_v"></a>uses_allocator_v

Szablon zmiennej pomocnika, aby uzyskać dostęp do wartości szablonu `uses_allocator`.

```cpp
template <class T, class Alloc>
inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Zobacz też

[> pamięci \<](memory.md)
