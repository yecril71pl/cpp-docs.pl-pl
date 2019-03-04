---
title: Zapewnianie aktywacji pozbawionej migotania
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
ms.openlocfilehash: fad24d6201260e87ff32436752a9fbf035e822ae
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287677"
---
# <a name="providing-flicker-free-activation"></a>Zapewnianie aktywacji pozbawionej migotania

Jeśli formant rysuje samą siebie identycznie w Stanach nieaktywne i aktywne (a nie korzysta z aktywacji niepowiązanej z oknami) można wyeliminować operacji rysowania i towarzyszące migotania visual, które zazwyczaj występują podczas wykonywania przejścia między nieaktywnych i Stany aktywne. Aby to zrobić, należy dołączyć **noFlickerActivate** flagi w zestawie flagi zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]

Kod, aby dołączyć tę flagę, jest generowany automatycznie po wybraniu **aktywacji pozbawionej migotania** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stronie podczas tworzenia kontrolki przy użyciu Kreatora kontrolek ActiveX MFC.

Jeśli używasz aktywacji niepowiązanej z oknami, tego rodzaju optymalizacji nie ma znaczenia.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)
