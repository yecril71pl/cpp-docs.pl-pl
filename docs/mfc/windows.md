---
title: Windows | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- windows [MFC]
- MFC, windows
- window objects [MFC], MFC Framework
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e81be5ef0216f7d8a28ea7d5046c127f18670a6c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="windows"></a>Windows
Tej rodziny artykułów obejmuje obiekty okna w ramach MFC. Wszystkie windows MFC pochodzi od klasy [CWnd](../mfc/reference/cwnd-class.md), w tym okien ramowych, widoki, okien dialogowych i formantów.  
  
 W tym artykule opisano pierwszej grupy artykułów [obiektów okien](../mfc/window-objects.md) ogólnie. Odwołuje się do tej grupy, aby uzyskać ogólne informacje o C++ okna obiektów, jak ich Hermetyzowanie HWND i sposób ich używania podczas tworzenia własnego systemu windows, takich jak okno podrzędne.  
  
 W tym artykule opisano drugiej grupy artykułów [okna ramowe](../mfc/frame-windows.md)— windows, które Umieść ramkę wokół zawartości — w szczególności. Odwołuje się do tej grupy, aby uzyskać informacje o zarządzaniu programu MFC framework okien ramowych i zawartość, która ich ramki, łącznie z widoków i paski sterowania.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
 *Tematy w obiektach okna w ogólne*  
  
-   [Obiekty okna](../mfc/window-objects.md)  
  
-   [Relacja między C++ obsługuje obiekty okna i HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Pochodne klasy okien](../mfc/derived-window-classes.md)  
  
-   [Tworzenie obiektów okien](../mfc/creating-windows.md)  
  
-   [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)  
  
-   [Rejestrowanie klas"okien"](../mfc/registering-window-classes.md)  
  
-   [Praca z obiektami okien](../mfc/working-with-window-objects.md)  
  
-   [Konteksty urządzenia](../mfc/device-contexts.md): obiektów rysunku Windows niezależnych od urządzenia  
  
-   [Obiekty graficzne](../mfc/graphic-objects.md): pióra, pędzle, czcionki, mapy bitowe, palet, regiony  
  
 *Tematy okna ramowe*  
  
-   [Okna ramowe](../mfc/frame-windows.md): obiektów okna, które dostarczają ramki  
  
-   [Widoków i okien ramowych](../mfc/frame-windows.md)  
  
-   [Klasy okien ramowych](../mfc/frame-window-classes.md)  
  
-   [Style okna ramowego](../mfc/frame-window-styles-cpp.md)  
  
-   [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
-   [Co robią okna ramowe](../mfc/what-frame-windows-do.md)  
  
-   [Używanie okien ramowych](../mfc/using-frame-windows.md)  
  
-   [Zarządzanie oknami MD/podrzędny (okno MDICLIENT)](../mfc/managing-mdi-child-windows.md)  
  
-   [Zarządzanie menu, paskami sterowania i akceleratorami](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
-   [Cframewnd —](../mfc/reference/cframewnd-class.md)  
  
-   [Cmdiframewnd —](../mfc/reference/cmdiframewnd-class.md)  
  
-   [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)  
  
-   [Używanie widoków](../mfc/using-views.md)  
  
-   [Wiele typów dokumentów, widoków i okien ramowych (windows podziału)](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [Komunikaty (map i funkcje programu obsługi)](../mfc/messages.md)  
  
 *Tworzenie i zniszcz systemu Windows*  
  
-   [Ogólna sekwencja tworzenia okna](../mfc/general-window-creation-sequence.md)  
  
-   [Destroy obiektów okien](../mfc/destroying-window-objects.md)  
  
-   [Tworzenie okien ramowych dokumentu](../mfc/creating-document-frame-windows.md)  
  
-   [Zniszczenie okna ramowe](../mfc/destroying-frame-windows.md)  
  
 *Tworzenie okna podziału*  
  
-   [Tworzenie okna podziału](../mfc/multiple-document-types-views-and-frame-windows.md)  
  
 *Zarządzanie oknami podrzędnymi i bieżący widok*  
  
-   [Zarządzanie oknami podrzędnymi MDI](../mfc/managing-mdi-child-windows.md)  
  
-   [Zarządzanie bieżącym widokiem](../mfc/managing-the-current-view.md)  
  
-   [Zarządzanie menu, paskami sterowania i akceleratorami](../mfc/managing-menus-control-bars-and-accelerators.md)  
  
 *Praca z konteksty urządzenia i style okna*  
  
-   [Użyj pióra i innych obiektów graficznych kontekstu urządzenia](../mfc/graphic-objects.md)  
  
-   [Zmienianie stylów okna utworzonego przez MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)   
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Paski narzędzi](../mfc/toolbars.md)   
 [Paski stanu](../mfc/status-bars.md)   
 [Paski dialogowe](../mfc/dialog-bars.md)

