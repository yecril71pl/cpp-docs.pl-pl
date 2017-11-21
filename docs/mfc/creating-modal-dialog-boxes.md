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
ms.openlocfilehash: 662455a3ad0c45b287f485e3b87cc5437343bffb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych
Aby utworzyć modalne okno dialogowe, wywołaj jednej z dwóch konstruktorów publicznych zadeklarowany w [cdialog —](../mfc/reference/cdialog-class.md). Następnie wywołaj obiektu okna dialogowego [DoModal](../mfc/reference/cdialog-class.md#domodal) funkcji członkowskiej, aby wyświetlić okno dialogowe i zarządzanie interakcji z nim, dopóki użytkownik wybierze OK lub przycisk Anuluj. To zarządzanie przez `DoModal` jest, co sprawia, że okno dialogowe modalne. Modalne okna dialogowe, aby uzyskać `DoModal` ładuje zasobu okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

