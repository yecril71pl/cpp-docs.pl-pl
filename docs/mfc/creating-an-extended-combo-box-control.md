---
title: Tworzenie formantu rozszerzonego pola kombi
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 554085304f5330ac9cd99a5b814af26ce3a9c7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616285"
---
# <a name="creating-an-extended-combo-box-control"></a>Tworzenie formantu rozszerzonego pola kombi

Sposób tworzenia rozszerzonej kontrolki pola kombi zależy od tego, czy używasz kontrolki w oknie dialogowym, czy też tworzysz ją w oknie niedialogowym.

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Aby używać korzystanie CComboBoxEx bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodaj rozszerzoną kontrolkę pole kombi do zasobu szablonu okna dialogowego. Określ jego identyfikator kontrolki.

1. Określ wymagane style przy użyciu okna dialogowego właściwości kontrolki rozszerzonego pola kombi.

1. Użyj [Kreatora dodawania zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md) , aby dodać zmienną członkowską typu [Korzystanie CComboBoxEx](reference/ccomboboxex-class.md) z właściwością Control. Tego elementu członkowskiego można użyć do wywołania `CComboBoxEx` funkcji Członkowskich.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) do mapowania funkcji obsługi w klasie okna dialogowego dla wszystkich komunikatów powiadomień rozszerzonego pola kombi, które są potrzebne do obsługi (zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md)).

1. W [OnInitDialog](reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style dla `CComboBoxEx` obiektu.

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Aby użyć korzystanie CComboBoxEx w oknie niedialogowym

1. Zdefiniuj formant w klasie widoku lub okna.

1. Wywoływanie funkcji [tworzenia](reference/ctabctrl-class.md#create) elementu członkowskiego kontrolki, prawdopodobnie w [OnInitialUpdate](reference/cview-class.md#oninitialupdate), prawdopodobnie tak wcześnie jak funkcja procedury obsługi [OnCreate](reference/cwnd-class.md#oncreate) okna nadrzędnego. Ustaw style dla kontrolki.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CComboBoxEx](using-ccomboboxex.md)<br/>
[Formanty](controls-mfc.md)
