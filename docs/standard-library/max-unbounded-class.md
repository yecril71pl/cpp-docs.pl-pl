---
title: max_unbounded — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 21a6673626e44e3c74a32eab1b545a16e4577b1b
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="maxunbounded-class"></a>max_unbounded — Klasa

W tym artykule opisano [maksymalnej liczby klasy](../standard-library/allocators-header.md) obiekt, który nie istnieje limit maksymalnego [elementu freelist](../standard-library/freelist-class.md) obiektu.

## <a name="syntax"></a>Składnia

```cpp
class max_unbounded
```

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[Przydzielone](#allocated)|Zwiększa liczbę bloków alokacji pamięci.|
|[Cofnięcie przydziału](#deallocated)|Zmniejsza liczbę przydzielonych bloków pamięci.|
|[full](#full)|Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.|
|[Wydane](#released)|Zmniejsza liczbę pamięci blokuje na liście wolne.|
|[zapisane](#saved)|Zwiększa liczbę bloków pamięci na liście wolne.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="allocated"></a>  max_unbounded::allocated

Zwiększa liczbę bloków alokacji pamięci.

```cpp
void allocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Nx`|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nie działa. Jest ona wywoływana po każdym pomyślnym wywołaniem przez `cache_freelist::allocate` operator `new`. Argument `_Nx` jest to liczba bloków pamięci we fragmencie przydzielone przez operatora `new`.

## <a name="deallocated"></a>  max_unbounded::deallocated

Zmniejsza liczbę przydzielonych bloków pamięci.

```cpp
void deallocated(std::size_t _Nx = 1);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`_Nx`|Wartość przyrostu.|

### <a name="remarks"></a>Uwagi

Funkcja członkowska nie działa. Ta funkcja elementu członkowskiego jest wywoływana po każdym wywołania `cache_freelist::deallocate` operator `delete`. Argument `_Nx` jest to liczba bloków pamięci we fragmencie alokację przez operatora `delete`.

## <a name="full"></a>  max_unbounded::Full

Zwraca wartość, która określa, czy należy dodać więcej bloków pamięci do wolnego listy.

```cpp
bool full();
```

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zawsze zwraca `false`.

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska jest wywoływana przez `cache_freelist::deallocate`. Jeśli wywołanie zwraca `true`, `deallocate` umieszcza blok pamięci na liście wolnego; Jeśli zwraca wartość false, `deallocate` operator wywołania `delete` można cofnąć alokacji bloku.

## <a name="released"></a>  max_unbounded::released

Zmniejsza liczbę pamięci blokuje na liście wolne.

```cpp
void released();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nie działa. `released` Funkcji członkowskiej klasy bieżący maksymalny jest wywoływana przez `cache_freelist::allocate` po każdej zmianie Usuwa blok pamięci z wolnego listy.

## <a name="saved"></a>  max_unbounded::Saved

Zwiększa liczbę bloków pamięci na liście wolne.

```cpp
void saved();
```

### <a name="remarks"></a>Uwagi

Ta funkcja członkowska nie działa. Jest ona wywoływana przez `cache_freelist::deallocate` zawsze, gdy blok pamięci są umieszczane na liście wolne.

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
