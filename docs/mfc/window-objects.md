---
title: Obiekty okna | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- objects [MFC], window
- Windows window [MFC]
- MFC, windows
- frame windows [MFC], C++ window objects
- window objects [MFC]
- windows [MFC], C++ window objects
- window messages [MFC]
- HWND
- messages [MFC], Windows
- Visual C++, window objects [MFC]
- HWND, window objects [MFC]
ms.assetid: 28b33ce2-af05-4617-9d03-1cb9a02be687
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 7f16b71d48bbd44a472c56aa1ad6aa1a1c510b1c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="window-objects"></a>Obiekty okien
Klasa dostarcza MFC [CWnd](../mfc/reference/cwnd-class.md) celu hermetyzacji `HWND` uchwytu okna. `CWnd` Obiekt jest obiektem okna języka C++ różne od `HWND` reprezentujący systemu Windows, ale okna zawierającego go. Użyj `CWnd` pochodzić okna podrzędnego klas, lub użyj jednego z wielu klas MFC z `CWnd`. Klasa `CWnd` jest klasą bazową dla wszystkich windows, w tym okien ramowych, okna dialogowe okno podrzędne, formanty i paski sterowania, takie jak pasków narzędzi. Dobrą znajomość [relacja między obiektem okna języka C++ a właściwością HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md) ma kluczowe znaczenie dla skuteczne programowanie z MFC.  
  
 Zapewnia MFC, niektóre funkcje domyślne i zarządzania systemu windows, ale mogą dziedziczyć klasy z `CWnd` i dostosować funkcjonalność podana przy użyciu funkcji jego elementów członkowskich. Można utworzyć podrzędnego windows tworząc `CWnd` obiektów i wywoływania jego [Utwórz](../mfc/reference/cwnd-class.md#create) element członkowski funkcji, a następnie dostosować okien podrzędnych za pomocą `CWnd` funkcji elementów członkowskich. Osadzić obiektów pochodzących od [CView](../mfc/reference/cview-class.md), takich jak widoki formularzy lub widok drzewa, w oknie ramowym. I może obsługiwać wiele widoków dokumentów za pomocą okienka podziału, dostarczone przez klasę [CSplitterWnd](../mfc/reference/csplitterwnd-class.md).  
  
 Każdy obiekt pochodzi od klasy `CWnd` zawiera mapy komunikatów, przez które mapowanie komunikatów systemu Windows lub identyfikatory poleceń do obsługi własnych.  
  
 Ogólne materiały dotyczące programowania dla systemu Windows jest dobrym zasobu poznanie `CWnd` funkcji elementów członkowskich, które hermetyzują `HWND` interfejsów API.  
  
## <a name="functions-for-operating-on-a-cwnd"></a>Funkcje obsługi na CWnd  
 `CWnd`i jego [okna klas pochodnych](../mfc/derived-window-classes.md) konstruktorów, destruktory i funkcje Członkowskie do inicjalizacji obiektu, tworzenie podstawowej struktury systemu Windows i dostęp hermetyzowany `HWND`. `CWnd`udostępnia funkcje Członkowskie, które hermetyzują interfejsów API systemu Windows do wysyłania wiadomości, uzyskiwanie dostępu do stanu okna, Konwersja współrzędnych, aktualizowanie, przewijania, dostęp do Schowka i wiele innych zadań. Większość Windows API zarządzania systemem Windows, prowadzące `HWND` argumentu są hermetyzowane jako funkcji Członkowskich `CWnd`. Nazwy funkcji i ich parametry są zachowywane w `CWnd` funkcję elementu członkowskiego. Szczegółowe informacje na temat interfejsów API systemu Windows zamknięte przez `CWnd`, zobacz klasę [CWnd](../mfc/reference/cwnd-class.md).  
  
## <a name="cwnd-and-windows-messages"></a>Komunikaty systemu Windows i CWnd  
 Jedną z głównych przeznaczeń `CWnd` jest zapewnienie interfejs do obsługi komunikatów systemu Windows, takich jak `WM_PAINT` lub `WM_MOUSEMOVE`. Wiele funkcji Członkowskich `CWnd` są programy obsługi dla standardowych komunikatów — zaczynających się od identyfikatora **afx_msg** i prefiksu "Włączone", takie jak `OnPaint` i **OnMouseMove**. [Obsługa i mapowanie komunikatów](../mfc/message-handling-and-mapping.md) obejmuje wiadomości i obsługa szczegółowo komunikatów. Informacje dotyczą jednakowo framework w systemie windows oraz te, utworzyć samodzielnie do celów specjalnych.  
  
### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Relacja między obiektem okna języka C++ a właściwością HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)  
  
-   [Pochodne klasy okien](../mfc/derived-window-classes.md)  
  
-   [Tworzenie okien](../mfc/creating-windows.md)  
  
-   [Niszczenie obiektów okien](../mfc/destroying-window-objects.md)  
  
-   [Odłączanie obiektu CWnd od jego właściwości HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
-   [Praca z obiektami okien](../mfc/working-with-window-objects.md)  
  
-   [Konteksty urządzenia](../mfc/device-contexts.md): obiektów rysowania urządzenia z systemem Windows niezależne  
  
-   [Obiekty graficzne](../mfc/graphic-objects.md): pióra, pędzle, czcionki, mapy bitowe, palet, regiony  
  
## <a name="see-also"></a>Zobacz też  
 [Windows](../mfc/windows.md)

