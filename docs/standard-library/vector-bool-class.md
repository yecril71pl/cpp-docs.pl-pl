---
title: Wektor&lt;bool&gt; klasy
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: f7663987b2759c762d1f6c1604923478915f5726
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521989"
---
# <a name="vectorltboolgt-class"></a>Wektor&lt;bool&gt; klasy

`vector<bool>` Klasa to częściowa specjalizacja [wektor](../standard-library/vector-class.md) dla elementów typu **bool**. Ma alokator dla podstawowego typu używanego przez specjalizację, który zapewnia optymalizację miejsca poprzez przechowywanie jednej **bool** wartość na bit.

## <a name="syntax"></a>Składnia

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Uwagi

Taka specjalizacja szablonu klasy zachowuje się jak wektora, z wyjątkiem różnic opisanych w tym artykule.

Operacje, które zajmują się **bool** typu odpowiadają wartościom w pamięci kontenera. `allocator_traits::construct` nie jest używana do konstruowania tych wartości.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Element typedef do `const_iterator` który może służyć jako stały wskaźnik do elementu typu Boolean `vector<bool>`.|
|[const_reference](#const_reference)|Element typedef dla **bool**. Po zainicjowaniu nie zwraca uwagi na aktualizacje do wartości pierwotnej.|
|[pointer](#pointer)|Element typedef do `iterator` który może służyć jako wskaźnik do elementu typu Boolean `vector<bool>`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[Przerzuć](#flip)|Odwraca wszystkie bity w `vector<bool>`.|
|[swap](#swap)|Zamienia elementy z dwóch `vector<bool>`s.|
|[operator&#91;&#93;](#op_at)|Zwraca symulowane odwołanie do `vector<bool>` elementu na określonej pozycji.|
|`at`|Działa tak samo, jak Niewyspecjalizowana [wektor](../standard-library/vector-class.md):: w funkcji, z wyjątkiem, że używa klasy proxy [wektor\<bool >:: odwołanie](#reference_class). Zobacz też [operator&#91;&#93;](#op_at).|
|`front`|Działa tak samo, jak Niewyspecjalizowana [wektor](../standard-library/vector-class.md):: frontonu funkcji, z tą różnicą, że używa klasy proxy [wektor\<bool >:: odwołanie](#reference_class). Zobacz też [operator&#91;&#93;](#op_at).|
|`back`|Działa tak samo, jak Niewyspecjalizowana [wektor](../standard-library/vector-class.md):: kopii funkcji, z tą różnicą, że używa klasy proxy [wektor\<bool >:: odwołanie](#reference_class). Zobacz też [operator&#91;&#93;](#op_at).|

### <a name="proxy-class"></a>Klasa proxy

|||
|-|-|
|[Wektor\<bool > reference — klasa](#reference_class)|Klasa, która działa jako serwer proxy do symulacji `bool&` zachowanie i której obiekty mogą dostarczyć odniesienia do elementów (pojedynczych bitów) w ramach `vector<bool>` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<wektor >

**Namespace:** standardowe

## <a name="const_pointer"></a>  Wektor\<bool >:: const_pointer

Typ opisujący obiekt, który może służyć jako stały wskaźnik do elementu Boolean sekwencji zawartej w `vector<bool>` obiektu.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>  Wektor\<bool >:: const_reference

Typ opisujący obiekt, który może służyć jako stałe odwołanie do elementu Boolean sekwencji zawartej w `vector<bool>` obiektu.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i przykłady kodu, zobacz [wektor&lt;bool&gt;:: reference::operator =](#reference_operator_eq).

## <a name="flip"></a>  Wektor\<bool >:: przerzucanie

Odwraca wszystkie bity w `vector<bool>`.

```cpp
void flip();
```

### <a name="example"></a>Przykład

```cpp
// vector_bool_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha; // format output for subsequent code

    vector<bool> vb = { true, false, false, true, true };
    cout << "The vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vb.flip();

    cout << "The flipped vector is:" << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

## <a name="op_at"></a>  Wektor\<bool >:: operator]

Zwraca symulowane odwołanie do `vector<bool>` elementu na określonej pozycji.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*punktu sprzedaży*|Pozycja `vector<bool>` elementu.|

### <a name="return-value"></a>Wartość zwracana

A [wektor\<bool >:: odwołanie](#reference_class) lub [wektor\<bool >:: const_reference](#const_reference) obiekt, który zawiera wartość indeksowanego elementu.

Jeśli określona pozycja jest większa niż lub równa rozmiarowi kontenera, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli kompilujesz z zestawem _ITERATOR_DEBUG_LEVEL błędów czasu wykonywania występuje, jeśli użytkownik podejmie próbę uzyskania dostępu do elementu poza granicami wektora.  Aby uzyskać więcej informacji, zobacz [Checked Iterators](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W tym przykładzie kodu pokazano sposób poprawnego użycia z `vector<bool>::operator[]` i dwie częste pomyłki w kodowaniu, które są zakomentowane. Te pomyłki powodują błędy, ponieważ adres `vector<bool>::reference` obiekt `vector<bool>::operator[]` zwraca nie może być przyjęty.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;
    vector<bool> vb;

    vb.push_back(true);
    vb.push_back(false);

    //    bool* pb = &vb[1]; // conversion error - do not use
    //    bool& refb = vb[1];   // conversion error - do not use
    bool hold = vb[1];
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;

    // Note this doesn't modify hold.
    vb[1] = true;
    cout << "The second element of vb is " << vb[1] << endl;
    cout << "The held value from the second element of vb is " << hold << endl;
}
```

## <a name="pointer"></a>  Wektor\<bool >:: wskaźnika

Typ opisujący obiekt, który może służyć jako wskaźnik do elementu Boolean sekwencji zawartej w `vector<bool>` obiektu.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>  Wektor\<bool >:: reference — klasa

`vector<bool>::reference` Klasa jest klasą proxy dostarczoną przez [wektor\<bool > klasa](../standard-library/vector-bool-class.md) do symulacji `bool&`.

### <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>` używa tylko jednego bitu na element, który można odwoływać się za pomocą tej klasy proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład ponieważ adres `vector<bool>::reference` obiektu nie może być przyjęty, następujący kod, który używa [wektor\<bool >:: operator&#91; &#93; ](#op_at) jest nieprawidłowy:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>  Wektor\<bool >:: reference::flip

Odwraca wartość logiczną odnośnego [wektor\<bool >](../standard-library/vector-bool-class.md) elementu.

```cpp
void flip();
```

#### <a name="example"></a>Przykład

```cpp
// vector_bool_ref_flip.cpp
// compile with: /EHsc /W4
#include <vector>
#include <iostream>

int main()
{
    using namespace std;
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    cout << "The vector is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;

    vector<bool>::reference vbref = vb.front();
    vbref.flip();

    cout << "The vector with first element flipped is: " << endl << "    ";
    for (const auto& b : vb) {
        cout << b << " ";
    }
    cout << endl;
}
```

```Output
The vector is:
    true false false true true
The vector with first element flipped is:
    false false false true true
```

###  <a name="reference_operator_bool"></a>  Wektor\<bool >:: reference::operator bool

Dostarcza niejawną konwersję z `vector<bool>::reference` do **bool**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna elementu wektora\<bool > obiektu.

#### <a name="remarks"></a>Uwagi

`vector<bool>` Ten operator nie można zmodyfikować obiektu.

###  <a name="reference_operator_eq"></a>  Wektor\<bool >:: reference::operator =

Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

*po prawej stronie*<br/>
Odwołanie elementu, którego wartość ma być przypisana do bitu.

*Val*<br/>
Wartość logiczna, który ma być przypisana do bitu.

#### <a name="example"></a>Przykład

```cpp
// vector_bool_ref_op_assign.cpp
// compile with: /EHsc
#include <vector>
#include <iostream>
#include <string>

using namespace std;

template <typename C> void print(const string& s, const C& c) {
    cout << s;

    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

int main()
{
    cout << boolalpha;

    vector<bool> vb = { true, false, false, true, true };

    print("The vector is: ", vb);

    // Invoke vector<bool>::reference::operator=()
    vector<bool>::reference refelem1 = vb[0];
    vector<bool>::reference refelem2 = vb[1];
    vector<bool>::reference refelem3 = vb[2];

    bool b1 = refelem1;
    bool b2 = refelem2;
    bool b3 = refelem3;
    cout << "The original value of the 1st element stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element stored in a bool: " << b3 << endl;
    cout << endl;

    refelem2 = refelem1;

    print("The vector after assigning refelem1 to refelem2 is now: ", vb);

    refelem3 = true;

    print("The vector after assigning false to refelem1 is now: ", vb);

    // The initial values are still stored in the bool variables and remained unchanged
    cout << "The original value of the 1st element still stored in a bool: " << b1 << endl;
    cout << "The original value of the 2nd element still stored in a bool: " << b2 << endl;
    cout << "The original value of the 3rd element still stored in a bool: " << b3 << endl;
    cout << endl;
}
```

```Output
The vector is: true false false true true
The original value of the 1st element stored in a bool: true
The original value of the 2nd element stored in a bool: false
The original value of the 3rd element stored in a bool: false

The vector after assigning refelem1 to refelem2 is now: true true false true true
The vector after assigning false to refelem1 is now: true true true true true
The original value of the 1st element still stored in a bool: true
The original value of the 2nd element still stored in a bool: false
The original value of the 3rd element still stored in a bool: false
```

## <a name="swap"></a>  Wektor\<bool >:: swap

Funkcja statycznej składowej, która wymienia dwa elementy wektorów typu Boolean ( `vector<bool>`) za pomocą klasy proxy [wektor\<bool >:: odwołanie](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

*po lewej stronie*<br/>
Element wymieniane z *po prawej stronie* elementu.

*po prawej stronie*<br/>
Element wymieniane z *po lewej stronie* elementu.

### <a name="remarks"></a>Uwagi

To przeciążenie obsługuje wymagania specjalne proxy `vector<bool>`. [Wektor](../standard-library/vector-class.md):: swap ma taką samą funkcjonalność jak przeciążenie jednego argumentu `vector<bool>::swap()`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
