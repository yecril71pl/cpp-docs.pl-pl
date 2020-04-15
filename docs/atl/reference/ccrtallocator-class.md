---
title: Klasa CCRTAllocator
ms.date: 11/04/2016
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
ms.openlocfilehash: 2f6bae3818fa0f1639e0e3cee4e09121580da768
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327171"
---
# <a name="ccrtallocator-class"></a>Klasa CCRTAllocator

Ta klasa zawiera metody zarządzania pamięcią przy użyciu procedur pamięci CRT.

## <a name="syntax"></a>Składnia

```
class ATL::CCRTAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCRTAllocator::Przydziel](#allocate)|(Statyczne) Wywołanie tej metody, aby przydzielić pamięć.|
|[CCRTAllocator::Za darmo](#free)|(Statyczne) Wywołanie tej metody, aby zwolnić pamięć.|
|[CCRTAllocator::Ponowne przydzielenie](#reallocate)|(Statyczne) Wywołanie tej metody, aby ponownie przydzielić pamięć.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez [CHeapPtr](../../atl/reference/cheapptr-class.md) do zapewnienia procedur alokacji pamięci CRT. Klasa odpowiednika, [CComAllocator,](../../atl/reference/ccomallocator-class.md)udostępnia te same metody przy użyciu procedur COM.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="ccrtallocatorallocate"></a><a name="allocate"></a>CCRTAllocator::Przydziel

Wywołanie tej funkcji statycznej, aby przydzielić pamięć.

```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Liczba bajtów do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik void do przydzielonego miejsca lub NULL, jeśli jest za mało dostępnej pamięci.

### <a name="remarks"></a>Uwagi

Przydziela pamięć. Zobacz [malloc](../../c-runtime-library/reference/malloc.md) więcej szczegółów.

## <a name="ccrtallocatorfree"></a><a name="free"></a>CCRTAllocator::Za darmo

Wywołanie tej funkcji statycznej w celu zwolnienia pamięci.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do przydzielonej pamięci.

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną pamięć. Zobacz [za darmo,](../../c-runtime-library/reference/free.md) aby uzyskać więcej informacji.

## <a name="ccrtallocatorreallocate"></a><a name="reallocate"></a>CCRTAllocator::Ponowne przydzielenie

Wywołanie tej funkcji statycznej w celu ponownego przydzielenia pamięci.

```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do przydzielonej pamięci.

*n Bajty*<br/>
Liczba bajtów do ponownego przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik void do przydzielonego miejsca lub NULL, jeśli jest za mało pamięci.

### <a name="remarks"></a>Uwagi

Zmienić rozmiar przydzielonej pamięci. Zobacz [realloc](../../c-runtime-library/reference/realloc.md) więcej szczegółów.

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
