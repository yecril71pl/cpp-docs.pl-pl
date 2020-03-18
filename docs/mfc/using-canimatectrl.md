---
title: Korzystanie z CAnimateCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- animation controls [MFC], CAnimateCtrl class
- controls [MFC], animation
- CAnimateCtrl class [MFC], about CAnimateCtrl class [MFC]
ms.assetid: 696c0805-bef0-4e2e-a9e7-b37b9215b7f0
ms.openlocfilehash: 79c1a0111317514ef6fd68acd0c6a2ebdccc3ba4
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447102"
---
# <a name="using-canimatectrl"></a>Korzystanie z CAnimateCtrl

Kontrolka animacji, reprezentowana przez klasę [Korzystanie CAnimateCtrl](../mfc/reference/canimatectrl-class.md), to okno, w którym jest wyświetlany klip w formacie audio video INTERLEAVED (AVI) — standardowy format wideo/audio systemu Windows. Klip AVI to seria klatek mapy bitowej, takich jak film.

Ponieważ wątek kontynuuje wykonywanie podczas wyświetlania klipu AVI, jednym typowym zastosowaniem formantu animacji jest wskazanie działania systemu podczas długotrwałej operacji. Na przykład okno dialogowe Znajdowanie systemu Windows wyświetla szklany lupę, w której system wyszukuje plik.

Kontrolki animacji mogą odtwarzać tylko proste klipy AVI i nie obsługują dźwięku. (Aby uzyskać pełną listę ograniczeń, zobacz [Korzystanie CAnimateCtrl](../mfc/reference/canimatectrl-class.md).) Ponieważ możliwości kontrolki animacji są poważnie ograniczone i mogą ulec zmianie, należy użyć alternatywnej metody, takiej jak kontrolka MCIWnd, jeśli potrzebna jest kontrolka umożliwiająca odtwarzanie i/lub nagrywanie multimediów. Więcej informacji o kontrolce MCIWnd można znaleźć w dokumentacji multimedialnej.

## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Używanie kontrolki animacji](../mfc/using-an-animation-control.md)

- [Powiadomienia wysyłane przez kontrolki animacji](../mfc/notifications-sent-by-animation-controls.md)

## <a name="see-also"></a>Zobacz też

[Kontrolki](../mfc/controls-mfc.md)
