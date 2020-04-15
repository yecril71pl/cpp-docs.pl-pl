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
ms.openlocfilehash: d596fd51c1bf33f606c1f14c9e8dbd2f1926c7f8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326942"
---
# <a name="cglobalheap-class"></a>Klasa CGlobalHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji globalnego sterty Win32.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGlobalHeap::Przydziel](#allocate)|Wywołanie tej metody, aby przydzielić blok pamięci.|
|[CGlobalHeap::Za darmo](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.|
|[CGlobalHeap::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać przydzielony rozmiar bloku pamięci przydzielone przez tego menedżera pamięci.|
|[CGlobalHeap::Ponowne przydzielenie](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić pamięć przydzieloną przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CGlobalHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji sterty globalnej Win32.

> [!NOTE]
> Globalne funkcje sterty są wolniejsze niż inne funkcje zarządzania pamięcią i nie zapewniają tak wielu funkcji. W związku z tym nowe aplikacje powinny używać [funkcji sterty](/windows/win32/Memory/heap-functions). Są one dostępne w [CWin32Heap](../../atl/reference/cwin32heap-class.md) klasy. Funkcje globalne są nadal używane przez DDE i funkcje schowka.

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

## <a name="cglobalheapallocate"></a><a name="allocate"></a>CGlobalHeap::Przydziel

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

Wywołanie [CGlobalHeap::Free](#free) lub [CGlobalHeap::Reallocate,](#reallocate) aby zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) z parametrem flagi GMEM_FIXED.

## <a name="cglobalheapfree"></a><a name="free"></a>CGlobalHeap::Za darmo

Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci. NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowano przy użyciu [programu GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

## <a name="cglobalheapgetsize"></a><a name="getsize"></a>CGlobalHeap::GetSize

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

Zaimplementowano przy użyciu [globalsize](/windows/win32/api/winbase/nf-winbase-globalsize).

## <a name="cglobalheapreallocate"></a><a name="reallocate"></a>CGlobalHeap::Ponowne przydzielenie

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

Wywołanie [CGlobalHeap::Free](#free) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [pliku GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[CWin32Klasa heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
