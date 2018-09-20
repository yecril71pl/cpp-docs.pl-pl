---
title: Operowanie formantem postępu | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9fe784dfd63ec5c27a3695df3e6bc42ae0de2f7f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46416776"
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

## <a name="see-also"></a>Zobacz też

[Korzystanie z CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

