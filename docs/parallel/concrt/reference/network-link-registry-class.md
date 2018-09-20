---
title: network_link_registry — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- network_link_registry
- AGENTS/concurrency::network_link_registry
- AGENTS/concurrency::network_link_registry::add
- AGENTS/concurrency::network_link_registry::begin
- AGENTS/concurrency::network_link_registry::contains
- AGENTS/concurrency::network_link_registry::count
- AGENTS/concurrency::network_link_registry::remove
dev_langs:
- C++
helpviewer_keywords:
- network_link_registry class
ms.assetid: 3e7b4097-09f1-4252-964e-b15b8f7f7fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2798c4abe33e49d2ac6199ad6f9a1013805fde7b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424420"
---
# <a name="networklinkregistry-class"></a>network_link_registry — Klasa

`network_link_registry` Abstrakcyjna klasa bazowa zarządza łącza między źródłowym i docelowym bloki.

## <a name="syntax"></a>Składnia

```
template<class _Block>
class network_link_registry;
```

#### <a name="parameters"></a>Parametry

*_Blok*<br/>
Typ danych bloku znajdujących się w `network_link_registry`.

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|`const_pointer`|Typ, który dostarcza wskaźnik do `const` element `network_link_registry` obiektu.|
|`const_reference`|Typ, który zawiera odwołanie do `const` przechowywanego w `network_link_registry` obiektu do odczytu i wykonywania operacji const.|
|`iterator`|Typ zapewniający iterator, który może odczytać lub zmodyfikować dowolny element w `network_link_registry` obiektu.|
|`type`|Typ, który reprezentuje typ bloku, przechowywane w `network_link_registry` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[add](#add)|W przypadku przesłonięcia w klasie pochodnej, dodaje link do `network_link_registry` obiektu.|
|[begin](#begin)|Po przesłonięciu w klasie pochodnej zwraca iterator do pierwszego elementu w `network_link_registry` obiektu.|
|[zawiera](#contains)|W przypadku przesłonięcia w klasie pochodnej, wyszukuje `network_link_registry` obiektu dla określonego bloku.|
|[Liczba](#count)|W przypadku przesłonięcia w klasie pochodnej zwraca liczbę elementów w `network_link_registry` obiektu.|
|[remove](#remove)|W przypadku przesłonięcia w klasie pochodnej, usuwa określony blok z `network_link_registry` obiektu.|

## <a name="remarks"></a>Uwagi

`network link registry` Nie jest bezpieczny dla równoczesny dostęp.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`network_link_registry`

## <a name="requirements"></a>Wymagania

**Nagłówek:** agents.h

**Namespace:** współbieżności

##  <a name="add"></a> Dodaj

W przypadku przesłonięcia w klasie pochodnej, dodaje link do `network_link_registry` obiektu.

```
virtual void add(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać dodana.

##  <a name="begin"></a> Rozpocznij

Po przesłonięciu w klasie pochodnej zwraca iterator do pierwszego elementu w `network_link_registry` obiektu.

```
virtual iterator begin() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Iterator odnoszący się do pierwszego elementu w `network_link_registry` obiektu.

### <a name="remarks"></a>Uwagi

Stan końcowy iterator który jest wskazywany przez `NULL` łącza.

##  <a name="contains"></a> zawiera

W przypadku przesłonięcia w klasie pochodnej, wyszukuje `network_link_registry` obiektu dla określonego bloku.

```
virtual bool contains(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który jest wyszukiwana w `network_link_registry` obiektu.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli blok został znaleziony, `false` inaczej.

##  <a name="count"></a> Liczba

W przypadku przesłonięcia w klasie pochodnej zwraca liczbę elementów w `network_link_registry` obiektu.

```
virtual size_t count() = 0;
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów w `network_link_registry` obiektu.

##  <a name="remove"></a> Usuń

W przypadku przesłonięcia w klasie pochodnej, usuwa określony blok z `network_link_registry` obiektu.

```
virtual bool remove(_EType _Link) = 0;
```

### <a name="parameters"></a>Parametry

*_Link*<br/>
Wskaźnik do bloku, który ma zostać usunięty, jeśli znaleziono.

### <a name="return-value"></a>Wartość zwracana

`true` Jeśli łącze zostało znalezione i usuwane, `false` inaczej.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw współbieżności](concurrency-namespace.md)<br/>
[single_link_registry, klasa](single-link-registry-class.md)<br/>
[multi_link_registry, klasa](multi-link-registry-class.md)
