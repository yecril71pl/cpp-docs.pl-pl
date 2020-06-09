---
title: Modalne i niemodalne okna dialogowe
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: 857bb3ea9e66ca0be155413faea23c0aba2abc9e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622209"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modalne i niemodalne okna dialogowe

Klasy [CDialog](reference/cdialog-class.md) można użyć do zarządzania dwoma rodzajami okien dialogowych:

- *Modalne okna dialogowe*, które wymagają, aby użytkownik mógł odpowiedzieć przed kontynuowaniem działania programu

- *Niemodalne okna dialogowe*, które pozostają na ekranie i są dostępne do użytku w dowolnym momencie, ale zezwalają na inne działania użytkownika

Edytowanie zasobów i procedury tworzenia szablonu okna dialogowego są takie same dla modalnych i niemodalnych okien dialogowych.

Tworzenie okna dialogowego dla programu wymaga wykonania następujących czynności:

1. Użyj [edytora okien dialogowych](../windows/dialog-editor.md) , aby zaprojektować okno dialogowe i utworzyć zasób szablonu okna dialogowego.

1. Utwórz klasę okna dialogowego.

1. Połącz [kontrolki zasobu okna dialogowego z obsługą komunikatów](../windows/adding-event-handlers-for-dialog-box-controls.md) w klasie okna dialogowego.

1. Dodaj elementy członkowskie danych skojarzone z kontrolkami okna dialogowego i, aby określić [wymianę danych okna](dialog-data-exchange.md) dialogowego i [Sprawdzanie poprawności danych okna](dialog-data-validation.md) dialogowego dla kontrolek.

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](dialog-boxes.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
