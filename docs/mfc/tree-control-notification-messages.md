---
title: Komunikaty powiadomień dotyczących formantu drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
ms.openlocfilehash: 90e2e112d7862dfed7d8af31cfb72ff45633a2c1
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278405"
---
# <a name="tree-control-notification-messages"></a>Komunikaty powiadomień dotyczących formantu drzewa

Kontrolka drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) wysyła następujące komunikaty powiadomień w postaci wiadomości WM_NOTIFY:

|Komunikat z powiadomieniem|Opis|
|--------------------------|-----------------|
|TVN_BEGINDRAG|Sygnalizuje rozpoczęcia operacji przeciągania i upuszczania|
|TVN_BEGINLABELEDIT|Sygnalizuje początek Edytowanie etykiet w miejscu|
|TVN_BEGINRDRAG|Sygnalizuje rozpoczęcia operacji przeciągania i upuszczania, za pomocą prawego przycisku myszy|
|TVN_DELETEITEM|Sygnalizuje usunięcie określonego elementu|
|TVN_ENDLABELEDIT|Sygnalizuje koniec Edytowanie etykiet|
|TVN_GETDISPINFO|Żąda informacji, że kontrolka drzewa wymaga, aby wyświetlić element|
|TVN_ITEMEXPANDED|Sygnały, że listy elementów podrzędnych elementu nadrzędnego została rozwinięta czy zwinięta|
|TVN_ITEMEXPANDING|Sygnalizuje, że chcesz być rozwijane czy zwijane listy elementów podrzędnych elementu nadrzędnego|
|TVN_KEYDOWN|Sygnalizuje zdarzenie|
|TVN_SELCHANGED|Sygnalizuje, że zaznaczenie zostało zmienione z jednego elementu do innego|
|TVN_SELCHANGING|Sygnalizuje, że zaznaczenie zostanie zmieniony z jednego elementu do innego|
|TVN_SETDISPINFO|Powiadomienie, aby zaktualizować informacje dla elementu|

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
