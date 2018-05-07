---
title: Bezpieczny dostęp do formantów w oknie dialogowym | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a876be701b680de0559f123aaaaa68d4c006e41a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Bezpieczny dostęp do formantów w oknie dialogowym
Kontrolki w oknie dialogowym można użyć interfejsów klasy formantów MFC takich jak `CListBox` i `CEdit`. Użytkownik może sam utworzyć obiekt formantu i dołączyć go do formantu w oknie dialogowym. Tak powstały formant będzie dostępny za pośrednictwem jego interfejsu klasy. W interfejsie można wywoływać funkcje składowe w celu wykonania różnych operacji na formancie. Opisane tutaj metody umożliwiają bezpieczny dostęp do formantu. Jest to szczególnie użyteczne w przypadku formantów takich jak pola listy i pola edycji.  
  
 Istnieją dwa podejścia do nawiązywania połączenia między formantu w oknie dialogowym i zmiennej członkowskiej C++ kontroli w `CDialog`-klasy:  
  
-   [Bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [Z użyciem kreatorów kodu](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Okna dialogowe](../mfc/dialog-boxes.md)

