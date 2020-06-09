---
title: Tworzenie formantu selektora dat i godzin
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: 5d753b166454b795932ec8f47b0897829fab9b8e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620468"
---
# <a name="creating-the-date-and-time-picker-control"></a>Tworzenie formantu selektora dat i godzin

Sposób tworzenia kontrolki selektora daty i godziny zależy od tego, czy używasz kontrolki w oknie dialogowym, czy też tworzysz ją w oknie niedialogowym.

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>Aby używać korzystanie CDateTimeCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodaj kontrolkę selektora daty i godziny do zasobu szablonu okna dialogowego. Określ jego identyfikator kontrolki.

1. Określ wymagane style przy użyciu okna dialogowego właściwości kontrolki selektora daty i godziny.

1. Użyj [Kreatora dodawania zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md) , aby dodać zmienną członkowską typu [Korzystanie CDateTimeCtrl](reference/cdatetimectrl-class.md) z właściwością Control. Tego elementu członkowskiego można użyć do wywołania `CDateTimeCtrl` funkcji Członkowskich.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby zamapować funkcje obsługi w klasie okna dialogowego dla dowolnego selektora dat kontroli i komunikatów [powiadomień](processing-notification-messages-in-date-and-time-picker-controls.md) potrzebnych do obsługi (zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style dla `CDateTimeCtrl` obiektu.

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>Aby użyć korzystanie CDateTimeCtrl w oknie niedialogowym

1. Zadeklaruj formant w klasie widoku lub okna.

1. Wywoływanie funkcji [tworzenia](reference/ctabctrl-class.md#create) elementu członkowskiego kontrolki, prawdopodobnie w [OnInitialUpdate](reference/cview-class.md#oninitialupdate), prawdopodobnie tak wcześnie jak funkcja procedury obsługi [OnCreate](reference/cwnd-class.md#oncreate) okna nadrzędnego (Jeśli jesteś podklasą kontrolki). Ustaw style dla kontrolki.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[Formanty](controls-mfc.md)
