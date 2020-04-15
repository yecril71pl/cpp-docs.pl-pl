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
ms.openlocfilehash: a38d1147e718870c03af84ec1487e226805b956e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327820"
---
# <a name="ccomheap-class"></a>Klasa CComHeap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji pamięci COM.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CComHeap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComHeap::Przydziel](#allocate)|Wywołanie tej metody, aby przydzielić blok pamięci.|
|[CComHeap::Za darmo](#free)|Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.|
|[CComHeap::GetSize](#getsize)|Wywołanie tej metody, aby uzyskać przydzielony rozmiar bloku pamięci przydzielone przez tego menedżera pamięci.|
|[CComHeap::Ponowne przydzielenie](#reallocate)|Wywołanie tej metody, aby ponownie przydzielić pamięć przydzieloną przez tego menedżera pamięci.|

## <a name="remarks"></a>Uwagi

`CComHeap`implementuje funkcje alokacji pamięci przy użyciu funkcji alokacji COM, w tym [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree), [IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize)i [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc). Maksymalna ilość pamięci, która może być przydzielona jest równa INT_MAX (2147483647) bajtów.

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CComHeap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** ATLComMem.h

## <a name="ccomheapallocate"></a><a name="allocate"></a>CComHeap::Przydziel

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

Wywołanie [CComHeap::Free](#free) lub [CComHeap::Reallocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [cotaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc).

## <a name="ccomheapfree"></a><a name="free"></a>CComHeap::Za darmo

Wywołanie tej metody, aby zwolnić blok pamięci przydzielone przez ten menedżer pamięci.

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do pamięci wcześniej przydzielonej przez tego menedżera pamięci. NULL jest prawidłową wartością i nic nie robi.

### <a name="remarks"></a>Uwagi

Zaimplementowano przy użyciu [cotaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree).

## <a name="ccomheapgetsize"></a><a name="getsize"></a>CComHeap::GetSize

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

Zaimplementowano przy użyciu [funkcji IMalloc::GetSize](/windows/win32/api/objidlbase/nf-objidlbase-imalloc-getsize).

## <a name="ccomheapreallocate"></a><a name="reallocate"></a>CComHeap::Ponowne przydzielenie

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

Wywołanie [CComHeap::Free](#free) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [cotaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc).

## <a name="see-also"></a>Zobacz też

[Przykład dynamicznego konsumera](../../overview/visual-cpp-samples.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[CWin32Klasa heap](../../atl/reference/cwin32heap-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)
