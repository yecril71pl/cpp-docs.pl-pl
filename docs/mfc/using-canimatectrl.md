---
title: Korzystanie z CAnimateCtrl | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CAnimateCtrl
dev_langs:
- C++
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b02a07b1f5a433ffa9525da8e8a7f942c9034d54
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398459"
---
# <a name="using-canimatectrl"></a>Korzystanie z CAnimateCtrl

Formantu animacji, reprezentowane przez klasę [CAnimateCtrl](../mfc/reference/canimatectrl-class.md), jest oknem, który wyświetla klip w formacie wideo z przeplotem AVI (Audio) — standardowego formatu audio/wideo Windows. Klip AVI to seria ramek mapy bitowej, takie jak film.

Ponieważ wątek kontynuuje wykonywanie, gdy jest wyświetlana tylko klip AVI, co spotykanym sposobem wykorzystania formantu animacji jest wskazujący aktywności systemu podczas długotrwałej operacji. Na przykład okno dialogowe Znajdź Windows wyświetla przenoszenie szkła powiększającego jako system wyszukuje plik.

Formanty animacji odtwarzać tylko proste klipy AVI, a nie obsługują one dźwięku. (Aby uzyskać pełną listę ograniczeń, zobacz [CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Ponieważ możliwości formantu animacji są znacznie ograniczone i może ulec zmianie, należy używać alternatywę, takie jak formant MCIWnd, jeśli potrzebujesz kontroli, aby zapewnić odtwarzania multimediów i/lub funkcje rejestrowania. Aby uzyskać więcej informacji na temat kontroli MCIWnd dokumentacji multimedialnych.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Używanie kontrolki animacji](../mfc/using-an-animation-control.md)

- [Powiadomienia wysyłane przez kontrolki animacji](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)

