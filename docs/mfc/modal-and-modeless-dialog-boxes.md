---
title: Modalne i Niemodalne okna dialogowe
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 886229a2b66968bf76129ecb1da838bd36e66215
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685182"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modalne i Niemodalne okna dialogowe

Klasy [CDialog](../mfc/reference/cdialog-class.md) można użyć do zarządzania dwoma rodzajami okien dialogowych:

- *Modalne okna dialogowe*, które wymagają, aby użytkownik mógł odpowiedzieć przed kontynuowaniem działania programu

- *Niemodalne okna dialogowe*, które pozostają na ekranie i są dostępne do użytku w dowolnym momencie, ale zezwalają na inne działania użytkownika

Edytowanie zasobów i procedury tworzenia szablonu okna dialogowego są takie same dla modalnych i niemodalnych okien dialogowych.

Tworzenie okna dialogowego dla programu wymaga wykonania następujących czynności:

1. Użyj [edytora okien dialogowych](../windows/dialog-editor.md) , aby zaprojektować okno dialogowe i utworzyć zasób szablonu okna dialogowego.

1. Utwórz klasę okna dialogowego.

1. Połącz [kontrolki zasobu okna dialogowego z obsługą komunikatów](../windows/adding-event-handlers-for-dialog-box-controls.md) w klasie okna dialogowego.

1. Dodaj elementy członkowskie danych skojarzone z kontrolkami okna dialogowego i, aby określić [wymianę danych okna](../mfc/dialog-data-exchange.md) dialogowego i [Sprawdzanie poprawności danych okna](../mfc/dialog-data-validation.md) dialogowego dla kontrolek.

## <a name="see-also"></a>Zobacz także

[Okna dialogowe](../mfc/dialog-boxes.md)<br/>
[Praca z polami okna dialogowego w MFC](../mfc/life-cycle-of-a-dialog-box.md)
