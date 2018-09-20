---
title: Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2685c946b9ee1c738ee83f9413b7fd955857febb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438343"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu

Pierwszym sposobem tworzenia bezpieczny dostęp do formantów używa wbudowanej funkcji elementu członkowskiego można rzutować zwracany typ klasy `CWnd`firmy `GetDlgItem` funkcja elementu członkowskiego do odpowiedniego typu formantu języka C++, jak w poniższym przykładzie:

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Ta funkcja elementu członkowskiego umożliwia następnie uzyskać dostęp do formantu w sposób bezpieczny kod podobny do następującego:

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Bezpieczny dostęp do kontrolek w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu](../mfc/type-safe-access-to-controls-with-code-wizards.md)

