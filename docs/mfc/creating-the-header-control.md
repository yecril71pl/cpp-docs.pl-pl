---
title: Tworzenie formantu nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 99269214666c324214422ad989dbbd8bff6fc345
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508811"
---
# <a name="creating-the-header-control"></a>Tworzenie formantu nagłówka

Kontrolka nagłówka nie jest bezpośrednio dostępna w edytorze okien dialogowych (chociaż można dodać kontrolkę listy, która zawiera kontrolkę nagłówka).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Aby umieścić kontrolkę nagłówka w oknie dialogowym

1. Ręcznie Osadź zmienną członkowską typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) w klasie okna dialogowego.

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)Utwórz i ustaw style dla `CHeaderCtrl`, umieść je i Wyświetl.

1. Dodaj elementy do kontrolki nagłówek.

1. Użyj okno Właściwości do mapowania funkcji obsługi w klasie okna dialogowego dla wszelkich komunikatów powiadomień o formancie nagłówka, które należy obsłużyć (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Aby umieścić kontrolkę nagłówka w widoku (nie CListView)

1. Osadź obiekt [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) w klasie widoku.

1. Styl, położenie i wyświetlanie okna kontrolki nagłówka w funkcji składowej [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) widoku.

1. Dodaj elementy do kontrolki nagłówek.

1. Użyj okno Właściwości do mapowania funkcji obsługi w klasie widoku dla wszelkich komunikatów powiadomień o formancie nagłówka, które należy obsłużyć (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

W obu przypadkach osadzony obiekt sterowania jest tworzony podczas tworzenia obiektu widoku lub okna dialogowego. Następnie należy wywołać [CHeaderCtrl:: Create](../mfc/reference/cheaderctrl-class.md#create) , aby utworzyć okno sterowania. Aby ustawić położenie kontrolki, wywołaj [CHeaderCtrl:: układ](../mfc/reference/cheaderctrl-class.md#layout) , aby określić początkowy rozmiar i położenie kontrolki oraz [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) w celu ustawienia żądanego położenia. Następnie Dodaj elementy zgodnie z opisem w temacie [Dodawanie elementów do formantu nagłówka](../mfc/adding-items-to-the-header-control.md).

Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki nagłówka](/windows/win32/Controls/header-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
