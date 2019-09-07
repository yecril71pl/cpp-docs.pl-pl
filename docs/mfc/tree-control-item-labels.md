---
title: Etykiety elementów formantu drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
ms.openlocfilehash: 16bb2bbe63eaf8ea4ce30040589d4a8a4cf4dfd3
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741466"
---
# <a name="tree-control-item-labels"></a>Etykiety elementów formantu drzewa

Zwykle określasz tekst etykiety elementu podczas dodawania elementu do kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). Funkcja członkowska może przekazać strukturę TVITEM, która definiuje właściwości elementu, w tym ciąg zawierający tekst etykiety. [](/windows/win32/api/commctrl/ns-commctrl-tvitemw) `InsertItem` `InsertItem`ma kilka przeciążeń, które można wywoływać przy użyciu różnych kombinacji parametrów.

Kontrolka drzewa przydziela pamięć do przechowywania każdego elementu; tekst etykiet elementów przyjmuje znaczną część tej pamięci. Jeśli aplikacja zachowuje kopię ciągów w kontrolce drzewa, można zmniejszyć wymagania dotyczące pamięci formantu, określając wartość **LPSTR_TEXTCALLBACK** w elemencie członkowskim `TV_ITEM` *pszText* lub *lpszItem* parametr zamiast przekazywania rzeczywistych ciągów do kontrolki drzewa. Użycie **LPSTR_TEXTCALLBACK** powoduje, że formant drzewa Pobiera tekst etykiety elementu z aplikacji za każdym razem, gdy element wymaga odrysowania. Aby pobrać tekst, formant drzewa wysyła komunikat powiadomienia [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) , który zawiera adres struktury [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) . Musisz odpowiedzieć przez ustawienie odpowiednich członków zawartej struktury.

Kontrolka drzewa używa pamięci przydzieloną z sterty procesu, który tworzy formant drzewa. Maksymalna liczba elementów w kontrolce drzewa zależy od ilości dostępnej pamięci w stercie. Każdy element pobiera 64 bajtów.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
