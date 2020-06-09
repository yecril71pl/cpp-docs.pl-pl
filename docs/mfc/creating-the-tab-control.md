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
ms.openlocfilehash: 6d5aa6873966ecb4c845f1c503b24c07b6c0c7a3
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619609"
---
# <a name="creating-the-tab-control"></a>Tworzenie formantu karty

Sposób tworzenia kontrolki karta zależy od tego, czy używasz kontrolki w oknie dialogowym, czy też tworzysz ją w oknie niedialogowym.

### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Aby używać CTabCtrl bezpośrednio w oknie dialogowym

1. W edytorze okien dialogowych Dodaj kontrolkę karta do zasobu szablon okna dialogowego. Określ jego identyfikator kontrolki.

1. Użyj [Kreatora dodawania zmiennej członkowskiej](../ide/adding-a-member-variable-visual-cpp.md) , aby dodać zmienną członkowską typu [CTabCtrl](reference/ctabctrl-class.md) z właściwością Control. Tego elementu członkowskiego można użyć do wywołania `CTabCtrl` funkcji Członkowskich.

1. Funkcje obsługi mapy w klasie okna dialogowego dla wszystkich komunikatów powiadomień o kontrolkach kart, które należy obsłużyć. Aby uzyskać więcej informacji, zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md).

1. W [OnInitDialog](reference/cdialog-class.md#oninitdialog)Ustaw style dla `CTabCtrl` .

### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Aby użyć CTabCtrl w oknie niedialogowym

1. Zdefiniuj formant w klasie widoku lub okna.

1. Wywoływanie funkcji [tworzenia](reference/ctabctrl-class.md#create) elementu członkowskiego kontrolki, prawdopodobnie w [OnInitialUpdate](reference/cview-class.md#oninitialupdate), prawdopodobnie tak wcześnie jak funkcja procedury obsługi [OnCreate](reference/cwnd-class.md#oncreate) okna nadrzędnego (Jeśli jesteś podklasą kontrolki). Ustaw style dla kontrolki.

Po `CTabCtrl` utworzeniu obiektu można ustawić lub wyczyścić następujące style rozszerzone:

- **TCS_EX_FLATSEPARATORS** Kontrolka karta będzie rysować separatory między elementami tabulacji. Ten styl rozszerzony ma wpływ tylko na kontrolki karty, które mają style **TCS_BUTTONS** i **TCS_FLATBUTTONS** . Domyślnie utworzenie kontrolki karta z stylem **TCS_FLATBUTTONS** ustawia ten rozszerzony styl.

- **TCS_EX_REGISTERDROP** Kontrolka karta generuje **TCN_GETOBJECT** komunikatów powiadomień, aby zażądać obiektu docelowego upuszczania, gdy obiekt jest przeciągany nad elementami tabulacji w kontrolce.

    > [!NOTE]
    >  Aby odebrać powiadomienie **TCN_GETOBJECT** , należy ZAINICJOWAĆ biblioteki OLE z wywołaniem do [AfxOleInit](reference/ole-initialization.md#afxoleinit).

Te style można pobrać i ustawić, po utworzeniu kontrolki, przy użyciu odpowiednich wywołań do funkcji [getextended](reference/ctabctrl-class.md#getextendedstyle) i [setextended](reference/ctabctrl-class.md#setextendedstyle) elementu członkowskiego.

Na przykład ustaw styl **TCS_EX_FLATSEPARATORS** z następującymi wierszami kodu:

[!code-cpp[NVC_MFCControlLadenDialog#33](codesnippet/cpp/creating-the-tab-control_1.cpp)]

Wyczyść styl **TCS_EX_FLATSEPARATORS** z `CTabCtrl` obiektu z następującymi wierszami kodu:

[!code-cpp[NVC_MFCControlLadenDialog#34](codesnippet/cpp/creating-the-tab-control_2.cpp)]

Spowoduje to usunięcie separatorów, które pojawiają się między przyciskami `CTabCtrl` obiektu.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTabCtrl](using-ctabctrl.md)<br/>
[Formanty](controls-mfc.md)
