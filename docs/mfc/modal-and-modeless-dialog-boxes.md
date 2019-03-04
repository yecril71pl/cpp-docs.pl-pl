---
title: Modalne i niemodalne okna dialogowe
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: c3a5263736324d7fe25066e8879d13b3a41768de
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268671"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modalne i niemodalne okna dialogowe

Można użyć klasy [CDialog](../mfc/reference/cdialog-class.md) Zarządzanie dwa rodzaje okien dialogowych:

- *Modalne okna dialogowe*, która wymaga od użytkownika odpowiada przed kontynuowaniem program

- *Niemodalne okna dialogowe*, które pozostają na ekranie i są dostępne do użycia w dowolnym momencie, ale zezwala na inne działania użytkownika

Edytowanie zasobów oraz procedury tworzenia szablonu okna dialogowego są takie same dla modalne i Niemodalne okna dialogowe.

Tworzenie okna dialogowego programu wymaga wykonania następujących czynności:

1. Użyj [Edytor okien dialogowych](../windows/dialog-editor.md) projektować okno dialogowe i utworzyć jej zasobów szablonu okna dialogowego.

1. Tworzenie klasy okien dialogowych.

1. Połącz [kontrolki zasobu okna dialogowego do obsługi komunikatów](../windows/adding-event-handlers-for-dialog-box-controls.md) klasy okna dialogowego.

1. Dodaj elementy członkowskie danych skojarzonych z formantów w oknie dialogowym oraz określić [wymiana danych okna dialogowego](../mfc/dialog-data-exchange.md) i [walidacji danych okna dialogowego](../mfc/dialog-data-validation.md) formantów.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Cykl życiowy okna dialogowego](../mfc/life-cycle-of-a-dialog-box.md)
