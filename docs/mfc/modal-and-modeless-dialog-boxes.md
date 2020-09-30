---
title: Modalne i niemodalne okna dialogowe
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], modeless
- modeless dialog boxes [MFC]
- MFC dialog boxes [MFC], modal
- modal dialog boxes [MFC]
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
ms.openlocfilehash: d3497a19ab14dcc9f14dc0419eb65ea033135b6e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508863"
---
# <a name="modal-and-modeless-dialog-boxes"></a>Modalne i niemodalne okna dialogowe

Klasy [CDialog](reference/cdialog-class.md) można użyć do zarządzania dwoma rodzajami okien dialogowych:

- *Modalne okna dialogowe*, które wymagają, aby użytkownik mógł odpowiedzieć przed kontynuowaniem działania programu

- *Niemodalne okna dialogowe*, które pozostają na ekranie i są dostępne do użytku w dowolnym momencie, ale zezwalają na inne działania użytkownika

Edytowanie zasobów i procedury tworzenia szablonu okna dialogowego są takie same dla modalnych i niemodalnych okien dialogowych.

Tworzenie okna dialogowego dla programu wymaga wykonania następujących czynności:

1. Użyj [edytora okien dialogowych](../windows/dialog-editor.md) , aby zaprojektować okno dialogowe i utworzyć zasób szablonu okna dialogowego.

1. Utwórz klasę okna dialogowego.

1. Połącz [kontrolki zasobu okna dialogowego z obsługą komunikatów](../windows/adding-editing-or-deleting-controls.md) w klasie okna dialogowego.

1. Dodaj elementy członkowskie danych skojarzone z kontrolkami okna dialogowego i, aby określić [wymianę danych okna](dialog-data-exchange.md) dialogowego i [Sprawdzanie poprawności danych okna](dialog-data-validation.md) dialogowego dla kontrolek.

## <a name="see-also"></a>Zobacz też

[Okna dialogowe](dialog-boxes.md)<br/>
[Praca z oknami dialogowymi w MFC](life-cycle-of-a-dialog-box.md)
