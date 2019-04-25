---
title: Ustawienia formantu postępu
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], settings
- progress controls [MFC], settings
ms.assetid: f4616e91-74fa-4000-ba0d-d3ddc0ee075b
ms.openlocfilehash: 1960b15c2f76d7cbfc9f249a77481b795e6a27ea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307682"
---
# <a name="settings-for-the-progress-control"></a>Ustawienia formantu postępu

Podstawowe ustawienia formantu postępu ([z CProgressCtrl](../mfc/reference/cprogressctrl-class.md)) to zakres i bieżącej pozycji. Zakres reprezentuje cały czas trwania operacji. Bieżąca pozycja reprezentuje postęp, który wprowadził aplikację do wykonywania operacji. Zmiany wprowadzone w zakresie lub pozycji spowodować kontrolki postępu do narysowania.

Domyślnie ustawiono zakres 0 - 100, a pozycja początkowa jest ustawiona na 0. Aby uzyskać bieżące ustawienia formantu postępu zakres, należy użyć [getrange —](../mfc/reference/cprogressctrl-class.md#getrange) funkcja elementu członkowskiego. Aby zmienić zakres, należy użyć [SetRange](../mfc/reference/cprogressctrl-class.md#setrange) funkcja elementu członkowskiego.

Aby ustawić położenie, użyj [SetPos](../mfc/reference/cprogressctrl-class.md#setpos). Aby pobrać bieżącą pozycję bez określenia nowej wartości, użyj [GetPos](../mfc/reference/cprogressctrl-class.md#getpos). Na przykład można po prostu zapytania o stan bieżącej operacji.

Aby wkraczać bieżące położenie kontrolki postępu, należy użyć [StepIt](../mfc/reference/cprogressctrl-class.md#stepit). Aby ustawić wartość każdego kroku, należy użyć [SetStep](../mfc/reference/cprogressctrl-class.md#setstep)

## <a name="see-also"></a>Zobacz także

[Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
