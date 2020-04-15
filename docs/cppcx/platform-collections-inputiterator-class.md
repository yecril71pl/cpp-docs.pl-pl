---
title: Platform::Collections::InputIterator, klasa
ms.date: 03/27/2019
ms.topic: reference
f1_keywords:
- COLLECTION/Platform::Collections::InputIterator::InputIterator
helpviewer_keywords:
- InputIterator Class
ms.assetid: ef72eea4-32a9-42b9-8119-ce87dbdcd3be
ms.openlocfilehash: 92f9b15f474a5aa3d063f0ccfb663f56baf8de31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81354565"
---
# <a name="platformcollectionsinputiterator-class"></a>Platform::Collections::InputIterator, klasa

Udostępnia standardowy szablon wejściowy biblioteki dla kolekcji pochodzących ze środowiska wykonawczego systemu Windows.

## <a name="syntax"></a>Składnia

```
template <typename X>
class InputIterator;
```

#### <a name="parameters"></a>Parametry

*X*<br/>
Nazwa typu klasy szablonu InputIterator.

### <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|`difference_type`|Różnica wskaźnika (ptrdiff_t).|
|`iterator_category`|Kategoria iteratora wejściowego (::std::input_iterator_tag).|
|`pointer`|Wskaźnik do`const X`|
|`reference`|Odniesienie do`const X`|
|`value_type`|Nazwa `X` typu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[InputIterator::InputIterator](#ctor)|Inicjuje nowe wystąpienie klasy InputIterator.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[InputIterator::operator!= Operator](#operator-inequality)|Wskazuje, czy bieżący InputIterator nie jest równy określonej inputIterator.|
|[InputIterator::operator* Operator](#operator-dereference)|Pobiera odwołanie do elementu określonego przez bieżący InputIterator.|
|[InputIterator::operator++ Operator](#operator-increment)|Zwiększa bieżący InputIterator.|
|[InputIterator::operator== Operator](#operator-equality)|Wskazuje, czy bieżący inputIterator jest równy określonej inputIterator.|
|[InputIterator::operator-operator > operator](#operator-arrow)|Pobiera adres elementu, do którego odwołuje się bieżący inputIterator.|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`InputIterator`

### <a name="requirements"></a>Wymagania

**Nagłówek:** collection.h

**Obszar nazw:** Platforma::Kolekcje

## <a name="inputiteratorinputiterator-constructor"></a><a name="ctor"></a>InputIterator::InputIterator Constructor

Inicjuje nowe wystąpienie klasy InputIterator.

### <a name="syntax"></a>Składnia

```
InputIterator();
explicit InputIterator(Windows::Foundation::Collections<X>^ iterator);
```

### <a name="parameters"></a>Parametry

*Sterująca*<br/>
Obiekt iteratora.

## <a name="inputiteratoroperator-gt-operator"></a><a name="operator-arrow"></a>InputIterator::operator-&gt; Operator

Pobiera adres elementu określonego przez bieżący InputIterator.

### <a name="syntax"></a>Składnia

```
pointer operator->() const;
```

### <a name="return-value"></a>Wartość zwracana

Adres elementu określonego przez bieżący inputIterator.

## <a name="inputiteratoroperator-operator"></a><a name="operator-dereference"></a>InputIterator::operator\* Operator

Pobiera odwołanie do elementu określonego przez bieżący InputIterator.

### <a name="syntax"></a>Składnia

```
reference operator*() const;
```

### <a name="return-value"></a>Wartość zwracana

Element określony przez bieżący InputIterator.

## <a name="inputiteratoroperator-operator"></a><a name="operator-equality"></a>InputIterator::operator== Operator

Wskazuje, czy bieżący inputIterator jest równy określonej inputIterator.

### <a name="syntax"></a>Składnia

```
bool operator== (const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Inny Inputiterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący InputIterator jest równy *innemu;* w przeciwnym razie **false**.

## <a name="inputiteratoroperator-operator"></a><a name="operator-increment"></a>InputIterator::operator++ Operator

Zwiększa bieżący InputIterator.

### <a name="syntax"></a>Składnia

```
InputIterator& operator++();
InputIterator operator++(int);
```

### <a name="return-value"></a>Wartość zwracana

Pierwsza składnia zwiększa się, a następnie zwraca bieżący inputIterator. Druga składnia zwraca kopię bieżącego inputIterator, a następnie zwiększa bieżący InputIterator.

### <a name="remarks"></a>Uwagi

Pierwsza składnia InputIterator wstępnie zwiększa bieżący inputIterator.

Druga składnia zwiększa przyrost bieżącego inputIterator. Typ `int` w drugiej składni wskazuje operację przyrostową, a nie rzeczywisty argument całkowity.

## <a name="inputiteratoroperator-operator"></a><a name="operator-inequality"></a>InputIterator::operator!= Operator

Wskazuje, czy bieżący InputIterator nie jest równy określonej inputIterator.

### <a name="syntax"></a>Składnia

```
bool operator!=(const InputIterator& other) const;
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Inny Inputiterator.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli bieżący InputIterator nie jest równy *innemu*; w przeciwnym razie **false**.

## <a name="see-also"></a>Zobacz też

[Obszar nazw platformy](platform-namespace-c-cx.md)
