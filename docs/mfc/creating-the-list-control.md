---
title: Tworzenie formantu listy
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: 7b2cb47699339dd413dc1bfae7623069da56e7a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242253"
---
# <a name="creating-the-list-control"></a>Tworzenie formantu listy

Jak kontrolować listy ([CListCtrl](../mfc/reference/clistctrl-class.md)) jest tworzony jest zależna od tego, czy jesteś bezpośrednio za pomocą formantu lub przy użyciu klasy [CListView](../mfc/reference/clistview-class.md) zamiast tego. Jeśli używasz `CListView`, struktura tworzy widok jako część jej Sekwencja tworzenia dokumentu/widoku. Utworzenie widoku listy powoduje utworzenie kontrolki listy również (dwa są tak samo). Formant zostanie utworzony w widoku [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi. W takim przypadku kontrolka jest gotowy do dodawania elementów poprzez wywołanie [GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl).

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>Aby użyć CListCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych należy dodać kontrolkę listy do zasobu szablonu okna dialogowego. Określ identyfikator kontrolki.

1. Użyj [Kreator dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej składowej typu `CListCtrl` z właściwością kontrolki. Można użyć tego elementu członkowskiego do wywołania `CListCtrl` funkcji elementów członkowskich.

1. Użyj okna właściwości do mapowania funkcji obsługi w klasy okien dialogowych dla wszystkich powiadomień formantu listy wiadomości musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustawianie stylów dla `CListCtrl`. Zobacz [Zmienianie stylów kontrolki listy](../mfc/changing-list-control-styles.md). Określa rodzaj "view" Pobierz w kontrolce, mimo że można później zmienić widok.

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>Aby użyć CListCtrl w oknie nondialog

1. Zdefiniuj kontrolki w klasie widoku lub w oknie.

1. Wywoływanie kontrolki [Utwórz](../mfc/reference/clistctrl-class.md#create) funkcję członkowską, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie jako wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy kontrolki). Ustawianie stylów dla formantu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
