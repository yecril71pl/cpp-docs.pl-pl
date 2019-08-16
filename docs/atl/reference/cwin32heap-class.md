---
title: Klasa CWin32Heap
ms.date: 11/04/2016
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
ms.openlocfilehash: ce3585310198ee3e2d7b2b8b829f4202b1021284
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496201"
---
# <a name="cwin32heap-class"></a>Klasa CWin32Heap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji sterty Win32.

> [!IMPORTANT]
>  Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w środowisko wykonawcze systemu Windows.

## <a name="syntax"></a>Składnia

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap:: CWin32Heap](#cwin32heap)|Konstruktor.|
|[CWin32Heap:: ~ CWin32Heap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap:: Allocate](#allocate)|Przydziela blok pamięci z obiektu sterty.|
|[CWin32Heap:: Attach](#attach)|Dołącza obiekt sterty do istniejącej sterty.|
|[CWin32Heap::D etach](#detach)|Odłącza obiekt sterty od istniejącej sterty.|
|[CWin32Heap:: Free](#free)|Zwalnia pamięć wcześniej przydzieloną ze sterty.|
|[CWin32Heap:: GetSize](#getsize)|Zwraca rozmiar bloku pamięci przydzieloną z obiektu sterty.|
|[CWin32Heap:: Reallocate](#reallocate)|Ponownie przydziela blok pamięci z obiektu sterty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Flaga służąca do określenia bieżącego własności dojścia sterty.|
|[CWin32Heap::m_hHeap](#m_hheap)|Dojście do obiektu sterty.|

## <a name="remarks"></a>Uwagi

`CWin32Heap`implementuje metody alokacji pamięci przy użyciu funkcji alokacji sterty Win32, w tym [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) i [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). W przeciwieństwie do innych klas `CWin32Heap` sterty, wymaga podania prawidłowego uchwytu sterty przed przydzieleniem pamięci: inne klasy domyślnie używają sterty procesu. Dojście może być dostarczone do konstruktora lub do metody [CWin32Heap:: Attach](#attach) . Aby uzyskać więcej informacji, zobacz metodę [CWin32Heap:: CWin32Heap](#cwin32heap) .

## <a name="example"></a>Przykład

Zobacz przykład dla [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem. h

##  <a name="allocate"></a>CWin32Heap:: Allocate

Przydziela blok pamięci z obiektu sterty.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [CWin32Heap:: Free](#free) lub [CWin32Heap:: Reallocate](#reallocate) w celu zwolnienia pamięci przydzielonej przez tę metodę.

Zaimplementowane przy użyciu [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

##  <a name="attach"></a>CWin32Heap:: Attach

Dołącza obiekt sterty do istniejącej sterty.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parametry

*hHeap*<br/>
Istniejące dojście sterty.

*bTakeOwnership*<br/>
Flaga wskazująca, `CWin32Heap` czy obiekt ma przejąć na własność zasoby sterty.

### <a name="remarks"></a>Uwagi

Jeśli *bTakeOwnership* ma wartość true, `CWin32Heap` obiekt jest odpowiedzialny za usunięcie dojścia sterty.

##  <a name="cwin32heap"></a>CWin32Heap:: CWin32Heap

Konstruktor.

```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```

### <a name="parameters"></a>Parametry

*hHeap*<br/>
Istniejący obiekt sterty.

*flagiDW*<br/>
Flagi używane do tworzenia sterty.

*nInitialSize*<br/>
Początkowy rozmiar sterty.

*nMaxSize*<br/>
Maksymalny rozmiar sterty.

### <a name="remarks"></a>Uwagi

Przed przydzieleniem pamięci należy podać `CWin32Heap` obiekt z prawidłowym dojściem sterty. Najprościej to osiągnąć przy użyciu sterty procesu:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Użytkownik może również dostarczyć istniejący uchwyt sterty do konstruktora, w którym to przypadku nowy obiekt nie przejmuje sterty na własność. Oryginalne dojście sterty będzie nadal obowiązywać po `CWin32Heap` usunięciu obiektu.

Istniejącą stertę można również dołączyć do nowego obiektu przy użyciu [CWin32Heap:: Attach](#attach).

Jeśli sterta jest wymagana tam, gdzie wszystkie operacje są wykonywane z jednego wątku, najlepszym sposobem jest utworzenie obiektu w następujący sposób:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Parametr HEAP_NO_SERIALIZE określa, że wzajemne wykluczenie nie będzie używane, gdy funkcje sterty przydzielą i zwalniają pamięć, z uwzględnieniem wzrostu wydajności.

Domyślne ustawienie trzeciego parametru to 0, dzięki czemu sterta może się rozrastać zgodnie z potrzebami. Zobacz [HeapCreate](/windows/win32/api/heapapi/nf-heapapi-heapcreate) , aby uzyskać wyjaśnienie rozmiaru i flag pamięci.

##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap

Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Uwagi

Niszczy uchwyt sterty, jeśli `CWin32Heap` obiekt ma własność sterty.

##  <a name="detach"></a>CWin32Heap::D etach

Odłącza obiekt sterty od istniejącej sterty.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt do sterty, do której obiekt został wcześniej dołączony.

##  <a name="free"></a>CWin32Heap:: Free

Zwalnia pamięć wcześniej przydzieloną ze sterty przez [CWin32Heap:: Allocate](#allocate) lub [CWin32Heap:: Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do bloku pamięci do zwolnienia. Wartość NULL jest prawidłowa i nic nie robi.

##  <a name="getsize"></a>CWin32Heap:: GetSize

Zwraca rozmiar bloku pamięci przydzieloną z obiektu sterty.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do bloku pamięci, którego rozmiar zostanie uzyskany przez metodę. Jest to wskaźnik zwrócony przez [CWin32Heap:: Allocate](#allocate) lub [CWin32Heap:: Reallocate](#reallocate).

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar w bajtach przydzielony blok pamięci.

##  <a name="m_bownheap"></a>CWin32Heap:: m_bOwnHeap

Flaga używana do określania bieżącego własności dojścia sterty przechowywanej w [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>CWin32Heap:: m_hHeap

Dojście do obiektu sterty.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Uwagi

Zmienna używana do przechowywania dojścia do obiektu sterty.

##  <a name="reallocate"></a>CWin32Heap:: Reallocate

Ponownie przydziela blok pamięci z obiektu sterty.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do bloku pamięci do ponownego przydzielenia.

*nBytes*<br/>
Nowy rozmiar w bajtach przydzielonych bloków. Blok może być większy lub mniejszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do nowo przydzielony blok pamięci.

### <a name="remarks"></a>Uwagi

Jeśli *p* ma wartość null, zakłada się, że blok pamięci nie został jeszcze przydzielony i [CWin32Heap:: Allocate](#allocate) jest wywoływana, z argumentem *nBytes*.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)
