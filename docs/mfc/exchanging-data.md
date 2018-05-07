---
title: Wymiana danych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- property sheets [MFC], data exchange
- exchanging data with property sheets [MFC]
- DDX (dialog data exchange) [MFC], property sheets
ms.assetid: 689f02d0-51a9-455b-8ffb-5b44f0aefa28
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e503bd9268423fbe63ec76de4bcb5443a7d52696
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="exchanging-data"></a>Wymiana danych
Podobnie jak w przypadku większości okien dialogowych wymiany danych między arkusz właściwości i aplikacji jest jednym z najważniejszych funkcji arkusza właściwości. W tym artykule opisano sposób wykonania tego zadania.  
  
 Wymiana danych z arkusza właściwości jest rzeczywiście wymiana danych z na stronach właściwości indywidualnych arkusza właściwości. Procedury wymiany danych za pomocą strony właściwości są takie same jak wymiana danych okna dialogowego, ponieważ [cpropertypage —](../mfc/reference/cpropertypage-class.md) obiekt jest tylko specjalne [cdialog —](../mfc/reference/cdialog-class.md) obiektu. Procedura wykorzystuje framework okna dialogowego danych programu exchange (DDX) urządzenia, które wymianie danych między formantami w zmiennych okna dialogowego pole i element członkowski obiektu okno dialogowe.  
  
 Istotną różnicą między wymiana danych z arkusza właściwości i okno dialogowe normalne jest arkusz właściwości wiele stron, konieczna jest wymiana danych ze wszystkich stron w arkuszu właściwości. Aby uzyskać więcej informacji o DDX, zobacz [wymiana danych okna dialogowego i weryfikacja](../mfc/dialog-data-exchange-and-validation.md).  
  
 Poniższy przykład przedstawia wymianie danych między widokiem i dwie strony arkusz właściwości:  
  
 [!code-cpp[NVC_MFCDocView#4](../mfc/codesnippet/cpp/exchanging-data_1.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Arkusze właściwości](../mfc/property-sheets-mfc.md)

