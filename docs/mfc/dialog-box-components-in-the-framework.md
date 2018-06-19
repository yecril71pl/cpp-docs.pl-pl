---
title: Składniki okna dialogowego w ramach | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], creating
- dialog classes [MFC], dialog box components
- MFC dialog boxes [MFC], about MFC dialog boxes
- dialog templates [MFC], MFC framework
- MFC dialog boxes [MFC], dialog resource
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a92846dc1d7b950d1eccfa4cd42b01ac84d96b34
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343970"
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

