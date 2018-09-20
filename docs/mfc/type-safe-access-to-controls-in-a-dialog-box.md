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
ms.openlocfilehash: 3ed8a374c34eacc48e1d877e704fdc60a20f33d9
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422717"
---
# <a name="type-safe-access-to-controls-in-a-dialog-box"></a>Bezpieczny dostęp do formantów w oknie dialogowym

Kontrolki w oknie dialogowym mogą używać interfejsów klas formantów biblioteki MFC w takich jak `CListBox` i `CEdit`. Użytkownik może sam utworzyć obiekt formantu i dołączyć go do formantu w oknie dialogowym. Tak powstały formant będzie dostępny za pośrednictwem jego interfejsu klasy. W interfejsie można wywoływać funkcje składowe w celu wykonania różnych operacji na formancie. Opisane tutaj metody umożliwiają bezpieczny dostęp do formantu. Jest to szczególnie użyteczne w przypadku formantów takich jak pola listy i pola edycji.

Istnieją dwa sposoby nawiązywania połączenia między formantu w oknie dialogowym a zmienną składową formantu języka C++, w `CDialog`-klasy pochodnej:

- [Bez użycia kreatorów kodu](../mfc/type-safe-access-to-controls-without-code-wizards.md)

- [Za pomocą kreatorów kodu](../mfc/type-safe-access-to-controls-with-code-wizards.md)

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](../mfc/dialog-boxes.md)

