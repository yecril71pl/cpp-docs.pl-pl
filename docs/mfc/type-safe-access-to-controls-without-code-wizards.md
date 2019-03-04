---
title: Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], accessing controls
- dialog box controls [MFC], accessing
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
ms.openlocfilehash: 5b4b604bf42a327edf3ac7a83dcfc42a5e0d8c54
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261118"
---
# <a name="type-safe-access-to-controls-without-code-wizards"></a>Bezpieczny dostęp do kontrolek bez użycia kreatorów kodu

Pierwszym sposobem tworzenia bezpieczny dostęp do formantów używa wbudowanej funkcji elementu członkowskiego można rzutować zwracany typ klasy `CWnd`firmy `GetDlgItem` funkcja elementu członkowskiego do odpowiedniego typu formantu języka C++, jak w poniższym przykładzie:

[!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_1.cpp)]

Ta funkcja elementu członkowskiego umożliwia następnie uzyskać dostęp do formantu w sposób bezpieczny kod podobny do następującego:

[!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/cpp/type-safe-access-to-controls-without-code-wizards_2.cpp)]

## <a name="see-also"></a>Zobacz także

[Bezpieczny dostęp do kontrolek w oknie dialogowym](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)<br/>
[Bezpieczny dostęp do kontrolek z użyciem kreatorów kodu](../mfc/type-safe-access-to-controls-with-code-wizards.md)
