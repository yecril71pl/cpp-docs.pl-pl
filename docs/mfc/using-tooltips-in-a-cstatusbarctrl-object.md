---
title: Używanie etykietek narzędzi w obiekcie CStatusBarCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f17dff6680209664e9d029404e4ef012b9f12046
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392362"
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

