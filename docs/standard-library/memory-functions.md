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
ms.openlocfilehash: 676f6522a5625103a00310c6ce5353ce40da9359
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltmemorygt-functions"></a>&lt;Pamięć&gt; funkcji

||||
|-|-|-|
|[AddressOf](#addressof)|[align](#align)|[allocate_shared](#allocate_shared)|
|[const_pointer_cast](#const_pointer_cast)|[declare_no_pointers](#declare_no_pointers)|[declare_reachable](#declare_reachable)|
|[default_delete](#default_delete)|[dynamic_pointer_cast](#dynamic_pointer_cast)|[get_deleter](#get_deleter)|
|[get_pointer_safety](#get_pointer_safety)|[get_temporary_buffer](#get_temporary_buffer)|[make_shared —](#make_shared)|
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

`Val` Obiekt lub funkcja, do których chcesz uzyskać adres wartość true.

### <a name="return-value"></a>Wartość zwracana

Rzeczywisty adres obiektu lub odwołuje się funkcja `Val`, nawet jeśli przeciążone `operator&()` istnieje.

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

`Alignment` Wyrównanie powiązany próby.

`Size` Rozmiar w bajtach dla wyrównany magazynu.

`Ptr` Adres początkowy puli pamięci masowej o ciągłej dostępności, które mają być używane. Ten parametr jest również parametr wyjściowy i ma ustawioną wartość zawiera nowy adres początkowy, jeśli wyrównanie zakończy się pomyślnie. Jeśli `align()` się nie powiedzie, ten parametr nie jest modyfikowany.

`Space` Całkowita ilość miejsca, dostępne dla `align()` do użycia podczas tworzenia wyrównany magazynu. Ten parametr to również parametr wyjściowy, zawiera skorygowane miejsce pozostawione w buforze pamięci po odjęciu wyrównanej pamięci i wszystkich powiązanych obciążeń.

Jeśli `align()` się nie powiedzie, ten parametr nie jest modyfikowany.

### <a name="return-value"></a>Wartość zwracana

Wskaźnika o wartości null, jeśli nie mieści się żądanego bufora wyrównany na dostępne miejsce; w przeciwnym razie nowa wartość `Ptr`.

### <a name="remarks"></a>Uwagi

Zmodyfikowane `Ptr` i `Space` parametry Włącz, aby wywołać `align()` wielokrotnie na tego samego buforu, prawdopodobnie z różnych wartości `Alignment` i `Size`. Poniższy fragment kodu przedstawia użycie jednego `align()`.

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

Tworzy `shared_ptr` do obiektów, które są przydzielone i zbudowany dla danego typu przy użyciu określonego programu przydzielania. Zwraca `shared_ptr`.

```cpp
template <class Type, class Allocator, class... Types>
shared_ptr<Type>
allocate_shared(Allocator Alloc, Types&&... Args);
```

### <a name="parameters"></a>Parametry

`Alloc` Program przydzielania używany do tworzenia obiektów.

`Args` Argumenty zero lub więcej, które stają się obiekty.

### <a name="remarks"></a>Uwagi

Funkcja tworzy obiekt `shared_ptr<Type>`, wskaźnik do `Type(Args...)` jako przydzielone i utworzone przez `Alloc`.

## <a name="const_pointer_cast"></a>  const_pointer_cast

Const Rzutowanie na shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
const_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

`Ty` Typ kontrolowane przez zwrócony wskaźnik udostępnionego.

`Other` Typ kontrolowane przez wskaźnik udostępnionego argumentu.

`Other` Wskaźnik udostępnionego argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca obiekt shared_ptr puste, jeśli `const_cast<Ty*>(sp.get())` zwraca wskaźnika o wartości null; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu, którego właścicielem jest `sp`. Wyrażenie `const_cast<Ty*>(sp.get())` musi być prawidłowy.

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

Informuje o modułu zbierającego elementy bezużyteczne, zdefiniowanego przez wskaźnik adres podstawowy znaków w bloku pamięci i rozmiar bloku zawiera nie zidentyfikowanie wykonującej wskaźników.

```cpp
void declare_no_pointers(
    char* ptr,
    size_t _Size);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`ptr`|Adres pierwszego znaku, który nie zawiera już zidentyfikowanie wykonującej wskaźników.|
|`_Size`|Rozmiar bloku, która rozpoczyna się od `ptr` zawierający nie zidentyfikowanie wykonującej wskaźników.|

### <a name="remarks"></a>Uwagi

Funkcja informuje o dowolnym modułu zbierającego elementy bezużyteczne który zakres adresów `[ ptr, ptr + _Size)` nie zawiera już zidentyfikowanie wykonującej wskaźników. (Wszystkie wskaźniki do Magazyn przydzielony musi nie można usunąć odwołania o ile dostępny.)

## <a name="declare_reachable"></a>  declare_reachable

Informuje moduł odśmiecania pamięci, że wskazany adres prowadzi do przydzielonej pamięci i jest osiągalny.

```cpp
void declare_reachable(void* ptr);
```

### <a name="parameters"></a>Parametry

`ptr` Wskaźnik do obszaru magazynu dostępny, przydzielone, prawidłowe.

### <a name="remarks"></a>Uwagi

Jeśli `ptr` nie ma wartości null, funkcja informuje o dowolnym modułu zbierającego elementy bezużyteczne który `ptr` poniżej jest osiągalny (wskazuje prawidłowy Magazyn przydzielony).

## <a name="default_delete"></a>  default_delete

Usuwa obiekty przydzielone za pomocą `operator new`. Nadaje się do użytku z `unique_ptr`.

```cpp
struct default_delete {
   constexpr default_delete() noexcept = default;
   template <class Other, class = typename enable_if<is_convertible<Other*, T*>::value, void>::type>>
   default_delete(const default_delete<Other>&) noexcept;
   void operator()(T* Ptr) const noexcept;
};
```

### <a name="parameters"></a>Parametry

`Ptr` Wskaźnik do obiektu do usunięcia.

Inne typ elementów w tablicy, która ma zostać usunięty.

### <a name="remarks"></a>Uwagi

W tym artykule opisano klasy szablonu `deleter` który usuwa skalarne obiektów przydzielonych za pomocą `operator new`, odpowiednie do użycia z klasy szablonu `unique_ptr`. Jawna specjalizacja ma również `default_delete<Type[]>`.

## <a name="dynamic_pointer_cast"></a>  dynamic_pointer_cast

Rzutowania dynamicznego do shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
dynamic_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

`Ty` Typ kontrolowane przez zwrócony wskaźnik udostępnionego.

`Other` Typ kontrolowane przez wskaźnik udostępnionego argumentu.

`sp` Wskaźnik udostępnionego argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca obiekt shared_ptr puste, jeśli `dynamic_cast<Ty*>(sp.get())` zwraca wskaźnika o wartości null; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu, którego właścicielem jest `sp`. Wyrażenie `dynamic_cast<Ty*>(sp.get())` musi być prawidłowy.

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

Pobierz deleter z shared_ptr.

```cpp
template <class D, class Ty>
D* get_deleter(const shared_ptr<Ty>& sp);
```

### <a name="parameters"></a>Parametry

`D` Typ deleter.

`Ty` Typ kontrolowane przez wskaźnik udostępnionego.

`sp` Wskaźnik udostępnionego.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca wskaźnik do deleter typu `D` należący do [shared_ptr — klasa](../standard-library/shared-ptr-class.md) obiektu `sp`. Jeśli `sp` ma nie deleter lub jego deleter nie jest typu `D` funkcja zwraca wartość 0.

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

Funkcja zwraca typ wskaźnika bezpieczeństwa przyjmowana przez wszystkie automatyczne modułu zbierającego elementy bezużyteczne.

## <a name="get_temporary_buffer"></a>  get_temporary_buffer

Przydziela tymczasową pamięć dla sekwencji elementów, która nie przekracza określonej liczby elementów.

```cpp
template <class Type>
pair<Type *, ptrdiff_t> get_temporary_buffer(ptrdiff_t count);
```

### <a name="parameters"></a>Parametry

`count` Maksymalna liczba elementów zażądał, dla którego ma zostać przydzielone pamięci.

### <a name="return-value"></a>Wartość zwracana

A `pair` których pierwszy składnik jest wskaźnik do pamięci, która została przydzielona, i których drugi składnik daje rozmiar buforu wskazująca największą liczbę elementów, które można go zapisać.

### <a name="remarks"></a>Uwagi

Funkcja sprawia, że żądanie pamięci i może nie zadziałać. Jeśli bufor nie jest przydzielona, funkcja zwraca parę z drugiego składnika równego zero i pierwszy składnik równe pustego wskaźnika.

Tej funkcji należy używać tylko w pamięci, która ma charakter przejściowy.

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

## <a name="make_shared"></a>  make_shared —

Tworzy i zwraca `shared_ptr` wskazującego przydzielone obiekty, które są tworzone na podstawie zero lub więcej argumentów używając programu przydzielania domyślne. Przydziela i tworzy zarówno obiektu określonego typu i `shared_ptr` do zarządzania wspólnej własności obiektu i zwraca `shared_ptr`.

```cpp
template <class Type, class... Types>
shared_ptr<Type>
make_shared(Types&&... _Args);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Args`|Zero lub więcej argumentów konstruktora. Funkcja wnioskuje przeładowania konstruktora, który można wywołać oparte na argumenty, które zostały opublikowane.|

### <a name="remarks"></a>Uwagi

Użyj `make_shared` jako prosty i bardziej wydajny sposób do utworzenia obiektu i `shared_ptr` do zarządzania współdzielonym dostępem do obiektu w tym samym czasie. Semantycznie te dwie instrukcje są równoważne:

```cpp
auto sp = std::shared_ptr<Example>(new Example(argument));
auto msp = std::make_shared<Example>(argument);
```

Jednak pierwszą instrukcją sprawia, że dwa alokacji i Jeśli alokacja `shared_ptr` nie powiedzie się po alokacja `Example` obiektu zakończyła się pomyślnie, następnie nienazwane `Example` przeciek obiektu. Instrukcja, która używa `make_shared` jest prostsze, ponieważ jest zaangażowany wywołanie funkcji tylko jeden. Jest bardziej wydajne, ponieważ biblioteki można wprowadzać pojedynczego alokacji dla obiekt i wskaźnika inteligentnego. To jest szybsze i prowadzi do mniej fragmentacji pamięci i bez możliwości wyjątek w jednej alokacji, ale nie drugiej nie istnieje. Lepsze lokalizacji dla kodu, który odwołuje się do obiektu i aktualizacje, które zlicza odwołania w wskaźnika inteligentnego znacznie poprawia wydajność.

Należy rozważyć użycie [make_unique](../standard-library/memory-functions.md#make_unique) Jeśli nie potrzebujesz dostępu współdzielonego do obiektu. Użyj [allocate_shared](../standard-library/memory-functions.md#allocate_shared) Jeśli trzeba określić niestandardowy program przydzielania dla obiekt. Nie można użyć `make_shared` Jeśli obiekt wymaga niestandardowych deleter, ponieważ nie można przekazać deleter jako argument.

Poniższy przykład przedstawia sposób tworzenia udostępnionego wskaźniki do typu przez wywołanie konstruktora określonego przeciążenia.

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

Przykład generuje dane wyjściowe w tym:

```Output
Playing Ode to Joy by Beethoven, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
Playing Greensleeves by Unknown, use count: 2
Playing Yesterday by The Beatles, use count: 3
Playing Blackbird by The Beatles, use count: 3
```

## <a name="make_unique"></a>  make_unique

Tworzy i zwraca [unique_ptr](../standard-library/unique-ptr-class.md) do obiektu określonego typu, który jest tworzony przy użyciu określonych argumentów.

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

`T` Typ obiektu, który `unique_ptr` wskaże.

`Types` Typy argumentów konstruktora określonego przez `Args`.

`Args` Argumenty do przekazania do konstruktora obiektu typu `T`.

`Elem` Tablica elementów typu `T`.

`Size` Liczba elementów, aby przydzielić miejsce dla nowych tablicy.

### <a name="remarks"></a>Uwagi

Pierwszy przeciążenia służy do pojedynczych obiektów, drugi przeciążenia jest wywoływany dla tablic i uniemożliwia trzeci przeciążenia nie pozwala na określenie rozmiaru tablicy w argumencie typu (make_unique\<T [N] >); ta konstrukcja nie jest obsługiwana. przez bieżący standard. Jeśli używasz `make_unique` utworzyć `unique_ptr` do tablicy, należy zainicjować elementów tablicy oddzielnie. Planując to przeciążenie, być może lepszym rozwiązaniem jest użycie [std::vector](../standard-library/vector-class.md).

Ponieważ `make_unique` dokładnie jest zaimplementowany dla bezpieczeństwa wyjątków, firma Microsoft zaleca użycie `make_unique` zamiast bezpośredniego wywoływania `unique_ptr` konstruktorów.

### <a name="example"></a>Przykład

Poniższy przykład przedstawia użycie `make_unique`. Aby uzyskać więcej przykładów, zobacz [porady: Tworzenie wystąpień unique_ptr i korzystanie](../cpp/how-to-create-and-use-unique-ptr-instances.md).

[!code-cpp[stl_smart_pointers#214](../cpp/codesnippet/CPP/memory-functions_1.cpp)]

Po wyświetleniu błędu C2280 w połączeniu z `unique_ptr`, jest prawie na pewno ponieważ podjęto próbę wywołania konstruktora kopiującego, który jest to usunięta funkcja.

## <a name="owner_less"></a>  owner_less —

Pozwala na mieszane porównania oparte na własności współdzielonych i słabych wskaźników. Zwraca `true` Jeśli lewy parametr jest umieszczane przed odpowiednich parametrów w funkcji członkowskiej `owner_before`.

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

`_left` Udostępnione lub słabe wskaźnika.

`right` Udostępnione lub słabe wskaźnika.

### <a name="remarks"></a>Uwagi

Klasy szablonów zdefiniować ich operatorów Członkowskich jako zwracanie `left.owner_before(right)`.

## <a name="return_temporary_buffer"></a>  return_temporary_buffer

Cofa alokację pamięci tymczasowej, który został przydzielony przy użyciu `get_temporary_buffer` funkcji szablonu.

```cpp
template <class Type>
void return_temporary_buffer(Type* _Pbuf);
```

### <a name="parameters"></a>Parametry

*_Pbuf* wskaźnik do pamięci do przydzielenia.

### <a name="remarks"></a>Uwagi

Tej funkcji należy używać tylko w pamięci, która ma charakter przejściowy.

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

## <a name="static_pointer_cast"></a>  static_pointer_cast

Rzutowania statycznego do shared_ptr.

```cpp
template <class Ty, class Other>
shared_ptr<Ty>
static_pointer_cast(const shared_ptr<Other>& sp);
```

### <a name="parameters"></a>Parametry

`Ty` Typ kontrolowane przez zwrócony wskaźnik udostępnionego.

`Other` Typ kontrolowane przez wskaźnik udostępnionego argumentu.

`Other` Wskaźnik udostępnionego argumentu.

### <a name="remarks"></a>Uwagi

Funkcja szablonu zwraca obiekt shared_ptr puste, jeśli `sp` jest pusta `shared_ptr` obiektu; w przeciwnym razie zwraca [shared_ptr — klasa](../standard-library/shared-ptr-class.md)\<Ty > obiekt, który jest właścicielem zasobu, którego właścicielem jest `sp`. Wyrażenie `static_cast<Ty*>(sp.get())` musi być prawidłowy.

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

`Ty` Typ kontrolowane przez wskaźnik po lewej stronie udostępnionych niska.

`Other` Typ kontrolowane przez wskaźnik udostępnionych prawo/niska.

`left` Po lewej stronie wskaźnik udostępnionych niska.

`right` Wskaźnik udostępnionych prawo/niska.

### <a name="remarks"></a>Uwagi

Wywołanie funkcji szablonu `left.swap(right)`.

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

Funkcja informuje o dowolnym modułu zbierającego elementy bezużyteczne który zakres adresów `[ptr, ptr + _Size)` teraz mogą zawierać zidentyfikowanie wykonującej wskaźników.

## <a name="undeclare_reachable"></a>  undeclare_reachable

Wycofanie deklaracji uzyskiwanie lokalizacji określonej pamięci.

```cpp
template <class Type>
Type *undeclare_reachable(Type* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`ptr`|Wskaźnik do można nie zadeklarować nieosiągalny adres pamięci.|

### <a name="remarks"></a>Uwagi

Jeśli `ptr` nie jest `nullptr`, funkcja informuje o dowolnym modułu zbierającego elementy bezużyteczne który `ptr` nie jest już dostępny. Zwraca wskaźnik bezpiecznie pochodnych, który porównuje w równa `ptr`.

## <a name="uninitialized_copy"></a>  uninitialized_copy

Kopiuje obiekty z określonego zakresu źródłowego do niezainicjowanego zakresu docelowego.

```cpp
template <class InputIterator, class ForwardIterator>
ForwardIterator uninitialized_copy(InputIterator first, InputIterator last, ForwardIterator dest);
```

### <a name="parameters"></a>Parametry

`first` Wejściowy iteratora adresowania pierwszym elementem w zakresie źródłowym.

`last` Wejściowy iteratora adresowania ostatnim elementem w zakresie źródłowym.

`dest` Pierwszym elementem w docelowy zakres adresów do przodu iteratora.

### <a name="return-value"></a>Wartość zwracana

Do przodu iteratora adresowania na pierwszym miejscu poza zakres docelowy, chyba że źródłowy zakres był pusty.

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

`first` Iterację wejściowych odwołuje się do obiektu do skopiowania.

`count` Podpisem lub unsigned integer — typ określenie, ile razy można skopiować obiektu.

`dest` Iterator do przodu, odnoszący się do gdzie nowe kopie.

### <a name="return-value"></a>Wartość zwracana

Iterator do przodu, który odnosi się do pierwszej pozycji poza miejscem docelowym. Jeśli źródłowy zakres było puste, adresy iteratora `first`.

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

`first` Adresowanie pierwszym elementem w zakres docelowy, który ma zostać zainicjowany do przodu iteratora.

`last` Adresowanie ostatni element docelowy zakres, który ma zostać zainicjowany do przodu iteratora.

`val` Wartość ma być używany do inicjowania zakresu docelowego.

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

`first` Iterator do przodu adresowania pierwszym elementem w zakresie docelowym inicjowanie.

`count` Liczba elementów, aby można było zainicjować.

`val` Wartość ma być używany do inicjowania zakresu docelowego.

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
