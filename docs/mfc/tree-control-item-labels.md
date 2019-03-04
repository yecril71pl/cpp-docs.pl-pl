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
ms.openlocfilehash: c945556ff9236db1ca61b15f1072efdc2f49541f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278889"
---
# <a name="tree-control-item-labels"></a>Etykiety elementów formantu drzewa

Zwykle określasz tekst etykiety elementu podczas dodawania elementu do kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). `InsertItem` Można przekazać funkcję członkowską [TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) strukturę, która definiuje właściwości elementów, w tym ciąg zawierający tekst etykiety. `InsertItem` ma kilka przeciążeń, które mogą być wywoływane przy użyciu różnych kombinacji parametrów.

Kontrolka drzewa przydziela pamięć do przechowywania każdego elementu; tekst etykiety elementu zajmuje znaczną część tej pamięci. Jeśli aplikacja przechowuje kopię ciągów w drzewie, można zmniejszyć wymagania dotyczące pamięci formantu, określając **LPSTR_TEXTCALLBACK** wartość w *pszText* członkiem `TV_ITEM` lub *lpszItem* parametru zamiast przekazywać parametry rzeczywiste do formantu drzewa. Za pomocą **LPSTR_TEXTCALLBACK** powoduje, że formant drzewa, aby pobrać tekst etykiety elementu z aplikacji zawsze wtedy, gdy element musi być narysowany ponownie. Aby pobrać tekst, formant drzewa wysyła [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) komunikat powiadomienia zawiera adres [NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) struktury. Musisz odpowiedzieć, ustawiając odpowiednich elementów członkowskich struktury uwzględnione.

Kontrolka drzewa używa pamięci zaalokowanej z sterty procesu, który tworzy formant drzewa. Maksymalna liczba elementów kontrolki drzewa zależy od ilości dostępnej pamięci na stosie. Każdy element ma 64 bajtów.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
