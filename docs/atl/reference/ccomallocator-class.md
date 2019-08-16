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
ms.openlocfilehash: de302c7a58bf1b15e63e7cd391621ed9558e5a70
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497596"
---
# <a name="ccomallocator-class"></a>Klasa CComAllocator

Ta klasa udostępnia metody zarządzania pamięcią za pomocą procedur pamięci COM.

## <a name="syntax"></a>Składnia

```
class CComAllocator
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComAllocator:: Allocate](#allocate)|Wywołaj tę metodę statyczną, aby przydzielić pamięć.|
|[CComAllocator::Free](#free)|Wywołaj tę metodę statyczną, aby zwolnić przydzieloną pamięć.|
|[CComAllocator:: Reallocate](#reallocate)|Wywołaj tę metodę statyczną, aby ponownie przydzielić pamięć.|

## <a name="remarks"></a>Uwagi

Ta klasa jest używana przez [CComHeapPtr](../../atl/reference/ccomheapptr-class.md) do udostępniania procedur alokacji pamięci com. Odpowiednik klasy, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), zapewnia te same metody przy użyciu procedur CRT.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="allocate"></a>CComAllocator:: Allocate

Wywołaj tę funkcję statyczną w celu przydzielenia pamięci.

```
static void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Liczba bajtów do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik void do przydzieloną miejsce lub wartość NULL, jeśli jest za mało dostępnej pamięci.

### <a name="remarks"></a>Uwagi

Przydziela pamięć. Aby uzyskać więcej informacji, zobacz [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc) .

##  <a name="free"></a>CComAllocator:: Free

Wywołaj tę funkcję statyczną, aby zwolnić przydzieloną pamięć.

```
static void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do przydzieloną pamięć.

### <a name="remarks"></a>Uwagi

Zwalnia przydzieloną pamięć. Aby uzyskać więcej informacji, zobacz [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree) .

##  <a name="reallocate"></a>CComAllocator:: Reallocate

Wywołaj tę funkcję statyczną, aby ponownie przydzielić pamięć.

```
static void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do przydzieloną pamięć.

*nBytes*<br/>
Liczba bajtów do ponownego przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik void do przydzieloną miejsce lub wartość NULL, jeśli jest za mało pamięci

### <a name="remarks"></a>Uwagi

Zmienia rozmiar przydzieloną pamięci. Aby uzyskać więcej informacji, zobacz [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc) .

## <a name="see-also"></a>Zobacz także

[Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Klasa CCRTAllocator](../../atl/reference/ccrtallocator-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
