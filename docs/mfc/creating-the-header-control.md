---
title: Tworzenie formantu nagłówka | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 29ba8f4d75071bc5d1859c7df721b86aa83f14e1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393974"
---
# <a name="creating-the-header-control"></a>Tworzenie formantu nagłówka

Kontrolki nagłówka nie jest dostępne bezpośrednio w edytorze okien dialogowych (mimo że można dodać kontrolkę listy, która zawiera kontrolki nagłówka o).

### <a name="to-put-a-header-control-in-a-dialog-box"></a>Umieszczenie kontrolki nagłówka w oknie dialogowym

1. Ręczne osadzania zmienną składową typu [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) w klasy okien dialogowych.

1. W [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), tworzenie i ustawianie stylów dla `CHeaderCtrl`, umieść ją i wyświetlenia go.

1. Dodawanie elementów do formantu nagłówka.

1. Użyj okna właściwości do mapowania funkcji obsługi w klasy okien dialogowych dla wszystkich powiadomień kontrolki nagłówka wiadomości, które musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>Umieszczenie kontrolki nagłówka w widoku (nie CListView)

1. Osadzanie [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md) obiektów w klasie widoku.

1. Styl, umieść i wyświetlić okno kontrolki nagłówka w widoku [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) funkcja elementu członkowskiego.

1. Dodawanie elementów do formantu nagłówka.

1. Użyj okna właściwości do mapowania funkcji obsługi w klasie widoku dla wszystkich powiadomień kontrolki nagłówka wiadomości, które musi obsłużyć (zobacz [mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)).

W obu przypadkach formantu osadzonego obiektu jest tworzony podczas tworzenia obiektu widoku lub w oknie dialogowym. Należy wywołać [CHeaderCtrl::Create](../mfc/reference/cheaderctrl-class.md#create) można utworzyć okna kontrolki. Położenie formantu, należy wywołać [CHeaderCtrl::Layout](../mfc/reference/cheaderctrl-class.md#layout) ustalenie, początkowy rozmiar i położenie kontrolki i [SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos) można ustawić odpowiednie miejsce. Następnie dodaj elementy, zgodnie z opisem w [Dodawanie elementów do formantu nagłówka](../mfc/adding-items-to-the-header-control.md).

Aby uzyskać więcej informacji, zobacz [Tworzenie formantu nagłówka](/windows/desktop/Controls/header-controls) w zestawie Windows SDK.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

