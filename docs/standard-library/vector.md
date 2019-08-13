---
title: '&lt;niemożliwe&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 59424a9f6a9434b5d7d3f4298cbb0bc03926621c
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957063"
---
# <a name="ltvectorgt"></a>&lt;niemożliwe&gt;

Definiuje wektor klasy szablonu kontenera i kilka szablonów pomocniczych.

`vector` Jest kontenerem, który organizuje elementy danego typu w sekwencji liniowej. Umożliwia szybki dostęp losowy do dowolnego elementu, a także dynamiczne dodawanie i usuwanie do i z sekwencji. Jest `vector` to preferowany kontener dla sekwencji, gdy wydajność dostępu swobodnego jest w warstwie Premium.

> [!NOTE]
> Biblioteka wektora > również `#include <initializer_list>` używa instrukcji. \<

Aby uzyskać więcej informacji na temat `vector`klasy, zobacz [Vector class](../standard-library/vector-class.md). Aby uzyskać informacje o specjalizacji `vector<bool>`, zobacz [Vector\<bool > Class](../standard-library/vector-bool-class.md).

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

|||
|-|-|
|[zakład! =](../standard-library/vector-operators.md#op_neq)|Testuje, czy obiekt Vector po lewej stronie operatora nie jest równy obiektowi wektora po prawej stronie.|
|[< operatora](../standard-library/vector-operators.md#op_lt)|Testuje, czy obiekt Vector po lewej stronie operatora jest mniejszy niż obiekt wektora po prawej stronie.|
|[zakład\<=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, czy obiekt Vector po lewej stronie operatora jest mniejszy niż lub równy obiektowi wektora po prawej stronie.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Testuje, czy obiekt Vector po lewej stronie operatora jest równy obiektowi wektora po prawej stronie.|
|[operator>](../standard-library/vector-operators.md#op_gt)|Testuje, czy obiekt Vector po lewej stronie operatora jest większy niż obiekt wektora po prawej stronie.|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Testuje, czy obiekt Vector po lewej stronie operatora jest większy niż lub równy obiektowi wektora po prawej stronie.|

### <a name="classes"></a>Klasy

|||
|-|-|
|[vector, klasa](../standard-library/vector-class.md)|Klasa szablonu kontenerów sekwencji, które układają elementy danego typu w rozmieszczeniu liniowym i umożliwiają szybki dostęp losowy do dowolnego elementu.|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|hash|Zwraca wartość skrótu wektora.|
|[Klasa\<bool > Vector](../standard-library/vector-bool-class.md)|Pełna specjalizacja klasy szablonu wektora dla elementów typu `bool` z alokatorem dla typu podstawowego używanego przez specjalizację.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<> wektora

**Przestrzeń nazw:** std

## <a name="see-also"></a>Zobacz także

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)
