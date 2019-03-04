---
title: Style przycisku pokrętła
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: d955ba1d76ee4d5648613ddaf6c5f6a652f3d3af
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304873"
---
# <a name="spin-button-styles"></a>Style przycisku pokrętła

Wiele ustawień dla przycisku pokrętła ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) są kontrolowane przez style. Można ustawić następujące style, przy użyciu **właściwości** okna w edytorze okien dialogowych.

- **Orientacja** pionowych lub poziomych. Określa orientację przycisków strzałek. Skojarzone ze stylem UDS_HORZ.

- **Wyrównanie** niedołączone, po lewej lub prawej. Określa położenie przycisku pokrętła. Lewy i prawy pozycji przycisku pokrętła obok okno cyklu. Szerokość okna zaprzyjaźnionego jest obniżona do uwzględnienia przycisku pokrętła. Skojarzone z UDS_ALIGNLEFT i UDS_ALIGNRIGHT style.

- **Auto Buddy** automatycznie wybiera poprzedniego okna w porządku osi Z jako okno buddy do przycisku pokrętła. W szablonu okna dialogowego to jest formant, który poprzedza przycisku pokrętła w kolejności tabulacji. Skojarzone ze stylem UDS_AUTOBUDDY.

- **Ustaw Buddy Integer** powoduje, że kontrolka pokrętła zwiększyć i zmniejszyć podpis okna zaprzyjaźnionego jako bieżące zmiany pozycji. Skojarzone ze stylem UDS_SETBUDDYINT.

- **Bez tysięcy** nie wstawia tysięcy separatorów w wartości w podpisie okno cyklu. Skojarzone ze stylem UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Ustaw ten styl, jeśli chcesz użyć wymiana danych okna dialogowego (DDX), aby uzyskać wartość całkowitą z formantu partnera. `DDX_Text` nie akceptuje osadzone separatory tysięcy.

- **OPAKOWYWANIE** sprawia, że położenie "wrap", wartość jest zwiększone lub zmniejszone poza zakresem formantu. Skojarzone ze stylem UDS_WRAP.

- **Klawisze strzałek** powoduje, że przycisk pokrętła, aby zwiększyć lub zmniejszyć pozycji po naciśnięciu klawisza Strzałka w górę i Strzałka w dół. Skojarzone ze stylem UDS_ARROWKEYS.

## <a name="see-also"></a>Zobacz także

[Korzystanie ze CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
