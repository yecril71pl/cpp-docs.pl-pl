---
title: Elementy nagłówka w formancie nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
ms.openlocfilehash: 31b6bcb134b62fc11df78a846b3c256a2ef69c14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240000"
---
# <a name="header-items-in-a-header-control"></a>Elementy nagłówka w formancie nagłówka

Masz znaczną kontrolę nad wygląd i zachowanie elementów nagłówka, które tworzą formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)). Każdy element nagłówek może mieć ciągu, obraz mapy bitowej, obrazu z listy skojarzony obraz lub zdefiniowanych przez aplikację 32-bitową wartość skojarzonych z nim. Ciąg, mapa bitowa lub obraz jest wyświetlany w elemencie nagłówka.

Gdy są one tworzone przez wywołania można dostosować wygląd i zawartość o nowych pozycjach [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem) lub modyfikując istniejący element z wywołaniem [CHeaderCtrl::GetItem](../mfc/reference/cheaderctrl-class.md#getitem) i [ CHeaderCtrl::SetItem](../mfc/reference/cheaderctrl-class.md#setitem).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Dostosowywanie wyglądu elementu nagłówka](../mfc/customizing-the-header-item-s-appearance.md)

- [Określanie kolejności elementów w formancie nagłówka](../mfc/ordering-items-in-the-header-control.md)

- [Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka](../mfc/providing-drag-and-drop-support-for-header-items.md)

- [Używanie list obrazów z formantami nagłówka](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)
