---
title: Tworzenie modalnych okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 815db891514eb03169dac2ad29e50469d74dcfee
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych
Aby utworzyć modalne okno dialogowe, wywołaj jednej z dwóch konstruktorów publicznych zadeklarowany w [cdialog —](../mfc/reference/cdialog-class.md). Następnie wywołaj obiektu okna dialogowego [DoModal](../mfc/reference/cdialog-class.md#domodal) funkcji członkowskiej, aby wyświetlić okno dialogowe i zarządzanie interakcji z nim, dopóki użytkownik wybierze OK lub przycisk Anuluj. To zarządzanie przez `DoModal` jest, co sprawia, że okno dialogowe modalne. Modalne okna dialogowe, aby uzyskać `DoModal` ładuje zasobu okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

