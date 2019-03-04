---
title: Edytowanie etykiety kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 446db94ec49859e2213f00d205df57e332c85af2
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264147"
---
# <a name="tree-control-label-editing"></a>Edytowanie etykiety kontrolki drzewa

Użytkownika można edytować bezpośrednio etykiety elementów kontrolki drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) zawierający **TVS_EDITLABELS** stylu. Użytkownik rozpoczyna edycję, klikając etykietę elementu, który ma fokus. Aplikacja rozpoczyna edytowanie przy użyciu [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) funkcja elementu członkowskiego. Kontrolka drzewa wysyła rozpoczyna się powiadomienie, gdy do edycji, a kiedy jest anulowane lub zakończone. Po zakończeniu edycji odpowiedzialność za aktualizowanie etykiety elementu, jeśli to stosowne.

Edytowanie etykiet rozpoczęcia, formant drzewa wysyła [TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit) wiadomość z powiadomieniem. Przez przetwarzanie tego powiadomienia, można zezwolić na edycję niektóre etykiety i uniemożliwiają edycję innych. Zwracanie wartości 0 zezwala na edytowanie i zwraca wartość różną od zera temu zapobiega.

Gdy edytowanie etykiet jest anulowane lub zakończone, formant drzewa wysyła [TVN_ENDLABELEDIT](/windows/desktop/Controls/tvn-endlabeledit) wiadomość z powiadomieniem. *LParam* parametru jest adresem [NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) struktury. **Elementu** element członkowski jest [TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) struktury, która identyfikuje element i obejmuje edytowanego tekstu. Jesteś odpowiedzialny za aktualizowanie etykiety elementu, jeśli to stosowne, prawdopodobnie po upewnieniu się, edytowany ciągu. *PszText* członkiem `TV_ITEM` wynosi 0, jeśli edycji zostało anulowane.

Podczas Edytowanie etykiet, zwykle w odpowiedzi na [TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit) komunikat powiadomienia, można uzyskać wskaźnik do kontrolki edycji umożliwiający edytowanie etykiet przy użyciu [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) elementu członkowskiego Funkcja. Możesz wywołać kontrolki edycji [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) funkcja elementu członkowskiego, aby ograniczyć ilość tekstu, użytkownik może wprowadzić lub podklasą kontrolki edycji, aby przechwycić i odrzucić nieprawidłowe znaki. Należy jednak pamiętać, że kontrolka edycji jest wyświetlany tylko *po* **TVN_BEGINLABELEDIT** są wysyłane.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
