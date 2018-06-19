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
ms.openlocfilehash: 7e9a8bf702f4373040a6f7255d67f551b5dbfa60
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846964"
---
# <a name="freelist-class"></a>freelist — Klasa

Zarządza listą bloki pamięci.

## <a name="syntax"></a>Składnia

```cpp
template <std::size_t Sz, class Max>
class freelist
 : public Max
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Sz`|Liczba elementów w tablicy do przydzielenia.|
|`Max`|Max Klasa reprezentująca maksymalną liczbę elementów, które mają być przechowywane w liście wolne. Max klasa może być [max_none —](../standard-library/max-none-class.md), [max_unbounded —](../standard-library/max-unbounded-class.md), [max_fixed_size —](../standard-library/max-fixed-size-class.md), lub [max_variable_size —](../standard-library/max-variable-size-class.md).|

## <a name="remarks"></a>Uwagi

Ta klasa szablonu zarządza listą bloki pamięci o rozmiarze `Sz` z maksymalną długość listy określony przez klasę max przekazano `Max`.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[FreeList —](#freelist)|Tworzy obiekt typu `freelist`.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[POP](#pop)|Usuwa pierwszy blok pamięci z wolnego listy.|
|[push](#push)|Dodaje blok pamięci do listy.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="freelist"></a>  FreeList::FreeList

Tworzy obiekt typu `freelist`.

```cpp
freelist();
```

### <a name="remarks"></a>Uwagi

## <a name="pop"></a>  FreeList::POP

Usuwa pierwszy blok pamięci z wolnego listy.

```cpp
void *pop();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci usunięty z listy.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca `NULL` Jeśli lista jest pusta. W przeciwnym razie pierwszy blok pamięci usuwa z listy.

## <a name="push"></a>  FreeList::push

Dodaje blok pamięci do listy.

```cpp
bool push(void* ptr);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`ptr`|Wskaźnik do bloku pamięci do dodania do listy wolne.|

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli `full` zwraca funkcja max klasy `false`; w przeciwnym razie `push` funkcja zwraca `false`.

### <a name="remarks"></a>Uwagi

Jeśli `full` zwraca funkcja max klasy `false`, funkcji członkowskiej dodaje blok pamięci wskazywanej przez `ptr` nagłówek listy.

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
