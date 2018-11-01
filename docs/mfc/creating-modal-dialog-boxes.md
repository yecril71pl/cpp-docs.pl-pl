---
title: Tworzenie modalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: eb9aab7e8579fbbbfdf5d0f2dca9b6e6abea0066
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657352"
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych

Aby utworzyć modalne okno dialogowe, wywołania jednej z dwóch konstruktorów publicznych zadeklarowanych w [CDialog](../mfc/reference/cdialog-class.md). Następnie wywołaj obiektu okna dialogowego [DoModal](../mfc/reference/cdialog-class.md#domodal) funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i zarządzać interakcji z nią, dopóki użytkownik zdecyduje się na OK lub przycisk Anuluj. Zarządzania przez `DoModal` to, co sprawia, że okno dialogowe modalnych. Modalne okno dialogowe pól `DoModal` ładuje zasobu okna dialogowego.

## <a name="see-also"></a>Zobacz też

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)

