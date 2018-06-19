---
title: Tworzenie w formancie rozszerzonego pola kombi | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6a891aeadf2fa8366eec52a967e13776db6523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341215"
---
# <a name="creating-an-extended-combo-box-control"></a>Tworzenie formantu rozszerzonego pola kombi
Sposób tworzenia formancie rozszerzonego pola kombi zależy od tego, czy za pomocą formantu w oknie dialogowym lub tworzenia go w oknie nondialog.  
  
### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Do użycia bezpośrednio w oknie dialogowym CComboBoxEx  
  
1.  W edytorze okien dialogowych Dodaj rozszerzone pola kombi do zasobu szablonu okna dialogowego. Określ jego identyfikator formantu.  
  
2.  Określ wszystkie style wymagane, za pomocą okna dialogowego właściwości w formancie rozszerzonego pola kombi.  
  
3.  Użyj [Kreator dodawania zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej członka typu [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) razem z właściwością formantu. Ten element członkowski można użyć do wywołania `CComboBoxEx` funkcji elementów członkowskich.  
  
4.  Użyj okna właściwości do mapowania funkcje obsługi klasy okna dialogowego dowolnego pola kombi rozszerzonej kontroli komunikatów powiadomień musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustaw wszelkie dodatkowe style `CComboBoxEx` obiektu.  
  
### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Aby użyć CComboBoxEx w oknie nondialog  
  
1.  Zdefiniuj formantu w klasie widoku lub okna.  
  
2.  Wywołanie formantu [Utwórz](../mfc/reference/ctabctrl-class.md#create) prawdopodobnie w funkcji członkowskiej [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie możliwie wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi. Ustawianie stylów formantu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Kontrolki](../mfc/controls-mfc.md)

