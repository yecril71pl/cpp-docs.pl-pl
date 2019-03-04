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
ms.openlocfilehash: 35c12a58adc846e0db6d7ee23f19984acbcfa861
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57297258"
---
# <a name="cwin32heap-class"></a>Klasa CWin32Heap

Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji sterty Win32.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

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
|[CWin32Heap::Allocate](#allocate)|Przydziela blok pamięci z obiektu sterty.|
|[CWin32Heap::Attach](#attach)|Dołącza obiekt sterty do istniejącej sterty.|
|[CWin32Heap::Detach](#detach)|Odłącza obiekt sterty od istniejącej sterty.|
|[CWin32Heap::Free](#free)|Zwalnia pamięci uprzednio przydzielony w stercie.|
|[CWin32Heap::GetSize](#getsize)|Zwraca rozmiar bloku pamięci zaalokowanej z obiekt sterty.|
|[CWin32Heap::Reallocate](#reallocate)|Przydzieli blok pamięci z obiektu sterty.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Flaga używana do określania bieżącego własności uchwyt sterty.|
|[CWin32Heap::m_hHeap](#m_hheap)|Uchwytu do obiektu sterty.|

## <a name="remarks"></a>Uwagi

`CWin32Heap` implementuje metody alokacji pamięci za pomocą funkcji alokacji sterty Win32, w tym [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc) i [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree). W przeciwieństwie do innych klas sterty `CWin32Heap` wymaga prawidłowym uchwytem sterty należy podać przed pamięć jest alokowana: innych klas domyślnie używa sterty procesu. Dojście mogą być dostarczane do konstruktora lub do [CWin32Heap::Attach](#attach) metody. Zobacz [CWin32Heap::CWin32Heap](#cwin32heap) metody, aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`IAtlMemMgr`

`CWin32Heap`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlmem.h

##  <a name="allocate"></a>  CWin32Heap::Allocate

Przydziela blok pamięci z obiektu sterty.

```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*nBytes*<br/>
Żądana liczba bajtów w nowy blok pamięci.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci nowo przydzielone.

### <a name="remarks"></a>Uwagi

Wywołaj [CWin32Heap::Free](#free) lub [CWin32Heap::Reallocate](#reallocate) zwolnienie pamięci przydzielonej przez tę metodę.

Implementowany przy użyciu [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc).

##  <a name="attach"></a>  CWin32Heap::Attach

Dołącza obiekt sterty do istniejącej sterty.

```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```

### <a name="parameters"></a>Parametry

*hHeap*<br/>
Istniejący uchwyt sterty.

*bTakeOwnership*<br/>
Jeśli wskazujące flagi `CWin32Heap` celem jest przejęcie na własność nad zasobami sterty.

### <a name="remarks"></a>Uwagi

Jeśli *bTakeOwnership* ma wartość PRAWDA, `CWin32Heap` obiekt jest odpowiedzialny za usunięcie uchwyt sterty.

##  <a name="cwin32heap"></a>  CWin32Heap::CWin32Heap

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

*dwFlags*<br/>
Flagi używane do tworzenia sterty.

*nInitialSize*<br/>
Początkowy rozmiar sterty.

*nMaxSize*<br/>
Maksymalny rozmiar sterty.

### <a name="remarks"></a>Uwagi

Przed przydzieleniem pamięci jest zapewnienie `CWin32Heap` obiektu z prawidłowym uchwytem sterty. Najprościej to osiągnąć przy użyciu sterty procesu:

[!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]

Użytkownik może również dostarczyć istniejący uchwyt sterty do konstruktora, w którym to przypadku nowy obiekt nie przejmuje sterty na własność. Oryginalny uchwyt sterty nadal będzie ważny po `CWin32Heap` obiekt zostanie usunięty.

Istniejącą stertę można również dołączyć do nowego obiektu przy użyciu [CWin32Heap::Attach](#attach).

Jeśli sterta jest wymagana tam, gdzie wszystkie operacje są wykonywane z jednego wątku, najlepszym sposobem jest utworzenie obiektu w następujący sposób:

[!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]

Parametr HEAP_NO_SERIALIZE Określa, że wzajemne wykluczenie nie będą używane, gdy funkcje sterty przydzielają i zwalniają pamięć, z adekwatnym wzrostem wydajności.

Domyślne ustawienie trzeciego parametru to 0, dzięki czemu sterta może się rozrastać zgodnie z potrzebami. Zobacz [HeapCreate](/windows/desktop/api/heapapi/nf-heapapi-heapcreate) objaśnienia dotyczące rozmiarów pamięci i flag.

##  <a name="dtor"></a>  CWin32Heap:: ~ CWin32Heap

Destruktor.

```
~CWin32Heap() throw();
```

### <a name="remarks"></a>Uwagi

Niszczy uchwyt sterty, jeśli `CWin32Heap` obiekt ma sterty na własność.

##  <a name="detach"></a>  CWin32Heap::Detach

Odłącza obiekt sterty od istniejącej sterty.

```
HANDLE Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca uchwyt sterty, do której wcześniej był dołączony obiekt.

##  <a name="free"></a>  CWin32Heap::Free

Powoduje zwolnienie pamięci uprzednio przydzielonej ze stosu przez [CWin32Heap::Allocate](#allocate) lub [CWin32Heap::Reallocate](#reallocate).

```
virtual void Free(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do bloku pamięci, aby zwolnić. Wartość NULL jest prawidłową wartością i nic nie robi.

##  <a name="getsize"></a>  CWin32Heap::GetSize

Zwraca rozmiar bloku pamięci zaalokowanej z obiekt sterty.

```
virtual size_t GetSize(void* p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do bloku pamięci, której rozmiar osiągnie metody. Jest to wskaźnik zwracany przez [CWin32Heap::Allocate](#allocate) lub [CWin32Heap::Reallocate](#reallocate).

### <a name="return-value"></a>Wartość zwracana

Zwraca rozmiar w bajtach, blok pamięci przydzielony.

##  <a name="m_bownheap"></a>  CWin32Heap::m_bOwnHeap

Flagi używane do określania bieżącego własności uchwyt sterty, przechowywane w [m_hHeap](#m_hheap).

```
bool m_bOwnHeap;
```

##  <a name="m_hheap"></a>  CWin32Heap::m_hHeap

Uchwytu do obiektu sterty.

```
HANDLE m_hHeap;
```

### <a name="remarks"></a>Uwagi

Zmienna, używany do przechowywania dojścia do obiektu sterty.

##  <a name="reallocate"></a>  CWin32Heap::Reallocate

Przydzieli blok pamięci z obiektu sterty.

```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
Wskaźnik do bloku pamięci w celu ponownego przydzielenia.

*nBytes*<br/>
Nowy rozmiar w bajtach przydzielonego bloku. Blok jest możliwe większy lub mniejszy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do bloku pamięci nowo przydzielone.

### <a name="remarks"></a>Uwagi

Jeśli *p* ma wartość NULL, zakłada się, że blok pamięci nie jest jeszcze przydzielone i [CWin32Heap::Allocate](#allocate) jest wywoływana z argumentem *nBytes*.

## <a name="see-also"></a>Zobacz także

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)<br/>
[Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)<br/>
[Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)<br/>
[Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)<br/>
[Klasa CComHeap](../../atl/reference/ccomheap-class.md)
