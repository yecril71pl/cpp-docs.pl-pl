---
title: Style przycisku pokrętła
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907859"
---
# <a name="spin-button-styles"></a>Style przycisku pokrętła

Wiele ustawień przycisku pokrętła ([Korzystanie CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) są kontrolowane przez style. Za pomocą [kreatora klas](reference/mfc-class-wizard.md)można ustawić następujące style.

- **Orientacja** Pionowa lub pozioma. Steruje orientacją przycisków strzałek. Skojarzone ze stylem UDS_HORZ.

- **Wyrównanie** Jeden z niedołączonych, lewy lub prawy. Kontroluje lokalizację przycisku pokrętła. Po lewej i prawej stronie umieść przycisk pokrętła obok okna partnera. Szerokość okna partnera zostanie zmniejszona, aby pomieścić przycisk pokrętła. Skojarzone ze stylami UDS_ALIGNLEFT i UDS_ALIGNRIGHT.

- **Autokolega** Automatycznie wybiera poprzednie okno w porządku osi Z jako okno kolega do przycisku pokrętła. W szablonie okna dialogowego jest to formant, który poprzedza przycisk pokrętła w kolejności tabulacji. Skojarzone ze stylem UDS_AUTOBUDDY.

- **Ustaw znajomą liczbę całkowitą** Powoduje, że formant pokrętła zwiększy i zmniejszy podpis okna partnera w miarę zmiany bieżącej pozycji. Skojarzone ze stylem UDS_SETBUDDYINT.

- **Brak tysięcy** Nie wstawia separatora tysięcy do wartości w podpisie okna partnera. Skojarzone ze stylem UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Ustaw ten styl, jeśli chcesz użyć wymiany danych okna dialogowego (DDX) w celu uzyskania wartości całkowitej z formantu partnera. `DDX_Text`nie akceptuje osadzonych separatorów tysięcy.

- **Zawijaj** Powoduje, że pozycja "Otocz" jako wartość jest zwiększana lub zmniejszana poza zakresem formantu. Skojarzone ze stylem UDS_WRAP.

- **Klawisze strzałek** Powoduje, że przycisk pokrętła zwiększa lub zmniejsza pozycję po naciśnięciu klawiszy Strzałka w górę i Strzałka w dół. Skojarzone ze stylem UDS_ARROWKEYS.

## <a name="see-also"></a>Zobacz także

[Korzystanie ze CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
