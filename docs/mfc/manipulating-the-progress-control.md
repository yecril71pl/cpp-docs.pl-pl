---
title: Operowanie formantem postępu
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: c9da6f8048adf1c7da184570ff7f94deee7441e5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289159"
---
# <a name="manipulating-the-progress-control"></a>Operowanie formantem postępu

Istnieją trzy sposoby, aby zmienić bieżącą pozycję formantu postępu ([z CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).

- Pozycja można zmienić wielkość przyrostu wstępnie zdefiniowane.

- Pozycja może zostać zmienione przez dowolnej ilości.

- Można zmienić położenie na określoną wartość.

### <a name="to-change-the-position-by-a-preset-amount"></a>Aby zmienić położenie według ilości wstępnie zdefiniowane

1. Użyj [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) funkcja elementu członkowskiego, aby ustawić wartość przyrostu. Domyślnie ta wartość wynosi 10. Ta wartość jest zazwyczaj ustawiana jako jedno z ustawień początkowych dla formantu. Wartość kroku może być ujemna.

1. Użyj [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) funkcja elementu członkowskiego, aby zwiększyć pozycji. To powoduje, że formant do narysowania.

    > [!NOTE]
    >  `StepIt` spowoduje, że położenie jest zawijane. Na przykład, biorąc pod uwagę zakresu 1 -100, krok 20 i położenie 90, `StepIt` ustawi pozycji do 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Aby zmienić położenie według dowolnej ilości

1. Użyj [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) funkcja elementu członkowskiego, aby zmienić położenie. `OffsetPos` będzie akceptować wartości ujemnych.

    > [!NOTE]
    >  `OffsetPos`, w odróżnieniu od `StepIt`, nie będzie zawijany w pozycji. Nowa pozycja jest dostosowywany pozostaje w zakresie.

### <a name="to-change-the-position-to-a-specific-value"></a>Aby zmienić położenie na określoną wartość

1. Użyj [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) funkcję elementu członkowskiego, aby ustawić położenie na określoną wartość. Jeśli to konieczne, nowe miejsce zostanie dopasowana do należeć do zakresu.

Zazwyczaj kontrolki postępu służy wyłącznie do danych wyjściowych. Aby uzyskać bieżącą pozycję bez określenia nowej wartości, użyj [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
