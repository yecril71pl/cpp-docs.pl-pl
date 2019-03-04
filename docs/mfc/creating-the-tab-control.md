---
title: Tworzenie formantu karty
ms.date: 11/04/2016
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
ms.openlocfilehash: 4627009e2e07d1c5692d83d8d6262a9fcd37977e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304915"
---
# <a name="creating-the-tab-control"></a>Tworzenie formantu karty

Sposób tworzenia kontrolki karty zależy od tego, czy za pomocą formantu w oknie dialogowym lub tworzenie go w oknie nondialog.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Aby użyć CTabCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodawanie formantu karty do zasobu szablonu okna dialogowego. Określ identyfikator kontrolki.

1. Użyj [Kreator dodawania zmiennej składowej](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej składowej typu [CTabCtrl](../mfc/reference/ctabctrl-class.md) z właściwością kontrolki. Można użyć tego elementu członkowskiego do wywołania `CTabCtrl` funkcji elementów członkowskich.

1. Mapowanie funkcji obsługi w klasy okien dialogowych dla dowolnej karcie komunikatów powiadomień dotyczących formantu potrzebnych do obsługi. Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustawianie stylów dla `CTabCtrl`.

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Aby użyć CTabCtrl w oknie nondialog

1. Zdefiniuj kontrolki w klasie widoku lub w oknie.

1. Wywoływanie kontrolki [Utwórz](../mfc/reference/ctabctrl-class.md#create) funkcję członkowską, prawdopodobnie w [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie jako wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy kontrolki). Ustawianie stylów dla formantu.

Po `CTabCtrl` obiekt został utworzony, można ustawić lub wyczyścić następujące style rozszerzone:

- **Tcs_ex_flatseparators —** formant karty będzie rysowanie separatory między elementami kartę. Rozszerzone style, tylko wpływa na karcie formantów, które mają **TCS_BUTTONS** i **TCS_FLATBUTTONS** style. Domyślnie, tworzenie formantu karty z **TCS_FLATBUTTONS** określa style rozszerzone style.

- **Tcs_ex_registerdrop —** generuje formant karty **TCN_GETOBJECT** powiadomienia do żądania miejsca docelowego obiektu, gdy obiekt jest przeciągany nad elementów karty w formancie.

    > [!NOTE]
    >  Aby otrzymać **TCN_GETOBJECT** powiadomienia, musisz zainicjować bibliotek OLE z wywołaniem [afxoleinit —](../mfc/reference/ole-initialization.md#afxoleinit).

Te style, można je pobrać i ustawić po utworzeniu kontrolki przy użyciu odpowiednich wywołań [GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) i [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) funkcji elementów członkowskich.

Na przykład ustawić **tcs_ex_flatseparators —** styl z następującymi wierszami kodu:

[!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]

Wyczyść **tcs_ex_flatseparators —** stylu z `CTabCtrl` obiektu z następującymi wierszami kodu:

[!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]

Spowoduje to usunięcie separatory, które pojawiają się między przyciskami z Twojej `CTabCtrl` obiektu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
