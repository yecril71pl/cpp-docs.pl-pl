---
title: '&lt;niemożliwe&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 7cecff1e5e0014c4f1a4294a5c6ba25c5d38da67
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88840014"
---
# <a name="ltvectorgt"></a>&lt;niemożliwe&gt;

Definiuje wektor szablonu klasy kontenera i kilka szablonów pomocniczych.

`vector`Jest kontenerem, który organizuje elementy danego typu w sekwencji liniowej. Umożliwia szybki dostęp losowy do dowolnego elementu, a także dynamiczne dodawanie i usuwanie do i z sekwencji. `vector`Jest to preferowany kontener dla sekwencji, gdy wydajność dostępu swobodnego jest w warstwie Premium.

> [!NOTE]
> \<vector>Biblioteka używa również `#include <initializer_list>` instrukcji.

Aby uzyskać więcej informacji na temat klasy `vector` , zobacz [Vector Class](../standard-library/vector-class.md). Aby uzyskać informacje o specjalizacji `vector<bool>` , zobacz [Vector \<bool> class](../standard-library/vector-bool-class.md).

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

*Wprowadź*\
Parametr szablonu dotyczący typu danych przechowywanych w wektorze.

*Alokator*\
Parametr szablonu dla przechowywanego obiektu alokatora odpowiedzialnego za alokację i cofanie alokacji pamięci.

*lewym*\
Pierwszy (lewy) wektor w operacji porównania

*Kliknij*\
Drugi (prawy) wektor w operacji porównania.

## <a name="members"></a>Elementy członkowskie

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[zakład! =](../standard-library/vector-operators.md#op_neq)|Testuje, czy obiekt Vector po lewej stronie operatora nie jest równy obiektowi wektora po prawej stronie.|
|[<operatora ](../standard-library/vector-operators.md#op_lt)|Testuje, czy obiekt Vector po lewej stronie operatora jest mniejszy niż obiekt wektora po prawej stronie.|
|[zakład\<=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, czy obiekt Vector po lewej stronie operatora jest mniejszy niż lub równy obiektowi wektora po prawej stronie.|
|[operator = =](../standard-library/vector-operators.md#op_eq_eq)|Testuje, czy obiekt Vector po lewej stronie operatora jest równy obiektowi wektora po prawej stronie.|
|[>operatora ](../standard-library/vector-operators.md#op_gt)|Testuje, czy obiekt Vector po lewej stronie operatora jest większy niż obiekt wektora po prawej stronie.|
|[>operatora =](../standard-library/vector-operators.md#op_gt_eq)|Testuje, czy obiekt Vector po lewej stronie operatora jest większy niż lub równy obiektowi wektora po prawej stronie.|

### <a name="classes"></a>Klasy

|Nazwa|Opis|
|-|-|
|[Vector — Klasa](../standard-library/vector-class.md)|Szablon klasy kontenerów sekwencji, który rozmieszcza elementy danego typu w rozmieszczeniu liniowym i umożliwia szybki dostęp losowy do dowolnego elementu.|

### <a name="specializations"></a>Specjalizacje

|Nazwa|Opis|
|-|-|
|hash|Zwraca wartość skrótu wektora.|
|[Vector — \<bool> Klasa](../standard-library/vector-bool-class.md)|Pełna specjalizacja wektora szablonu klasy dla elementów typu **`bool`** z alokatorem dla typu podstawowego używanego przez specjalizację.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<vector>

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md)
