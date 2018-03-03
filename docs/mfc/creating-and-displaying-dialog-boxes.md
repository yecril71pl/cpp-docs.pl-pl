---
title: "Tworzenie i wyświetlanie okien dialogowych | Dokumentacja firmy Microsoft"
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
- modal dialog boxes [MFC], creating
- opening dialog boxes
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], displaying
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d436301a979dbba2bc4a922f8427f355a398f654
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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

