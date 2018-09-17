---
title: FreeList — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::freelist
- allocators/stdext::freelist::pop
- allocators/stdext::freelist::push
dev_langs:
- C++
helpviewer_keywords:
- stdext::freelist
- stdext::freelist [C++], pop
- stdext::freelist [C++], push
ms.assetid: 8ad7e35c-4c80-4479-8ede-1a2497b06d71
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ae7e56fd33de888ad31a24ad1e3130acc96daa28
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702833"
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

## <a name="push"></a>  FreeList::push

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

[\<allocators — >](../standard-library/allocators-header.md)<br/>
