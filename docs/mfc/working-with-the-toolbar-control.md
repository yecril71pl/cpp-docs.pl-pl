---
title: Praca z formantem paska narzędzi
ms.date: 11/04/2016
helpviewer_keywords:
- GetToolBarCtrl method [MFC]
- toolbars [MFC], accessing common control
- CToolBarCtrl class [MFC], accessing toolbar
- toolbar controls [MFC], accessing
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
ms.openlocfilehash: 88c00bf60f2ce1fccecd757d13b2f814e3a18be4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399502"
---
# <a name="working-with-the-toolbar-control"></a>Praca z formantem paska narzędzi

W tym artykule wyjaśniono, jak można pobrać [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu bazowego [CToolBar](../mfc/reference/ctoolbar-class.md) uzyskać większą kontrolę nad pasków narzędzi. Jest to zaawansowane tematu.

## <a name="procedures"></a>Procedury

#### <a name="to-access-the-toolbar-common-control-underlying-your-ctoolbar-object"></a>Aby uzyskać dostęp bazowy obiekt CToolBar formantu typowego paska narzędzi

1. Wywołaj [CToolBar::GetToolBarCtrl](../mfc/reference/ctoolbar-class.md#gettoolbarctrl).

`GetToolBarCtrl` Zwraca odwołanie do [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) obiektu. Odwołania można użyć do wywołania funkcji elementów członkowskich klasy kontrolki paska narzędzi.

> [!CAUTION]
>  Podczas wywoływania `CToolBarCtrl` **uzyskać** funkcji jest bezpieczne, jeśli wywołasz należy zachować ostrożność **ustaw** funkcji. Jest to zaawansowane tematu. Zwykle nie należy uzyskać dostęp do podstawowych formantu paska narzędzi.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej na temat

- [Formanty (wspólnych formantów Windows)](../mfc/controls-mfc.md)

- [Podstawowe informacje dotyczące narzędzi](../mfc/toolbar-fundamentals.md)

- [Zadokowane i przestawne paski narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Dynamiczne zmiany rozmiaru na pasku narzędzi](../mfc/docking-and-floating-toolbars.md)

- [Etykietki narzędzi paska narzędzi](../mfc/toolbar-tool-tips.md)

- [Aktualizacje paska stanu flyby —](../mfc/toolbar-tool-tips.md)

- [Obsługa powiadomień dotyczących etykietek narzędzi](../mfc/handling-tool-tip-notifications.md)

- [CToolBar](../mfc/reference/ctoolbar-class.md) i [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) klas

- [Obsługa powiadomień dotyczących dostosowania](../mfc/handling-customization-notifications.md)

- [Wiele pasków narzędzi](../mfc/toolbar-fundamentals.md)

- [Używanie swoich starych pasków narzędzi](../mfc/using-your-old-toolbars.md)

- [Paski sterowania](../mfc/control-bars.md)

Aby uzyskać ogólne informacje o użyciu wspólnych formantów Windows, zobacz [wspólnych formantów](/windows/desktop/Controls/common-controls-intro).

## <a name="see-also"></a>Zobacz także

[MFC, implementacja paska narzędzi](../mfc/mfc-toolbar-implementation.md)
