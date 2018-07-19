---
title: '&lt;Wektor&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <vector>
dev_langs:
- C++
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e49fcc87c4c074494164a085e01581077bbfe118
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38953865"
---
# <a name="ltvectorgt"></a>&lt;Wektor&gt;

Definiuje wektor klasy szablonu kontenera i kilka szablonów pomocniczych.

`vector` Jest kontenerem, który służy do organizowania elementów danego typu w liniowej sekwencji. Umożliwia szybkiego losowego dostęp do dowolnego elementu i dynamiczne dodań i usunięć wpisów do i z sekwencji. `vector` Jest preferowanym kontenerem dla sekwencji, gdy wydajność dostępu swobodnego znajduje się w warstwie premium.

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

*Typ*  
 Parametr szablonu dla typu danych przechowywanych w wektorze.

*Allocator*  
 Parametr szablonu, aby uzyskać przechowywany obiekt alokatora odpowiedzialny za alokacji i dezalokacji pamięci.

*left*  
 Pierwszego wektora (po lewej stronie) w ramach operacji porównania

*right*  
 Drugi wektor (po prawej) w ramach operacji porównania.

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|Sprawdza, czy obiekt wektora po lewej stronie operatora nie jest równy obiektowi wektora po prawej stronie.|
|[Operator <](../standard-library/vector-operators.md#op_lt)|Sprawdza, czy obiektu wektora po lewej stronie operatora jest mniejszy niż obiekt wektora po prawej stronie.|
|[Operator\<=](../standard-library/vector-operators.md#op_gt_eq)|Sprawdza, czy wektora obiektu po lewej stronie operatora jest mniejszy niż lub równy obiektowi wektora po prawej stronie.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Sprawdza, czy obiekt wektora po lewej stronie operatora jest równy obiektowi wektora po prawej stronie.|
|[operator>](../standard-library/vector-operators.md#op_gt)|Sprawdza, czy obiekt wektora, po lewej stronie operatora jest większy niż obiektu wektora po prawej stronie.|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Sprawdza, czy obiekt wektora po lewej stronie operatora jest większy lub równy obiektowi wektora po prawej stronie.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[vector, klasa](../standard-library/vector-class.md)|Klasa szablonu kontenerów sekwencji, które Rozmieść elementy danego typu w układzie liniowych i zezwolić na dostęp szybkiego losowego do dowolnego elementu.|

### <a name="specializations"></a>Specjalizacje

|||
|-|-|
|[Wektor\<bool > klasa](../standard-library/vector-bool-class.md)|Pełne specjalizacji wektora klasy szablonu dla elementów typu `bool` z alokator dla podstawowego typu, które są używane przez specjalizację.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<wektor >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Dokumentacja standardowej biblioteki C++](../standard-library/cpp-standard-library-reference.md)<br/>
