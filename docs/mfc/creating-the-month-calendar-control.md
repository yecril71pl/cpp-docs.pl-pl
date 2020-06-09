---
title: Tworzenie formantu kalendarza miesięcznego
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 49d21bd4ce5aae23d5fc4c74567bc1c1d5a43570
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616237"
---
# <a name="creating-the-month-calendar-control"></a>Tworzenie formantu kalendarza miesięcznego

Sposób tworzenia kontrolki kalendarza miesięcznego zależy od tego, czy kontrolka jest używana w oknie dialogowym, czy też jest tworzona w oknie niedialogowym.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Aby używać CMonthCalCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodaj formant kalendarza miesięcznego do zasobu szablonu okna dialogowego. Określ jego identyfikator kontrolki.

1. Określ wymagane style przy użyciu okna dialogowego właściwości kontrolki kalendarza miesięcznego.

1. Użyj [Kreatora dodawania zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md) , aby dodać zmienną członkowską typu [CMonthCalCtrl](reference/cmonthcalctrl-class.md) z właściwością Control. Tego elementu członkowskiego można użyć do wywołania `CMonthCalCtrl` funkcji Członkowskich.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby zamapować funkcje obsługi w klasie okna dialogowego na komunikaty powiadomień o dowolnym miesiącu, które mają być obsługiwane (zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style dla `CMonthCalCtrl` obiektu.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Aby użyć CMonthCalCtrl w oknie niedialogowym

1. Zdefiniuj formant w klasie widoku lub okna.

1. Wywoływanie funkcji [tworzenia](reference/cmonthcalctrl-class.md#create) elementu członkowskiego kontrolki, prawdopodobnie w [OnInitialUpdate](reference/cview-class.md#oninitialupdate), prawdopodobnie tak wcześnie jak funkcja procedury obsługi [OnCreate](reference/cwnd-class.md#oncreate) okna nadrzędnego (Jeśli jesteś podklasą kontrolki). Ustaw style dla kontrolki.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CMonthCalCtrl](using-cmonthcalctrl.md)<br/>
[Formanty](controls-mfc.md)
