---
title: Etykiety elementów formantu drzewa | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 3fc207dcff5002262c345b106be99a775ed626b9
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953728"
---
# <a name="tree-control-item-labels"></a>Etykiety elementów kontrolki drzewa
Zazwyczaj należy określić tekst etykiety elementu podczas dodawania elementu do kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)). `InsertItem` Może przekazać funkcji członkowskiej [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktury, która definiuje właściwości elementu, w tym ciąg zawierający tekst etykiety. `InsertItem` ma kilka przeciążeń, które mogą być wywoływane z różnych kombinacji parametrów.  
  
 Formant drzewa przydziela pamięć do przechowywania każdego elementu; tekst etykiety elementu zajmuje znaczna część tej pamięci. Jeśli aplikacja przechowuje kopię ciągów w drzewie, można zmniejszyć wymagania dotyczące pamięci formantu, określając **LPSTR_TEXTCALLBACK** wartość w *pszText* członkiem `TV_ITEM` lub *lpszItem* parametru zamiast przekazywanie rzeczywistych parametrów do formantu drzewa. Przy użyciu **LPSTR_TEXTCALLBACK** powoduje, że formant drzewa, aby pobrać tekst etykiety elementu z aplikacji zawsze, gdy element musi zostać narysowany ponownie. Aby pobrać tekst, wysyła do drzewa [TVN_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) komunikat powiadomienia, który zawiera adres [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) struktury. Musi odpowiadać, ustawiając odpowiednie elementy członkowskie struktury uwzględnione.  
  
 Formant drzewa używa pamięci przydzielonej sterty procesu, który tworzy na drzewie. Maksymalną liczbę elementów formantu drzewa zależy od ilości pamięci w stosie. Każdy element ma 64 bajtów.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

