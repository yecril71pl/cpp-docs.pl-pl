---
title: Klasa CComHeap
ms.date: 11/04/2016
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
ms.openlocfilehash: 1ded73047b895a44a22bdd5730886f7fc088c77a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497348"
---
# <a name="ccomheap-class"></a>Klasa CComHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji pamięci com.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComHeap:: Allocate](#allocate)|Wywołaj tę metodę, aby przydzielić blok pamięci.|
|[CComHeap:: Free](#free)|Wywołaj tę metodę, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.|
|[CComHeap:: GetSize](#getsize)|Wywołaj tę metodę, aby uzyskać przydzielonego rozmiaru bloku pamięci przydzielonego przez ten Menedżer pamięci.|
|[CComHeap:: Reallocate](#reallocate)|Wywołaj tę metodę, aby ponownie przydzielić pamięć przydzieloną przez ten Menedżer pamięci.|

## <a name="remarks"></a>Uwagi

`CComHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji alokacji COM, w tym [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [Alloc:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)i [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Maksymalna ilość pamięci, którą można przydzieleniu, jest równa INT_MAX (2147483647) bajtów.

## <a name="example"></a>Przykład

Zobacz przykład dla [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Wymagania

**Nagłówki** ATLComMem.h

##  <a name="allocate"></a>CComHeap:: Allocate

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

Wywołanie [CComHeap:: Free](#free) lub [CComHeap:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

Zaimplementowane przy użyciu [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

##  <a name="free"></a>CComHeap:: Free

Wywołaj tę metodę, aby zwolnić blok pamięci przydzielonej przez ten Menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do pamięci przydzielonej wcześniej przez ten Menedżer pamięci. Wartość NULL jest prawidłowa i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowane przy użyciu [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

##  <a name="getsize"></a>CComHeap:: GetSize

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

Zaimplementowane przy użyciu funkcji [allocd:: GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

##  <a name="reallocate"></a>CComHeap:: Reallocate

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

Wywołaj [CComHeap:: Free](#free) , aby zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowane przy użyciu [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Zobacz także

[Przykład DynamicConsumer](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa CWin32Heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
