---
title: Etykiety elementów kontrolki drzewa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item labels
- labels, CTreeCtrl items
- CTreeCtrl class [MFC], item labels
- item labels, tree controls
- item labels
ms.assetid: fe834107-1a25-4280-aced-774c11565805
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3f07032a203761e78bd44f40456093eae9a84d07
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46399889"
---
# <a name="tree-control-item-labels"></a>Etykiety elementów kontrolki drzewa

Zwykle określasz tekst etykiety elementu podczas dodawania elementu do kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). `InsertItem` Można przekazać funkcję członkowską [TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) strukturę, która definiuje właściwości elementów, w tym ciąg zawierający tekst etykiety. `InsertItem` ma kilka przeciążeń, które mogą być wywoływane przy użyciu różnych kombinacji parametrów.

Kontrolka drzewa przydziela pamięć do przechowywania każdego elementu; tekst etykiety elementu zajmuje znaczną część tej pamięci. Jeśli aplikacja przechowuje kopię ciągów w drzewie, można zmniejszyć wymagania dotyczące pamięci formantu, określając **LPSTR_TEXTCALLBACK** wartość w *pszText* członkiem `TV_ITEM` lub *lpszItem* parametru zamiast przekazywać parametry rzeczywiste do formantu drzewa. Za pomocą **LPSTR_TEXTCALLBACK** powoduje, że formant drzewa, aby pobrać tekst etykiety elementu z aplikacji zawsze wtedy, gdy element musi być narysowany ponownie. Aby pobrać tekst, formant drzewa wysyła [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) komunikat powiadomienia zawiera adres [NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) struktury. Musisz odpowiedzieć, ustawiając odpowiednich elementów członkowskich struktury uwzględnione.

Kontrolka drzewa używa pamięci zaalokowanej z sterty procesu, który tworzy formant drzewa. Maksymalna liczba elementów kontrolki drzewa zależy od ilości dostępnej pamięci na stosie. Każdy element ma 64 bajtów.

## <a name="see-also"></a>Zobacz też

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)

