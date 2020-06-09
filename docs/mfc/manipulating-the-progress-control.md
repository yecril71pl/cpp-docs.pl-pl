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
ms.openlocfilehash: 3e3521a82854a85062f9b06bc33eb268d4b9c7a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622430"
---
# <a name="manipulating-the-progress-control"></a>Operowanie formantem postępu

Istnieją trzy sposoby zmiany bieżącej pozycji kontrolki postępu ([Korzystanie CProgressCtrl](reference/cprogressctrl-class.md)).

- Pozycję można zmienić przez wstępnie ustawioną wartość przyrostu.

- Pozycję można zmienić za pomocą dowolnej kwoty.

- Pozycję można zmienić na określoną wartość.

### <a name="to-change-the-position-by-a-preset-amount"></a>Aby zmienić pozycję przez wstępnie ustawioną kwotę

1. Użyj funkcji elementu członkowskiego [SetStep](reference/cprogressctrl-class.md#setstep) , aby ustawić wartość przyrostu. Wartość domyślna to 10. Ta wartość jest zazwyczaj ustawiana jako jedno z ustawień początkowych dla kontrolki. Wartość kroku może być ujemna.

1. Użyj funkcji składowej [StepIt](reference/cprogressctrl-class.md#stepit) , aby zwiększyć położenie. Powoduje to, że formant będzie ponownie rysowany.

    > [!NOTE]
    >  `StepIt`spowoduje Zawijanie pozycji. Na przykład, mając zakres od 1 -100, krok 20 i pozycja 90, `StepIt` ustawi pozycję na 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Aby zmienić pozycję przez dowolną kwotę

1. Aby zmienić pozycję, użyj funkcji składowej [OffsetPos](reference/cprogressctrl-class.md#offsetpos) . `OffsetPos`akceptuje wartości ujemne.

    > [!NOTE]
    >  `OffsetPos`, w przeciwieństwie `StepIt` do, nie otacza położenia. Nowe położenie zostanie dostosowane do zakresu.

### <a name="to-change-the-position-to-a-specific-value"></a>Aby zmienić pozycję na określoną wartość

1. Użyj funkcji składowej [SetPos](reference/cprogressctrl-class.md#setpos) , aby ustawić pozycję na określoną wartość. W razie potrzeby nowe położenie zostanie dostosowane do zakresu.

Zazwyczaj kontrolka postępu jest używana wyłącznie dla danych wyjściowych. Aby uzyskać bieżącą pozycję bez określania nowej wartości, użyj [GetPos](reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Zobacz też

[Korzystanie z CProgressCtrl](using-cprogressctrl.md)<br/>
[Formanty](controls-mfc.md)
