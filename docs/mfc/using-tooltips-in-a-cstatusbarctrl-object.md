---
title: Używanie etykietek narzędzi w obiekcie CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- tool tips [MFC], using in status bars
- status bars [MFC], tool tips
- CStatusBarCtrl class [MFC], tool tips
ms.assetid: a77597a7-43ef-4b8f-87bc-a8ea1dc63dc3
ms.openlocfilehash: a607a5fb8c9470df42d12c771865b924891b2dac
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442544"
---
# <a name="using-tooltips-in-a-cstatusbarctrl-object"></a>Używanie etykietek narzędzi w obiekcie CStatusBarCtrl

Aby włączyć etykietki narzędzi dla kontrolki pasek stanu, Utwórz obiekt `CStatusBarCtrl` z stylem SBT_TOOLTIPS.

> [!NOTE]
>  Jeśli używasz obiektu `CStatusBar`, aby zaimplementować swój pasek stanu, użyj funkcji `CStatusBar::CreateEx`. Umożliwia określenie dodatkowych stylów dla osadzonego obiektu `CStatusBarCtrl`.

Po pomyślnym utworzeniu obiektu `CStatusBarCtrl` Użyj [CStatusBarCtrl:: SetTipText](../mfc/reference/cstatusbarctrl-class.md#settiptext) i [CStatusBarCtrl:: GetTipText](../mfc/reference/cstatusbarctrl-class.md#gettiptext) , aby ustawić i pobrać tekst porady dla określonego okienka.

Po ustawieniu etykietki narzędzia jest wyświetlana tylko wtedy, gdy część ma ikonę i nie ma tekstu, lub jeśli nie można wyświetlić całego tekstu w części. Etykietki narzędzi nie są obsługiwane w trybie prostym.

## <a name="see-also"></a>Zobacz też

[Korzystanie ze CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
