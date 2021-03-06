---
title: Formanty paska pomocniczego i paski
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], working with bands in
- bands, in rebar controls
ms.assetid: b647e7a5-9ea7-48b1-8e5f-096d104748f0
ms.openlocfilehash: 4bb7b4aeab1478138aa2b52649f41ca943b5daa4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378170"
---
# <a name="rebar-controls-and-bands"></a>Formanty paska pomocniczego i paski

Głównym celem formantu paska pomocniczego jest działa jako kontener dla okien podrzędnych, formanty standardowe okno dialogowe, menu, paski narzędzi i tak dalej. Zawieranie ten jest obsługiwany przez pojęcie "poza pasmem". Każdego pasma paska pomocniczego może zawierać dowolną kombinację pasek uchwytu, mapy bitowej, etykietę tekstową i okna podrzędnego.

Klasa `CReBarCtrl` ma wiele funkcji elementów członkowskich służy do pobierania i manipulowania informacje dotyczące grupy określonego paska pomocniczego:

- [GetBandCount](../mfc/reference/crebarctrl-class.md#getbandcount) pobiera numer bieżącej paskami w formancie paska pomocniczego.

- [GetBandInfo](../mfc/reference/crebarctrl-class.md#getbandinfo) inicjuje **REBARBANDINFO** strukturę z informacjami z określonym poza pasmem. Istnieje odpowiedni [SetBandInfo](../mfc/reference/crebarctrl-class.md#setbandinfo) funkcja elementu członkowskiego.

- [GetRect —](../mfc/reference/crebarctrl-class.md#getrect) pobiera prostokąt otaczający przedziałów.

- [GetRowCount](../mfc/reference/crebarctrl-class.md#getrowcount) pobiera liczbę wierszy poza pasmem w formancie paska pomocniczego.

- [IDToIndex](../mfc/reference/crebarctrl-class.md#idtoindex) pobiera indeks przedziałów.

- [GetBandBorders](../mfc/reference/crebarctrl-class.md#getbandborders) pobiera obramowania grupy.

Oprócz manipulowanie kilka elementów członkowskich są dostarczane, pozwalają na działanie w określonym paskami.

[InsertBand](../mfc/reference/crebarctrl-class.md#insertband) i [DeleteBand](../mfc/reference/crebarctrl-class.md#deleteband) dodawać i usuwać paskami. [MinimizeBand](../mfc/reference/crebarctrl-class.md#minimizeband) i [MaximizeBand](../mfc/reference/crebarctrl-class.md#maximizeband) wpływają na rozmiar bieżący obiekt band określonego paska pomocniczego. [MoveBand](../mfc/reference/crebarctrl-class.md#moveband) zmienia indeks pasma określonego paska pomocniczego. [ShowBand](../mfc/reference/crebarctrl-class.md#showband) pokazuje lub ukrywa pasek paska pomocniczego, od użytkownika.

W poniższym przykładzie pokazano, dodając pasek narzędzi (*m_wndToolBar*) do istniejącego formantu paska pomocniczego (*m_wndReBar*). Pasmo jest opisana przez inicjowanie `rbi` struktury, a następnie wywołując `InsertBand` funkcja elementu członkowskiego:

[!code-cpp[NVC_MFCControlLadenDialog#27](../mfc/codesnippet/cpp/rebar-controls-and-bands_1.cpp)]

## <a name="see-also"></a>Zobacz także

[Korzystanie z CReBarCtrl](../mfc/using-crebarctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
