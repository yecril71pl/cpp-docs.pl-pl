---
title: freelist — Klasa
ms.date: 11/04/2016
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
ms.openlocfilehash: 7425f99f7966548bdb1f94d3007382eeb99863df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193227"
---
# <a name="freelist-class"></a>freelist — Klasa

Zarządza listą bloków pamięci.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy, która ma zostać przypisana.|
|*Maksymalny*|Maksymalna liczba elementów, które mają być przechowywane na liście bezpłatnych. Maksymalna Klasa może być [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md), [max_fixed_size](../standard-library/max-fixed-size-class.md)lub [max_variable_size](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Uwagi

Ten szablon klasy służy do zarządzania listą bloków pamięci o rozmiarze *sz* z maksymalną długością listy określoną przez maksymalną przekazaną długość klasy *.*

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[freelist](#freelist)|Konstruuje obiekt typu `freelist` .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[skakując](#pop)|Usuwa pierwszy blok pamięci z listy bezpłatnych.|
|[push](#push)|Dodaje blok pamięci do listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<allocators>

**Przestrzeń nazw:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>freelist:: freelist

Konstruuje obiekt typu `freelist` .

```cpp
freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="freelistpop"></a><a name="pop"></a>freelist::p op

Usuwa pierwszy blok pamięci z listy bezpłatnych.

```cpp
void *pop();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci usunięty z listy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość NULL, jeśli lista jest pusta. W przeciwnym razie usuwa pierwszy blok pamięci z listy.

## <a name="freelistpush"></a><a name="push"></a>freelist::p USH

Dodaje blok pamięci do listy.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do bloku pamięci, który ma zostać dodany do listy bezpłatnych.|

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli `full` Funkcja klasy Max zwraca **`false`** ; w przeciwnym razie `push` Funkcja zwraca wartość **`false`** .

### <a name="remarks"></a>Uwagi

Jeśli `full` Funkcja klasy Max zwraca **`false`** , ta funkcja członkowska dodaje blok pamięci wskazywany przez *PTR* do nagłówka listy.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)
