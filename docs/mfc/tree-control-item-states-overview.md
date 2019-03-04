---
title: Przegląd stanów elementu formantu drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- states, CTreeCtrl items
- tree controls [MFC], item states overview
- CTreeCtrl class [MFC], item states
ms.assetid: 2db11ae0-0d87-499d-8c1f-5e0dbe9e94c8
ms.openlocfilehash: 57c6714073f4939ffb791a78454e9eac6342309b
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264602"
---
# <a name="tree-control-item-states-overview"></a>Przegląd stanów elementu formantu drzewa

Każdego elementu kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) ma bieżącego stanu. Na przykład, można wybrać element, wyłączone, rozwinięty i tak dalej. W większości przypadków formant drzewa automatycznie ustawia stan elementu do odzwierciedlenia czynności użytkownika, takie jak zaznaczenie elementu. Jednak również można ustawić stanu elementu przy użyciu [SetItemState](../mfc/reference/ctreectrl-class.md#setitemstate) funkcja elementu członkowskiego i pobrać bieżący stan elementu za pomocą [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate) funkcja elementu członkowskiego. Aby uzyskać pełną listę stanów elementu, zobacz [stałe kontrolki widoku drzewa](/windows/desktop/Controls/tree-view-control-item-states) w zestawie Windows SDK.

Bieżący stan elementu jest określona przez *nInformacje* parametru. Kontrolka drzewa mogą ulec zmianie stanu elementu do odzwierciedlenia czynności użytkownika, takie jak wybór element lub ustawienie fokusu do elementu. Ponadto aplikacji mogą ulec zmianie stanu elementu wyłączenie lub ukrycie elementu lub określić nakładki obraz lub obrazu stanu.

Po określeniu lub zmienić stan elementu *nStateMask* parametr określa, których stan bity do ustawienia, a *nInformacje* parametr zawiera nowe wartości dla tych bitów. Na przykład, poniższy przykład zmienia bieżący stan elementu nadrzędnego (określony przez *hParentItem*) w `CTreeCtrl` obiektu (`m_treeCtrl`) do `TVIS_EXPANDPARTIAL`:

[!code-cpp[NVC_MFCControlLadenDialog#71](../mfc/codesnippet/cpp/tree-control-item-states-overview_1.cpp)]

Inny przykład zmiany stanu, będzie można ustawić elementu nakładki obrazów. Aby to osiągnąć, *nStateMask* musi zawierać `TVIS_OVERLAYMASK` wartości, a *nInformacje* musi zawierać liczonego od jednego indeksu obrazu nakładki przesunięte left osiem bitów przy użyciu [ INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) makra. Indeks może być 0, aby określić Brak obrazu nakładki. Obraz nakładki musi zostały dodane do listy formantu drzewa nakładki obrazów przez poprzednie wywołanie [CImageList::SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) funkcji. Funkcja określa indeksu liczonego od jednego obrazu, aby dodać; jest to indeks używany przy użyciu makra INDEXTOOVERLAYMASK. Kontrolka drzewa może mieć maksymalnie cztery nakładki obrazów.

Aby ustawić element obrazu stanu, *nStateMask* musi zawierać `TVIS_STATEIMAGEMASK` wartości i *nInformacje* musi zawierać liczonego od jednego indeksu obrazu stanu przesunięte pozostałych bitów 12 przy użyciu [ INDEXTOSTATEIMAGEMASK](/windows/desktop/api/commctrl/nf-commctrl-indextostateimagemask) makra. Indeks może być 0, aby określić Brak obrazu stanu. Aby uzyskać więcej informacji o obrazach w nakładce, a stan, zobacz [listy obrazów kontrolki drzewa](../mfc/tree-control-image-lists.md).

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
