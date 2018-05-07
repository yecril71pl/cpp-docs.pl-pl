---
title: Scalanie Menu Pomoc | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menus [MFC], merging
- merging Help menus [MFC]
- Help [MFC], for active document containers
ms.assetid: 9d615999-79ba-471a-9288-718f0c903d49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ce8d5212f78546c08734aed6fd7e236fa4446007
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="help-menu-merging"></a>Scalanie menu Pomoc
Gdy obiekt jest aktywny w kontenerze, menu scalanie protokołu dokumentów OLE daje obiektu pełną kontrolę nad **pomocy** menu. W związku z tym kontenera tematy pomocy nie są dostępne, chyba że użytkownik dezaktywuje obiektu. Architektura zawierania dokumentów aktywnych rozszerza reguły menu w miejscu scalanie umożliwia aktywny dokument, który jest aktywny, aby udostępnić menu i kontenera. Nowe zasady są po prostu dodatkowe konwencje o jakie składnik jest właścicielem części menu i sposób jest tworzony udostępnionego menu.  
  
 Nowe Konwencji jest proste. W dokumentach active **pomocy** menu zawiera dwa elementy menu najwyższego poziomu, uporządkowanych w następujący sposób:  
  
 `Help`  
  
 `Container Help >`  
  
 `Object Help    >`  
  
 Na przykład, gdy jest aktywny w Office Binder sekcji Word, a następnie **pomocy** menu będzie wyglądać następująco:  
  
 `Help`  
  
 `Binder Help >`  
  
 `Word Help   >`  
  
 Oba elementy menu są kaskadowych menu, w których wszystkie elementy menu dodatkowe określonego kontenera i obiektu są udostępniane użytkownikowi. Jakie elementy są wyświetlane tutaj zależy kontenera i obiekty związane.  
  
 Do utworzenia to scalić **pomocy** menu, architektura zawierania dokumentów aktywnych modyfikuje normalnej procedury dokumentów OLE. Zgodnie z dokumentów OLE na pasku menu scalone grupy mogą być sześć menu, czyli **pliku**, **Edytuj**, **kontenera**, `Object`, **okna**, **Pomocy**, w tej kolejności. W każdej grupie może być zero lub więcej menu. Grupy **pliku**, **kontenera**, i **okna** należy do kontenera i grupy **Edytuj**, **obiekt,** i **pomocy** należy do obiektu. Gdy obiekt chce wykonać scalania menu, tworzy pasek menu puste i przekazuje je do kontenera. Kontener wstawia jego menu, wywołując **IOleInPlaceFrame::InsertMenus**. Struktura, która jest tablicą sześciu długie wartości przekazuje także obiekt (**OLEMENUGROUPWIDTHS**). Po wstawieniu menu, kontenera oznacza liczbę menu dodać go w każdej z jej grupy, a następnie zwraca. Następnie obiekt wstawia jego menu, zwracając uwagę liczba menu w każdej grupie kontenera. Na koniec obiekt przekazuje na pasku menu scalone i tablicy (zawierający liczba menu w każdej grupie) do OLE, które zwraca moduł nieprzezroczyste "deskryptora menu" obsługi. Później obiekt przekazuje dojścia i na pasku menu scalone z kontenerem przy użyciu **IOleInPlaceFrame::SetMenu**. W tej chwili kontenera Wyświetla pasek menu scalone i przekazuje dojście do OLE, tak, aby zrobić OLE właściwego podczas wysyłania wiadomości menu.  
  
 W procedurze modyfikacji dokumentów aktywnych najpierw należy zainicjować obiektu **OLEMENUGROUPWIDTHS** elementy do zera przed przekazaniem go do kontenera. Kontener wykona wstawiania normalne menu, z jednym wyjątkiem: wstawia kontenera **pomocy** menu jako ostatni element i przechowuje wartość 1 w ostatni wpis (szóstego) **OLEMENUGROUPWIDTHS** tablicy (oznacza to, że szerokość [5], który należy do grupy pomocy obiektu). To **pomocy** menu będzie mieć tylko jeden element, który jest podmenu, "**kontenera pomocy** >" menu cascade, jak opisano wcześniej.  
  
 Obiekt wykonuje następnie jego kod wstawiania normalne menu, z wyjątkiem przed wstawieniem jego **pomocy** menu sprawdza szóstego wpisu **OLEMENUGROUPWIDTHS** tablicy. Jeśli wartość to 1, nazwa ostatniego menu **pomocy** (lub odpowiedni zlokalizowany ciąg), a następnie wstawia obiekt jego **pomocy** menu jako podmenu kontenera **Pomoc** menu.  
  
 Obiekt następnie ustawia szóstego elementu **OLEMENUGROUPWIDTHS** od zera i zwiększa piątej element o jeden. Dzięki temu OLE pamiętać, że **pomocy** menu należy do kontenera i komunikaty menu odpowiadającego danego menu (i jego podmenu) powinny być kierowane do kontenera. Następnie jest odpowiedzialny za kontenera do przekazywania `WM_INITMENUPOPUP`, **WM_SELECT**, **WM_COMMAND**i inne związane z menu komunikaty, które należą do obiektu część **pomocy**  menu. Jest to zrobić za pomocą `WM_INITMENU` Wyczyść flagę kontenera informuje, czy użytkownik ma przeszedł do obiektu **pomocy** menu. Następnie Obserwujący kontenera `WM_MENUSELECT` dla wejścia lub wyjścia z dowolny element widoczny na **pomocy** menu kontenera nie dodano samej siebie. Na wejściu, oznacza to użytkownik nawigację do menu obiekt, więc ustawia flagę "w menu Pomoc dla obiekt" i używa stan tej flagi do przekazywania żadnego kontenera `WM_MENUSELECT`, `WM_INITMENUPOPUP`, i **WM_COMMAND** komunikaty, co najmniej do okno obiektu. (Po zakończeniu kontenera usuwa flagę i przetwarza te komunikaty o tej samej sam) Kontener należy użyć okna zwrócony z obiektu **IOleInPlaceActiveObejct::GetWindow** działać jako miejsce docelowe dla tych wiadomości.  
  
 Jeśli obiekt wykrywa zero w elemencie szóstego **OLEMENUGROUPWIDTHS**, będzie kontynuowana, zgodnie z normalnym regułami dokumentów OLE. Ta procedura obejmuje kontenerów, które uczestniczą w **pomocy** scalanie oraz te, które nie mają menu.  
  
 Gdy wywołuje obiekt **IOleInPlaceFrame::SetMenu**, zanim czy wyświetlanie menu scalone paska kontroli kontenera **pomocy** menu ma dodatkowe podmenu, oprócz ma kontenera dodaje. Jeśli tak, pozostawia kontenera jego **pomocy** menu na pasku menu scalone. Jeśli **pomocy** menu nie ma dodatkowych podmenu, kontener spowoduje usunięcie jej **pomocy** menu na pasku menu scalone. Ta procedura obejmuje obiekty, które uczestniczą w **pomocy** scalanie oraz te, które nie mają menu.  
  
 Na koniec, gdy nadejdzie czas na dezasemblować menu Obiekt usuwa wstawionego **pomocy** menu oprócz innych usuwanie dodaje menu. Gdy kontener usuwa jego menu, spowoduje usunięcie jej **pomocy** menu oprócz menu, które ma on włożony.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontenery dokumentów aktywnych](../mfc/active-document-containers.md)

