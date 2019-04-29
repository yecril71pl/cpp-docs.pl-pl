---
title: Wybór elementu kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: a88a2c8ea5b935bbcb1f40b705337ff676d8b8a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363559"
---
# <a name="tree-control-item-selection"></a>Wybór elementu kontrolki drzewa

Gdy zmieni się zaznaczenie z jednego elementu do innej kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła [TVN_SELCHANGING](/windows/desktop/Controls/tvn-selchanging) i [TVN_SELCHANGED](/windows/desktop/Controls/tvn-selchanged) wiadomości z powiadomieniami. Zarówno powiadomienia obejmują wartość, która określa, czy zmiana jest wynikiem kliknięcia lub naciśnięcia klawisza. Powiadomienia obejmują także informacji na temat elementu, który zyskuje zaznaczenie i element, który jest utraty zaznaczenia. Można ustawić atrybuty elementów, które są zależne od stan zaznaczenia elementu, można użyć tych informacji. Zwracanie **TRUE** w odpowiedzi na `TVN_SELCHANGING` zapobiega wybór Zmienianie; zwracanie **FALSE** umożliwia zmianę.

Aplikację można zmienić wybór, wywołując [selectitem —](../mfc/reference/ctreectrl-class.md#selectitem) funkcja elementu członkowskiego.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
