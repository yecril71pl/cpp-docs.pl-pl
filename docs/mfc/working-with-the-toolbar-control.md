---
title: Praca z formantem paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 60cc527493e2a68751c201b998ab171c564d6c1f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510580"
---
# <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi

W tym artykule wyjaśniono, jak uzyskać dostęp do obiektu [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) bazowego [CToolBar](../mfc/reference/ctoolbar-class.md) w celu uzyskania większej kontroli nad paskami narzędzi. To jest zaawansowany temat.

## <a name="procedures"></a>Procedury

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Aby uzyskać dostęp do typowej kontrolki paska narzędzi leżącej pod obiektem CToolBar

1. Wywołanie [CToolBar:: GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl`Zwraca odwołanie do obiektu [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) . Można użyć odwołania do wywołania funkcji członkowskich klasy formantu Toolbar.

> [!CAUTION]
>  Gdy wywoływanie `CToolBarCtrl` funkcji **Get** jest bezpieczne, należy zachować ostrożność w przypadku wywołania funkcji **Set** . To jest zaawansowany temat. Zwykle nie trzeba uzyskiwać dostępu do podstawowego formantu paska narzędzi.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o

- [Kontrolki (formanty standardowe systemu Windows)](../mfc/controls-mfc.md)

- [Podstawy paska narzędzi](../mfc/toolbar-fundamentals.md)

- [Dokowanie i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Dynamiczne zmienianie rozmiarów paska narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Wskazówki dotyczące narzędzia paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Aktualizacje paska stanu Flyby](../mfc/toolbar-tool-tips.md)

- [Obsługa powiadomień dotyczących etykietek narzędzi](../mfc/handling-tool-tip-notifications.md)

- Klasy [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)

- [Obsługa powiadomień dotyczących dostosowania](../mfc/handling-customization-notifications.md)

- [Wiele pasków narzędzi](../mfc/toolbar-fundamentals.md)

- [Używanie starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

- [Paski sterowania](../mfc/control-bars.md)

Aby uzyskać ogólne informacje dotyczące korzystania z formantów wspólnych systemu Windows, zobacz temat [typowe formanty](/windows/win32/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz także

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
