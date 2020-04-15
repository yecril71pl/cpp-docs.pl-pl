---
title: Praca z formantem paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 371f1944fae655556bbc9f89d7ffcce7cc326e5e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365246"
---
# <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi

W tym artykule wyjaśniono, jak można uzyskać dostęp do [obiektu CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) leżącego u podstaw [CToolBar](../mfc/reference/ctoolbar-class.md) dla większej kontroli nad paskami narzędzi. Jest to zaawansowany temat.

## <a name="procedures"></a>Procedury

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Aby uzyskać dostęp do wspólnego formantu paska narzędzi leżącego u podstaw obiektu CToolBar

1. Wywołanie [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`zwraca odwołanie do [obiektu CToolBarCtrl.](../mfc/reference/ctoolbarctrl-class.md) Odwołanie służy do wywoływania funkcji członkowskich klasy sterowania paska narzędzi.

> [!CAUTION]
> Podczas `CToolBarCtrl` wywoływania **Funkcji Pobierz** jest bezpieczne, należy zachować ostrożność, jeśli wywołasz **Ustaw** funkcje. Jest to zaawansowany temat. Zwykle nie należy mieć dostępu do podstawowej kontroli paska narzędzi.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz wiedzieć więcej o

- [Formanty (typowe formanty systemu Windows)](../mfc/controls-mfc.md)

- [Podstawy paska narzędzi](../mfc/toolbar-fundamentals.md)

- [Dokowanie i pływające paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Dynamiczna zmiana rozmiaru paska narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Wskazówki dotyczące narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Aktualizacje paska stanu flyby](../mfc/toolbar-tool-tips.md)

- [Powiadomienia o etykietkach narzędzi obsługi](../mfc/handling-tool-tip-notifications.md)

- Klasy [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Obsługa powiadomień o dostosowywaniu](../mfc/handling-customization-notifications.md)

- [Wiele pasków narzędzi](../mfc/toolbar-fundamentals.md)

- [Korzystanie ze starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

- [Pręty sterujące](../mfc/control-bars.md)

Aby uzyskać ogólne informacje dotyczące korzystania z typowych formantów systemu Windows, zobacz [Typowe formanty](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz też

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
