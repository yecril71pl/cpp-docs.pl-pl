---
title: Elementy nagłówka w formancie nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21f1893861c5cb6a134cffa75806cc53eadaf059
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442373"
---
# <a name="header-items-in-a-header-control"></a>Elementy nagłówka w formancie nagłówka

Masz znaczną kontrolę nad wygląd i zachowanie elementów nagłówka, które tworzą formantu nagłówka ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)). Każdy element nagłówek może mieć ciągu, obraz mapy bitowej, obrazu z listy skojarzony obraz lub zdefiniowanych przez aplikację 32-bitową wartość skojarzonych z nim. Ciąg, mapa bitowa lub obraz jest wyświetlany w elemencie nagłówka.

Gdy są one tworzone przez wywołania można dostosować wygląd i zawartość o nowych pozycjach [CHeaderCtrl::InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem) lub modyfikując istniejący element z wywołaniem [CHeaderCtrl::GetItem](../mfc/reference/cheaderctrl-class.md#getitem) i [ CHeaderCtrl::SetItem](../mfc/reference/cheaderctrl-class.md#setitem).

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Dostosowywanie wyglądu elementu nagłówka](../mfc/customizing-the-header-item-s-appearance.md)

- [Określanie kolejności elementów w formancie nagłówka](../mfc/ordering-items-in-the-header-control.md)

- [Zapewnianie obsługi przeciągania i upuszczania w przypadku elementów nagłówka](../mfc/providing-drag-and-drop-support-for-header-items.md)

- [Używanie list obrazów z formantami nagłówka](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)

