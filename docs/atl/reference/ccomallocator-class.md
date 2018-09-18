---
title: Klasa CComAllocator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f867d3a7ca81d190ee363c7539e56a62004eb377
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088946"
---
# <a name="ccomallocator-class"></a>Klasa CComAllocator

Ta klasa dostarcza metody do zarządzania ilości pamięci za pomocą procedury pamięci COM.

## <a name="syntax"></a>Składnia

```
class CComAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAllocator::Allocate](#allocate)|Wywołanie tej metody statyczne, można przydzielić pamięci.|
|[CComAllocator::Free](#free)|Wywołanie tej metody statycznej, aby zwolnić alokacji pamięci.|
|[CComAllocator::Reallocate](#reallocate)|Wywołanie tej metody statyczne do ponownego przydzielenia pamięci.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) do dostarczenia pamięci COM procedur alokacji. Klasa odpowiednika [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), oferuje te same metody, przy użyciu procedur CRT.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="allocate"></a>  CComAllocator::Allocate

Wywołaj tę funkcję statyczne można przydzielić pamięci.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba bajtów do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca pusty wskaźnik do przydzielonego miejsca lub wartość NULL, jeśli ma za mało pamięci.

### <a name="remarks"></a>Uwagi

Przydziela pamięć. Zobacz [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc) Aby uzyskać więcej informacji.

##  <a name="free"></a>  CComAllocator::Free

Wywołaj tę funkcję statycznej, aby zwolnić alokacji pamięci.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do alokacji pamięci.

### <a name="remarks"></a>Uwagi

Zwalnia ilość przydzielonej pamięci. Zobacz [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree) Aby uzyskać więcej informacji.

##  <a name="reallocate"></a>  CComAllocator::Reallocate

Wywołaj tę funkcję statycznych w celu ponownego przydzielenia pamięci.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do alokacji pamięci.

*nBytes*<br/>
Liczba bajtów w celu ponownego przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca pusty wskaźnik do przydzielonego miejsca lub wartość NULL, jeśli jest za mało pamięci

### <a name="remarks"></a>Uwagi

Zmienia rozmiar ilość ilość przydzielonej pamięci. Zobacz [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc) Aby uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
