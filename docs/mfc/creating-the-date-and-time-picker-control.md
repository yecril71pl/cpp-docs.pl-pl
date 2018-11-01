---
title: Tworzenie formantu selektora dat i godzin
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: 27a3a654a73300b7dd667d422fe84c73de524f3c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456131"
---
# <a name="creating-the-date-and-time-picker-control"></a>Tworzenie formantu selektora dat i godzin

Sposób tworzenia kontrolki selektora daty i godziny zależy od tego, czy są przy użyciu formantu w oknie dialogowym lub tworzenie go w oknie nondialog.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Aby użyć CDateTimeCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodawanie daty i czasu kontrolkę selektora do zasobu szablonu okna dialogowego. Określ identyfikator kontrolki.

1. Określ wszystkie style, wymagane, za pomocą okna dialogowego właściwości kontrolki selektora daty i godziny.

1. Użyj [Kreator dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej składowej typu [CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md) z właściwością kontrolki. Można użyć tego elementu członkowskiego do wywołania `CDateTimeCtrl` funkcji elementów członkowskich.

1. Użyj okna właściwości do mapowania funkcji obsługi w klasy okien dialogowych dla każdego formantu selektora czasu daty [powiadomień](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md) wymagana jest obsługa komunikatów (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style `CDateTimeCtrl` obiektu.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Aby użyć CDateTimeCtrl w oknie nondialog

1. Zadeklaruj kontrola w klasie widoku lub w oknie.

1. Wywoływanie kontrolki [Utwórz](../mfc/reference/ctabctrl-class.md#create) funkcję członkowską, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie jako wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy kontrolki). Ustawianie stylów dla formantu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

