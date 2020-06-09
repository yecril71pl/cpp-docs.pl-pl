---
title: Tworzenie modalnych okien dialogowych
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed7cc94982a46e542a5174d4d46b8013cc84ffa4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622977"
---
# <a name="creating-modal-dialog-boxes"></a>Tworzenie modalnych okien dialogowych

Aby utworzyć modalne okno dialogowe, wywołaj jeden z dwóch publicznych konstruktorów zadeklarowanych w [CDialog](reference/cdialog-class.md). Następnie wywołaj funkcję elementu członkowskiego [DoModal](reference/cdialog-class.md#domodal) obiektu okna dialogowego, aby wyświetlić okno dialogowe i zarządzać interakcją z nim, dopóki użytkownik nie wybierze przycisku OK lub anuluje. To zarządzanie przez `DoModal` to, co sprawia, że okno dialogowe jest modalne. W przypadku modalnych okien dialogowych `DoModal` wczytuje zasób okna dialogowego.

## <a name="see-also"></a>Zobacz też

[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
