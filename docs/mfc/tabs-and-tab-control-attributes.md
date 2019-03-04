---
title: Karty i atrybuty formantu karty
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: ca9f89565770e60a59007d609d132fae15eacae6
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304798"
---
# <a name="tabs-and-tab-control-attributes"></a>Karty i atrybuty formantu karty

Masz znaczną kontrolę nad wyglądu i zachowania kart, które tworzą formantu karty ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Każda karta może mieć etykietę, ikony, stan elementu i zdefiniowanych przez aplikację 32-bitową wartość skojarzonych z nim. Dla każdej karty można wyświetlić, ikona i/lub etykiety.

Ponadto każdy element karta może mieć trzy stany: naciśnięty, nieklikniętego lub wyróżnione. Ten stan można ustawić tylko przez zmodyfikowanie istniejącego elementu karty. Aby zmodyfikować istniejący element kartę, należy pobrać go przy użyciu wywołania do [GetItem](../mfc/reference/ctabctrl-class.md#getitem), zmodyfikować `TCITEM` struktury (w szczególności *dwState* i *dwStateMask* elementy członkowskie danych ), a następnie zwracają zmodyfikowanego `TCITEM` struktury z wywołaniem [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Jeśli musisz wyczyścić stanów elementu wszystkich elementów w karcie `CTabCtrl` obiektu, wywołanie [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Ta funkcja resetuje stan wszystkich elementów kartę lub wszystkie elementy z wyjątkiem aktualnie wybrany.

Poniższy kod usuwa stan wszystkich elementów w karcie i następnie modyfikuje stan trzeci element:

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Aby uzyskać więcej informacji na temat atrybutów karty zobacz [karty i atrybuty w karcie](/windows/desktop/Controls/tab-controls) w zestawie Windows SDK. Aby uzyskać więcej informacji na temat Dodawanie kart do formantu karty zobacz [Dodawanie kart do formantu karty](../mfc/adding-tabs-to-a-tab-control.md) w dalszej części tego tematu.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
