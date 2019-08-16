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
ms.openlocfilehash: 2b5aa09357ddcc77b6b10de58545bea86eff2488
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496762"
---
# <a name="cglobalheap-class"></a>Klasa CGlobalHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu globalnych funkcji sterty Win32.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CGlobalHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CGlobalHeap:: Allocate](#allocate)|Wywołaj tę metodę, aby przydzielić blok pamięci.|
|[CGlobalHeap:: Free](#free)|Wywołaj tę metodę, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|
|[CGlobalHeap:: GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielonego rozmiaru bloku pamięci przydzielonego przez ten Menedżer pamięci.|
|[CGlobalHeap:: Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięć przydzieloną przez ten Menedżer pamięci.|

## <a name="remarks"></a>Uwagi

`CGlobalHeap`implementuje funkcje alokacji pamięci przy użyciu globalnych funkcji sterty Win32.

> [!NOTE]
>  Globalne funkcje sterty są wolniejsze niż inne funkcje zarządzania pamięcią i nie zapewniają jak wielu funkcji. W związku z tym nowe aplikacje powinny używać [funkcji sterty](/windows/win32/Memory/heap-functions). Są one dostępne w klasie [CWin32Heap](../../atl/reference/cwin32heap-class.md) . Funkcje globalne są nadal używane przez DDE i funkcje Schowka.

## <a name="example"></a>Przykład

Zobacz przykład dla [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CGlobalHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem. h

##  <a name="allocate"></a>CGlobalHeap:: Allocate

Wywołaj tę metodę, aby przydzielić blok pamięci.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [CGlobalHeap:: Free](#free) lub [CGlobalHeap:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

Zaimplementowane przy użyciu [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc) z parametrem flagi GMEM_FIXED.

##  <a name="free"></a>CGlobalHeap:: Free

Wywołaj tę metodę, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci. Wartość NULL jest prawidłowa i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowane przy użyciu [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree).

##  <a name="getsize"></a>CGlobalHeap:: GetSize

Wywołaj tę metodę, aby uzyskać przydzielonego rozmiaru bloku pamięci przydzielonego przez ten Menedżer pamięci.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar przydzielony blok pamięci w bajtach.

### <a name="remarks"></a>Uwagi

Zaimplementowane przy użyciu [GlobalSize](/windows/win32/api/winbase/nf-winbase-globalsize).

##  <a name="reallocate"></a>CGlobalHeap:: Reallocate

Wywołaj tę metodę, aby ponownie przydzielić pamięć przydzieloną przez ten Menedżer pamięci.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci.

*nBytes*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do początku nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj [CGlobalHeap:: Free](#free) , aby zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowane przy użyciu [GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
