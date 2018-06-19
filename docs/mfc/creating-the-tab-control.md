---
title: Tworzenie formantu karty | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TCS_EX_REGISTERDROP
- TCS_EX_FLATSEPARATORS
dev_langs:
- C++
helpviewer_keywords:
- TCS_EX_REGISTERDROP extended style [MFC]
- tab controls [MFC], creating
- CTabCtrl class [MFC], creating
- TCS_EX_FLATSEPARATORS extended style
ms.assetid: 3a9c2d64-f5f4-41ea-84ab-fceb73c3dbdc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3945d441130d723bbda3d137f2adae637d56c2b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33344094"
---
# <a name="creating-the-tab-control"></a>Tworzenie formantu karty
Sposób tworzenia formantu karty zależy od tego, czy za pomocą formantu w oknie dialogowym lub tworzenia go w oknie nondialog.  
  
### <a name="to-use-ctabctrl-directly-in-a-dialog-box"></a>Do użycia bezpośrednio w oknie dialogowym CTabCtrl  
  
1.  W edytorze okna dialogowego Dodawanie formantu karty zasobu szablonu okna dialogowego. Określ jego identyfikator formantu.  
  
2.  Użyj [Kreator dodawania zmiennej elementu członkowskiego](../ide/adding-a-member-variable-visual-cpp.md) można dodać zmiennej członka typu [CTabCtrl](../mfc/reference/ctabctrl-class.md) razem z właściwością formantu. Ten element członkowski można użyć do wywołania `CTabCtrl` funkcji elementów członkowskich.  
  
3.  Mapowanie funkcji programu obsługi w klasy okien dialogowych dla dowolnego karta komunikaty powiadomień dotyczących formantu potrzebnych do obsługi. Aby uzyskać więcej informacji, zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md).  
  
4.  W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), ustawianie stylów dla `CTabCtrl`.  
  
### <a name="to-use-ctabctrl-in-a-nondialog-window"></a>Do użycia w oknie nondialog CTabCtrl  
  
1.  Zdefiniuj formantu w klasie widoku lub okna.  
  
2.  Wywołanie formantu [Utwórz](../mfc/reference/ctabctrl-class.md#create) prawdopodobnie w funkcji członkowskiej [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), prawdopodobnie możliwie wczesne jako okno nadrzędne [OnCreate](../mfc/reference/cwnd-class.md#oncreate) funkcji obsługi (w przypadku Tworzenie podklasy formantu). Ustawianie stylów formantu.  
  
 Po `CTabCtrl` obiekt został utworzony, możesz zaznaczyć lub wyczyścić następujące rozszerzone style:  
  
-   **Tcs_ex_flatseparators —** formantu karty narysuje separatorów między elementami kartę. Rozszerzone style, tylko wpływa na karcie formantów, które mają **TCS_BUTTONS** i **TCS_FLATBUTTONS** style. Domyślnie tworzenie formantu karty z **TCS_FLATBUTTONS** ustawia styl, to rozszerzone style.  
  
-   **Tcs_ex_registerdrop —** generuje formantu karty **TCN_GETOBJECT** komunikatów powiadomień, aby zażądać miejsca docelowego obiektu, gdy obiekt zostanie przeciągnięty nad elementami kartę w formancie.  
  
    > [!NOTE]
    >  Aby otrzymywać **TCN_GETOBJECT** powiadomienia, należy zainicjować bibliotek OLE z wywołaniem do [afxoleinit —](../mfc/reference/ole-initialization.md#afxoleinit).  
  
 Można je pobrać i ustawić po utworzeniu formantu z odpowiedniego wywołania te style [GetExtendedStyle](../mfc/reference/ctabctrl-class.md#getextendedstyle) i [SetExtendedStyle](../mfc/reference/ctabctrl-class.md#setextendedstyle) funkcji elementów członkowskich.  
  
 Na przykład ustawić **tcs_ex_flatseparators —** styl następujące wiersze kodu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#33](../mfc/codesnippet/cpp/creating-the-tab-control_1.cpp)]  
  
 Wyczyść **tcs_ex_flatseparators —** stylu z `CTabCtrl` obiektu następujące wiersze kodu:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#34](../mfc/codesnippet/cpp/creating-the-tab-control_2.cpp)]  
  
 Spowoduje to usunięcie separatorów, które pojawiają się między przyciskami z Twojej `CTabCtrl` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

