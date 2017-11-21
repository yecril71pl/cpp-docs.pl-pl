---
title: Grupy z kartami MDI | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- mdi [MFC], tabbed groups
- tabbed grous [MFC]
ms.assetid: 0a464f36-39b7-4e68-8b67-ec175de28377
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d58c079fc08935a11f65170b804f6a4b2786cbb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="mdi-tabbed-groups"></a>Grupy z kartami MDI
Wiele funkcji grupy z kartami interfejsu (MDI) dokumentu umożliwia wielu dokumenty i aplikacje interfejsu (MDI) do wyświetlenia co najmniej jeden z kartami systemu windows (lub grup z kartami systemu Windows, znany jako *grupy z kartami*) w obszarze klienta MDI. Okno systemu windows można wyrównać pionie lub poziomie. Jeśli aplikacja obsługuje więcej niż jednej grupy z kartami MDI, grup oddzielonych rozdzielaczy.  
  
## <a name="features"></a>Funkcje  
 Poniżej przedstawiono funkcje grup z kartami MDI:  
  
-   Aplikacja może dynamicznie utworzyć okno systemu windows.  
  
-   Aplikację można wyrównać systemu windows z kartami poziomo czy pionowo.  
  
-   Grupy z kartami systemu Windows są oddzielane rozdzielaczy. Użytkownika można zmienić rozmiar grupy z kartami przy użyciu rozdzielacza.  
  
-   Użytkownik może przeciągać poszczególnych kart między grupami.  
  
-   Użytkownik może przeciągać poszczególnych kart, aby utworzyć nową grupę.  
  
-   Użytkownik może przenieść karty lub tworzyć nowe grupy przy użyciu menu skrótów.  
  
-   Aplikację można zapisywać i załadować układu systemu windows z kartami.  
  
-   Aplikację można zapisywać i załadować listy dokumentów MDI.  
  
-   Aplikacji można uzyskać dostępu do poszczególnych grup z kartami i modyfikowanie ich parametrów.  
  
### <a name="using-mdi-tabbed-groups"></a>Przy użyciu MDI grupy z kartami  
 Zadań wykonywanych przy użyciu grup z kartami MDI są następujące:  
  
-   Aby włączyć grupy z kartami MDI okna ramki głównej, należy wywołać [CMDIFrameWndEx::EnableMDITabbedGroups](../mfc/reference/cmdiframewndex-class.md#enablemditabbedgroups). Drugi parametr tej metody jest wystąpieniem `CMDITabInfo` klasy. Można używać parametrów domyślnych lub modyfikować przed wywołaniem `CMDIFrameWndEx::EnableMDITabbedGroups`.  
  
-   Aby zmodyfikować właściwości grupy z kartami MDI w czasie wykonywania, należy utworzyć lub zmodyfikować `CMDITabInfo` obiekt i wywołanie `CMDIFrameWndEx::EnableMDITabbedGroups` ponownie  
  
-   Aby uzyskać listę MDI kartach systemu windows, należy wywołać `CMDIFrameWndEx::GetMDITabGroups`.  
  
-   Aby utworzyć nową grupę z kartami MDI obok aktywnej grupy z kartami, należy wywołać `CMDIFrameWndEx::MDITabNewGroup`.  
  
-   Aby zmiana fokusu wprowadzania do okna poprzedniego lub następnego grupy z kartami wywołać `CMDIFrameWndEx::MDITabMoveToNextGroup`.  
  
-   Czy okno jest członkiem MDI kartach wywołania grupy `CMDIFrameWndEx::IsMemberOfMDITabGroup`.  
  
-   Aby ustalić, czy kart MDI lub grup z kartami MDI są włączone dla główne okno ramowe, należy wywołać `CMDIFrameWndEx::AreMDITabs`. Można tylko określić, czy grupy z kartami MDI są włączone, należy wywołać `CMDIFrameWndEx::IsMDITabbedGroup`.  
  
-   Aby wyświetlić menu skrótów, gdy użytkownik kliknie kartę lub przeciągania go do innej grupy z kartami MDI, Przesłoń `CMDIFrameWndEx::OnShowMDITabContextMenu` w `CMDIFrameWndEx`-klasy. Jeśli ta metoda nie należy implementować, aplikacja nie wyświetlają menu skrótów.  
  
-   Aby zapisać układ grup z kartami MDI w aplikacji, należy wywołać `CMDIFrameWndEx::SaveMDIState`. Można załadować uprzednio zapisanego MDI kartach profil grupy, należy wywołać `CMDIFrameWndEx::LoadMDIState`. Można również wywołać tych metod ładowania lub zapisywania w aplikacji MDI listy otwartych dokumentów. Aby uzyskać więcej informacji na temat zapisywanie i ładowanie MDI stanu, zobacz [CMDIFrameWndEx::LoadMDIState](../mfc/reference/cmdiframewndex-class.md#loadmdistate).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Klasa CMDIFrameWndEx](../mfc/reference/cmdiframewndex-class.md)   
 [Klasa CMDIChildWndEx](../mfc/reference/cmdichildwndex-class.md)   
 [Klasa CMDITabInfo](../mfc/reference/cmditabinfo-class.md)
