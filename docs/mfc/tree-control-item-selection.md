---
title: Wybór elementu kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 07c7b673e0f9029f8ece928b0ab17760b3863cc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513341"
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa

Gdy zaznaczenie zostanie zmienione z jednego elementu na inny, formant drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła komunikaty powiadomień [TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging) i [TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged) . Obie powiadomienia obejmują wartość określającą, czy zmiana jest wynikiem kliknięcia myszą, czy naciśnięciem klawisza. Powiadomienia obejmują również informacje o elemencie, który uzyskuje zaznaczenie i element, który utraci zaznaczenie. Korzystając z tych informacji, można ustawić atrybuty elementu, które zależą od stanu zaznaczenia elementu. Zwrócenie **wartości true** w odpowiedzi `TVN_SELCHANGING` uniemożliwia zmianę zaznaczenia; zwrócenie **wartości false** umożliwia zmianę.

Aplikacja może zmienić zaznaczenie, wywołując funkcję elementu członkowskiego [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) .

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
