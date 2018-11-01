---
title: Używanie etykietek narzędzi w obiekcie CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a5ebefe3d5daab9917cdb1db7eface09c78b456a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438795"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Używanie etykietek narzędzi w obiekcie CStatusBarCtrl

Aby włączyć etykietki narzędzi dla formantu paska stanu, Utwórz `CStatusBarCtrl` obiektu ze stylem SBT_TOOLTIPS.

> [!NOTE]
>  Jeśli używasz `CStatusBar` obiekt implementuje pasek stanu, należy użyć `CStatusBar::CreateEx` funkcji. Pozwala określić dodatkowe style osadzonego `CStatusBarCtrl` obiektu.

Gdy `CStatusBarCtrl` obiektu została pomyślnie utworzona, należy użyć [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) i [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) do ustawiania i pobierania tekst porady dla określonych okienka.

Po ustawieniu etykietka narzędzia która jest wyświetlana, tylko wtedy, gdy część ikonę i tekst nie, czy cały tekst nie będzie wyświetlany w części. Etykietki narzędzi są nieobsługiwane w trybie uproszczonym.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

