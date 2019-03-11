---
title: 'Platform::Collections:: backinsertiterator, klasa'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::BackInsertIterator::BackInsertIterator
helpviewer_keywords:
- BackInsertIterator Class
ms.assetid: aecee1ff-100d-4129-b84b-1966f0923dbf
ms.openlocfilehash: 7478555b19bbe5c984fcbe531d2d8be1a0b865a9
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739530"
---
# <a name="platformcollectionsbackinsertiterator-class"></a>Platform::Collections:: backinsertiterator, klasa

Reprezentuje iterator, który wstawia, a nie zastępuje elementy do tylnego końca sekwencyjną kolekcją.

## <a name="syntax"></a>Składnia

```
template <typename T>
class BackInsertIterator :
public ::std::iterator<::std::output_iterator_tag, void, void, void, void>;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ elementu bieżącej kolekcji.

### <a name="remarks"></a>Uwagi

Klasa BackInsertIterator implementuje zasady wymagane [back_insert_iterator — klasa](../standard-library/back-insert-iterator-class.md).

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[BackInsertIterator::BackInsertIterator](#ctor)|Inicjuje nowe wystąpienie klasy BackInsertIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[BackInsertIterator::operator * — Operator](#operator-dereference)|Pobiera odwołanie do bieżącego BackInsertIterator.|
|[BackInsertIterator::operator++ Operator](#operator-increment)|Zwraca odwołanie do bieżącego BackInsertIterator. Iterator który pozostaje niezmieniona.|
|[BackInsertIterator::operator = — Operator](#operator-assign)|Dołącza określony obiekt do końca bieżącego sekwencyjną kolekcją.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`BackInsertIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Namespace:** Platform::Collections

---
## <a name="ctor"></a>  Konstruktor BackInsertIterator::BackInsertIterator

Inicjuje nowe wystąpienie klasy `BackInsertIterator` klasy.

## <a name="syntax"></a>Składnia

```

explicit BackInsertIterator(
   Windows::Foundation::Collections::IVector<T>^ v);
```

#### <a name="parameters"></a>Parametry

*v*<br/>
IVector\<T > obiektu.

### <a name="remarks"></a>Uwagi

A `BackInsertIterator` Wstawia elementy za ostatnim elementem w obiekcie określonym przez parametr `v`.

## <a name="operator-assign"></a>  BackInsertIterator::operator = — Operator

Dołącza określony obiekt do końca bieżącego sekwencyjną kolekcją.

## <a name="syntax"></a>Składnia

```
BackInsertIterator& operator=( const T& t);
```

#### <a name="parameters"></a>Parametry

*t*<br/>
Obiekt, który można dołączyć do bieżącej kolekcji.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego BackInsertIterator.

## <a name="operator-dereference"></a>  BackInsertIterator::operator * — Operator

Pobiera odwołanie do bieżącego BackInsertIterator.

## <a name="syntax"></a>Składnia

```
BackInsertIterator& operator*();
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego BackInsertIterator.

### <a name="remarks"></a>Uwagi

Ten operator zwraca odwołanie do bieżącego BackInsertIterator; nie do dowolnego elementu bieżącej kolekcji.

## <a name="operator-increment"></a>  BackInsertIterator::operator ++ — Operator

Zwraca odwołanie do bieżącego BackInsertIterator. Iterator który pozostaje niezmieniona.

## <a name="syntax"></a>Składnia

```

BackInsertIterator& operator++();

BackInsertIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego BackInsertIterator.

### <a name="remarks"></a>Uwagi

Zgodnie z projektem w pierwszym przykładzie składni wstępnie zwiększa bieżącego BackInsertIterator, i drugi składni po zwiększa BackInsertIterator bieżącego. `int` Typu w drugim składni wskazuje operacji po inkrementacji, nie operandu rzeczywistej liczby całkowitej.

Jednak ten operator nie modyfikuje w rzeczywistości BackInsertIterator. Zamiast tego operatora zwraca odwołanie do iteratora niezmodyfikowanego; bieżący. To jest takie samo zachowanie jako [operator *](#dereference-operator).

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)
