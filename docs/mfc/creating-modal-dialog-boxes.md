---
title: Tworzenie modalnych okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a8bc947dbaf9cecc680f3cdbd8e6b429d2bcd5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342432"
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych
Aby utworzyć modalne okno dialogowe, wywołaj jednej z dwóch konstruktorów publicznych zadeklarowany w [cdialog —](../mfc/reference/cdialog-class.md). Następnie wywołaj obiektu okna dialogowego [DoModal](../mfc/reference/cdialog-class.md#domodal) funkcji członkowskiej, aby wyświetlić okno dialogowe i zarządzanie interakcji z nim, dopóki użytkownik wybierze OK lub przycisk Anuluj. To zarządzanie przez `DoModal` jest, co sprawia, że okno dialogowe modalne. Modalne okna dialogowe, aby uzyskać `DoModal` ładuje zasobu okna dialogowego.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

