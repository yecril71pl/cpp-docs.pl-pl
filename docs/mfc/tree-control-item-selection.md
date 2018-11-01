---
title: Wybór elementu kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: bd3ade31ce1e41481943659ba9a8ef8dd77117fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592728"
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa

Gdy zmieni się zaznaczenie z jednego elementu do innej kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) i [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) wiadomości z powiadomieniami. Zarówno powiadomienia obejmują wartość, która określa, czy zmiana jest wynikiem kliknięcia lub naciśnięcia klawisza. Powiadomienia obejmują także informacji na temat elementu, który zyskuje zaznaczenie i element, który jest utraty zaznaczenia. Można ustawić atrybuty elementów, które są zależne od stan zaznaczenia elementu, można użyć tych informacji. Zwracanie **TRUE** w odpowiedzi na `TVN_SELCHANGING` zapobiega wybór Zmienianie; zwracanie **FALSE** umożliwia zmianę.

Aplikację można zmienić wybór, wywołując [selectitem —](../mfc/reference/ctreectrl-class.md#selectitem) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

