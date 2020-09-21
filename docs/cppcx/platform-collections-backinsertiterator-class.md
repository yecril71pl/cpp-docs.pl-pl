---
title: 'Platform:: Collections:: BackInsertIterator, Klasa'
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: f5c82a776a537d469d42a16bd4f425e7bb2c13aa
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742934"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform:: Collections:: BackInsertIterator, Klasa

Reprezentuje iterator, który wstawia zamiast nadpisać elementy do zaplecza kolekcji sekwencyjnej.

## <a name="syntax"></a>Składnia

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementu w bieżącej kolekcji.

### <a name="remarks"></a>Uwagi

Klasa BackInsertIterator implementuje reguły wymagane przez [klasę back_insert_iterator](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicjuje nowe wystąpienie klasy BackInsertIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[BackInsertIterator:: operator * — operator](#operator-dereference)|Pobiera odwołanie do bieżącego BackInsertIterator.|
|[Operator BackInsertIterator:: operator + +](#operator-increment)|Zwraca odwołanie do bieżącego BackInsertIterator. Iterator nie jest modyfikowany.|
|[BackInsertIterator:: operator = — operator](#operator-assign)|Dołącza określony obiekt do końca bieżącej kolekcji sekwencyjnej.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BackInsertIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** Collection. h

**Przestrzeń nazw:** Platform:: Collections

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a> BackInsertIterator:: BackInsertIterator — Konstruktor

Inicjuje nowe wystąpienie klasy `BackInsertIterator`.

### <a name="syntax"></a>Składnia

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*v*<br/>
Obiekt IVector \<T> .

### <a name="remarks"></a>Uwagi

`BackInsertIterator`Wstawia elementy po ostatnim elemencie obiektu określonego przez parametr `v` .

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a> BackInsertIterator:: operator = — operator

Dołącza określony obiekt do końca bieżącej kolekcji sekwencyjnej.

### <a name="syntax"></a>Składnia

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parametry

*&*<br/>
Obiekt do dołączenia do bieżącej kolekcji.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego BackInsertIterator.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a> BackInsertIterator:: operator * — operator

Pobiera odwołanie do bieżącego BackInsertIterator.

### <a name="syntax"></a>Składnia

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego BackInsertIterator.

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do bieżącego BackInsertIterator; nie do żadnego elementu w bieżącej kolekcji.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a> Operator BackInsertIterator:: operator + +

Zwraca odwołanie do bieżącego BackInsertIterator. Iterator nie jest modyfikowany.

### <a name="syntax"></a>Składnia

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego BackInsertIterator.

### <a name="remarks"></a>Uwagi

Zgodnie z projektem pierwsza Przykładowa składnia umożliwia wstępne zwiększenie bieżącej BackInsertIterator, a druga — zwiększa bieżącą BackInsertIterator. **`int`** Typ w drugiej składni wskazuje operację po przyrostie, a nie rzeczywisty argument operacji całkowitej.

Jednak ten operator nie modyfikuje BackInsertIterator. Zamiast tego, ten operator zwraca odwołanie do niemodyfikowanego, bieżącego iteratora. Jest to takie samo zachowanie jak [operator *](#operator-dereference).

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](platform-namespace-c-cx.md)
