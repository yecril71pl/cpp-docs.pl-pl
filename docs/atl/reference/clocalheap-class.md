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
ms.openlocfilehash: 303e3b85ad11c309f862f59d6ec610701c4ef6db
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326758"
---
# <a name="clocalheap-class"></a>Klasa CLocalHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty lokalnej Win32.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLocalHeap::Przydziel](#allocate)|Wywołanie tej metody, aby przydzielić blok pamięci.|
|[CLocalHeap::Za darmo](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.|
|[CLocalHeap::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać przydzielony rozmiar bloku pamięci przydzielone przez tego menedżera pamięci.|
|[CLocalHeap::Ponowne przydzielenie](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić pamięć przydzieloną przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CLocalHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji sterty lokalnej Win32.

> [!NOTE]
> Funkcje sterty lokalnej są wolniejsze niż inne funkcje zarządzania pamięcią i nie zapewniają tylu funkcji. W związku z tym nowe aplikacje powinny używać [funkcji sterty](/windows/win32/Memory/heap-functions). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy.

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

## <a name="clocalheapallocate"></a><a name="allocate"></a>CLocalHeap::Przydziel

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

Wywołanie [CLocalHeap::Free](#free) lub [CLocalHeap::Reallocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) z parametrem flagi LMEM_FIXED.

## <a name="clocalheapfree"></a><a name="free"></a>CLocalHeap::Za darmo

Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci. NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowano przy użyciu [localfree](/windows/win32/api/winbase/nf-winbase-localfree).

## <a name="clocalheapgetsize"></a><a name="getsize"></a>CLocalHeap::GetSize

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

Zaimplementowano przy użyciu [localsize](/windows/win32/api/winbase/nf-winbase-localsize).

## <a name="clocalheapreallocate"></a><a name="reallocate"></a>CLocalHeap::Ponowne przydzielenie

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

Wywołanie [CLocalHeap::Free](#free) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [localrealloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Klasa heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
