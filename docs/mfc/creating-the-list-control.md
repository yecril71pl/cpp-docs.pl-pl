---
title: Tworzenie formantu listy
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: f1c5d8db93421e1d3ae0e39aec82bdf0f5529f1f
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907924"
---
# <a name="creating-the-list-control"></a>Tworzenie formantu listy

Sposób tworzenia kontrolki listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) zależy od tego, czy używasz kontrolki bezpośrednio, czy przy użyciu klasy [CListView](../mfc/reference/clistview-class.md) . Jeśli używasz `CListView`, struktura konstruuje widok jako część sekwencji tworzenia dokumentu/widoku. Utworzenie widoku listy spowoduje również utworzenie kontrolki listy (dwa są takie same). Kontrolka jest tworzona w funkcji obsługi [OnCreate](../mfc/reference/cwnd-class.md#oncreate) widoku. W takim przypadku kontrolka jest gotowa do dodania elementów za pośrednictwem wywołania do [funkcji GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Aby używać CListCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodaj kontrolkę listy do zasobu szablonu okna dialogowego. Określ jego identyfikator kontrolki.

1. Użyj [Kreatora dodawania zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md) , aby dodać zmienną członkowską typu `CListCtrl` z właściwością kontrolki. Tego elementu członkowskiego można użyć do `CListCtrl` wywołania funkcji Członkowskich.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) do mapowania funkcji obsługi w klasie okna dialogowego dla wszystkich komunikatów powiadomień o kontrolkach listy, które są potrzebne do obsługi (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)Ustaw style dla `CListCtrl`. Zobacz [Zmiana stylów kontrolki listy](../mfc/changing-list-control-styles.md). Określa rodzaj "widoku", który otrzymujesz w kontrolce, chociaż można później zmienić widok.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Aby użyć CListCtrl w oknie niedialogowym

1. Zdefiniuj formant w klasie widoku lub okna.

1. Wywoływanie funkcji [tworzenia](../mfc/reference/clistctrl-class.md#create) elementu członkowskiego kontrolki, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie tak wcześnie jak funkcja procedury obsługi [OnCreate](../mfc/reference/cwnd-class.md#oncreate) okna nadrzędnego (Jeśli jesteś podklasą kontrolki). Ustaw style dla kontrolki.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
