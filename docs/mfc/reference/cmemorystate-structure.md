---
title: Struktura CMemoryState | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CMemoryState
dev_langs:
- C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 17da583b770fcab1d682868c38c04e0aa97155dd
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39026436"
---
# <a name="cmemorystate-structure"></a>Struktura CMemoryState
Zapewnia wygodny sposób wykrywania przecieki pamięci w programie.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|Tworzy strukturę typu klasa, która określa punkty kontrolne w pamięci.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|Pobiera migawkę bieżącego stanu pamięci (punktu kontrolnego).|  
|[CMemoryState::Difference](#difference)|Oblicza różnicę między dwoma obiektami typu `CMemoryState`.|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Zrzuca podsumowanie wszystkie aktualnie przydzielone obiekty od poprzedniego punktu kontrolnego.|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|Wyświetla statystyki alokacji pamięci dla `CMemoryState` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CMemoryState` jest to struktura i nie ma klasy bazowej.  
  
 "Przeciek pamięci" występuje, gdy pamięć dla obiektu jest przydzielony na stosie, ale nie cofnięto przydziału, gdy nie jest już wymagany. Takie przecieki pamięci po pewnym czasie może prowadzić do błędów braku pamięci. Istnieje kilka sposobów, aby przydzielić i cofanie przydziału pamięci w programie:  
  
-   Za pomocą `malloc` /  `free` rodziny funkcji z biblioteki wykonawczej.  
  
-   Za pomocą interfejsu API Windows funkcje zarządzania pamięcią, `LocalAlloc` /  `LocalFree` i `GlobalAlloc` /  `GlobalFree`.  
  
-   Przy użyciu języka C++ **nowe** i **Usuń** operatorów.  
  
 `CMemoryState` Diagnostyki tylko wykrywania pamięci przecieki przyczyną pamięci przydzielony przy użyciu **nowe** operator nie cofnięto przydziału przy użyciu **Usuń**. Dwie grupy zarządzania pamięcią funkcji są przeznaczone dla programów C++ inny niż i mieszanie ich za pomocą **nowe** i **Usuń** w ten sam program nie jest zalecane. Dodatkowe — makro DEBUG_NEW, znajduje się zastąpić **nowe** operatora, gdy będziesz potrzebować pliku i numer wiersza śledzenia alokacji pamięci. DEBUG_NEW jest używana zawsze, gdy zwykle są używane **nowe** operatora.  
  
 Podobnie jak w przypadku innych diagnostyki `CMemoryState` diagnostyki są dostępne tylko w wersji debugowania programu. Wersja do debugowania musi mieć stałą _DEBUG zdefiniowane.  
  
 Jeśli podejrzewasz, program nie ma przeciek pamięci, możesz użyć `Checkpoint`, `Difference`, i `DumpStatistics` funkcji odnajdywania różnica między stanu pamięci (przydzielone obiekty) w dwóch różnych punktach wykonywania programu. Te informacje mogą być przydatne w określaniu, czy funkcja czyści wszystkie obiekty, które go przydziela.  
  
 Jeśli po prostu, wiedząc, gdzie występuje nierównowagi alokacji i dezalokacji nie dostarczać wystarczających informacji, możesz użyć `DumpAllObjectsSince` zrzut wszystkich obiektach przydzielonych od poprzedniego wywołania do funkcji `Checkpoint`. Ten zrzut przedstawia kolejność alokacji, plik źródłowy i wiersza, w którym obiekt został przydzielony (Jeśli używasz DEBUG_NEW alokacji), i wyprowadzania obiektu, jej adres oraz jego rozmiaru. `DumpAllObjectsSince` Ponadto wywołuje każdy obiekt `Dump` funkcję, aby podać informacje o bieżącym stanie.  
  
 Aby uzyskać więcej informacji o sposobie używania `CMemoryState` i inne dane diagnostyczne, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Deklaracje obiektów typu `CMemoryState` i wywołania funkcji elementów członkowskich powinna być oddzielona przez `#if defined(_DEBUG)/#endif` dyrektywy. To powoduje, że Diagnostyka pamięci, które mają zostać uwzględnione tylko w przypadku debugowania kompilacji programu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CMemoryState`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="checkpoint"></a>  CMemoryState::Checkpoint  
 Tworzy migawkę podsumowania pamięci i zapisuje go w tym `CMemoryState` obiektu.  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>Uwagi  
 `CMemoryState` Elementów członkowskich [różnica](#difference) i [DumpAllObjectsSince](#dumpallobjectssince) Użyj danych z migawki.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMemoryState](#cmemorystate) konstruktora.  
  
##  <a name="cmemorystate"></a>  CMemoryState::CMemoryState  
 Tworzy pustą `CMemoryState` obiekt, który musi być wypełnione przez [punktu kontrolnego](#checkpoint) lub [różnica](#difference) funkcja elementu członkowskiego.  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>  CMemoryState::Difference  
 Porównuje dwa `CMemoryState` obiektów, a następnie zapisuje różnicę to `CMemoryState` obiektu.  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>Parametry  
 *oldState*  
 Stan pamięci początkowej, zgodnie z definicją `CMemoryState` punktu kontrolnego.  
  
 *Nowy stan*  
 Nowy stan pamięci określonych przez `CMemoryState` punktu kontrolnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wartość różną od zera, jeśli stanami dwóch pamięci są różne; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [Punkt kontrolny](#checkpoint) musi wywołana dla każdego z tych dwóch parametrów stanu pamięci.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMemoryState](#cmemorystate) konstruktora.  
  
##  <a name="dumpallobjectssince"></a>  CMemoryState::DumpAllObjectsSince  
 Wywołania `Dump` funkcji dla wszystkich obiektów typu pochodną klasy `CObject` która została przydzielona (i nadal są przydzielane) od momentu ostatniego [punktu kontrolnego](#checkpoint) wywołanie tego `CMemoryState` obiektu.  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>Uwagi  
 Wywoływanie `DumpAllObjectsSince` z niezainicjowaną `CMemoryState` obiektu będzie zrzutu się wszystkie obiekty aktualnie w pamięci.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMemoryState](#cmemorystate) konstruktora.  
  
##  <a name="dumpstatistics"></a>  CMemoryState::DumpStatistics  
 Drukuje raport statystyki pamięci zwięzłe z `CMemoryState` obiekt, który jest wypełniana przez [różnica](#difference) funkcja elementu członkowskiego.  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>Uwagi  
 Raport, który zostanie wydrukowany na [afxDump](diagnostic-services.md#afxdump) urządzenia zawiera następujące czynności:  
  
 Przykładowy raport zawiera informacje na numer (lub ilość) dla:  
  
-   bezpłatne bloków  
  
-   bloków normalnych  
  
-   Bloki CRT  
  
-   bloki do ignorowania  
  
-   bloki klienta  
  
-   maksymalne użycie pamięci przez program w dowolnym momencie (w bajtach)  
  
-   Całkowita pamięć, aktualnie używane przez program (w bajtach)  
  
 Wolne bloki to liczba bloków, których dezalokacji została opóźniona, jeśli `afxMemDF` została ustawiona na `delayFreeMemDF`. Aby uzyskać więcej informacji, zobacz [afxmemdf —](diagnostic-services.md#afxmemdf), w sekcji "Makra i globalne MFC". Zobacz [typy bloków na stercie debugowania](http://msdn.microsoft.com/db2e7f62-0679-4b39-a23f-26f2c2f407c5) dla więcej informacji na ten temat blokowania typów.  
  
### <a name="example"></a>Przykład  
  Poniższy kod, należy umieścić w *projname*App.cpp. Zdefiniuj następujące zmienne globalne:  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 W `InitInstance` funkcji, Dodaj wiersz:  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 Dodaj program obsługi `ExitInstance` działać, a następnie użyj poniższego kodu:  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 Teraz możesz uruchomić program w trybie debugowania, aby wyświetlić dane wyjściowe `DumpStatistics` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



