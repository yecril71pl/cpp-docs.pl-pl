---
title: Vector&lt;—&gt; Klasa logiczna
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
ms.openlocfilehash: d4ae53f9a14f04d5656a13c32e75494688c5cdd0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68452269"
---
# <a name="vectorltboolgt-class"></a>Vector&lt;—&gt; Klasa logiczna

Klasa jest częściową specjalizacją wektora dla elementów typu **bool**. [](../standard-library/vector-class.md) `vector<bool>` Ma Alokator dla typu podstawowego, który jest używany przez specjalizację, która zapewnia optymalizację przestrzeni przez przechowywanie jednej wartości **logicznej** na bit.

## <a name="syntax"></a>Składnia

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Uwagi

Ta specjalizacja szablonu klasy zachowuje się jak wektor, z wyjątkiem różnic wyjaśnionych w tym artykule.

Operacje, które zajmują się typem **bool** , odpowiadają wartościom w magazynie kontenerów. `allocator_traits::construct`nie jest używany do konstruowania tych wartości.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Element typedef do `const_iterator` obiektu, który może być używany jako stały wskaźnik do elementu `vector<bool>`typu Boolean.|
|[const_reference](#const_reference)|Element typedef dla elementu **bool**. Po zainicjowaniu nie zwraca uwagi na aktualizacje do wartości pierwotnej.|
|[pointer](#pointer)|Element typedef do obiektu `iterator` , który może być używany jako wskaźnik do elementu `vector<bool>`typu Boolean.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[stosowane](#flip)|Odwraca wszystkie bity w `vector<bool>`.|
|[swap](#swap)|Wymienia elementy dwóch `vector<bool>`s.|
|[operator&#91;&#93;](#op_at)|Zwraca symulowane odwołanie do `vector<bool>` elementu w określonej pozycji.|
|`at`|Działa tak samo, jak Niewyspecjalizowany [wektor](../standard-library/vector-class.md):: at, z tą różnicą, że używa klasy [proxy\<Vector bool >:: Reference](#reference_class). Zobacz również [operator&#91;](#op_at).|
|`front`|Działa tak samo jak Niewyspecjalizowana funkcja [Vector](../standard-library/vector-class.md):: Front, z tą różnicą, że używa klasy [proxy\<Vector bool >:: Reference](#reference_class). Zobacz również [operator&#91;](#op_at).|
|`back`|Działa tak samo jak Niewyspecjalizowana funkcja [Vector](../standard-library/vector-class.md):: Back, z tą różnicą, że używa klasy [proxy\<Vector bool >:: Reference](#reference_class). Zobacz również [operator&#91;](#op_at).|

### <a name="proxy-class"></a>Klasa proxy

|||
|-|-|
|[Klasa\<referencyjna bool > Vector](#reference_class)|Klasa, która działa jako serwer proxy w celu symulowania `bool&` zachowania i którego obiekty mogą udostępniać odwołania do elementów (pojedynczych bitów) `vector<bool>` w obrębie obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<wektor >

**Przestrzeń nazw:** std

## <a name="const_pointer"></a>>\<bool wektora:: const_pointer

Typ opisujący obiekt, który może obsłużyć jako stały wskaźnik do elementu typu Boolean sekwencji zawartej `vector<bool>` w obiekcie.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>>\<bool wektora:: const_reference

Typ opisujący obiekt, który może obsłużyć jako stałe odwołanie do elementu typu Boolean sekwencji zawartej `vector<bool>` w obiekcie.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i przykładów kodu, [Zobacz&lt;Vector&gt;bool:: Reference:: operator =](#reference_operator_eq).

## <a name="flip"></a>bool\<Vector >:: flip

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

## <a name="op_at"></a>bool\<Vector >:: operator []

Zwraca symulowane odwołanie do `vector<bool>` elementu w określonej pozycji.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Terminal*|Pozycja `vector<bool>` elementu.|

### <a name="return-value"></a>Wartość zwracana

[Bool Vector\<>:: Reference](#reference_class) lub [Vector\<bool >:: const_reference](#const_reference) Object, który zawiera wartość indeksowanego elementu.

Jeśli określona pozycja jest większa niż lub równa rozmiarowi kontenera, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli kompilujesz za pomocą zestawu _ITERATOR_DEBUG_LEVEL, wystąpi błąd czasu wykonywania, jeśli spróbujesz uzyskać dostęp do elementu poza granicami wektora.  Aby uzyskać więcej informacji, zobacz [sprawdzone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

Ten przykład kodu pokazuje poprawne użycie `vector<bool>::operator[]` i dwa typowe błędy kodowania, które są oznaczone jako komentarz. Takie błędy powodują błędy, ponieważ adres `vector<bool>::reference` obiektu, który `vector<bool>::operator[]` zwraca nie może zostać pobrany.

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

## <a name="pointer"></a>>\<bool wektora::p ointer

Typ opisujący obiekt, który może obsłużyć jako wskaźnik do elementu typu Boolean sekwencji zawartej `vector<bool>` w obiekcie.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>Vector\<bool >:: Reference — Klasa

Klasa jest klasą proxy dostarczoną przez `bool&` [klasę >\<bool wektorowego](../standard-library/vector-bool-class.md) do symulowania. `vector<bool>::reference`

### <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>`wykorzystuje tylko jeden bit na element, do którego można odwoływać się za pomocą tej klasy proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład, ponieważ nie można wykonać adresu `vector<bool>::reference` obiektu, następujący kod używający [bool Vector\<>:: operator&#91; ](#op_at) jest niepoprawny:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>bool\<Vector >:: Reference:: flip

Odwraca wartość logiczną elementu [> bool wektora\<](../standard-library/vector-bool-class.md) , do którego istnieje odwołanie.

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

###  <a name="reference_operator_bool"></a>bool\<Vector >:: Reference:: operator bool

Zapewnia niejawną konwersję z `vector<bool>::reference` na wartość **logiczną**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna elementu obiektu logicznego > wektora\<.

#### <a name="remarks"></a>Uwagi

Ten operator nie może modyfikować obiektu.`vector<bool>`

###  <a name="reference_operator_eq"></a>bool\<Vector >:: Reference:: operator =

Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie elementu, którego wartość ma być przypisana do bitu.

*Użyte*\
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

## <a name="swap"></a>bool\<Vector >:: swap

Statyczna funkcja członkowska, która wymienia dwa elementy wektorów `vector<bool>`logicznych () przy użyciu wektora [\<klasy proxy bool >:: Reference](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

*Lewym*\
Element, który ma być wymieniany z *prawidłowym* elementem.

*Kliknij*\
Element, który ma być wymieniany z *lewej strony* .

### <a name="remarks"></a>Uwagi

To Przeciążenie obsługuje specjalne wymagania serwera proxy programu `vector<bool>`. [Vector](../standard-library/vector-class.md):: swap ma takie same funkcje jak przeciążenia `vector<bool>::swap()`jednego argumentu.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
