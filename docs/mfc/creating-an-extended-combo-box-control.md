---
title: Tworzenie formantu rozszerzonego pola kombi
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: bfc201fbb10c3caa3eaabd0e81206b9493ff7196
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153284"
---
# <a name="creating-an-extended-combo-box-control"></a>Tworzenie formantu rozszerzonego pola kombi

Sposób tworzenia formantu rozszerzonego pola kombi zależy od tego, czy za pomocą formantu w oknie dialogowym lub tworzenie go w oknie nondialog.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Aby korzystać z CComboBoxEx bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych należy dodać formant rozszerzone pola kombi do zasobu szablonu okna dialogowego. Określ identyfikator kontrolki.

1. Określ wszystkie style, wymagane, za pomocą okna dialogowego właściwości w formancie rozszerzonego pola kombi.

1. Użyj [Kreator dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej składowej typu [z CComboBoxEx](../mfc/reference/ccomboboxex-class.md) z właściwością kontrolki. Można użyć tego elementu członkowskiego do wywołania `CComboBoxEx` funkcji elementów członkowskich.

1. Użyj okna właściwości do mapowania funkcji obsługi w klasy okien dialogowych dowolnego pola kombi rozszerzonej kontroli komunikatów powiadomień będzie konieczna Obsługa (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style `CComboBoxEx` obiektu.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Aby korzystać z CComboBoxEx w oknie nondialog

1. Zdefiniuj kontrolki w klasie widoku lub w oknie.

1. Wywoływanie kontrolki [Utwórz](../mfc/reference/ctabctrl-class.md#create) funkcję członkowską, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie jako wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi. Ustawianie stylów dla formantu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
