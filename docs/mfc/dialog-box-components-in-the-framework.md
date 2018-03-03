---
title: "Składniki okna dialogowego w ramach | Dokumentacja firmy Microsoft"
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
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 840e66def6a908b26b5021537eddee68c50a9628
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="dialog-box-components-in-the-framework"></a>Składniki okna dialogowego w strukturze
W ramach MFC okno dialogowe zawiera dwa składniki:  
  
-   Zasób szablonu okna dialogowego, który określa formantów okna dialogowego i ich położenia.  
  
     Zasób okna dialogowego przechowuje szablonu okna dialogowego, w którym tworzy okno dialogowe systemu Windows i wyświetla je. Szablon określa właściwości okna dialogowego, w tym jej rozmiaru, lokalizacji, styl i typy i położenia kontrolki w oknie dialogowym. Zazwyczaj użyje szablonu okna dialogowego przechowywane jako zasób, ale można też utworzyć własny szablon w pamięci.  
  
-   Pochodne klasy okien dialogowych, [cdialog —](../mfc/reference/cdialog-class.md)w celu zapewnienia interfejsu programowego zarządzania okna dialogowego.  
  
     Okno dialogowe to okno i zostanie podłączony do okna systemu Windows, gdy jest widoczne. Podczas tworzenia okna dialogowego zasobu szablonu okna dialogowego służy jako szablon do tworzenia podrzędnego kontrolki okna dla okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)   
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

