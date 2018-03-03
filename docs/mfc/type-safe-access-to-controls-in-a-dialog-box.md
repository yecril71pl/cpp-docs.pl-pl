---
title: "Bezpieczny dostęp do formantów w oknie dialogowym | Dokumentacja firmy Microsoft"
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
- common controls [MFC], in dialog boxes
- Windows common controls [MFC], in dialog boxes
- safe access to dialog box controls
- dialog boxes [MFC], type-safe access to controls
- controls [MFC], accessing in dialog boxes
- type-safe access to dialog box controls
- MFC dialog boxes [MFC], type-safe access to controls
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b6005f34b28a634b36aad93186a34a8806b8033d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Bezpieczny dostęp do formantów w oknie dialogowym
Kontrolki w oknie dialogowym można użyć interfejsów klasy formantów MFC takich jak `CListBox` i `CEdit`. Użytkownik może sam utworzyć obiekt formantu i dołączyć go do formantu w oknie dialogowym. Tak powstały formant będzie dostępny za pośrednictwem jego interfejsu klasy. W interfejsie można wywoływać funkcje składowe w celu wykonania różnych operacji na formancie. Opisane tutaj metody umożliwiają bezpieczny dostęp do formantu. Jest to szczególnie użyteczne w przypadku formantów takich jak pola listy i pola edycji.  
  
 Istnieją dwa podejścia do nawiązywania połączenia między formantu w oknie dialogowym i zmiennej członkowskiej C++ kontroli w `CDialog`-klasy:  
  
-   [Bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [Z użyciem kreatorów kodu](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)

