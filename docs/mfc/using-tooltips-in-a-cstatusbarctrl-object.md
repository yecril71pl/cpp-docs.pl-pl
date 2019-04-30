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
ms.openlocfilehash: 3f9a1fec7eb951fa76c542e09df751b4c58ddb16
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411438"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Używanie etykietek narzędzi w obiekcie CStatusBarCtrl

Aby włączyć etykietki narzędzi dla formantu paska stanu, Utwórz `CStatusBarCtrl` obiektu ze stylem SBT_TOOLTIPS.

> [!NOTE]
>  Jeśli używasz `CStatusBar` obiekt implementuje pasek stanu, należy użyć `CStatusBar::CreateEx` funkcji. Pozwala określić dodatkowe style osadzonego `CStatusBarCtrl` obiektu.

Gdy `CStatusBarCtrl` obiektu została pomyślnie utworzona, należy użyć [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) i [CStatusBarCtrl::GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) do ustawiania i pobierania tekst porady dla określonych okienka.

Po ustawieniu etykietka narzędzia która jest wyświetlana, tylko wtedy, gdy część ikonę i tekst nie, czy cały tekst nie będzie wyświetlany w części. Etykietki narzędzi są nieobsługiwane w trybie uproszczonym.

## <a name="see-also"></a>Zobacz także

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
