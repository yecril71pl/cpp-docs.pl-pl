---
title: '&lt;funkcje&gt; pamięci'
ms.date: 02/06/2019
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
ms.openlocfilehash: 14818e93e79a0be9960ba67088f81d51d402b717
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448490"
---
# <a name="ltmemorygt-functions"></a>&lt;funkcje&gt; pamięci

## <a name="addressof"></a>AddressOf

Pobiera prawdziwy adres obiektu.

```cpp
template <class T>
    T* addressof(T& Val);
```

### <a name="parameters"></a>Parametry

*Użyte*\
Obiekt lub funkcja, dla których ma być uzyskany prawdziwy adres.

### <a name="return-value"></a>Wartość zwracana

Rzeczywisty adres obiektu lub funkcji, do których odwołuje się *Val*, nawet jeśli istnieje `operator&()` przeciążona wartość.

### <a name="remarks"></a>Uwagi

## <a name="align"></a>dostosowania

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

*Struktury*\
Wyrównanie powiązane z próbą.

*Zmienia*\
Rozmiar w bajtach dla wyrównanej pamięci.

*PTR*\
Adres początkowy dostępnej puli ciągłej pamięci, która ma być użyta. Ten parametr jest również parametrem wyjściowym i jest ustawiony tak, aby zawierał nowy adres początkowy w przypadku pomyślnego wyrównania. Jeśli `align()` to się nie powiedzie, ten parametr nie jest modyfikowany.

*Odstęp*\
Całkowite miejsce dostępne do `align()` użycia podczas tworzenia wyrównanego magazynu. Ten parametr to również parametr wyjściowy, zawiera skorygowane miejsce pozostawione w buforze pamięci po odjęciu wyrównanej pamięci i wszystkich powiązanych obciążeń.

Jeśli `align()` to się nie powiedzie, ten parametr nie jest modyfikowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik o wartości null, jeśli żądany bufor wyrównany nie mieści się w dostępnym miejscu; w przeciwnym razie nowa wartość *PTR*.

### <a name="remarks"></a>Uwagi

Zmodyfikowane parametry *PTR* i *Space* umożliwiają wielokrotne wywoływanie `align()` tego samego buforu, prawdopodobnie z różnymi wartościami do wyrównania  i *rozmiaru*. Poniższy fragment kodu przedstawia jedno użycie `align()`.

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

`shared_ptr` Tworzy do obiektów, które są przydzielane i skonstruowane dla danego typu przy użyciu określonego alokatora. Zwraca wartość `shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
    shared_ptr<Type> allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parametry

*Alokacj*\
Alokator używany do tworzenia obiektów.

*Argumentów*\
Zero lub więcej argumentów, które stają się obiektami.

### <a name="remarks"></a>Uwagi

Funkcja tworzy obiekt `shared_ptr<Type>`, wskaźnik do `Type(Args...)` jako przydzielone i skonstruowane przez *Alloc*.

## <a name="atomic_compare_exchange_strong"></a>atomic_compare_exchange_strong

```cpp
template<class T>
    bool atomic_compare_exchange_strong(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_weak"></a>atomic_compare_exchange_weak

```cpp
template<class T>
    bool atomic_compare_exchange_weak(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w);
```

## <a name="atomic_compare_exchange_strong_explicit"></a>atomic_compare_exchange_strong_explicit

```cpp
template<class T>
    bool atomic_compare_exchange_strong_explicit(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w, memory_order success, memory_order failure);
```

## <a name="atomic_compare_exchange_weak_explicit"></a>atomic_compare_exchange_weak_explicit

```cpp
template<class T>
    bool atomic_compare_exchange_weak_explicit(shared_ptr<T>* p, shared_ptr<T>* v, shared_ptr<T> w, memory_order success, memory_order failure);
```

## <a name="atomic_exchange"></a>atomic_exchange

```cpp
template<class T>
    shared_ptr<T> atomic_exchange(shared_ptr<T>* p, shared_ptr<T> r);
```

## <a name="atomic_exchange_explicit"></a>atomic_exchange_explicit

```cpp
template<class T>
    shared_ptr<T> atomic_exchange_explicit(shared_ptr<T>* p, shared_ptr<T> r, memory_order mo);
```

## <a name="atomic_is_lock_free"></a>atomic_is_lock_free

```cpp
template<class T>
    bool atomic_is_lock_free(const shared_ptr<T>* p);
```

## <a name="atomic_load"></a>atomic_load

```cpp
template<class T>
    shared_ptr<T> atomic_load(const shared_ptr<T>* p);
```

## <a name="atomic_load_explicit"></a>atomic_load_explicit

```cpp
template<class T>
    shared_ptr<T> atomic_load_explicit(const shared_ptr<T>* p, memory_order mo);
```

## <a name="atomic_store"></a>atomic_store

```cpp
template<class T>
    void atomic_store(shared_ptr<T>* p, shared_ptr<T> r);
```

## <a name="atomic_store_explicit"></a>atomic_store_explicit

```cpp
template<class T>
    void atomic_store_explicit(shared_ptr<T>* p, shared_ptr<T> r, memory_order mo);
```

## <a name="const_pointer_cast"></a>const_pointer_cast

Rzutowanie const na shared_ptr.

```cpp
template <class Ty, class Other>
    shared_ptr<Ty> const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Br*\
Typ kontrolowany przez zwracany wskaźnik udostępniony.

*Różnych*\
Typ kontrolowany przez wspólny wskaźnik argumentu.

*Różnych*\
Wspólny wskaźnik argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca pusty obiekt `const_cast<Ty*>(sp.get())` shared_ptr, jeśli zwraca wskaźnik o wartości null; w przeciwnym razie zwraca obiekt [shared_ptr klasy](../standard-library/shared-ptr-class.md)\<> ty, który jest `sp`właścicielem zasobu, do którego należy. Wyrażenie `const_cast<Ty*>(sp.get())` musi być prawidłowe.

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
void declare_no_pointers(char* ptr, size_t _Size);
```

### <a name="parameters"></a>Parametry

*PTR*\
Adres pierwszego znaku, który nie zawiera już wskaźników śledzonych.

*_Size*\
Rozmiar bloku, który zaczyna się od wartości *PTR* , która nie zawiera wskaźników do śledzenia.

### <a name="remarks"></a>Uwagi

Funkcja informuje dowolny moduł wyrzucania elementów bezużytecznych, że `[ ptr, ptr + _Size)` zakres adresów nie zawiera już wskaźników do śledzenia. (Nie można usunąć odwołania do żadnych wskaźników do przydzielnego magazynu, chyba że jest on dostępny).

## <a name="declare_reachable"></a>declare_reachable

Informuje moduł odśmiecania pamięci, że wskazany adres prowadzi do przydzielonej pamięci i jest osiągalny.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do dostępnego, przydzielenia prawidłowego obszaru magazynowania.

### <a name="remarks"></a>Uwagi

Jeśli *PTR* nie ma wartości null, funkcja informuje każdy moduł wyrzucania elementów bezużytecznych, że *PTR* jest dalej osiągalny (wskazuje prawidłowy magazyn).

## <a name="default_delete"></a>default_delete

Usuwa obiekty przydzielono do **operatora new**. Odpowiednie do użycia z `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
        default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do obiektu do usunięcia.

*Różnych*\
Typ elementów w tablicy, który ma zostać usunięty.

### <a name="remarks"></a>Uwagi

Klasa szablonu opisuje `deleter` , że usuwa obiekty skalarne przydzielono z **operatorem New**, odpowiednie do użycia z `unique_ptr`klasą szablonu. Ma także jawną specjalizację `default_delete<Type[]>`.

## <a name="destroy_at"></a>destroy_at

```cpp
template <class T>
    void destroy_at(T* location);
```

Analogicznie `location->~T()`jak.

## <a name="destroy"></a>usunięcie

```cpp
template <class ForwardIterator>
    void destroy(ForwardIterator first, ForwardIterator last);
```

Analogicznie `for (; first!=last; ++first) destroy_at(addressof(*first)); `jak.

## <a name="destroy_n"></a>destroy_n

```cpp
template <class ForwardIterator, class Size>
    ForwardIterator destroy_n(ForwardIterator first, Size n);
```

Analogicznie `for (; n > 0; (void)++first, --n) destroy_at(addressof(*first)); return first;`jak.

## <a name="dynamic_pointer_cast"></a>dynamic_pointer_cast

Dynamiczne rzutowanie na shared_ptr.

```cpp
template <class Ty, class Other>
    shared_ptr<Ty> dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Br*\
Typ kontrolowany przez zwracany wskaźnik udostępniony.

*Różnych*\
Typ kontrolowany przez wspólny wskaźnik argumentu.

*requirement*\
Wspólny wskaźnik argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca pusty obiekt shared_ptr `dynamic_cast<Ty*>(sp.get())` , jeśli zwraca wskaźnik o wartości null; w przeciwnym razie zwraca > [klasę](../standard-library/shared-ptr-class.md)\<shared_ptr, która jest właścicielem zasobu, którego właścicielem jest obiekt *SP*. Wyrażenie `dynamic_cast<Ty*>(sp.get())` musi być prawidłowe.

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

## <a name="get_deleter"></a>get_deleter

Pobierz usuwanie z shared_ptr.

```cpp
template <class D, class Ty>
    D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

*WYKRES*\
Typ obiektu do usuwania.

*Br*\
Typ kontrolowany przez wspólny wskaźnik.

*requirement*\
Udostępniony wskaźnik.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wskaźnik do elementu Delete typu *D* , który należy do obiektu [klasy shared_ptr](../standard-library/shared-ptr-class.md) *SP*. Jeśli *SP* nie ma żadnego elementu DELETE lub jeśli jego typ nie jest typu *D* , funkcja zwraca wartość 0.

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

## <a name="get_pointer_safety"></a>get_pointer_safety

Zwraca typ bezpieczeństwa wskaźnika założony przez dowolny moduł odśmiecania pamięci.

```cpp
pointer_safety get_pointer_safety();
```

### <a name="remarks"></a>Uwagi

Funkcja zwraca typ bezpieczeństwa wskaźnika przyjęty przez jakikolwiek automatyczny moduł wyrzucania elementów bezużytecznych.

## <a name="get_temporary_buffer"></a>get_temporary_buffer

Przydziela tymczasową pamięć dla sekwencji elementów, która nie przekracza określonej liczby elementów.

```cpp
template <class Type>
    pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Maksymalna liczba elementów żądanych do przydzielenia pamięci.

### <a name="return-value"></a>Wartość zwracana

`pair` Którego pierwszy składnik jest wskaźnikiem do pamięci, która została przypisana, a drugi składnik ma rozmiar buforu, wskazując największą liczbę elementów, które mogą być przechowywane.

### <a name="remarks"></a>Uwagi

Funkcja wysyła żądanie dotyczące pamięci i może się nie powieść. Jeśli bufor nie zostanie przydzielony, funkcja zwraca parę, z drugim składnikiem równym zero, a pierwszy składnik równy wskaźnikowi o wartości null.

Ta funkcja powinna być używana tylko w przypadku pamięci, która jest tymczasowa.

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

## <a name="make_shared"></a>make_shared

Tworzy i zwraca `shared_ptr` wartość wskazującą przydzielone obiekty, które są zbudowane z zero lub więcej argumentów przy użyciu domyślnego alokatora. Przydziela i konstruuje zarówno obiekt określonego typu, jak i `shared_ptr` do zarządzania współużytkowaną własność obiektu i `shared_ptr`zwraca.

```cpp
template <class Type, class... Types>
    shared_ptr<Type> make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

*_Args*\
Zero lub więcej argumentów konstruktora. Funkcja wnioskuje, jakie przeciążenie konstruktora ma zostać wywołane na podstawie podanych argumentów.

### <a name="remarks"></a>Uwagi

Użyj `make_shared` jako prostej i wydajniejszej metody tworzenia obiektu i a `shared_ptr` do zarządzania dostępem współdzielonym do obiektu w tym samym czasie. Semantycznie te dwie instrukcje są równoważne:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Jednak Pierwsza instrukcja tworzy dwie alokacje i jeśli alokacja `shared_ptr` zakończy się niepowodzeniem po pomyślnym przypisaniu `Example` obiektu, nienazwany `Example` obiekt jest wycieka. Używana `make_shared` instrukcja jest prostsza, ponieważ istnieje tylko jedno wywołanie funkcji. Jest to bardziej wydajne, ponieważ biblioteka może wykonać pojedyncze alokacje dla obiektu i wskaźnika inteligentnego. Jest to szybsze i może prowadzić do mniejszej fragmentacji pamięci i nie ma możliwości wystąpienia wyjątku w jednej alokacji, ale innym. Wydajność jest ulepszona dzięki lepszej lokalizacji w kodzie, który odwołuje się do obiektu i aktualizuje liczbę odwołań w inteligentnym wskaźniku.

Rozważ użycie [make_unique](../standard-library/memory-functions.md#make_unique) , jeśli nie potrzebujesz dostępu współdzielonego do obiektu. Użyj [allocate_shared](../standard-library/memory-functions.md#allocate_shared) , jeśli chcesz określić niestandardowy Alokator dla obiektu. Nie można użyć `make_shared` , jeśli obiekt wymaga niestandardowego obiektu do usuwania, ponieważ nie ma możliwości przekazania elementu Delete jako argumentu.

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

Tworzy i zwraca [unique_ptr](../standard-library/unique-ptr-class.md) do obiektu określonego typu, który jest zbudowany przy użyciu określonych argumentów.

```cpp
// make_unique<T>
template <class T, class... Types>
    unique_ptr<T> make_unique(Types&&... Args)
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
    typename enable_if<extent<T>::value != 0, void>::type make_unique(Types&&...) = delete;
```

### <a name="parameters"></a>Parametry

*&* \
Typ obiektu, do którego `unique_ptr` będzie wskazywał.

*Typ*\
Typy argumentów konstruktora określonych przez *argumenty*.

*Argumentów*\
Argumenty, które mają zostać przekazane do konstruktora obiektu typu *T*.

*Elem*\
Tablica elementów typu *T*.

*Zmienia*\
Liczba elementów do przydzielenia miejsca dla nowej tablicy.

### <a name="remarks"></a>Uwagi

Pierwsze przeciążenie jest używane dla pojedynczych obiektów, drugie Przeciążenie jest wywoływane dla tablic, a trzecie Przeciążenie uniemożliwia określenie rozmiaru tablicy w argumencie typu (make_unique\<T [N] >); Ta konstrukcja nie jest obsługiwana przez bieżącą Standardowa. Gdy używasz `make_unique` do `unique_ptr` tworzenia tablicy, musisz zainicjować elementy tablicy osobno. Jeśli rozważasz to Przeciążenie, być może lepszym wyborem jest użycie [std:: Vector](../standard-library/vector-class.md).

Ze `make_unique` względu na to, że jest to uważnie zaimplementowane pod kątem `make_unique` bezpieczeństwa wyjątków, zalecamy `unique_ptr` użycie zamiast bezpośrednio wywoływanych konstruktorów.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać `make_unique`. Aby uzyskać więcej przykładów, [zobacz How to: Tworzenie wystąpień](../cpp/how-to-create-and-use-unique-ptr-instances.md)unique_ptr i korzystanie z nich.

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Gdy zobaczysz błąd C2280 w połączeniu z `unique_ptr`, prawie jest to spowodowane tym, że podjęto próbę wywołania konstruktora kopiującego, który jest funkcją usuniętą.

## <a name="owner_less"></a>owner_less

Pozwala na mieszane porównania oparte na własności współdzielonych i słabych wskaźników. Zwraca **wartość true** , jeśli lewy parametr jest uporządkowany przed właściwym parametrem przez `owner_before`funkcję członkowską.

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

*_left*\
Udostępniony lub słaby wskaźnik.

*Kliknij*\
Udostępniony lub słaby wskaźnik.

### <a name="remarks"></a>Uwagi

Klasy szablonów definiują wszystkie ich operatory składowe jako `left.owner_before(right)`zwracające.

## <a name="return_temporary_buffer"></a>return_temporary_buffer

Zwalnia pamięć tymczasową, która została przydzielona za pomocą `get_temporary_buffer` funkcji szablonu.

```cpp
template <class Type>
    void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parametry

*_Pbuf*\
Wskaźnik do pamięci, która ma zostać cofnięta alokacja.

### <a name="remarks"></a>Uwagi

Ta funkcja powinna być używana tylko w przypadku pamięci, która jest tymczasowa.

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

## <a name="static_pointer_cast"></a>static_pointer_cast

Statyczne rzutowanie na shared_ptr.

```cpp
template <class Ty, class Other>
    shared_ptr<Ty> static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

*Br*\
Typ kontrolowany przez zwracany wskaźnik udostępniony.

*Różnych*\
Typ kontrolowany przez wspólny wskaźnik argumentu.

*Różnych*\
Wspólny wskaźnik argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca pusty obiekt shared_ptr `sp` , jeśli jest pustym `shared_ptr` obiektem; w przeciwnym razie zwraca obiekt [shared_ptr klasy](../standard-library/shared-ptr-class.md)\< `sp`> ty, który jest właścicielem zasobu, którego właścicielem jest. Wyrażenie `static_cast<Ty*>(sp.get())` musi być prawidłowe.

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

## <a name="swap"></a>wymiany

Zamień dwa obiekty shared_ptr lub weak_ptr.

```cpp
template <class Ty, class Other>
    void swap(shared_ptr<Ty>& left, shared_ptr<Other>& right);

template <class Ty, class Other>
    void swap(weak_ptr<Ty>& left, weak_ptr<Other>& right);
```

### <a name="parameters"></a>Parametry

*Br*\
Typ kontrolowany przez lewy udostępniony/słaby wskaźnik.

*Różnych*\
Typ kontrolowany przez prawy udostępniony/słaby wskaźnik.

*lewym*\
Lewy udostępniony/słaby wskaźnik.

*Kliknij*\
Prawy udostępniony/słaby wskaźnik.

### <a name="remarks"></a>Uwagi

Wywołanie `left.swap(right)`funkcji szablonu.

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

## <a name="undeclare_no_pointers"></a>undeclare_no_pointers

Informuje moduł odśmiecający pamięci, że znaki w bloku pamięci zdefiniowane przez wskaźnik adresu podstawowego i rozmiar bloku mogą teraz zawierać wskaźniki mogące podlegać śledzeniu.

```cpp
void undeclare_no_pointers(char* ptr, size_t _Size);
```

### <a name="remarks"></a>Uwagi

Funkcja informuje wszystkie wyrzucanie elementów bezużytecznych, że zakres `[ptr, ptr + _Size)` adresów może teraz zawierać wskaźniki możliwe do śledzenia.

## <a name="undeclare_reachable"></a>undeclare_reachable

Odwołuje deklarację osiągalności dla określonej lokalizacji pamięci.

```cpp
template <class Type>
    Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik na adres pamięci, który ma zostać zadeklarowany jako nieosiągalny.

### <a name="remarks"></a>Uwagi

Jeśli *PTR* nie jest **nullptr**, funkcja informuje wszystkie Moduł wyrzucania elementów bezużytecznych, że *PTR* nie jest już osiągalny. Zwraca bezpieczny wskaźnik, który jest porównywany z równy *PTR*.

## <a name="uninitialized_copy"></a>uninitialized_copy

Kopiuje obiekty z określonego zakresu źródłowego do niezainicjowanego zakresu docelowego.

```cpp
template <class InputIterator, class ForwardIterator>
    ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych, odnoszący się do pierwszego elementu w zakresie źródłowym.

*ostatniego*\
Iterator danych wejściowych, odnoszący się do ostatniego elementu w zakresie źródłowym.

*dest*\
Iterator do przodu, który dotyczy pierwszego elementu w zakresie docelowym.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, odnoszący się do pierwszej pozycji poza zakresem docelowym, chyba że zakres źródłowy był pusty.

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

## <a name="uninitialized_copy_n"></a>uninitialized_copy_n

Tworzy kopię określonej liczby elementów z iteratora danych wejściowych. Kopie są wprowadzane do iteratora do przodu.

```cpp
template <class InputIterator, class Size, class ForwardIterator>
ForwardIterator uninitialized_copy_n(
    InputIterator first,
    Size count,
    ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator danych wejściowych, który odwołuje się do obiektu do skopiowania.

*liczbą*\
Typ całkowitoliczbowy ze znakiem lub bez znaku, określający, ile razy obiekt ma być skopiowany.

*dest*\
Iterator do przodu odwołujący się do lokalizacji nowych kopii.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który odnosi się do pierwszej pozycji poza miejscem docelowym. Jeśli zakres źródłowy był pusty, *najpierw*adresy iteratora.

### <a name="remarks"></a>Uwagi

Funkcja szablonu skutecznie wykonuje następujące:

```cpp
    for (; 0 < count; --count)
        new (static_cast<void*>(&* dest++))
            typename iterator_traits<InputIterator>::value_type(*first++);
    return dest;
```

chyba że kod zgłasza wyjątek. W takim przypadku wszystkie skonstruowane obiekty są niszczone, a wyjątek jest zgłaszany ponownie.

## <a name="uninitialized_default_construct"></a>uninitialized_default_construct

```cpp
template <class ForwardIterator>
    void uninitialized_default_construct(ForwardIterator first, ForwardIterator last); 
```

### <a name="remarks"></a>Uwagi

Analogicznie jak:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type;
```

## <a name="uninitialized_default_construct_n"></a>uninitialized_default_construct_n

```cpp
template <class ForwardIterator, class Size>
    ForwardIterator uninitialized_default_construct_n(ForwardIterator first, Size n)
```

### <a name="remarks"></a>Uwagi

Analogicznie jak:

```cpp
for (; n>0; (void)++first, --n)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type; return first;
```

## <a name="uninitialized_fill"></a>uninitialized_fill

Kopiuje obiekty z określoną wartością do niezainicjowanego zakresu docelowego.

```cpp
template <class ForwardIterator, class Type>
    void uninitialized_fill(ForwardIterator first, ForwardIterator last, const Type& val);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator do przodu, odnoszący się do pierwszego elementu w zakresie docelowym, który ma zostać zainicjowany.

*ostatniego*\
Iterator do przodu, odnoszący się do ostatniego elementu w zakresie docelowym, który ma zostać zainicjowany.

*użyte*\
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

## <a name="uninitialized_fill_n"></a>uninitialized_fill_n

Kopiuje obiekty z określoną wartością do określonej liczby elementów w niezainicjowanym zakresie docelowym.

```cpp
template <class FwdIt, class Size, class Type>
    void uninitialized_fill_n(ForwardIterator first, Size count, const Type& val);
```

### <a name="parameters"></a>Parametry

*pierwszego*\
Iterator do przodu, odnoszący się do pierwszego elementu w zakresie docelowym, który ma być zainicjowany.

*liczbą*\
Liczba elementów, które mają być zainicjowane.

*użyte*\
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

## <a name="uninitialized_move"></a>uninitialized_move

```cpp
template <class InputIterator, class ForwardIterator>
    ForwardIterator uninitialized_move(InputIterator first, InputIterator last, ForwardIterator result); 
```

### <a name="remarks"></a>Uwagi

Analogicznie jak:

```cpp
for (; first != last; (void)++result, ++first)
    ::new (static_cast<void*>(addressof(*result)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first)); 
        return result;
```

Jeśli wyjątek jest zgłaszany, niektóre obiekty w zakresie mogą pozostać w prawidłowym, ale nieokreślonym stanie.

## <a name="uninitialized_move_n"></a>uninitialized_move_n

```cpp
template <class InputIterator, class Size, class ForwardIterator>
    pair<InputIterator, ForwardIterator> uninitialized_move_n(InputIterator first, Size n, ForwardIterator result);
```

### <a name="remarks"></a>Uwagi

Analogicznie jak:

```cpp
for (; n > 0; ++result, (void) ++first, --n)
    ::new (static_cast<void*>(addressof(*result)))
        typename iterator_traits<ForwardIterator>::value_type(std::move(*first)); return {first,result};
```

Jeśli wyjątek jest zgłaszany, niektóre obiekty w zakresie mogą pozostać w prawidłowym, ale nieokreślonym stanie.

## <a name="uninitialized_value_construct"></a>uninitialized_value_construct

```cpp
template <class ForwardIterator>
    void uninitialized_value_construct(ForwardIterator first, ForwardIterator last);
```

### <a name="remarks"></a>Uwagi

Analogicznie jak:

```cpp
for (; first != last; ++first)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type();
```

## <a name="uninitialized_value_construct_n"></a>uninitialized_value_construct_n

```cpp
template <class ForwardIterator, class Size>
    ForwardIterator uninitialized_value_construct_n(ForwardIterator first, Size n);
```

Analogicznie jak:
```cpp
for (; n>0; (void)++first, --n)
    ::new (static_cast<void*>(addressof(*first)))
        typename iterator_traits<ForwardIterator>::value_type(); return first;
```

## <a name="uses_allocator_v"></a>uses_allocator_v

```cpp
template <class T, class Alloc>
    inline constexpr bool uses_allocator_v = uses_allocator<T, Alloc>::value;
```

## <a name="see-also"></a>Zobacz także

[\<memory>](../standard-library/memory.md)
