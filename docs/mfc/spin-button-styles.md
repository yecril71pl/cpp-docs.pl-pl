---
title: Style przycisku pokrętła | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71da44858ea018d0393af6267e4bb522a2c57391
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393597"
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

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

