---
title: Tworzenie niemodalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 4cc2bc0ce54ad658a8bf13e70a8fa54479cbbf79
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50453709"
---
# <a name="creating-modeless-dialog-boxes"></a>Tworzenie niemodalnych okien dialogowych

Niemodalne okno dialogowe trzeba podać publicznego konstruktora w klasy okien dialogowych. Aby utworzyć niemodalne okno dialogowe, wywołania konstruktora publicznego, a następnie wywołać obiektu okna dialogowego [Utwórz](../mfc/reference/cdialog-class.md#create) funkcja elementu członkowskiego, które można załadować zasobu okna dialogowego. Możesz wywołać **Utwórz** podczas lub po wywołaniu konstruktora. Jeśli zasobu okna dialogowego właściwości **WS_VISIBLE**, natychmiast pojawi się okno dialogowe. Jeśli nie, należy wywołać jej [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

