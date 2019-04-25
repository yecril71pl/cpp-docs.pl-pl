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
ms.openlocfilehash: ef1f2e617e93869a1084dc030c6496c819f1ed96
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159395"
---
# <a name="freelist-class"></a>freelist — Klasa

Zarządza listą bloki pamięci.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, class Max>
class freelist : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Sz*|Liczba elementów w tablicy do przydzielenia.|
|*Maksymalna*|Maksymalna Klasa reprezentująca maksymalną liczbę elementów, które mają być przechowywane na liście bezpłatne. Klasa max może być [max_none —](../standard-library/max-none-class.md), [max_unbounded —](../standard-library/max-unbounded-class.md), [max_fixed_size —](../standard-library/max-fixed-size-class.md), lub [max_variable_size —](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Uwagi

Tej klasy szablonu zarządza listą bloki pamięci o rozmiarze *Sz* z maksymalną długość listy określane przez klasę max przekazanej *Max*.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[FreeList —](#freelist)|Tworzy obiekt typu `freelist`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[POP](#pop)|Usuwa pierwszy blok pamięci z bezpłatnych listy.|
|[push](#push)|Blok pamięci dodaje do listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<buforów >

**Namespace:** stdext

## <a name="freelist"></a>  FreeList::FreeList

Tworzy obiekt typu `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="pop"></a>  FreeList::POP

Usuwa pierwszy blok pamięci z bezpłatnych listy.

```cpp
void *pop();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci usunięty z listy.

### <a name="remarks"></a>Uwagi

Element członkowski funkcji zwraca wartość NULL, jeśli lista jest pusta. W przeciwnym razie usuwa pierwszy blok pamięci z listy.

## <a name="push"></a>  freelist::push

Blok pamięci dodaje do listy.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*ptr*|Wskaźnik do bloku pamięci, które mają zostać dodane do listy bezpłatne.|

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli `full` klasy max:: gettotalsize() zwróciło **false**; w przeciwnym razie `push` funkcja zwraca **false**.

### <a name="remarks"></a>Uwagi

Jeśli `full` klasy max:: gettotalsize() zwróciło **false**, ta funkcja elementu członkowskiego dodaje blok pamięci wskazywany przez *ptr* porównanie listy.

## <a name="see-also"></a>Zobacz także

[\<allocators>](../standard-library/allocators-header.md)<br/>
