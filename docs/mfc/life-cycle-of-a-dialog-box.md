---
title: "Cykl życiowy okna dialogowego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], life cycle
- modal dialog boxes [MFC], life cycle
- modeless dialog boxes [MFC], life cycle
- MFC dialog boxes [MFC], life cycle
- life cycle of dialog boxes [MFC]
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e2cc5c841a7951d9fc0b351ed7763637b065b729
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="life-cycle-of-a-dialog-box"></a>Cykl życiowy okna dialogowego
Podczas cyklu okno dialogowe użytkownik wywołuje okno dialogowe, zwykle wewnątrz obsługi polecenia, które tworzy i inicjuje obiektu okna dialogowego, użytkownik wchodzi w interakcję z okna dialogowego i zamyka okno dialogowe.  
  
 Dla modalnych okien dialogowych programu obsługi zbiera wszystkie dane, które użytkownik wprowadził po zamknięciu okna dialogowego. Ponieważ istnieje obiekt okna dialogowego po jego okno dialogowe zostało zamknięte, po prostu umożliwia zmienne Członkowskie klasy okien dialogowych wyodrębnić dane.  
  
 Niemodalne okna dialogowe, aby uzyskać może często wyodrębniania danych z obiektu okna dialogowego, gdy okno dialogowe jest nadal widoczny. W pewnym momencie zostanie zniszczony obiektu okna dialogowego; w takim przypadku zależy od kodu.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Tworzenie i wyświetlanie okien dialogowych](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Tworzenie modalnych okien dialogowych](../mfc/creating-modal-dialog-boxes.md)  
  
-   [Tworzenie niemodalnych okien dialogowych](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [Używanie szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [Ustawianie koloru tła okna dialogowego](../mfc/setting-the-dialog-boxs-background-color.md)  
  
-   [Inicjowanie okna dialogowego](../mfc/initializing-the-dialog-box.md)  
  
-   [Obsługa komunikatów systemu Windows w oknie dialogowym](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [Pobieranie danych z obiektu okna dialogowego](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [Zamykanie okna dialogowego](../mfc/closing-the-dialog-box.md)  
  
-   [Niszczenie okna dialogowego](../mfc/destroying-the-dialog-box.md)  
  
-   [Wymiana danych okna dialogowego (DDX) i sprawdzania poprawności (DDV)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Okna dialogowe arkusza właściwości](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)

