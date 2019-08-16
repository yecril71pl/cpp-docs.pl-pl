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
ms.openlocfilehash: a302ba4ea55c42ce214c8de4a24be843d6cb1b9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496747"
---
# <a name="clocalheap-class"></a>Klasa CLocalHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji sterty lokalnej Win32.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CLocalHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CLocalHeap:: Allocate](#allocate)|Wywołaj tę metodę, aby przydzielić blok pamięci.|
|[CLocalHeap:: Free](#free)|Wywołaj tę metodę, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|
|[CLocalHeap:: GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielonego rozmiaru bloku pamięci przydzielonego przez ten Menedżer pamięci.|
|[CLocalHeap:: Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięć przydzieloną przez ten Menedżer pamięci.|

## <a name="remarks"></a>Uwagi

`CLocalHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji sterty lokalnej Win32.

> [!NOTE]
>  Funkcje sterty lokalnej są wolniejsze niż inne funkcje zarządzania pamięcią i nie zapewniają jak wielu funkcji. W związku z tym nowe aplikacje powinny używać [funkcji sterty](/windows/win32/Memory/heap-functions). Są one dostępne w klasie [CWin32Heap](../../atl/reference/cwin32heap-class.md) .

## <a name="example"></a>Przykład

Zobacz przykład dla [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CLocalHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem. h

##  <a name="allocate"></a>CLocalHeap:: Allocate

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

Wywołanie [CLocalHeap:: Free](#free) lub [CLocalHeap:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

Zaimplementowane przy użyciu [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc) z parametrem flagi LMEM_FIXED.

##  <a name="free"></a>CLocalHeap:: Free

Wywołaj tę metodę, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci. Wartość NULL jest prawidłowa i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowane przy użyciu [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree).

##  <a name="getsize"></a>CLocalHeap:: GetSize

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

Zaimplementowane przy użyciu [LocalSize](/windows/win32/api/winbase/nf-winbase-localsize).

##  <a name="reallocate"></a>CLocalHeap:: Reallocate

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

Wywołaj [CLocalHeap:: Free](#free) , aby zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowane przy użyciu [LocalReAlloc](/windows/win32/api/winbase/nf-winbase-localrealloc).

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)<br/>
[Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
