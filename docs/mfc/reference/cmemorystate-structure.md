---
title: Struktura CMemoryState | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: CMemoryState
dev_langs: C++
helpviewer_keywords:
- CMemoryState structure [MFC]
- memory leaks [MFC], detecting
- detecting memory leaks [MFC]
ms.assetid: 229d9de7-a6f3-4cc6-805b-5a9d9b1bfe1d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 20f4c2d7d33d07a5eca5a980c376056c3fe68e2d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cmemorystate-structure"></a>Struktura CMemoryState
Zapewnia to wygodny sposób wykrywania przecieki pamięci w programie.  
  
## <a name="syntax"></a>Składnia  
  
```  
struct CMemoryState  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemoryState::CMemoryState](#cmemorystate)|Struktura konstrukcje typu klasa, która steruje pamięci punkty kontrolne.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CMemoryState::Checkpoint](#checkpoint)|Pobiera bieżący stan pamięci migawkę (punktu kontrolnego).|  
|[CMemoryState::Difference](#difference)|Oblicza różnicę między dwoma obiektami typu `CMemoryState`.|  
|[CMemoryState::DumpAllObjectsSince](#dumpallobjectssince)|Zrzuty podsumowanie wszystkie aktualnie przydzielone obiekty od poprzedniego punktu kontrolnego.|  
|[CMemoryState::DumpStatistics](#dumpstatistics)|Wyświetla statystyki alokacji pamięci dla `CMemoryState` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CMemoryState`jest to struktura i nie ma klasy podstawowej.  
  
 "Przeciek pamięci" występuje, gdy pamięć dla obiekt jest przydzielony na stosie, ale nie alokację, gdy nie jest już wymagane. Takie przecieki pamięci po pewnym czasie może prowadzić do błędów braku pamięci. Istnieje kilka sposobów, aby przydzielić i cofnięcia przydzielenia pamięci w programie:  
  
-   Przy użyciu `malloc` /  **wolnego** rodziny funkcji z biblioteki czasu wykonywania.  
  
-   Przy użyciu interfejsu API systemu Windows funkcje zarządzania pamięcią, **Funkcja LocalAlloc**/ **LocalFree** i **działanie funkcji GlobalAlloc**/ **GlobalFree** .  
  
-   Za pomocą języka C++ **nowe** i **usunąć** operatorów.  
  
 `CMemoryState` Diagnostyki tylko wykrywania pamięci przecieki spowodowane pamięci przydzielony przy użyciu **nowe** operator nie cofnięciu przydziału przy użyciu **usunąć**. Dwie grupy zarządzania pamięcią funkcji dotyczą programów innych niż C++ i łączenie ich z **nowe** i **usunąć** w ten sam program nie jest zalecane. Dodatkowe makro `DEBUG_NEW`, znajduje się w celu zastąpienia **nowe** operatora, gdy będziesz potrzebować plików i numer wiersza śledzenia alokacji pamięci. `DEBUG_NEW`jest używana zawsze, gdy normalnie korzystałby **nowe** operatora.  
  
 Podobnie jak w przypadku innych diagnostyki `CMemoryState` diagnostyki są dostępne tylko w wersjach debugowania programu. Wersja do debugowania musi mieć **_DEBUG** stała zdefiniowane.  
  
 Jeśli podejrzewasz, program ma przeciek pamięci, możesz użyć `Checkpoint`, **różnica**, i `DumpStatistics` funkcje odnajdywania różnica między stanem pamięci (obiekty przydzielone) w dwóch różnych punktach w programie wykonanie. Ta informacje mogą być przydatne w określeniu, czy funkcja czyści wszystkie obiekty, które go przydziela.  
  
 Jeśli po prostu wiedząc, gdzie występuje niezgodność alokacji i dezalokacji nie zawiera wystarczającej ilości informacji, możesz użyć `DumpAllObjectsSince` zrzut wszystkich obiektów przydzielonych od czasu poprzedniego wywołania funkcji `Checkpoint`. Ten zrzut zawiera kolejność alokacji, plik źródłowy oraz wiersza, w którym obiekt został przydzielony (Jeśli używasz `DEBUG_NEW` alokacji) i pochodnym obiektu, jego adres oraz jego rozmiaru. `DumpAllObjectsSince`Każdy obiekt wymaga także `Dump` funkcji, aby podać informacje o bieżącym stanie.  
  
 Aby uzyskać więcej informacji o sposobie używania `CMemoryState` i innych diagnostycznych, zobacz [debugowania aplikacji MFC](/visualstudio/debugger/mfc-debugging-techniques).  
  
> [!NOTE]
>  Deklaracje obiektów typu `CMemoryState` i wywołania funkcji Członkowskich powinna być oddzielona przez `#if defined(_DEBUG)/#endif` dyrektywy. Powoduje to Diagnostyka pamięci, które mają zostać uwzględnione tylko w przypadku debugowania kompilacji programu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `CMemoryState`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** afx.h  
  
##  <a name="checkpoint"></a>CMemoryState::Checkpoint  
 Tworzy migawkę podsumowania pamięci i zapisuje go w tym `CMemoryState` obiektu.  
  
```  
void Checkpoint();
```  
  
### <a name="remarks"></a>Uwagi  
 `CMemoryState` Funkcje Członkowskie [różnica](#difference) i [DumpAllObjectsSince](#dumpallobjectssince) używać tych danych migawki.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMemoryState](#cmemorystate) konstruktora.  
  
##  <a name="cmemorystate"></a>CMemoryState::CMemoryState  
 Tworzy pustą `CMemoryState` obiekt, który musi być wypełniona przez [punktu kontrolnego](#checkpoint) lub [różnica](#difference) funkcję elementu członkowskiego.  
  
```  
CMemoryState();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_MFC_Utilities#18](../../mfc/codesnippet/cpp/cmemorystate-structure_1.cpp)]  
  
##  <a name="difference"></a>CMemoryState::Difference  
 Porównuje dwa `CMemoryState` obiektów, a następnie przechowuje różnicę to `CMemoryState` obiektu.  
  
```  
BOOL Difference(
    const CMemoryState& oldState,   
    const CMemoryState& newState);
```  
  
### <a name="parameters"></a>Parametry  
 *oldState*  
 Stan pamięci początkowej, zgodnie z definicją w `CMemoryState` punktu kontrolnego.  
  
 *Nowy stan*  
 Nowy stan pamięci zdefiniowane przez `CMemoryState` punktu kontrolnego.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli pamięć dwa stany są różne; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 [Punkt kontrolny](#checkpoint) musi zostać wywołany dla każdego z tych dwóch parametrów stanu pamięci.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMemoryState](#cmemorystate) konstruktora.  
  
##  <a name="dumpallobjectssince"></a>CMemoryState::DumpAllObjectsSince  
 Wywołania `Dump` funkcji dla wszystkich obiektów typu pochodzi od klasy `CObject` czy przydzielone (i nadal są przydzielane) od momentu ostatniego [punktu kontrolnego](#checkpoint) wywołania tej `CMemoryState` obiektu.  
  
```  
void DumpAllObjectsSince() const;

 
```  
  
### <a name="remarks"></a>Uwagi  
 Wywoływanie `DumpAllObjectsSince` z niezainicjowaną `CMemoryState` obiektu będzie zrzut wszystkich obiektów aktualnie w pamięci.  
  
### <a name="example"></a>Przykład  
  Zobacz przykład [CMemoryState](#cmemorystate) konstruktora.  
  
##  <a name="dumpstatistics"></a>CMemoryState::DumpStatistics  
 Drukuje raport statystyki zwięzły pamięci z `CMemoryState` obiekt, który jest wypełniana przez [różnica](#difference) funkcję elementu członkowskiego.  
  
```  
void DumpStatistics() const;

 
```  
  
### <a name="remarks"></a>Uwagi  
 Raport, która jest drukowana na [afxdump —](diagnostic-services.md#afxdump) urządzeniu, są wyświetlane następujące:  
  
 Przykładowy raport wyświetla informacje na numer (lub kwota):  
  
-   bezpłatne bloków  
  
-   normalne bloków  
  
-   Bloki CRT  
  
-   Ignoruj bloków  
  
-   bloki klienta  
  
-   Maksymalna ilość pamięci używanych przez program w dowolnym momencie (w bajtach)  
  
-   pamięć aktualnie używane przez program (w bajtach)  
  
 Bloki wolnego to liczba bloków, których dezalokacji zostało opóźnione, jeżeli `afxMemDF` ustawiono **delayfreememdf —**. Aby uzyskać więcej informacji, zobacz [afxmemdf —](diagnostic-services.md#afxmemdf), w sekcji "MFC makra i funkcje globalne". Zobacz [typów bloków na stercie debugowania](http://msdn.microsoft.com/en-us/db2e7f62-0679-4b39-a23f-26f2c2f407c5) dla blokadę więcej informacji na temat tych typów.  
  
### <a name="example"></a>Przykład  
  Następujący kod należy umieścić w *nazwa_projektu.nazwa_modułu.nazwa_procedury*App.cpp. Zdefiniuj następujące zmienne globalne:  
  
 [!code-cpp[NVC_MFC_Utilities#40](../../mfc/codesnippet/cpp/cmemorystate-structure_2.cpp)]  
  
 W `InitInstance` funkcji, Dodaj wiersz:  
  
 [!code-cpp[NVC_MFC_Utilities#41](../../mfc/codesnippet/cpp/cmemorystate-structure_3.cpp)]  
  
 Dodaj obsługę `ExitInstance` działać, a następnie użyć poniższego kodu:  
  
 [!code-cpp[NVC_MFC_Utilities#42](../../mfc/codesnippet/cpp/cmemorystate-structure_4.cpp)]  
  
 Teraz możesz uruchomić program w trybie debugowania, aby wyświetlić dane wyjściowe `DumpStatistics` funkcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wykres hierarchii](../../mfc/hierarchy-chart.md)



