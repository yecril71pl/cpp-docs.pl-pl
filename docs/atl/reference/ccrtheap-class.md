---
title: Klasa CCRTHeap
ms.date: 11/04/2016
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
ms.openlocfilehash: caf5508079332689c2fff42f130951375dc35512
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327159"
---
# <a name="ccrtheap-class"></a>Klasa CCRTHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty CRT.

## <a name="syntax"></a>Składnia

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCRTHeap::Przydziel](#allocate)|Wywołanie tej metody, aby przydzielić blok pamięci.|
|[CCRTHeap::Za darmo](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.|
|[CCRTHeap::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać przydzielony rozmiar bloku pamięci przydzielone przez tego menedżera pamięci.|
|[CCRTHeap::Ponowne przydzielenie](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić pamięć przydzieloną przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CCRTHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji sterty CRT, w tym [malloc](../../c-runtime-library/reference/malloc.md), [free](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md)i [_msize](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

## <a name="ccrtheapallocate"></a><a name="allocate"></a>CCRTHeap::Przydziel

Wywołanie tej metody, aby przydzielić blok pamięci.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [CCRTHeap::Free](#free) lub [CCRTHeap::Reallocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano za pomocą [malloc](../../c-runtime-library/reference/malloc.md).

## <a name="ccrtheapfree"></a><a name="free"></a>CCRTHeap::Za darmo

Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci. NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowano za pomocą [bezpłatnego](../../c-runtime-library/reference/free.md).

## <a name="ccrtheapgetsize"></a><a name="getsize"></a>CCRTHeap::GetSize

Wywołanie tej metody, aby uzyskać przydzielony rozmiar bloku pamięci przydzielone przez tego menedżera pamięci.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar przydzielonego bloku pamięci w bajtach.

### <a name="remarks"></a>Uwagi

Zaimplementowana przy użyciu [_msize](../../c-runtime-library/reference/msize.md).

## <a name="ccrtheapreallocate"></a><a name="reallocate"></a>CCRTHeap::Ponowne przydzielenie

Wywołanie tej metody, aby ponownie przydzielić pamięć przydzieloną przez tego menedżera pamięci.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci.

*n Bajty*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [CCRTHeap::Free](#free) zwolnić pamięć przydzieloną przez tę metodę. Zaimplementowano przy użyciu [realloc](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Klasa heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
