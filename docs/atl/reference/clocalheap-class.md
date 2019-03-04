---
title: Klasa CLocalHeap
ms.date: 11/04/2016
f1_keywords:
- CLocalHeap
- ATLMEM/ATL::CLocalHeap
- ATLMEM/ATL::CLocalHeap::Allocate
- ATLMEM/ATL::CLocalHeap::Free
- ATLMEM/ATL::CLocalHeap::GetSize
- ATLMEM/ATL::CLocalHeap::Reallocate
helpviewer_keywords:
- CLocalHeap class
ms.assetid: 1ffa87a5-5fc8-4f8d-8809-58e87e963bd2
ms.openlocfilehash: 53288bea8a50f62437eab4dd81d5d816abf78f44
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57283088"
---
# <a name="clocalheap-class"></a>Klasa CLocalHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji lokalnej sterty systemu Win32.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLocalHeap::Allocate](#allocate)|Wywołaj tę metodę można przydzielić bloku pamięci.|
|[CLocalHeap::Free](#free)|Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.|
|[CLocalHeap::GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielony rozmiar bloku pamięci przydzielonej przez tego menedżera pamięci.|
|[CLocalHeap::Reallocate](#reallocate)|Wywołaj tę metodę w celu ponownego przydzielenia pamięci przydzielonej przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CLocalHeap` implementuje funkcje alokacji pamięci za pomocą funkcji lokalnej sterty systemu Win32.

> [!NOTE]
>  Funkcje lokalnej sterty wolniej niż inne funkcje zarządzania pamięcią i nie są oferowane jako wiele funkcji. W związku z tym, nowe aplikacje powinny używać [sterty funkcji](/windows/desktop/Memory/heap-functions). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy.

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

##  <a name="allocate"></a>  CLocalHeap::Allocate

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

Wywołaj [CLocalHeap::Free](#free) lub [CLocalHeap::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

Implementowany przy użyciu [Funkcja LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc) z parametrem flagi LMEM_FIXED.

##  <a name="free"></a>  CLocalHeap::Free

Wywołaj tę metodę w celu zwolnienia bloku pamięci przydzielonej przez tego menedżera pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci uprzednio przydzielonej przez tego menedżera pamięci. Wartość NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Implementowany przy użyciu [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>  CLocalHeap::GetSize

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

Implementowany przy użyciu [LocalSize](/windows/desktop/api/winbase/nf-winbase-localsize).

##  <a name="reallocate"></a>  CLocalHeap::Reallocate

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

Wywołaj [CLocalHeap::Free](#free) zwolnienie pamięci przydzielonej przez tę metodę.

Implementowany przy użyciu [LocalReAlloc](/windows/desktop/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
