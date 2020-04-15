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
ms.openlocfilehash: 712c1f1638b954d1580eb527dd9eab7401917517
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317203"
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
|*Sz*|Liczba elementów w tablicy, które mają zostać przydzielone.|
|*Max*|Klasa max reprezentująca maksymalną liczbę elementów, które mają być przechowywane na liście wolnych. Klasa max może być [max_none,](../standard-library/max-none-class.md) [max_unbounded,](../standard-library/max-unbounded-class.md) [max_fixed_size](../standard-library/max-fixed-size-class.md)lub [max_variable_size.](../standard-library/max-variable-size-class.md)|

## <a name="remarks"></a>Uwagi

Ten szablon klasy zarządza listą bloków pamięci o rozmiarze *Sz* z maksymalną długością listy określoną przez klasę max przekazyzoną w *Max*.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[freelist](#freelist)|Konstruuje obiekt `freelist`typu .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Pop](#pop)|Usuwa pierwszy blok pamięci z listy wolnych.|
|[Push](#push)|Dodaje blok pamięci do listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<alokatory>

**Obszar nazw:** stdext

## <a name="freelistfreelist"></a><a name="freelist"></a>freelist::freelist

Konstruuje obiekt `freelist`typu .

```cpp
freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="freelistpop"></a><a name="pop"></a>freelist::pop

Usuwa pierwszy blok pamięci z listy wolnych.

```cpp
void *pop();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci usuniętego z listy.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca wartość NULL, jeśli lista jest pusta. W przeciwnym razie usuwa pierwszy blok pamięci z listy.

## <a name="freelistpush"></a><a name="push"></a>freelist::push

Dodaje blok pamięci do listy.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Ptr*|Wskaźnik do bloku pamięci, który ma zostać dodany do listy wolnych.|

### <a name="return-value"></a>Wartość zwracana

**true,** `full` jeśli funkcja klasy max zwraca **false**; w przeciwnym `push` razie funkcja zwraca **false**.

### <a name="remarks"></a>Uwagi

Jeśli `full` funkcja klasy max zwraca **false,** ta funkcja elementu członkowskiego dodaje blok pamięci wskazywal przez *ptr* do głowy listy.

## <a name="see-also"></a>Zobacz też

[\<>alokatorów](../standard-library/allocators-header.md)
