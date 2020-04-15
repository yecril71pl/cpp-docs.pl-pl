---
title: klasa bool&lt;&gt; wektora
ms.date: 11/04/2016
f1_keywords:
- vector<bool>
- vector/std::vector::flip
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
ms.openlocfilehash: 6c67e3d9ba1b33cb99a7d3afb2522f443003fa38
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376085"
---
# <a name="vectorltboolgt-class"></a>klasa bool&lt;&gt; wektora

Klasa `vector<bool>` jest częściową specjalizacją [wektora](../standard-library/vector-class.md) dla elementów typu **bool**. Ma alokator dla typu źródłowego, który jest używany przez specjalizację, która zapewnia optymalizację przestrzeni przez przechowywanie jednej wartości **bool** na bit.

## <a name="syntax"></a>Składnia

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Uwagi

Ta specjalizacja szablonu klasy zachowuje się jak wektor, z wyjątkiem różnic wyjaśnionych w tym artykule.

Operacje, które dotyczą typu **bool** odpowiadają wartościom w magazynie kontenerów. `allocator_traits::construct`nie jest używany do konstruowania tych wartości.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Typedef do `const_iterator` a, który może służyć jako stały wskaźnik `vector<bool>`do elementu logicznego .|
|[const_reference](#const_reference)|Typedef dla **bool**. Po zainicjowaniu nie zwraca uwagi na aktualizacje do wartości pierwotnej.|
|[pointer](#pointer)|Typedef `iterator` do, który może służyć jako wskaźnik do `vector<bool>`elementu logicznego .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Flip](#flip)|Odwraca wszystkie bity `vector<bool>`w pliku .|
|[Wymiany](#swap)|Wymienia elementy dwóch `vector<bool>`s.|
|[&#91;&#93;operatora](#op_at)|Zwraca symulowane odwołanie `vector<bool>` do elementu w określonym położeniu.|
|`at`|Funkcje takie same jak [wektor](../standard-library/vector-class.md)bezspecjalizowany ::at function, z tą różnicą, że używa klasy proxy [\<bool wektora>::reference](#reference_class). Zobacz też [&#91;&#93;operatora ](#op_at).|
|`front`|Funkcje takie same jak niespecjalizowany [wektor](../standard-library/vector-class.md)::front, z tą różnicą, że używa klasy proxy [\<bool wektora>::reference](#reference_class). Zobacz też [&#91;&#93;operatora ](#op_at).|
|`back`|Funkcje takie same jak niespecjalizowany [wektor](../standard-library/vector-class.md)::back funkcja, z tą różnicą, że używa [\<klasy proxy bool wektora>::reference](#reference_class). Zobacz też [&#91;&#93;operatora ](#op_at).|

### <a name="proxy-class"></a>Klasa proxy

|||
|-|-|
|[klasa referencyjna bool> wektora\<](#reference_class)|Klasa, która działa jako serwer `bool&` proxy do symulowania zachowania i których obiekty mogą `vector<bool>` dostarczać odwołania do elementów (pojedyncze bity) w obiekcie.|

## <a name="requirements"></a>Wymagania

**Nagłówek** \<: wektor>

**Przestrzeń nazw:** std

## <a name="vectorboolconst_pointer"></a><a name="const_pointer"></a>bool\<wektorowy>::const_pointer

Typ opisujący obiekt, który może służyć jako stały wskaźnik do elementu logicznego sekwencji zawartej `vector<bool>` w obiekcie.

```cpp
typedef const_iterator const_pointer;
```

## <a name="vectorboolconst_reference"></a><a name="const_reference"></a>bool\<wektorowy>::const_reference

Typ, który opisuje obiekt, który może służyć jako stałe odwołanie do elementu `vector<bool>` logicznego sekwencji zawartej w obiekcie.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji i przykłady kodu, zobacz [&lt;wektor bool&gt;::reference::operator=](#reference_operator_eq).

## <a name="vectorboolflip"></a><a name="flip"></a>bool\<wektorowy>::flip

Odwraca wszystkie bity `vector<bool>`w pliku .

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

## <a name="vectorbooloperator"></a><a name="op_at"></a>bool\<wektorowy>::operator[]

Zwraca symulowane odwołanie `vector<bool>` do elementu w określonym położeniu.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|*Poz*|Położenie `vector<bool>` elementu.|

### <a name="return-value"></a>Wartość zwracana

[Wektor\<bool>::reference](#reference_class) lub [wektorowy\<bool>::const_reference](#const_reference) obiekt, który zawiera wartość elementu indeksowanego.

Jeśli określona pozycja jest większa niż lub równa rozmiarowi kontenera, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli kompilujesz z _ITERATOR_DEBUG_LEVEL zestawem, błąd w czasie wykonywania występuje, jeśli spróbujesz uzyskać dostęp do elementu poza granicami wektora.  Aby uzyskać więcej informacji, zobacz [Sprawdzanie iteratorów](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W tym przykładzie kodu `vector<bool>::operator[]` pokazano prawidłowe użycie i dwa typowe błędy kodowania, które są komentowane. Te błędy powodują błędy, ponieważ `vector<bool>::reference` nie `vector<bool>::operator[]` można wziąć adresu obiektu, który zwraca.

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

## <a name="vectorboolpointer"></a><a name="pointer"></a>bool\<wektorowy>::pointer

Typ, który opisuje obiekt, który może służyć jako wskaźnik do elementu `vector<bool>` logicznego sekwencji zawartej w obiekcie.

```cpp
typedef iterator pointer;
```

## <a name="vectorboolreference-class"></a><a name="reference_class"></a>wektor\<bool>::klasa referencyjna

Klasa `vector<bool>::reference` jest klasą proxy dostarczaną przez [klasę wektora\<bool>](../standard-library/vector-bool-class.md) do symulacji `bool&`.

### <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>`używa tylko jednego bitu na element, do którego można się odwoływać przy użyciu tej klasy proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład, ponieważ nie `vector<bool>::reference` można podjąć adresu obiektu, następujący kod, który używa [wektora\<bool>::operator&#91;&#93;](#op_at) nie jest poprawna:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

### <a name="vectorboolreferenceflip"></a><a name="reference_flip"></a>bool\<wektorowy>::reference::flip

Odwraca wartość logiczną elementu [wektorowego,\<](../standard-library/vector-bool-class.md) do którego istnieje odwołanie, bool>.

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

### <a name="vectorboolreferenceoperator-bool"></a><a name="reference_operator_bool"></a>wektor\<bool>::reference::operator bool

Zapewnia niejawną `vector<bool>::reference` konwersję z **bool**.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna elementu wektorowego\<bool> obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt `vector<bool>` nie może być modyfikowany przez tego operatora.

### <a name="vectorboolreferenceoperator"></a><a name="reference_operator_eq"></a>bool\<wektorowy>::reference::operator=

Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie elementu, którego wartość ma być przypisana do bitu.

*Val*\
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

## <a name="vectorboolswap"></a><a name="swap"></a>wektor\<bool>::swap

Funkcja statycznego elementu członkowskiego, która wymienia dwa `vector<bool>`elementy wektorów logicznych ( ) przy użyciu klasy proxy [\<bool wektora>::reference](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

*Lewej*\
Element, który ma być wymieniany z *prawym* elementem.

*Prawo*\
Element, który ma być wymieniany z *elementem Left.*

### <a name="remarks"></a>Uwagi

To przeciążenie obsługuje specjalne `vector<bool>`wymagania proxy . [vector](../standard-library/vector-class.md)::swap ma taką samą funkcjonalność jak `vector<bool>::swap()`przeciążenie pojedynczego argumentu .

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Odwołanie do standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
