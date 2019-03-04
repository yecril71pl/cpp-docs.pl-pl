---
title: Style formantu suwaka
ms.date: 11/04/2016
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
ms.openlocfilehash: c6765445552826b71cca278c1fbbc66e500cb75a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296855"
---
# <a name="slider-control-styles"></a>Style formantu suwaka

Formanty suwaka ([z CSliderCtrl](../mfc/reference/csliderctrl-class.md)) może mieć orientacji pionowej lub poziomej. Mogą mieć znaczniki osi po obu stronach obu stronach lub żadnego z tych celów. One można również określić zakres kolejnych wartości. Te właściwości są kontrolowane za pomocą style formantu suwaka, które określają, kiedy utworzyć formant suwaka.

Style TBS_HORZ i TBS_VERT określają orientację przestrzenną kontrolki slider. Jeśli nie określisz orientację, suwak jest ustawiony w poziomie.

Styl TBS_AUTOTICKS tworzy formant suwaka, który zawiera znacznik osi dla każdego przyrostu w swoim zakresie wartości. Te znaczniki są dodawane automatycznie, gdy wywołujesz [SetRange](../mfc/reference/csliderctrl-class.md#setrange) funkcja elementu członkowskiego. Jeśli nie określisz TBS_AUTOTICKS, funkcje składowe można użyć takich jak [SetTic](../mfc/reference/csliderctrl-class.md#settic) i [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), aby określić położenie znaczników. Aby utworzyć formant suwaka, które nie są wyświetlane znaczniki, można użyć stylu TBS_NOTICKS.

Znaczniki można wyświetlić z jednego lub obu tych stron kontrolki suwaka. Dla kontrolki suwaka poziomej można określić TBS_BOTTOM lub TBS_TOP stylu. Dla formantów w pionowej kontrolce slider można określić TBS_RIGHT lub TBS_LEFT stylu. (TBS_BOTTOM i TBS_RIGHT są ustawienia domyślne). Znaczniki osi po obu stronach kontrolki suwaka w dowolnym orientacji można określić w stylu TBS_BOTH.

Kontrolki suwaka można wyświetlić wybranego zakresu, tylko wtedy, gdy styl TBS_ENABLESELRANGE należy określić podczas jego tworzenia. Gdy ten styl znajdują się w kontrolce suwaka, znaczniki w pozycjach datę początkową i końcową wybranego zakresu są wyświetlane jako trójkąty (zamiast kreski pionowej) i jest wyróżniona wybranego zakresu. Na przykład może być przydatne w prostej aplikacji planowania zaznaczenie zakresów. Użytkownik może wybrać zakres znaczniki odpowiadający godzin w ciągu dnia, aby zidentyfikować czas zaplanowanego spotkania.

Domyślnie długość suwaka kontrolki suwaka zmienia się zgodnie ze zmianami zakres wyboru. Jeśli kontrolka suwaka ma styl TBS_FIXEDLENGTH, długość suwak pozostaje taki sam, nawet w przypadku zmiany wybranego zakresu. Kontrolki suwaka, którego styl TBS_NOTHUMB nie obejmuje suwaka.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
