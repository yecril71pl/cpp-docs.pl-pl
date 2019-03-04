---
title: Tworzenie modalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: 5de6eeb616f32c7b8829d827988a972e41658530
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304967"
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych

Aby utworzyć modalne okno dialogowe, wywołania jednej z dwóch konstruktorów publicznych zadeklarowanych w [CDialog](../mfc/reference/cdialog-class.md). Następnie wywołaj obiektu okna dialogowego [DoModal](../mfc/reference/cdialog-class.md#domodal) funkcja elementu członkowskiego, aby wyświetlić okno dialogowe i zarządzać interakcji z nią, dopóki użytkownik zdecyduje się na OK lub przycisk Anuluj. Zarządzania przez `DoModal` to, co sprawia, że okno dialogowe modalnych. Modalne okno dialogowe pól `DoModal` ładuje zasobu okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
