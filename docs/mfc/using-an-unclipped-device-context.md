---
title: Używanie nieobcinanego kontekstu urządzenia
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 0f129c0bfa5bd76df4ba34b117e7ed8aa08c2ecb
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57270673"
---
# <a name="using-an-unclipped-device-context"></a>Używanie nieobcinanego kontekstu urządzenia

Jeśli masz pewność, że kontroli nad nie można malować poza obszarem prostokąta jego klienta, można korzystać z zalet Uzyskaj prędkość małą ale wykrywalny, wyłączając wywołanie `IntersectClipRect` wykonanym przez `COleControl`. Aby to zrobić, należy usunąć *clipPaintDC* flagi z zestawu flag zwrócony przez [COleControl::GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Na przykład:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

Kod, aby usunąć ta flaga jest generowany automatycznie po wybraniu **Nieobcinanego kontekstu urządzenia** opcja [ustawienia kontroli](../mfc/reference/control-settings-mfc-activex-control-wizard.md) stronie podczas tworzenia kontrolki przy użyciu Kreatora kontrolek ActiveX MFC.

Jeśli używasz aktywacji niepowiązanej z oknami, tego rodzaju optymalizacji nie ma znaczenia.

## <a name="see-also"></a>Zobacz także

[Kontrolki ActiveX MFC: Optymalizacja](../mfc/mfc-activex-controls-optimization.md)
