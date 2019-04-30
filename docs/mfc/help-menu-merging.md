---
title: Scalanie menu Pomoc
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
ms.openlocfilehash: e1e8f9af696b6ea4cd485f4215e1c8425098e987
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396408"
---
# <a name="help-menu-merging"></a>Scalanie menu Pomoc

Gdy obiekt jest aktywny w kontenerze, menu, scalanie protokołu dokumentów OLE zapewnia obiekt, pełną kontrolę nad **pomocy** menu. W rezultacie tematy pomocy kontenera nie są dostępne, chyba że użytkownik dezaktywuje obiektu. Architektura zawierania dokumentów aktywnych rozszerza zasady menu w miejscu scalania, aby zezwolić na aktywny dokument aktywny, aby udostępnić menu i kontenera. Nowe zasady są po prostu dodatkowe konwencje o jakie składnik jest właścicielem, jakie części menu i jak jest konstruowany udostępnionego menu.

Nowa Konwencja jest proste. W dokumentach active **pomocy** menu zawiera dwa elementy menu najwyższego poziomu zorganizowane w następujący sposób:

`Help`

`Container Help >`

`Object Help    >`

Na przykład, gdy sekcji Word jest aktywny w Office Binder, a następnie **pomocy** menu wyglądałby następująco:

`Help`

`Binder Help >`

`Word Help   >`

Oba elementy menu są kaskadowych menu, w których wszelkie dodatkowe elementy menu specyficzne dla kontenera i obiektu są dostarczane do użytkownika. Jakie elementy są wyświetlane w tym miejscu będą się różnić z kontenerów i obiektów związane.

Do utworzenia tego scalone **pomocy** menu architektura zawierania dokumentów aktywnych modyfikuje normalnej procedury dokumenty OLE. Zgodnie z dokumentów OLE, na pasku menu scalone może mieć sześć grup menu, a mianowicie **pliku**, **Edytuj**, **kontenera**, **obiektu**,  **Okno**, **pomocy**, w tej kolejności. W każdej grupie można menu zero lub więcej. Grupy **pliku**, **kontenera**, i **okna** należą do grup i kontener **Edytuj**, **Object,** i **pomocy** należy do obiektu. Gdy obiekt chce wykonać scalanie menu, tworzy pasek menu puste i przekazuje je do kontenera. Kontener wstawia jego menu, wywołując `IOleInPlaceFrame::InsertMenus`. Obiekt przekazuje strukturę, która jest tablicą sześć długie wartości (**OLEMENUGROUPWIDTHS**). Po wstawieniu menu, kontener oznacza menu ile ono dodane w każdej z jej grupy, a następnie zwraca. Następnie obiekt wstawia jego menu, zwracając uwagę na liczbę menu w każdej grupy kontenerów. Na koniec obiekt przekazuje pasek menu scalonych i tablicy (co zawiera liczbę menu w każdej grupie) OLE, co powoduje zwrócenie wiadomość nieprzezroczysty "menu deskryptora" obsługi. Później obiekt przekazuje dojścia i pasek menu scalone z kontenerem przy użyciu `IOleInPlaceFrame::SetMenu`. W tej chwili kontenera jest wyświetlany pasek menu scalone i przekazuje dojście do OLE, tak, aby OLE można wykonać odpowiednie wysyłania komunikatów menu.

W procedurze zmodyfikowane aktywnego dokumentu najpierw należy zainicjować obiekt **OLEMENUGROUPWIDTHS** elementy do zera przed przekazaniem go do kontenera. Następnie kontenera wykonuje wstawiania normalne menu, z jednym wyjątkiem: Wstawia kontenera **pomocy** menu jako ostatni element i zapisuje wartość 1 w ostatni wpis (szóstego) **OLEMENUGROUPWIDTHS** tablicy (oznacza to szerokość [5], która należy do grupy pomocy obiektu). To **pomocy** menu będzie mieć tylko jeden element, który jest podmenu, "**kontenera pomocy** >" menu cascade, jak opisano wcześniej.

Obiekt jest następnie wykonuje jego kod wstawiania menu normalne, chyba że przed wstawieniem jego **pomocy** menu sprawdza szóstego wpis **OLEMENUGROUPWIDTHS** tablicy. Jeśli wartość wynosi 1, a nazwa ostatniego menu jest **pomocy** (lub odpowiedniego zlokalizowany ciąg), a następnie obiekt wstawia jego **pomocy** menu jako podmenu kontenera **pomocy** menu.

Obiekt jest następnie ustawia szóstego elementu **OLEMENUGROUPWIDTHS** zero i zwiększa piąty element o jeden. Dzięki temu OLE poinformować, że **pomocy** menu należy do kontenera i komunikaty menu odpowiadający menu (i jego podmenu) powinien kierowane do kontenera. Odpowiada za następnie kontenera do przekazywania **WM_INITMENUPOPUP**, **WM_SELECT**, **WM_COMMAND**, a inne menu komunikatów, które należą do obiektu część **pomocy** menu. Jest to realizowane przy użyciu **WM_INITMENU** Wyczyść flagę, która informuje kontenera, czy użytkownik ma przeszedł do obiektu **pomocy** menu. Kontener jest następnie obserwuje **WM_MENUSELECT** wejścia lub wyjścia z dowolnym elementem **pomocy** menu kontenera nie został dodany sam. Przy uruchamianiu, oznacza to, użytkownik ma przeszedł do menu obiektu, więc kontener ustawia flagę "w menu Pomoc obiektu" i używa stan tej flagi, aby przekazywać dowolne **WM_MENUSELECT**, **WM_INITMENUPOPUP**i  **WM_COMMAND** wiadomości, co najmniej do okna obiektu. (Przy zamykaniu, kontener czyści flagę i następnie przetwarza te tymi samymi komunikatami sama.) Kontener należy używać okna zwrócony z obiektu `IOleInPlaceActiveObejct::GetWindow` działa jako miejsce docelowe dla tych wiadomości.

Jeśli obiekt wykrywa zero w elemencie szóstego **OLEMENUGROUPWIDTHS**, rozpoczynające się zgodnie ze zwykłymi regułami dokumenty OLE. Ta procedura obejmuje kontenerów, które uczestniczą w **pomocy** menu scalania, a także tych, które nie obsługują.

Kiedy wywołuje obiekt `IOleInPlaceFrame::SetMenu`, zanim czy wyświetlanie scalonych menu paska kontroli kontenera **pomocy** menu zawiera dodatkowe podmenu, oprócz co został wstawiony w kontenerze. Jeśli tak, kontener jego **pomocy** menu na pasku menu scalone. Jeśli **pomocy** menu nie ma dodatkowych podmenu, spowoduje to usunięcie kontenera jego **pomocy** menu na pasku menu scalone. Ta procedura obejmuje obiekty, które uczestniczą w **pomocy** menu scalania, a także tych, które nie obsługują.

Na koniec, gdy nadejdzie czas, aby zdemontować menu, obiekt usuwa wstawionego **pomocy** menu oprócz usunięcie z drugiej dodaje menu. Gdy kontener usuwa jego menu, spowoduje usunięcie jej **pomocy** menu oprócz menu, które go został wstawiony.

## <a name="see-also"></a>Zobacz także

[Kontenery dokumentów aktywnych](../mfc/active-document-containers.md)
