---
title: Klasa CGlobalHeap
ms.date: 11/04/2016
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
helpviewer_keywords:
- CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
ms.openlocfilehash: a4bc8b18a1c29049e17576082a30de4a8704eaee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50468955"
---
# <a name="cglobalheap-class"></a>Klasa CGlobalHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty globalnej Win32.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGlobalHeap::Allocate](#allocate)|Wywołaj tę metodę można przydzielić bloku pamięci.|
|[CGlobalHeap::Free](#free)|Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.|
|[CGlobalHeap::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielony rozmiar bloku pamięci przydzielonej przez tego menedżera pamięci.|
|[CGlobalHeap::Reallocate](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CGlobalHeap` implementuje funkcje alokacji pamięci za pomocą funkcji sterty globalnej Win32.

> [!NOTE]
>  Funkcje globalne sterty wolniej niż inne funkcje zarządzania pamięcią i nie są oferowane jako wiele funkcji. W związku z tym, nowe aplikacje powinny używać [sterty funkcji](/windows/desktop/Memory/heap-functions). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy. Funkcje globalne są nadal używane przez DDE i funkcje Schowka.

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

##  <a name="allocate"></a>  CGlobalHeap::Allocate

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

Wywołaj [CGlobalHeap::Free](#free) lub [CGlobalHeap::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

Implementowany przy użyciu [działanie funkcji GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc) z parametrem flagi GMEM_FIXED.

##  <a name="free"></a>  CGlobalHeap::Free

Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci. Wartość NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Implementowany przy użyciu [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree).

##  <a name="getsize"></a>  CGlobalHeap::GetSize

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

Implementowany przy użyciu [Funkcja GlobalSize](/windows/desktop/api/winbase/nf-winbase-globalsize).

##  <a name="reallocate"></a>  CGlobalHeap::Reallocate

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

Wywołaj [CGlobalHeap::Free](#free) zwolnienie pamięci przydzielonej przez tę metodę.

Implementowany przy użyciu [GlobalReAlloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
