---
title: Tworzenie i wyświetlanie okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fcac345a572f8b33d76692d6852e2dc28698367
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-and-displaying-dialog-boxes"></a>Tworzenie i wyświetlanie okien dialogowych
Tworzenie obiektu okna dialogowego jest fazach. Po pierwsze konstruowania obiektu okna dialogowego, a następnie utworzyć okno dialogowe. Modalne i Niemodalne okna dialogowe różni się nieco w procesie używany do tworzenia i wyświetlania ich. W poniższej tabeli przedstawiono sposób modalne i niemodalne okno dialogowe pola są zazwyczaj zbudowane i wyświetlane.  
  
### <a name="dialog-creation"></a>Tworzenie okna dialogowego  
  
|Typ okna dialogowego|Jak utworzyć go|  
|-----------------|----------------------|  
|[Niemodalny](../mfc/creating-modeless-dialog-boxes.md)|Utworzyć `CDialog`, następnie wywołaj **Utwórz** funkcję elementu członkowskiego.|  
|[Modalne](../mfc/creating-modal-dialog-boxes.md)|Utworzyć `CDialog`, następnie wywołaj `DoModal` funkcję elementu członkowskiego.|  
  
 Można należy utworzyć użytkownika — okno dialogowe z [szablonu okna dialogowego w pamięci](../mfc/using-a-dialog-template-in-memory.md) że zostały wykonane, a nie z zasobów szablonu okna dialogowego. Jednak to zaawansowane tematu.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

