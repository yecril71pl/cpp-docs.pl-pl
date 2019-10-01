---
title: Tworzenie modalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685678"
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych

Aby utworzyć modalne okno dialogowe, wywołaj jeden z dwóch publicznych konstruktorów zadeklarowanych w [CDialog](../mfc/reference/cdialog-class.md). Następnie wywołaj funkcję elementu członkowskiego [DoModal](../mfc/reference/cdialog-class.md#domodal) obiektu okna dialogowego, aby wyświetlić okno dialogowe i zarządzać interakcją z nim, dopóki użytkownik nie wybierze przycisku OK lub anuluje. To zarządzanie przez `DoModal` powoduje, że okno dialogowe jest modalne. W przypadku modalnych okien dialogowych `DoModal` wczytuje zasób okna dialogowego.

## <a name="see-also"></a>Zobacz także

[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
