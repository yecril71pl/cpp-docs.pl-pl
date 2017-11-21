---
title: Implementacja paska stanu w MFC | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: COldStatusBar
dev_langs: C++
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ad340de74193bedbe817f1cd5bb5cc29b3417195
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="status-bar-implementation-in-mfc"></a>Implementacja paska stanu w MFC
A [cstatusbar —](../mfc/reference/cstatusbar-class.md) obiekt jest pasek sterowania z wiersza okienek tekstu wyjściowego. Okienka dane wyjściowe są często używane jako wiersze komunikat, a wskaźniki stanu. Przykładami krótko opisano wybrane polecenie Wiersze komunikat pomocy menu i wskaźników określenia stanu blokady PRZEWIJANIA, NUM LOCK i kluczy.  
  
 Począwszy od wersji 4.0 MFC, pasków stanu są implementowane za pomocą klasy [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), który hermetyzuje stan paska formantu wspólnego. W celu zapewnienia zgodności z poprzednimi wersjami MFC zachowuje starsze implementacja paska stanu w klasie **COldStatusBar**. Opisuje dokumentacja dla wcześniejszych wersji MFC **COldStatusBar** w obszarze `CStatusBar`.  
  
 [CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), funkcji członkowskiej nowych 4.0 MFC umożliwia skorzystać z obsługi systemu Windows formantu wspólnego stanu paska dostosowania i dodatkowe funkcje. `CStatusBar`Funkcje Członkowskie zapewniają większość funkcjonalności formanty standardowe systemu Windows; Jednak jeśli wywołasz `GetStatusBarCtrl`, z paskami stanu można nadać jeszcze więcej właściwości paska stanu. Podczas wywoływania `GetStatusBarCtrl`, zwróci odwołanie do `CStatusBarCtrl` obiektu. Można użyć tego odwołania do manipulowania formantu paska stanu.  
  
 Na poniższej ilustracji przedstawiono pasek stanu, który wyświetla kilka wskaźniki.  
  
 ![Pasek stanu](../mfc/media/vc37dy1.gif "vc37dy1")  
Pasek stanu  
  
 Jak narzędzi pasek stanu obiektu jest osadzony w jego oknie ramka nadrzędny i jest tworzony automatycznie, gdy okno ramowe jest utworzony. Pasek stanu, takie jak paski sterowania wszystkie, zostanie zniszczony automatycznie oraz gdy ramka nadrzędny zostanie zniszczony.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Aktualizowanie tekstu w okienku paska stanu](../mfc/updating-the-text-of-a-status-bar-pane.md)  
  
-   Klasy MFC [cstatusbar —](../mfc/reference/cstatusbar-class.md) i [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)  
  
-   [Paski sterowania](../mfc/control-bars.md)  
  
-   [Paski dialogowe](../mfc/dialog-bars.md)  
  
-   [Paski narzędzi (MFC — implementacja paska narzędzi)](../mfc/mfc-toolbar-implementation.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Paski stanu](../mfc/status-bars.md)

