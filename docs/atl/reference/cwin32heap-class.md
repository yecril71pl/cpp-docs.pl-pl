---
title: Klasa CWin32Heap | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9b26d979ccb99d3d99bc91af03c4836603d31c01
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="cwin32heap-class"></a>Klasa CWin32Heap
Ta klasa implementuje [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) przy użyciu funkcji alokacji sterty Win32.  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
class CWin32Heap : public IAtlMemMgr
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWin32Heap::CWin32Heap](#cwin32heap)|Konstruktor.|  
|[CWin32Heap:: ~ CWin32Heap](#dtor)|Destruktor.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWin32Heap::Allocate](#allocate)|Przydziela bloku pamięci z obiektu heap.|  
|[CWin32Heap::Attach](#attach)|Dołącza obiektu heap do istniejącego stosu.|  
|[CWin32Heap::Detach](#detach)|Odłącza obiektu sterty z istniejącego stosu.|  
|[CWin32Heap::Free](#free)|Zwalnia pamięć przydzielona wcześniej ze stosu.|  
|[CWin32Heap::GetSize](#getsize)|Zwraca rozmiar blok pamięci przydzielony z obiektu heap.|  
|[CWin32Heap::Reallocate](#reallocate)|Przydziela ponownie blok pamięci z obiektu heap.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Flaga używana do określenia bieżącego prawa własności dojścia stosu.|  
|[CWin32Heap::m_hHeap](#m_hheap)|Dojście do obiektu heap.|  
  
## <a name="remarks"></a>Uwagi  
 `CWin32Heap` implementuje metody alokacji pamięci za pomocą funkcji alokacji sterty Win32, w tym [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) i [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701). W przeciwieństwie do innych klas sterty `CWin32Heap` wymaga dojścia prawidłowy sterty należy wprowadzić, aby przydzielić pamięci: wartość domyślna klasy przy użyciu sterty procesu. Dojście mogą być dostarczane do konstruktora lub do [CWin32Heap::Attach](#attach) metody. Zobacz [CWin32Heap::CWin32Heap](#cwin32heap) metody, aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Zobacz przykład [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlmem.h  
  
##  <a name="allocate"></a>  CWin32Heap::Allocate  
 Przydziela bloku pamięci z obiektu heap.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `nBytes`  
 Żądana liczba bajtów w nowego bloku pamięci.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie [CWin32Heap::Free](#free) lub [CWin32Heap::Reallocate](#reallocate) zwolnienia pamięci przydzielonej przez tę metodę.  
  
 Implementowane za pomocą [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597).  
  
##  <a name="attach"></a>  CWin32Heap::Attach  
 Dołącza obiektu heap do istniejącego stosu.  
  
```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `hHeap`  
 Dojście do istniejących sterty.  
  
 `bTakeOwnership`  
 Jeśli wskazujące flagi `CWin32Heap` obiekt ma przejąć prawo własności zasobów sterty.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `bTakeOwnership` ma wartość PRAWDA, `CWin32Heap` obiektu jest odpowiedzialny za usuwanie dojście stosu.  
  
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
 `hHeap`  
 Istniejący obiekt sterty.  
  
 `dwFlags`  
 Flagi używane do tworzenia sterty.  
  
 *nInitialSize*  
 Początkowy rozmiar sterty.  
  
 `nMaxSize`  
 Maksymalny rozmiar sterty.  
  
### <a name="remarks"></a>Uwagi  
 Przed przydzielania pamięci, jest niezbędne do zapewnienia `CWin32Heap` obiektu z dojściem sterty prawidłowe. Najprościej to osiągnąć przy użyciu sterty procesu:  
  
 [!code-cpp[NVC_ATL_Utilities#92](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]  
  
 Użytkownik może również dostarczyć istniejący uchwyt sterty do konstruktora, w którym to przypadku nowy obiekt nie przejmuje sterty na własność. Oryginalny dojście sterty nadal będzie prawidłowy podczas `CWin32Heap` obiekt jest usunięty.  
  
 Istniejące sterty również można dołączyć do nowego obiektu, przy użyciu [CWin32Heap::Attach](#attach).  
  
 Jeśli sterta jest wymagana tam, gdzie wszystkie operacje są wykonywane z jednego wątku, najlepszym sposobem jest utworzenie obiektu w następujący sposób:  
  
 [!code-cpp[NVC_ATL_Utilities#93](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]  
  
 Parametr **HEAP_NO_SERIALIZE** Określa, że wzajemne wykluczenie nie będzie można używać, jeśli funkcje sterty przydzielić i zwolnić pamięć, zgodnie z zwiększania wydajności.  
  
 Domyślne ustawienie trzeciego parametru to 0, dzięki czemu sterta może się rozrastać zgodnie z potrzebami. Zobacz [HeapCreate](http://msdn.microsoft.com/library/windows/desktop/aa366599\(v=vs.85\).aspx) wyjaśnienie flagi i wielkości pamięci.  
  
##  <a name="dtor"></a>  CWin32Heap:: ~ CWin32Heap  
 Destruktor.  
  
```
~CWin32Heap() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Niszczy dojście sterty, jeśli `CWin32Heap` obiekt ma własność sterty.  
  
##  <a name="detach"></a>  CWin32Heap::Detach  
 Odłącza obiektu sterty z istniejącego stosu.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca dojście do stosu, do której obiekt był wcześniej dołączony.  
  
##  <a name="free"></a>  CWin32Heap::Free  
 Zwalnia pamięć przydzielona wcześniej ze stosu przez [CWin32Heap::Allocate](#allocate) lub [CWin32Heap::Reallocate](#reallocate).  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do bloku pamięci zwolnienia. Wartość NULL jest nieprawidłowa i nie działają.  
  
##  <a name="getsize"></a>  CWin32Heap::GetSize  
 Zwraca rozmiar blok pamięci przydzielony z obiektu heap.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do którego metoda będzie pobierał rozmiar bloku pamięci. Jest to wskaźnik zwrócony przez [CWin32Heap::Allocate](#allocate) lub [CWin32Heap::Reallocate](#reallocate).  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca rozmiar w bajtach blok pamięci przydzielony.  
  
##  <a name="m_bownheap"></a>  CWin32Heap::m_bOwnHeap  
 Flaga używana do określenia bieżącego prawa własności dojścia sterty przechowywane w [m_hHeap](#m_hheap).  
  
```
bool m_bOwnHeap;
```  
  
##  <a name="m_hheap"></a>  CWin32Heap::m_hHeap  
 Dojście do obiektu heap.  
  
```
HANDLE m_hHeap;
```  
  
### <a name="remarks"></a>Uwagi  
 Zmienna używany do przechowywania dojścia do obiektu heap.  
  
##  <a name="reallocate"></a>  CWin32Heap::Reallocate  
 Przydziela ponownie blok pamięci z obiektu heap.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 Wskaźnik do bloku pamięci, aby ponownie przydzielić.  
  
 `nBytes`  
 Nowy rozmiar w bajtach przydzielony blok. Blok jest możliwe większy lub mniejszy.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wskaźnik do bloku nowo alokacji pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `p` ma wartość NULL, zakłada się, że blok pamięci nie został jeszcze przydzielony i [CWin32Heap::Allocate](#allocate) jest wywoływana z argumentem `nBytes`.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [Klasa IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md)   
 [Klasa CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Klasa CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Klasa CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [Klasa CComHeap](../../atl/reference/ccomheap-class.md)
