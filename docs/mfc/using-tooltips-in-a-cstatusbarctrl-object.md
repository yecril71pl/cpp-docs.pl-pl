---
title: Używanie etykietek narzędzi w obiekcie CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: 29d326c708743424686d616bbaf172ccd72481ce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374694"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Używanie etykietek narzędzi w obiekcie CStatusBarCtrl

Aby włączyć etykietki narzędzi dla formantu paska stanu, utwórz `CStatusBarCtrl` obiekt o SBT_TOOLTIPS stylu.

> [!NOTE]
> Jeśli używasz `CStatusBar` obiektu do zaimplementowania `CStatusBar::CreateEx` paska stanu, użyj funkcji. Umożliwia określenie dodatkowych stylów dla `CStatusBarCtrl` obiektu osadzonego.

Po `CStatusBarCtrl` pomyślnym utworzeniu obiektu użyj [CStatusBarCtrl::SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) i [CStatusBarCtrl::GetTipText,](../mfc/reference/cstatusbarctrl-class.md#gettiptext) aby ustawić i pobrać tekst końcówki dla określonego okienka.

Po ustawieniu etykietki narzędzia jest wyświetlana tylko wtedy, gdy część ma ikonę i nie ma tekstu lub jeśli cały tekst nie może być wyświetlany wewnątrz części. Porady dotyczące narzędzi nie są obsługiwane w trybie prostym.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Formanty](../mfc/controls-mfc.md)
