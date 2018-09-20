---
title: Tworzenie kalendarza miesięcznego kontrolki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a0fadc3b56d0aa64068071ee7230ed125c6af925
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410874"
---
# <a name="creating-the-month-calendar-control"></a>Tworzenie formantu kalendarza miesięcznego

Sposób tworzenia formant kalendarza miesięcznego zależy od tego, czy są przy użyciu formantu w oknie dialogowym lub tworzenie go w oknie nondialog.

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>Aby użyć CMonthCalCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych należy dodać formant kalendarza miesięcznego do zasobu szablonu okna dialogowego. Określ identyfikator kontrolki.

1. Określ wszystkie style, wymagane, za pomocą okna dialogowego właściwości formantu kalendarza miesięcznego.

1. Użyj [Kreator dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej składowej typu [CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md) z właściwością kontrolki. Można użyć tego elementu członkowskiego do wywołania `CMonthCalCtrl` funkcji elementów członkowskich.

1. Użyj okna właściwości do mapowania funkcji obsługi w klasy okien dialogowych dla powiadomień formantu kalendarza miesięcznego wiadomości musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style `CMonthCalCtrl` obiektu.

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>Aby użyć CMonthCalCtrl w oknie nondialog

1. Zdefiniuj kontrolki w klasie widoku lub w oknie.

1. Wywoływanie kontrolki [Utwórz](../mfc/reference/cmonthcalctrl-class.md#create) funkcję członkowską, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie jako wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy kontrolki). Ustawianie stylów dla formantu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

