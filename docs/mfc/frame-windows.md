---
title: Okna ramowe | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame widows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 648e0cada61e15c29ab908e93cc8e457581f9239
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="frame-windows"></a>Okna ramowe
Gdy aplikacja działa w systemie Windows, użytkownik wchodzi w interakcję z dokumentów wyświetlanych w oknach ramowych. Okno ramowe dokument ma dwa główne składniki: ramki i zawartość, która go ramki. Okna ramowe dokumentu może być [interfejs pojedynczego dokumentu](../mfc/sdi-and-mdi.md) okien ramowych (SDI) lub [interfejsu wielu dokumentów](../mfc/sdi-and-mdi.md) okna podrzędnego (MDI). System Windows zarządza większość interakcji z okno ramowe: przenoszenie i zmienia rozmiar okna, zamknięcia, minimalizując i jego zmaksymalizowaniu. Możesz zarządzać zawartości wewnątrz ramki.  
  
## <a name="frame-windows-and-views"></a>Widoków i okien ramowych  
 Struktura MFC używa okien ramowych zawiera widoki. Dwa składniki — ramki i zawartości — reprezentowane i zarządza dwoma różnymi klasami w MFC. Klasy okien ramowych zarządza ramki oraz klasę widoku zarządza zawartość. Okno widoku jest elementem podrzędnym ramkę okna. Rysowanie i innych interakcji z użytkownikiem z dokumentem odbywa się w widoku obszaru klienta, nie obszar kliencki okno ramowe. Okno ramowe zapewnia widoczne ramki wokół widoku, wraz z paska podpisu i formanty standardowe okno, takie jak menu sterowania przycisków, aby zminimalizować i zmaksymalizuj okno i formanty do zmiany rozmiaru okna. "Zawartość" zawiera obszar klienta okna, w pełni jest zajęta przez okno podrzędne — widok. Na poniższej ilustracji przedstawiono relację między okno ramowe oraz widok.  
  
 ![Wyświetl okno ramowe](../mfc/media/vc37fx1.gif "vc37fx1")  
Okno ramowe i widoku  
  
## <a name="frame-windows-and-splitter-windows"></a>Okna ramowe i okna podziału  
 Rozmieszczenie wspólnej innego dotyczy ramkę okna do ramki wiele widoków, zwykle za pomocą [okna podziału](../mfc/multiple-document-types-views-and-frame-windows.md). W oknie podziału obszar kliencki okno ramowe jest zajęte przez okno podziału, który z kolei ma wiele okien podrzędnych, o nazwie okienka, które są widoków.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
 **Tematy ogólne ramkę okna**  
  
-   [Obiekty okna](../mfc/window-objects.md)  
  
-   [Klasy okien ramowych](../mfc/frame-window-classes.md)  
  
-   [Klasy okien ramowych tworzone przez Kreatora aplikacji](../mfc/frame-window-classes-created-by-the-application-wizard.md)  
  
-   [Style okna ramowe](../mfc/frame-window-styles-cpp.md)  
  
-   [Co robią okna ramowe](../mfc/what-frame-windows-do.md)  
  
 **Tematy dotyczące używanie okien ramowych**  
  
-   [Używanie okien ramowych](../mfc/using-frame-windows.md)  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Niszczenie okien ramowych](../mfc/destroying-frame-windows.md)  
  
-   [Zarządzanie oknami podrzędnymi MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Zarządzanie bieżącym widokiem](../mfc/managing-the-current-view.md) w oknie ramowym, który zawiera więcej niż jeden widok  
  
-   [Zarządzanie menu, paskami sterowania i akceleratorami (inne obiekty, które mają miejsce okno ramowe)](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 **Tematy dotyczące możliwości okno ramowe specjalne**  
  
-   [Przeciąganie i upuszczanie plików](../mfc/dragging-and-dropping-files-in-a-frame-window.md) z Eksploratora plików lub Menedżera plików w oknie ramowym  
  
-   [Odpowiadanie na dynamiczną wymianę danych (DDE)](../mfc/responding-to-dynamic-data-exchange-dde.md)  
  
-   [Stany półmodalne: Context-sensitive z pomocy systemu Windows (organizowanie innych akcji okna)](../mfc/orchestrating-other-window-actions.md)  
  
-   [Stany półmodalne: drukowania i podglądu wydruku (organizowanie innych akcji okna)](../mfc/orchestrating-other-window-actions.md)  
  
 **Tematy dotyczące inne rodzaje okien**  
  
-   [Korzystanie z widoków](../mfc/using-views.md)  
  
-   [Okna dialogowe](../mfc/dialog-boxes.md)  
  
-   [Formanty](../mfc/controls-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Windows](../mfc/windows.md)

