---
title: allocator_chunklist — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- allocators/stdext::allocator_chunklist
- allocators/stdext::allocators::allocator_chunklist
dev_langs:
- C++
helpviewer_keywords:
- stdext::allocator_chunklist
- stdext::allocators [C++], allocator_chunklist
ms.assetid: ea72ed0a-dfdb-4c8b-8096-e4baf567b80f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aaa7b01fe4008089cb8a773fc866d62a269ae717
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="allocatorchunklist-class"></a>allocator_chunklist — Klasa

Opisuje obiekt, który zarządza Alokacja magazynu i zwalnianie obiektów przy użyciu pamięci podręcznej typu [cache_chunklist —](../standard-library/cache-chunklist-class.md).

## <a name="syntax"></a>Składnia

```cpp
template <class Type>
class allocator_chunklist;
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Type`|Typ elementów przydzielonej przez program przydzielania.|

## <a name="remarks"></a>Uwagi

[Allocator_decl —](../standard-library/allocators-functions.md#allocator_decl) makro przekazuje tę klasę jako `name` parametru w następujących instrukcji: `ALLOCATOR_DECL(CACHE_CHUNKLIST, SYNC_DEFAULT, allocator_chunklist);`

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<allocators — >

**Namespace:** stdext —

## <a name="see-also"></a>Zobacz także

[\<allocators — >](../standard-library/allocators-header.md)<br/>
