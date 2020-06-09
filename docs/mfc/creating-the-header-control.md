---
title: Tworzenie formantu nagłówka
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: b08dd4d3f12c70ae495b20b936d44f6a695d1ae1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616244"
---
# <a name="creating-the-header-control"></a>Tworzenie formantu nagłówka

Kontrolka nagłówka nie jest bezpośrednio dostępna w edytorze okien dialogowych (chociaż można dodać kontrolkę listy, która zawiera kontrolkę nagłówka).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Aby umieścić kontrolkę nagłówka w oknie dialogowym

1. Ręcznie Osadź zmienną członkowską typu [CHeaderCtrl](reference/cheaderctrl-class.md) w klasie okna dialogowego.

1. W [OnInitDialog](reference/cdialog-class.md#oninitdialog)Utwórz i ustaw style dla `CHeaderCtrl` , umieść je i Wyświetl.

1. Dodaj elementy do kontrolki nagłówek.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) do mapowania funkcji obsługi w klasie okna dialogowego dla wszelkich komunikatów powiadomień o formancie nagłówka, które są potrzebne do obsługi (zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Aby umieścić kontrolkę nagłówka w widoku (nie CListView)

1. Osadź obiekt [CHeaderCtrl](reference/cheaderctrl-class.md) w klasie widoku.

1. Styl, położenie i wyświetlanie okna kontrolki nagłówka w funkcji składowej [OnInitialUpdate](reference/cview-class.md#oninitialupdate) widoku.

1. Dodaj elementy do kontrolki nagłówek.

1. Użyj [kreatora klas](reference/mfc-class-wizard.md) , aby zamapować funkcje obsługi w klasie widoku dla wszystkich komunikatów powiadomień o formancie nagłówka, które są potrzebne do obsługi (zobacz [Mapowanie komunikatów do funkcji](reference/mapping-messages-to-functions.md)).

W obu przypadkach osadzony obiekt sterowania jest tworzony podczas tworzenia obiektu widoku lub okna dialogowego. Następnie należy wywołać [CHeaderCtrl:: Create](reference/cheaderctrl-class.md#create) , aby utworzyć okno sterowania. Aby ustawić położenie kontrolki, wywołaj [CHeaderCtrl:: układ](reference/cheaderctrl-class.md#layout) , aby określić początkowy rozmiar i położenie kontrolki oraz [SetWindowPos](reference/cwnd-class.md#setwindowpos) w celu ustawienia żądanego położenia. Następnie Dodaj elementy zgodnie z opisem w temacie [Dodawanie elementów do formantu nagłówka](adding-items-to-the-header-control.md).

Aby uzyskać więcej informacji, zobacz [Tworzenie kontrolki nagłówka](/windows/win32/Controls/header-controls) w Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](using-cheaderctrl.md)<br/>
[Formanty](controls-mfc.md)
