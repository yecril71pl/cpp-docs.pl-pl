---
title: Scalanie menu Pomoc
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: 1bd70af6f24ee6f9873b89b2060f4b2d90149c90
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620133"
---
# <a name="help-menu-merging"></a>Scalanie menu Pomoc

Gdy obiekt jest aktywny w kontenerze, menu scalające protokołu dokumentów OLE zapewnia obiektowi pełną kontrolę nad menu **Pomoc** . W związku z tym tematy pomocy kontenera nie są dostępne, chyba że użytkownik dezaktywuje obiekt. Architektura zawierania aktywnego dokumentu rozszerza reguły dotyczące scalania menu w miejscu, aby umożliwić zarówno kontener, jak i aktywny dokument, który jest aktywny do udostępniania menu. Nowe reguły są po prostu dodatkowymi konwencjami dotyczącymi składnika menu i sposobu konstruowania menu udostępnionego.

Nowa Konwencja jest prosta. W dokumentach aktywnych menu **Pomoc** ma dwa elementy menu najwyższego poziomu zorganizowane w następujący sposób:

`Help`

`Container Help >`

`Object Help    >`

Na przykład, gdy sekcja słowa jest aktywna w programie Office Binder, menu **Pomoc** będzie wyglądać w następujący sposób:

`Help`

`Binder Help >`

`Word Help   >`

Oba elementy menu to menu kaskadowe, w ramach których wszystkie dodatkowe elementy menu specyficzne dla kontenera i obiektu są udostępniane użytkownikowi. Elementy, które są wyświetlane w tym miejscu, będą się różnić w zależności od kontenera i obiektów.

Aby utworzyć scalone menu **Pomoc** , architektura zawierania aktywnych dokumentów modyfikuje normalne procedury dokumentów OLE. Zgodnie z dokumentami OLE scalony pasek menu może zawierać sześć grup menu, mianowicie **plik**, **Edycja**, **kontener**, **obiekt**, **okno**, **Pomoc**, w tej kolejności. W każdej grupie może istnieć co najmniej zero menu. **Plik**grup, **kontener**i **okno** należy do kontenera, a grupy **Edytuj**, **obiekt** i **Pomoc** należy do obiektu. Gdy obiekt chce wykonać Scalanie menu, tworzy pusty pasek menu i przekazuje go do kontenera. Następnie kontener wstawia swoje menu, wywołując `IOleInPlaceFrame::InsertMenus` . Obiekt przekazuje również strukturę, która jest tablicą zawierającą sześć długich wartości (**OLEMENUGROUPWIDTHS**). Po wstawieniu menu kontener oznaczy, ile menu zostało dodane w każdej z nich, a następnie zwraca. Następnie obiekt wstawia swoje menu, zwracając uwagę na liczbę menu w każdej grupie kontenerów. Na koniec obiekt przeszedł scalony pasek menu i tablicę (zawierającą liczbę menu w każdej grupie) do OLE, która zwraca nieprzezroczysty uchwyt "deskryptora menu". Później obiekt przekazuje ten uchwyt i scalony pasek menu do kontenera za pośrednictwem `IOleInPlaceFrame::SetMenu` . W tym momencie kontener wyświetla scalony pasek menu, a także przekazuje uchwyt do OLE, dzięki czemu OLE może wykonać odpowiednie wysłanie komunikatów menu.

W procedurze zmodyfikowanego dokumentu aktywnego obiekt musi najpierw zainicjować elementy **OLEMENUGROUPWIDTHS** w wartości zero przed przekazaniem ich do kontenera. Następnie kontener wykonuje normalne Wstawianie menu z jednym wyjątkiem: kontener wstawia menu **Pomoc** jako ostatni element i przechowuje wartość 1 w ostatnim (szóstym) wpisie tablicy **OLEMENUGROUPWIDTHS** (czyli szerokość [5], która należy do grupy pomocy obiektu). To menu **Pomoc** będzie miało tylko jeden element, który jest podmenu, czyli menu kaskadowego ">**pomocy kontenera** ", jak opisano wcześniej.

Następnie obiekt wykonuje swój normalny kod wstawiania menu, z wyjątkiem tego, że przed wstawieniem jego menu **Pomoc** sprawdza szósty wpis tablicy **OLEMENUGROUPWIDTHS** . Jeśli wartość jest równa 1, a nazwa ostatniego menu jest **pomocna** (lub odpowiedni zlokalizowany ciąg), wówczas obiekt wstawia jego menu **Pomoc** jako podmenu menu **Pomoc** kontenera.

Następnie obiekt ustawia szósty element **OLEMENUGROUPWIDTHS** na zero i zwiększa piąty element o jeden. Dzięki temu mechanizm OLE wie, że menu **Pomoc** należy do kontenera, a komunikaty menu odpowiadające temu menu (i jego podmenu) powinny być kierowane do kontenera. Jest to następnie odpowiedzialność kontenera do przesyłania dalej **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**i innych komunikatów związanych z menu, które należą do części tego obiektu menu **Pomoc** . Jest to realizowane za pomocą **WM_INITMENU** , aby wyczyścić flagę, która informuje kontener o tym, czy użytkownik przeszedł do menu **Pomoc** tego obiektu. Następnie kontener przeczujuje **WM_MENUSELECT** do wejścia lub wyjścia z dowolnego elementu w menu **Pomoc** , które nie zostały dodane do kontenera. Oznacza to, że użytkownik przeszedł do menu obiekt, więc kontener ustawia flagę "w menu Pomoc obiektu" i używa stanu tej flagi do przesyłania dalej dowolnych **WM_MENUSELECT**, **WM_INITMENUPOPUP**i **WM_COMMAND** komunikatów jako minimum do okna obiektu. (Po zakończeniu kontener czyści flagę, a następnie przetwarza te same komunikaty). Kontener powinien używać okna zwróconego przez `IOleInPlaceActiveObejct::GetWindow` funkcję obiektu jako miejsca docelowego dla tych komunikatów.

Jeśli obiekt wykryje zero w szóstym elemencie **OLEMENUGROUPWIDTHS**, postępuje zgodnie z normalnymi regułami dotyczącymi dokumentów OLE. Ta procedura obejmuje kontenery, które uczestniczą w scalaniu menu **Pomoc** , a także te, które nie.

Gdy obiekt wywołuje `IOleInPlaceFrame::SetMenu` , przed wyświetleniem scalonego paska menu, kontener sprawdza, czy menu **Pomoc** ma dodatkowe podmenu, a także informacje o tym, co kontener został wstawiony. Jeśli tak, kontener pozostawia menu **Pomoc** na scalonym pasku menu. Jeśli menu **Pomoc** nie ma dodatkowego podmenu, kontener usunie jego menu **Pomoc** ze scalonego paska menu. Ta procedura obejmuje obiekty, które uczestniczą w menu **Pomoc** scalanie, a także te, które nie.

Na koniec, gdy jest czas na odłączenie menu, obiekt usuwa wstawione menu **pomocy** oprócz usuwania innych wstawionych menu. Gdy kontener usuwa jego menu, spowoduje usunięcie jego menu **Pomoc** , a także innych menu, które zostały wstawione.

## <a name="see-also"></a>Zobacz też

[Kontenery dokumentów aktywnych](active-document-containers.md)
