---
title: Klasa CCRTHeap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 537785bab555bffb5278da27926b4adbb1a6f226
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022022"
---
# <a name="ccrtheap-class"></a>Klasa CCRTHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu stosu CRT.

## <a name="syntax"></a>Składnia

```
class CCRTHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CCRTHeap::Allocate](#allocate)|Wywołaj tę metodę można przydzielić bloku pamięci.|
|[CCRTHeap::Free](#free)|Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.|
|[CCRTHeap::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielony rozmiar bloku pamięci przydzielonej przez tego menedżera pamięci.|
|[CCRTHeap::Reallocate](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CCRTHeap` implementuje pamięci funkcji alokacji przy użyciu CRT sterty funkcje, w tym [— funkcja malloc](../../c-runtime-library/reference/malloc.md), [bezpłatne](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md), i [_msize —](../../c-runtime-library/reference/msize.md).

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CCRTHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

##  <a name="allocate"></a>  CCRTHeap::Allocate

Wywołaj tę metodę można przydzielić bloku pamięci.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Żądana liczba bajtów w nowy blok pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku bloku nowo alokacji pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj [CCRTHeap::Free](#free) lub [CCRTHeap::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

Implementowany przy użyciu [— funkcja malloc](../../c-runtime-library/reference/malloc.md).

##  <a name="free"></a>  CCRTHeap::Free

Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci. Wartość NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Implementowany przy użyciu [bezpłatne](../../c-runtime-library/reference/free.md).

##  <a name="getsize"></a>  CCRTHeap::GetSize

Wywołaj tę metodę, aby uzyskać przydzielony rozmiar bloku pamięci przydzielonej przez tego menedżera pamięci.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar bloku ilość przydzielonej pamięci w bajtach.

### <a name="remarks"></a>Uwagi

Implementowany przy użyciu [_msize —](../../c-runtime-library/reference/msize.md).

##  <a name="reallocate"></a>  CCRTHeap::Reallocate

Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci.

*nBytes*<br/>
Żądana liczba bajtów w nowy blok pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku bloku nowo alokacji pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj [CCRTHeap::Free](#free) zwolnienie pamięci przydzielonej przez tę metodę. Implementowany przy użyciu [realloc](../../c-runtime-library/reference/realloc.md).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
