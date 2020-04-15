---
title: Platforma::Kolekcje::Klasa BackInsertIterator
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: fcb680c8f43a50801d081762bb5b546cb110c52d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354769"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platforma::Kolekcje::Klasa BackInsertIterator

Reprezentuje iteratora, który wstawia, a nie zastępuje, elementy do tylnej części kolekcji sekwencyjnej.

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
|[BackInsertiterator::BackInsertiterator](#ctor)|Inicjuje nowe wystąpienie klasy BackInsertIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[BackInsertIterator::operator* Operator](#operator-dereference)|Pobiera odwołanie do bieżącego backInsertIterator.|
|[BackInsertIterator::operator++ Operator](#operator-increment)|Zwraca odwołanie do bieżącego backInsertIterator. Iterator jest niezmodyfikowany.|
|[BackInsertIterator::operator= Operator](#operator-assign)|Dołącza określony obiekt na końcu bieżącej kolekcji sekwencyjnej.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BackInsertIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="backinsertiteratorbackinsertiterator-constructor"></a><a name="ctor"></a>BackInsertiterator::Konstruktor zaplecza

Inicjuje nowe wystąpienie klasy `BackInsertIterator`.

## <a name="syntax"></a>Składnia

```
explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*v*<br/>
Obiekt> IVector\<T.

### <a name="remarks"></a>Uwagi

A `BackInsertIterator` wstawia elementy po ostatnim elemencie obiektu określonego przez parametr `v`.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-assign"></a>BackInsertIterator::operator= Operator

Dołącza określony obiekt na końcu bieżącej kolekcji sekwencyjnej.

## <a name="syntax"></a>Składnia

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parametry

*t*<br/>
Obiekt do dołączona do bieżącej kolekcji.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego backInsertIterator.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-dereference"></a>BackInsertIterator::operator* Operator

Pobiera odwołanie do bieżącego backInsertIterator.

## <a name="syntax"></a>Składnia

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego backInsertIterator.

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do bieżącego backInsertIterator; nie do żadnego elementu w bieżącej kolekcji.

## <a name="backinsertiteratoroperator-operator"></a><a name="operator-increment"></a>BackInsertIterator::operator++ Operator

Zwraca odwołanie do bieżącego backInsertIterator. Iterator jest niezmodyfikowany.

## <a name="syntax"></a>Składnia

```
BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego backInsertIterator.

### <a name="remarks"></a>Uwagi

Zgodnie z projektem pierwszy przykład składni wstępnie zwiększa bieżący program BackInsertIterator, a druga składnia zwiększa bieżący program BackInsertIterator. Typ `int` w drugiej składni wskazuje operację przyrostową, a nie rzeczywisty argument całkowity.

Jednak ten operator faktycznie nie modyfikuje BackInsertIterator. Zamiast tego operator zwraca odwołanie do niezmodyfikowanego, bieżącego iteratora. Jest to takie samo zachowanie jak [operator*](#operator-dereference).

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)
