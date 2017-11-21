---
title: Tworzenie klasy okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: cd80d55df3ae9adc4a586d1cc5387ee6d1f53282
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-your-dialog-class"></a>Tworzenie klasy okien dialogowych
Dla każdego pola dialogowe w programie Utwórz nową klasę okna dialogowego do pracy z zasobu okna dialogowego.  
  
 [Dodawanie klasy](../ide/adding-a-class-visual-cpp.md) wyjaśniono, jak utworzyć nową klasę okna dialogowego. Po utworzeniu klasy okien dialogowych za pomocą Kreatora dodawania klasy zapisuje następujące elementy. H i. CPP określone pliki:  
  
 W. Plik H:  
  
-   Deklaracja klasy dla klasy okien dialogowych. Klasa pochodzi od [cdialog —](../mfc/reference/cdialog-class.md).  
  
 W. Pliku CPP:  
  
-   Mapy komunikatów dla klasy.  
  
-   Konstruktor standardowe okno dialogowe.  
  
-   Zastępowanie [DoDataExchange](../mfc/reference/cwnd-class.md#dodataexchange) funkcję elementu członkowskiego. Edytuj tej funkcji. Jest on używany do funkcji wymiana i Walidacja danych okna dialogowego, zgodnie z opisem później w [wymiana danych okna dialogowego i weryfikacja](../mfc/dialog-data-exchange-and-validation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie klasy okien dialogowych za pomocą kreatorów kodu](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

