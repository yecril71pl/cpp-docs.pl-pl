---
title: Tworzenie Niemodalnych okien dialogowych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2055312c7418b14c9b274649db8faa297554257e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-modeless-dialog-boxes"></a>Tworzenie niemodalnych okien dialogowych
Pola z niemodalnego okna dialogowego należy podać własne Konstruktor publiczny w klasy okien dialogowych. Aby utworzyć niemodalne okno dialogowe, wywołaj z publicznego konstruktora, a następnie wywołać obiektu okna dialogowego [Utwórz](../mfc/reference/cdialog-class.md#create) funkcji członkowskiej można załadować zasobu okna dialogowego. Możesz wywołać **Utwórz** podczas lub po wywołaniu konstruktora. Jeśli właściwość ma zasobu okna dialogowego **ws_visible —**, natychmiast pojawi się okno dialogowe. Jeśli nie, należy wywołać jej [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) funkcję elementu członkowskiego.  
  
## <a name="see-also"></a>Zobacz też  
 [Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

