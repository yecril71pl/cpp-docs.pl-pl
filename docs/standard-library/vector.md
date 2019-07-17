---
title: '&lt;Wektor&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 96f329bfdcc13bb557ef0cc487a1f414612e96c5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240963"
---
# <a name="ltvectorgt"></a>&lt;Wektor&gt;

Definiuje wektor klasy szablonu kontenera i kilka szablonów pomocniczych.

`vector` Jest kontenerem, który służy do organizowania elementów danego typu w liniowej sekwencji. Umożliwia szybkiego losowego dostęp do dowolnego elementu i dynamiczne dodań i usunięć wpisów do i z sekwencji. `vector` Jest preferowanym kontenerem dla sekwencji, gdy wydajność dostępu swobodnego znajduje się w warstwie premium.

> [!NOTE]
> \<Wektor > używa również biblioteki `#include <initializer_list>` instrukcji.

Aby uzyskać więcej informacji o klasie `vector`, zobacz [vector, klasa](../standard-library/vector-class.md). Aby uzyskać informacje o specjalizacji `vector<bool>`, zobacz [wektora\<bool > klasa](../standard-library/vector-bool-class.md).

## <a name="syntax"></a>Składnia

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;

// TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Parametry

*Typ*\
Parametr szablonu dla typu danych przechowywanych w wektorze.

*Allocator*\
Parametr szablonu, aby uzyskać przechowywany obiekt alokatora odpowiedzialny za alokacji i dezalokacji pamięci.

*po lewej stronie*\
Pierwszego wektora (po lewej stronie) w ramach operacji porównania

*po prawej stronie*\
Drugi wektor (po prawej) w ramach operacji porównania.

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|Sprawdza, czy obiekt wektora po lewej stronie operatora nie jest równy obiektowi wektora po prawej stronie.|
|[Operator <](../standard-library/vector-operators.md#op_lt)|Sprawdza, czy obiektu wektora po lewej stronie operatora jest mniejszy niż obiekt wektora po prawej stronie.|
|[Operator\<=](../standard-library/vector-operators.md#op_gt_eq)|Sprawdza, czy wektora obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi wektora po prawej stronie.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Sprawdza, czy obiekt wektora po lewej stronie operatora jest równy obiektowi wektora po prawej stronie.|
|[operator>](../standard-library/vector-operators.md#op_gt)|Sprawdza, czy obiekt wektora, po lewej stronie operatora jest większy niż obiektu wektora po prawej stronie.|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Sprawdza, czy obiekt wektora po lewej stronie operatora jest większy lub równy obiektowi wektora po prawej stronie.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[vector, klasa](../standard-library/vector-class.md)|Klasa szablonu kontenerów sekwencji, które Rozmieść elementy danego typu w układzie liniowych i zezwolić na dostęp szybkiego losowego do dowolnego elementu.|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[Skrót]()||
|[Wektor\<bool > klasa](../standard-library/vector-bool-class.md)|Pełne specjalizacji wektora klasy szablonu dla elementów typu `bool` z alokator dla podstawowego typu, które są używane przez specjalizację.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wektor >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
