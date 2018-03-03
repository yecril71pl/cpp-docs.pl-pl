---
title: Etykiety formantu drzewa edycji | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 03fb11c29b51b30b1aaffccbe3e999f1cefc3fbb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-label-editing"></a>Edytowanie etykiety kontrolki drzewa
Użytkownik może edytować bezpośrednio etykiety elementów formantu drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) mający **TVS_EDITLABELS** stylu. Użytkownik rozpoczyna edycję, klikając etykietę elementu, który ma fokus. Aplikacja rozpoczyna edycję przy użyciu [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) funkcję elementu członkowskiego. Formant drzewa wysyła powiadomienia podczas edytowania rozpoczyna się i gdy jest anulowane lub zakończone. Po zakończeniu edycji jest odpowiedzialny za aktualizowanie etykiety elementu w razie potrzeby.  
  
 Edytowanie etykiet rozpoczęcia, wysyła formant drzewa [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) wiadomość z powiadomieniem. Przez przetwarzanie tego powiadomienia, można zezwolić na edycję niektóre etykiety i uniemożliwiają edycję innych. Zwracanie wartości 0 pozwala na edycję i powoduje zwracanie różną od zera.  
  
 Edytowanie etykiet jest anulowane lub zakończone, wysyła formantu drzewa [TVN_ENDLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773515) wiadomość z powiadomieniem. `lParam` Parametru jest adresem [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) struktury. **Elementu** element członkowski jest [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) struktury, która identyfikuje element i edytowany tekst. Jest odpowiedzialny za aktualizowania etykiety elementu w razie potrzeby, możliwe, że po sprawdzanie poprawności edytowanej ciągu. **PszText** członkiem `TV_ITEM` wynosi 0, jeśli edycji zostało anulowane.  
  
 Podczas Edytowanie etykiet, zazwyczaj w odpowiedzi na [TVN_BEGINLABELEDIT](http://msdn.microsoft.com/library/windows/desktop/bb773506) komunikatu powiadomienia mogą otrzymywać wskaźnik do kontrolki edycji używanych do edycji etykiety przy użyciu [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) elementu członkowskiego Funkcja. Kontrolki edycji można wywołać [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) funkcji członkowskiej, aby ograniczyć ilość tekstu, użytkownik może wprowadzić lub podklasy kontrolki edycji, aby przechwycić i odrzucić nieprawidłowe znaki. Należy jednak pamiętać, że kontrolka edycji jest wyświetlany tylko *po* **TVN_BEGINLABELEDIT** są wysyłane.  
  
## <a name="see-also"></a>Zobacz też  
 [Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Kontrolki](../mfc/controls-mfc.md)

