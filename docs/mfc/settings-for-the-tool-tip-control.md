---
title: Ustawienia narzędzia formantu etykietki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6d0adfd1c7a7ae1e1f36fa8dd53610d19ad8e7b2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46379557"
---
# <a name="settings-for-the-tool-tip-control"></a>Ustawienia formantu etykietki narzędzia

Możesz ustawić formantem etykietki narzędzia ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) jako aktywną lub nieaktywną. Po ustawieniu go jako aktywny formantem etykietki narzędzia jest wyświetlany, gdy kursor znajduje się nad narzędziem. Po ustawieniu go jako nieaktywne formantem etykietki narzędzia jest niewidoczny, nawet jeśli kursor znajduje się nad narzędziem. Wywołaj [Aktywuj](../mfc/reference/ctooltipctrl-class.md#activate) aby aktywować lub dezaktywować formantem etykietki narzędzia.

Można ustawić aktywny podpowiedzi do wyświetlenia etykietki narzędzia, gdy kursor znajduje się nad narzędziem, czy okno właściciela formantem etykietki narzędzia jest aktywne lub nieaktywne, przy użyciu stylu TTS_ALWAYSTIP. Jeśli nie używasz ten styl, formantem etykietki narzędzia pojawia się, gdy okno właściciela tego narzędzia jest aktywna, ale nie w przypadku, gdy jest nieaktywny.

Większość aplikacji zawiera pasków narzędzi za pomocą narzędzi, które odnoszą się do poleceń menu. Dla tych narzędzi jest wygodne formantem etykietki narzędzia wyświetlić ten sam tekst jako odpowiedniego elementu menu. System automatycznie usuwa handlowe "i" (&) akceleratora znaków z wszystkie ciągi przekazywane do formantem etykietki narzędzia, chyba, że kontrolka ma styl TTS_NOPREFIX.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

