---
title: Tworzenie klasy okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- files [MFC], creating
- dialog classes [MFC], Add Class Wizard
- dialog classes [MFC], creating
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d70f27639344fd00a2e99ad79bf2db166f3270a8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341913"
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

