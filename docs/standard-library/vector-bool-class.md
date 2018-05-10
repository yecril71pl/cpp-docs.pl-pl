---
title: Wektor&lt;bool&gt; klasy | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- vector<bool>
- vector/std::vector::const_pointer
- vector/std::vector::const_reference
- vector/std::vector::pointer
- vector/std::vector::flip
- vector/std::vector::swap
dev_langs:
- C++
helpviewer_keywords:
- std::vector [C++], const_pointer
- std::vector [C++], const_reference
- std::vector [C++], pointer
- std::vector [C++], flip
- std::vector [C++], swap
ms.assetid: 8028c8ed-ac9c-4f06-aba1-5de45c00aafb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ab7f4e185f19b07ddcec47b8f167e7040a5bef28
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="vectorltboolgt-class"></a>Wektor&lt;bool&gt; — klasa

`vector<bool>` Klasy jest częściowa specjalizacja [wektor](../standard-library/vector-class.md) dla elementów typu `bool`. Ma ona alokatora dla typu podstawowego, który jest używany przez specjalizacji, co zapewnia optymalizacji miejsca dzięki przechowywaniu jedną `bool` wartość w każdej z bitowego.

## <a name="syntax"></a>Składnia

```cpp
template <class Allocator = allocator<bool>>
class vector<bool, Allocator>
```

## <a name="remarks"></a>Uwagi

Ta klasa specjalizacja szablonu zachowuje się jak wektora, z wyjątkiem różnice opisane w tym artykule.

Operacje, które zajmują się `bool` typu odpowiadają wartościom w magazynie kontenera. `allocator_traits::construct` nie jest używany do tworzenia tych wartości.

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[const_pointer](#const_pointer)|Element typedef do `const_iterator` który może służyć jako stałej wskaźnika do elementu logiczna `vector<bool>`.|
|[const_reference](#const_reference)|Element typedef dla `bool`. Po zainicjowaniu nie zwraca uwagi na aktualizacje do wartości pierwotnej.|
|[pointer](#pointer)|Element typedef do `iterator` który może służyć jako wskaźnik do elementu Boolean elementu `vector<bool>`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Przerzuć](#flip)|Odwraca wszystkie bity w `vector<bool>`.|
|[swap](#swap)|Zamienia elementy dwóch `vector<bool>`s.|
|[operator&#91;&#93;](#op_at)|Zwraca symulowane odwołanie do `vector<bool>` elementu w określonej pozycji.|
|`at`|Odpowiada to klasy niespecjalizowanej [wektor](../standard-library/vector-class.md):: w funkcji, z wyjątkiem, że używa klasy serwera proxy [wektor\<bool >:: odwołanie](#reference_class). Zobacz też [operator&#91;&#93;](#op_at).|
|`front`|Odpowiada to klasy niespecjalizowanej [wektor](../standard-library/vector-class.md):: FrontPage funkcji, z wyjątkiem tego, że używa klasy serwera proxy [wektor\<bool >:: odwołanie](#reference_class). Zobacz też [operator&#91;&#93;](#op_at).|
|`back`|Odpowiada to klasy niespecjalizowanej [wektor](../standard-library/vector-class.md):: kopii funkcji, z wyjątkiem tego, że używa klasy serwera proxy [wektor\<bool >:: odwołanie](#reference_class). Zobacz też [operator&#91;&#93;](#op_at).|

### <a name="proxy-class"></a>Klasa proxy

|||
|-|-|
|[Wektor\<bool > klasę referencyjną](#reference_class)|Klasa, która działa jako serwer proxy, aby symulować `bool&` zachowanie i których obiekty zapewniają odwołania do elementów (pojedynczy bits) w ramach `vector<bool>` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek**: \<wektor >

**Namespace:** Standard

## <a name="const_pointer"></a>  Wektor\<bool >:: const_pointer

Typ, który opisuje obiekt, który może służyć jako stałej wskaźnika do elementu logiczna sekwencji zawarty w `vector<bool>` obiektu.

```cpp
typedef const_iterator const_pointer;
```

## <a name="const_reference"></a>  Wektor\<bool >:: const_reference

Typ, który opisuje obiekt, który może służyć jako odwołanie stałej dla elementu logiczna sekwencji zawarty w `vector<bool>` obiektu.

```cpp
typedef bool const_reference;
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji oraz przykłady kodu, zobacz [wektor&lt;bool&gt;:: reference::operator =](#reference_operator_eq).

## <a name="flip"></a>  Wektor\<bool >:: Przerzuć

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

## <a name="op_at"></a>  Wektor\<bool >:: — operator]

Zwraca symulowane odwołanie do `vector<bool>` elementu w określonej pozycji.

```cpp
vector<bool>::reference operator[](size_type Pos);

vector&<bool&>::const_reference operator[](size_type Pos) const;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|-|-|
|`Pos`|Pozycja `vector<bool>` elementu.|

### <a name="return-value"></a>Wartość zwracana

A [wektor\<bool >:: odwołanie](#reference_class) lub [wektor\<bool >:: const_reference](#const_reference) obiekt, który zawiera wartość indeksowanego elementu.

Jeśli określona pozycja jest większa niż lub równa rozmiarowi kontenera, wynik jest niezdefiniowany.

### <a name="remarks"></a>Uwagi

Jeśli kompilacji z `_ITERATOR_DEBUG_LEVEL` ustawiona, błędów czasu wykonywania wystąpi przy próbie uzyskania dostępu do elementu poza granicami wektora.  Aby uzyskać więcej informacji, zobacz [zaznaczone Iteratory](../standard-library/checked-iterators.md).

### <a name="example"></a>Przykład

W tym przykładzie kodu pokazano sposób użycia poprawne `vector<bool>::operator[]` i dwie typowe kody błędów, które są oznaczone jako komentarz. Te błędy powodować błędy, ponieważ adres `vector<bool>::reference` obiekt, który `vector<bool>::operator[]` zwraca nie można wykonywać.

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

Typ, który opisuje obiekt, który może służyć jako wskaźnik do elementu logiczna zawarty w sekwencji `vector<bool>` obiektu.

```cpp
typedef iterator pointer;
```

## <a name="reference_class"></a>  Wektor\<bool >:: klasę referencyjną

`vector<bool>::reference` Klasa jest klasą proxy dostarczonych przez [wektor\<bool > klasy](../standard-library/vector-bool-class.md) do symulowania `bool&`.

### <a name="remarks"></a>Uwagi

Symulowane odwołanie jest wymagane, ponieważ C++ nie zezwala natywnie na bezpośrednie odwołania do bitów. `vector<bool>` używa tylko jeden bit na element, który można odwoływać się za pomocą tej klasy serwera proxy. Jednakże symulacja odwołania nie jest kompletna, ponieważ niektóre przypisania nie są prawidłowe. Na przykład ponieważ adres `vector<bool>::reference` obiektu nie można wykonywać, następujący kod, który używa [wektor\<bool >:: operator&#91; &#93; ](#op_at) jest nieprawidłowy:

```cpp
vector<bool> vb;
//...
bool* pb = &vb[1]; // conversion error - do not use
bool& refb = vb[1];   // conversion error - do not use
```

###  <a name="reference_flip"></a>  Wektor\<bool >:: reference::flip

Odwraca wartość logiczną odwoływany [wektor\<bool >](../standard-library/vector-bool-class.md) elementu.

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

Udostępnia niejawna konwersja z `vector<bool>::reference` do `bool`.

```cpp
operator bool() const;
```

#### <a name="return-value"></a>Wartość zwracana

Wartość logiczna elementu wektora\<bool > obiektu.

#### <a name="remarks"></a>Uwagi

`vector<bool>` Obiektu nie może modyfikować tego operatora.

###  <a name="reference_operator_eq"></a>  Wektor\<bool >:: reference::operator =

Przypisuje do bitu wartość logiczną lub wartość przechowywaną przez odnośny element.

```cpp
reference& operator=(const reference& Right);
reference& operator=(bool Val);
```

### <a name="parameters"></a>Parametry

`Right` Odwołanie do elementu, którego wartość ma być przypisana do bitu.

`Val` Wartość logiczna ma być przypisany do bitu.

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

## <a name="swap"></a>  Wektor\<bool >:: wymiany

Funkcja statycznego elementu członkowskiego, który wymienia dwa elementy wektorów logiczna ( `vector<bool>`) przy użyciu klasy serwera proxy [wektor\<bool >:: odwołanie](#reference_class).

```cpp
static void swap(
    reference Left,
    reference Right);
```

### <a name="parameters"></a>Parametry

`Left` Element wymienianych z `Right` elementu.

`Right` Element wymienianych z `Left` elementu.

### <a name="remarks"></a>Uwagi

To przeciążenie obsługuje proxy specjalne wymagania `vector<bool>`. [Wektor](../standard-library/vector-class.md):: wymiany ma te same funkcje co przeciążenia jednym argumentem `vector<bool>::swap()`.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
