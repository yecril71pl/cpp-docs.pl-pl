---
title: Tworzenie niemodalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
ms.assetid: 70d78c7f-3d40-477b-9f78-0f33c359f88b
ms.openlocfilehash: 71cca82e667ddbf5cfc4c2abb5880cd69c7fafae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388491"
---
# <a name="creating-modeless-dialog-boxes"></a>Tworzenie niemodalnych okien dialogowych

Niemodalne okno dialogowe trzeba podać publicznego konstruktora w klasy okien dialogowych. Aby utworzyć niemodalne okno dialogowe, wywołania konstruktora publicznego, a następnie wywołać obiektu okna dialogowego [Utwórz](../mfc/reference/cdialog-class.md#create) funkcja elementu członkowskiego, które można załadować zasobu okna dialogowego. Możesz wywołać **Utwórz** podczas lub po wywołaniu konstruktora. Jeśli zasobu okna dialogowego właściwości **WS_VISIBLE**, natychmiast pojawi się okno dialogowe. Jeśli nie, należy wywołać jej [ShowWindow](../mfc/reference/cwnd-class.md#showwindow) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
