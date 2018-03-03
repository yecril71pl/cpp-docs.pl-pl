---
title: "Drukowanie i Podgląd wydruku | Dokumentacja firmy Microsoft"
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
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bedcf1ecf851ed6d9dd396ee6a82d6d2c058930b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="printing-and-print-preview"></a>Drukowanie i podgląd wydruku
MFC obsługuje drukowania i podglądu wydruku dla dokumentów programu za pomocą klasy [CView](../mfc/reference/cview-class.md). Podstawowe drukowania i podglądu wydruku, po prostu zastępują klasie widoku [OnDraw](../mfc/reference/cview-class.md#ondraw) funkcji członkowskiej, co należy zrobić, mimo to. Tej funkcji można narysować do widoku na ekranie do kontekstu urządzenia drukarki rzeczywiste drukarki, lub do kontekstu urządzenia, która symuluje drukarki na ekranie.  
  
 Można również dodać kod do zarządzania wielostronicowe dokumentu drukowanie i Podgląd wydruku dokumentów z podziałem na strony i dodawanie nagłówków i stopek do nich.  
  
 Tej rodziny artykułów opisano sposób drukowania jest zaimplementowana w Microsoft Foundation Class biblioteki (MFC) oraz przeprowadzać Architektura drukowania, które są wbudowane w platformę. Artykuły opisano również sposób MFC obsługuje łatwe implementacją funkcji podglądu wydruku i sposobu użycia i zmodyfikuj te funkcje.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o  
  
-   [Drukowanie](../mfc/printing.md)  
  
-   [Architektura podglądu wydruku](../mfc/print-preview-architecture.md)  
  
-   [Próbki](../visual-cpp-samples.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy interfejsu użytkownika](../mfc/user-interface-elements-mfc.md)
