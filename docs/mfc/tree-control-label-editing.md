---
title: Edytowanie etykiety kontrolki drzewa
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 10148ef0dd8ccb2cf82c14c1c80ade6e8e5aa2b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513308"
---
# <a name="tree-control-label-editing"></a>Edytowanie etykiety kontrolki drzewa

Użytkownik może bezpośrednio edytować etykiety elementów w kontrolce drzewa ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)), która ma styl **TVS_EDITLABELS** . Użytkownik rozpoczyna edycję, klikając etykietę elementu, który ma fokus. Aplikacja rozpoczyna edytowanie przy użyciu funkcji składowej [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) . Formant drzewa wysyła powiadomienie po rozpoczęciu edycji i po jego anulowaniu lub zakończeniu. Po zakończeniu edycji użytkownik jest odpowiedzialny za aktualizowanie etykiety elementu, jeśli jest to konieczne.

Po rozpoczęciu edycji etykiet formant drzewa wysyła komunikat powiadomienia [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) . Przetwarzając to powiadomienie, możesz zezwolić na edycję niektórych etykiet i uniemożliwić edytowanie innych. Zwrócenie wartości 0 pozwala na edycję i zwrócenie jej przez zero.

Gdy Edycja etykiet zostanie anulowana lub ukończona, formant drzewa wysyła komunikat powiadomienia [TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit) . Parametr *lParam* jest adresem struktury [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-tvdispinfow) . **Element członkowski elementu** jest strukturą [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) , która identyfikuje element i zawiera edytowany tekst. Użytkownik jest odpowiedzialny za aktualizowanie etykiety elementu, jeśli jest to konieczne, ewentualnie po zweryfikowaniu edytowanego ciągu. Element członkowski `TV_ITEM` pszText ma wartość 0, jeśli edytowanie zostało anulowane.

Podczas edytowania etykiety, zazwyczaj w odpowiedzi na komunikat powiadomienia [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) , można uzyskać wskaźnik do kontrolki edycji używanej do edycji etykiet przy użyciu funkcji składowej [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) . Można wywołać funkcję elementu członkowskiego [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) kontrolki edycji, aby ograniczyć ilość tekstu, który użytkownik może wprowadzać lub podwoływać kontrolkę edycji w celu przechwycenia i odrzucenia nieprawidłowych znaków. Należy jednak pamiętać, że kontrolka edycji jest wyświetlana dopiero *po* wysłaniu **TVN_BEGINLABELEDIT** .

## <a name="see-also"></a>Zobacz także

[Korzystanie z CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
