---
title: Tworzenie formantu rozszerzonego pola kombi
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 87e2e1cd3c29ba838a17c24ece4a89adda21db0c
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907725"
---
# <a name="creating-an-extended-combo-box-control"></a>Tworzenie formantu rozszerzonego pola kombi

Sposób tworzenia rozszerzonej kontrolki pola kombi zależy od tego, czy używasz kontrolki w oknie dialogowym, czy też tworzysz ją w oknie niedialogowym.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Aby używać korzystanie CComboBoxEx bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodaj rozszerzoną kontrolkę pole kombi do zasobu szablonu okna dialogowego. Określ jego identyfikator kontrolki.

1. Określ wymagane style przy użyciu okna dialogowego właściwości kontrolki rozszerzonego pola kombi.

1. Użyj [Kreatora dodawania zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md) , aby dodać zmienną członkowską typu [Korzystanie CComboBoxEx](../mfc/reference/ccomboboxex-class.md) z właściwością Control. Tego elementu członkowskiego można użyć do `CComboBoxEx` wywołania funkcji Członkowskich.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) do mapowania funkcji obsługi w klasie okna dialogowego dla wszystkich komunikatów powiadomień rozszerzonego pola kombi, które są potrzebne do obsługi (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style dla `CComboBoxEx` obiektu.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Aby użyć korzystanie CComboBoxEx w oknie niedialogowym

1. Zdefiniuj formant w klasie widoku lub okna.

1. Wywoływanie funkcji [tworzenia](../mfc/reference/ctabctrl-class.md#create) elementu członkowskiego kontrolki, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie tak wcześnie jak funkcja procedury obsługi [OnCreate](../mfc/reference/cwnd-class.md#oncreate) okna nadrzędnego. Ustaw style dla kontrolki.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
