---
title: CWin32Klasa heap
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
ms.openlocfilehash: 2d79de308b1afb3059cf04ad40b63b6e603073c8
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746028"
---
# <a name="cwin32heap-class"></a>CWin32Klasa heap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji sterty Win32.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
class CWin32Heap : public IAtlMemMgr
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap::CWin32Heap](#cwin32heap)|Konstruktor.|
|[CWin32Heap::~CWin32Heap](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap::Przydziel](#allocate)|Przydziela blok pamięci z obiektu sterty.|
|[CWin32Heap::Dołącz](#attach)|Dołącza obiekt sterty do istniejącej sterty.|
|[CWin32Heap::Detach](#detach)|Odłącza obiekt sterty od istniejącej sterty.|
|[CWin32Heap::Wolny](#free)|Zwalnia pamięć wcześniej przydzieloną ze sterty.|
|[CWin32Heap::GetSize](#getsize)|Zwraca rozmiar bloku pamięci przydzielonego z obiektu sterty.|
|[CWin32Heap::Ponowne przydzielenie](#reallocate)|Ponownie przydziela blok pamięci z obiektu sterty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Flaga używana do określenia bieżącej własności uchwytu sterty.|
|[CWin32Heap::m_hHeap](#m_hheap)|Dojście do obiektu sterty.|

## <a name="remarks"></a>Uwagi

`CWin32Heap`implementuje metody alokacji pamięci przy użyciu funkcji alokacji sterty Win32, w tym [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc) i [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree). W przeciwieństwie do `CWin32Heap` innych klas sterty, wymaga prawidłowego dojścia sterty, które mają być dostarczone przed przydzieleniem pamięci: inne klasy domyślnie przy użyciu sterty procesu. Dojście może być dostarczone do konstruktora lub [CWin32Heap::Attach](#attach) metody. Zobacz [CWin32Heap::CWin32Nap.](#cwin32heap)

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

## <a name="cwin32heapallocate"></a><a name="allocate"></a>CWin32Heap::Przydziel

Przydziela blok pamięci z obiektu sterty.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Żądana liczba bajtów w nowym bloku pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie [CWin32Heap::Free](#free) lub [CWin32Heap::Reallocate](#reallocate) zwolnić pamięć przydzieloną przez tę metodę.

Zaimplementowano przy użyciu [funkcji HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc).

## <a name="cwin32heapattach"></a><a name="attach"></a>CWin32Heap::Dołącz

Dołącza obiekt sterty do istniejącej sterty.

```cpp
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parametry

*hHeap (Heap)*<br/>
Istniejący uchwyt sterty.

*bWłażanie*<br/>
Flaga wskazująca, `CWin32Heap` czy obiekt ma przejąć na własność zasoby sterty.

### <a name="remarks"></a>Uwagi

Jeśli *bTakeOwnership* jest `CWin32Heap` TRUE, obiekt jest odpowiedzialny za usunięcie uchwyt sterty.

## <a name="cwin32heapcwin32heap"></a><a name="cwin32heap"></a>CWin32Heap::CWin32Heap

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

*hHeap (Heap)*<br/>
Istniejący obiekt sterty.

*Dwflags*<br/>
Flagi używane do tworzenia sterty.

*nInitialSize*<br/>
Początkowy rozmiar sterty.

*rozmiar nMaxSize*<br/>
Maksymalny rozmiar sterty.

### <a name="remarks"></a>Uwagi

Przed przydzieleniem pamięci należy zapewnić `CWin32Heap` obiektowi prawidłowy uchwyt sterty. Najprościej to osiągnąć przy użyciu sterty procesu:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Użytkownik może również dostarczyć istniejący uchwyt sterty do konstruktora, w którym to przypadku nowy obiekt nie przejmuje sterty na własność. Oryginalny uchwyt sterty będzie nadal `CWin32Heap` prawidłowy po usunięciu obiektu.

Istniejący stos można również dołączyć do nowego obiektu, używając [CWin32Heap::Attach](#attach).

Jeśli sterta jest wymagana tam, gdzie wszystkie operacje są wykonywane z jednego wątku, najlepszym sposobem jest utworzenie obiektu w następujący sposób:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Parametr HEAP_NO_SERIALIZE określa, że wzajemne wykluczenie nie będzie używane, gdy funkcje sterty przydzielić i wolnej pamięci, ze wzrostem wydajności.

Domyślne ustawienie trzeciego parametru to 0, dzięki czemu sterta może się rozrastać zgodnie z potrzebami. Zobacz [HeapCreate wyjaśnienie](/windows/win32/api/heapapi/nf-heapapi-heapcreate) rozmiarów pamięci i flag.

## <a name="cwin32heapcwin32heap"></a><a name="dtor"></a>CWin32Heap::~CWin32Heap

Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Uwagi

Niszczy uchwyt sterty, `CWin32Heap` jeśli obiekt ma własność sterty.

## <a name="cwin32heapdetach"></a><a name="detach"></a>CWin32Heap::Detach

Odłącza obiekt sterty od istniejącej sterty.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca dojście do stosu, do którego obiekt został wcześniej dołączony.

## <a name="cwin32heapfree"></a><a name="free"></a>CWin32Heap::Wolny

Zwalnia pamięć wcześniej przydzieloną ze sterty przez [CWin32Heap::Allocate](#allocate) lub [CWin32Heap::Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do bloku pamięci, aby zwolnić. NULL jest prawidłową wartością i nic nie robi.

## <a name="cwin32heapgetsize"></a><a name="getsize"></a>CWin32Heap::GetSize

Zwraca rozmiar bloku pamięci przydzielonego z obiektu sterty.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do bloku pamięci, którego rozmiar metoda zostanie uzyskana. Jest to wskaźnik zwrócony przez [CWin32Heap::Allocate](#allocate) lub [CWin32Heap::Reallocate](#reallocate).

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar przydzielonego bloku pamięci w bajtach.

## <a name="cwin32heapm_bownheap"></a><a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap

Flaga używana do określenia bieżącej własności uchwytu sterty przechowywanego w [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

## <a name="cwin32heapm_hheap"></a><a name="m_hheap"></a>CWin32Heap::m_hHeap

Dojście do obiektu sterty.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Uwagi

Zmienna używana do przechowywania dojścia do obiektu sterty.

## <a name="cwin32heapreallocate"></a><a name="reallocate"></a>CWin32Heap::Ponowne przydzielenie

Ponownie przydziela blok pamięci z obiektu sterty.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
Wskaźnik do bloku pamięci, aby ponownie przydzielić.

*n Bajty*<br/>
Nowy rozmiar w bajtach przydzielonego bloku. Blok może być większy lub mniejszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do nowo przydzielonego bloku pamięci.

### <a name="remarks"></a>Uwagi

Jeśli *p* ma wartość NULL, zakłada się, że blok pamięci nie został jeszcze przydzielony, a [CWin32Heap::Allocate](#allocate) jest wywoływany, z argumentem *nBytes*.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)
