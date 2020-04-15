---
title: Klasa CComAllocator
ms.date: 11/04/2016
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
ms.openlocfilehash: 165cdb8b0b16a4872214f4556c26ee141e6a4d89
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321137"
---
# <a name="ccomallocator-class"></a>Klasa CComAllocator

Ta klasa zawiera metody zarządzania pamięcią przy użyciu procedur pamięci COM.

## <a name="syntax"></a>Składnia

```
class CComAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAllocator::Przydziel](#allocate)|Wywołanie tej metody statycznej, aby przydzielić pamięć.|
|[CComAllocator::Za darmo](#free)|Wywołanie tej metody statycznej, aby zwolnić przydzieloną pamięć.|
|[CComAllocator::Ponowne przydzielenie](#reallocate)|Wywołanie tej metody statycznej, aby ponownie przydzielić pamięć.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) do zapewnienia procedur alokacji pamięci COM. Klasa odpowiednika, [CCRTAllocator,](../../atl/reference/ccrtallocator-class.md)udostępnia te same metody przy użyciu procedur CRT.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccomallocatorallocate"></a><a name="allocate"></a>CComAllocator::Przydziel

Wywołanie tej funkcji statycznej, aby przydzielić pamięć.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Liczba bajtów do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik void do przydzielonego miejsca lub NULL, jeśli jest za mało dostępnej pamięci.

### <a name="remarks"></a>Uwagi

Przydziela pamięć. Zobacz [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) aby uzyskać więcej informacji.

## <a name="ccomallocatorfree"></a><a name="free"></a>CComAllocator::Za darmo

Wywołanie tej funkcji statycznej do zwolnienia przydzielonej pamięci.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do przydzielonej pamięci.

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną pamięć. Zobacz [CoTaskMemFree aby](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) uzyskać więcej informacji.

## <a name="ccomallocatorreallocate"></a><a name="reallocate"></a>CComAllocator::Ponowne przydzielenie

Wywołanie tej funkcji statycznej w celu ponownego przydzielenia pamięci.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do przydzielonej pamięci.

*n Bajty*<br/>
Liczba bajtów do ponownego przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik void do przydzielonego miejsca lub null, jeśli nie ma wystarczającej ilości pamięci

### <a name="remarks"></a>Uwagi

Zmienić rozmiar przydzielonej pamięci. Zobacz [CoTaskMemRealloc aby](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) uzyskać więcej informacji.

## <a name="see-also"></a>Zobacz też

[Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
