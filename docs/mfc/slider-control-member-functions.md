---
title: "Funkcje Członkowskie formantu suwaka | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CSliderCtrl class [MFC], methods
- slider controls [MFC], member functions
ms.assetid: dbde49ee-7306-4d14-a6ce-d09aa198178f
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1bd6c1d05ce7b137e6153ad2ea3fc5df99565a52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="slider-control-member-functions"></a>Funkcje członkowskie formantu suwaka
Aplikację można wywołać suwak funkcje Członkowskie formantu można pobrać informacji o suwaka ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) i zmianę jego właściwości.  
  
 Pozycja suwaka (czyli wartość użytkownik wybrał), użyj [GetPos](../mfc/reference/csliderctrl-class.md#getpos) funkcję elementu członkowskiego. Aby ustawić pozycji suwaka, użyj [SetPos](../mfc/reference/csliderctrl-class.md#setpos) funkcję elementu członkowskiego. W dowolnym momencie można użyć `VerifyPos` funkcji członkowskiej, aby upewnić się, że suwak jest między minimalną i maksymalną wartość.  
  
 Zakres formantu suwaka to zbiór wartości ciągłym, reprezentujące suwaka. Większość aplikacji używa [SetRange](../mfc/reference/csliderctrl-class.md#setrange) funkcji członkowskiej można ustawić zakresu formantu suwaka po pierwszym utworzeniu. Aplikacje można dynamicznie zmieniać zakresu po utworzeniu za pomocą suwaka [SetRangeMax](../mfc/reference/csliderctrl-class.md#setrangemax) i [SetRangeMin](../mfc/reference/csliderctrl-class.md#setrangemin) funkcji elementów członkowskich. Aplikacja, która umożliwia zakresu do można zmienić dynamicznie zwykle pobiera ustawienia końcowy zakresu, gdy użytkownik zakończył pracę z suwaka. Aby pobrać te ustawienia, należy użyć [GetRange](../mfc/reference/csliderctrl-class.md#getrange), [GetRangeMax](../mfc/reference/csliderctrl-class.md#getrangemax), i [GetRangeMin](../mfc/reference/csliderctrl-class.md#getrangemin) funkcji elementów członkowskich.  
  
 Aplikacja może użyć `TBS_AUTOTICKS` styl, który ma znaczniki formantu suwaka wyświetlane automatycznie. Jeśli aplikacja musi kontrolować częstotliwość znaczników lub pozycji, jednak kilka funkcji członkowskich można.  
  
 Aby ustawić pozycji znacznika, aplikacja może użyć [SetTic](../mfc/reference/csliderctrl-class.md#settic) funkcję elementu członkowskiego. [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq) funkcji członkowskiej umożliwia aplikacji ustaw znaczników znaczników znajdujących się w regularnych odstępach czasu w zakresie kontrolka suwaka. Na przykład aplikacja można używać funkcji członkowskiej do wyświetlenia tylko 10 znaczniki w zakresie od 1 do 100.  
  
 Aby uzyskać indeks w zakresie odpowiadający znacznika, użyj [GetTic](../mfc/reference/csliderctrl-class.md#gettic) funkcję elementu członkowskiego. [GetTicArray](../mfc/reference/csliderctrl-class.md#getticarray) funkcji członkowskiej pobiera tablicę tych wskaźników. Aby pobrać pozycja znacznika, we współrzędnych klienta, należy użyć [GetTicPos](../mfc/reference/csliderctrl-class.md#getticpos) funkcję elementu członkowskiego. Aplikacja może pobrać liczbę znaczników przy użyciu [GetNumTics](../mfc/reference/csliderctrl-class.md#getnumtics) funkcję elementu członkowskiego.  
  
 [ClearTics](../mfc/reference/csliderctrl-class.md#cleartics) funkcji członkowskiej powoduje usunięcie wszystkich znaczników osi suwaka.  
  
 Rozmiar wiersza formantu suwaka Określa, jak daleko zostanie przesunięty suwak, gdy aplikacja odbiera **TB_LINEDOWN** lub **TB_LINEUP** wiadomość z powiadomieniem. Podobnie, rozmiar strony określa odpowiedź na **TB_PAGEDOWN** i **TB_PAGEUP** komunikaty powiadomień. Aplikacje można pobierać i ustawiać wartości rozmiar wiersza i strony za pomocą [GetLineSize](../mfc/reference/csliderctrl-class.md#getlinesize), [SetLineSize](../mfc/reference/csliderctrl-class.md#setlinesize), [GetPageSize](../mfc/reference/csliderctrl-class.md#getpagesize), i [SetPageSize](../mfc/reference/csliderctrl-class.md#setpagesize) funkcji elementów członkowskich.  
  
 Aplikacja może używać funkcji elementów członkowskich do pobrania wymiarów kontrolki suwaka. [GetThumbRect](../mfc/reference/csliderctrl-class.md#getthumbrect) funkcji członkowskiej pobiera prostokąt ograniczający dla suwaka. [GetChannelRect](../mfc/reference/csliderctrl-class.md#getchannelrect) funkcji członkowskiej pobiera prostokąt ograniczający dla kanału kontroli suwaka. (Kanał jest obszar za pośrednictwem zostanie przesunięty suwak i zawierający wyróżnienie po wybraniu zakresu).  
  
 Jeśli w kontrolce slider `TBS_ENABLESELRANGE` stylu, użytkownik może wybrać zakres sąsiadujących wartości z niego. Liczba funkcji Członkowskich Zezwalaj wybranego zakresu do skorygowania dynamicznie. [SetSelection](../mfc/reference/csliderctrl-class.md#setselection) funkcji członkowskiej ustawia początkową i końcową pozycji zaznaczenia. Gdy użytkownik zakończy ustawienie wybranego zakresu, aplikacja może pobrać ustawienia za pomocą [GetSelection](../mfc/reference/csliderctrl-class.md#getselection) funkcję elementu członkowskiego. Aby wyczyścić określonego przez użytkownika, należy użyć [ClearSel](../mfc/reference/csliderctrl-class.md#clearsel) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

