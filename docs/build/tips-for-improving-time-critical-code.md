---
title: Wskazówki dotyczące poprawiania kodu wrażliwego na czas
ms.date: 11/04/2016
helpviewer_keywords:
- _lsearch function
- qsort function
- background tasks
- standard sort routines
- clock cycle losses
- code, time-critical
- memory [C++], monitoring usage
- execution, speed improvements
- local heap performance
- optimization [C++], time-critical code
- performance [C++], time-critical code
- threading [C++], performance
- cache [C++], hits and misses
- linear search performance
- page faults
- best practices, time-critical code
- searching [C++], improving performance
- sorting data, improving performance
- threading [C++], best practices
- threading [C++], background tasks
- lists, sorting
- bsearch function
- MFC [C++], performance
- sort routines
- programs [C++], performance
- _lfind function
- heap allocation, time-critical code performance
ms.assetid: 3e95a8cc-6239-48d1-9d6d-feb701eccb54
ms.openlocfilehash: 039b86eec024daf8e3473bba5d89f190507f3cfd
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335458"
---
# <a name="tips-for-improving-time-critical-code"></a>Wskazówki dotyczące poprawiania kodu wrażliwego na czas

Pisanie szybkiego kodu wymaga zrozumienia wszystkich aspektów aplikacji i sposobu interakcji z systemem. W tym temacie sugeruje alternatywy dla niektórych technik kodowania bardziej oczywiste, aby zapewnić, że krytyczne czas części kodu wykonać zadowalająco.

Podsumowując, poprawa kodu krytycznego dla czasu wymaga:

- Wiedzieć, które części programu muszą być szybkie.

- Poznaj rozmiar i szybkość kodu.

- Poznaj koszt nowych funkcji.

- Poznaj minimalną pracę potrzebną do wykonania zadania.

Aby zebrać informacje na temat wydajności kodu, można użyć monitora wydajności (perfmon.exe).

## <a name="sections-in-this-article"></a>Sekcje w niniejszym artykule

- [Chybienia w pamięci podręcznej i błędy strony](#_core_cache_hits_and_page_faults)

- [Sortowanie i wyszukiwanie](#_core_sorting_and_searching)

- [Biblioteki MFC i klas](#_core_mfc_and_class_libraries)

- [Biblioteki udostępnione](#vcovrsharedlibraries)

- [Stert](#_core_heaps)

- [Wątki](#_core_threads)

- [Mały zestaw roboczy](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a>Chybienia w pamięci podręcznej i błędy strony

Nieodebrane trafienia w pamięci podręcznej, zarówno w pamięci wewnętrznej, jak i zewnętrznej, a także błędy strony (przechodzenie do dodatkowego magazynu w celu uzyskania instrukcji programu i danych) spowalniają działanie programu.

Trafienie pamięci podręcznej procesora może kosztować program 10-20 cykli zegara. Trafienie zewnętrznej pamięci podręcznej może kosztować 20-40 cykli zegara. Błąd strony może kosztować milion cykli zegara (przy założeniu, że procesor obsługuje 500 milionów instrukcji na sekundę i czas 2 milisekundy dla błędu strony). W związku z tym jest w najlepszym interesie wykonania programu do pisania kodu, który zmniejszy liczbę nieodebranych trafień pamięci podręcznej i błędów strony.

Jednym z powodów powolnych programów jest to, że biorą więcej błędów strony lub przegapić pamięć podręczną częściej niż to konieczne. Aby tego uniknąć, należy używać struktur danych z dobrą lokalizacja odniesienia, co oznacza utrzymanie powiązanych rzeczy razem. Czasami struktura danych, która wygląda świetnie, okazuje się być okropna z powodu słabej lokalizacji odniesienia, a czasami jest odwrotnie. Poniżej przedstawiono dwa przykłady:

- Dynamicznie przydzielone połączone listy mogą zmniejszyć wydajność programu, ponieważ podczas wyszukiwania elementu lub przechodzenia przez listę do końca każde pominięte łącze może spowodować pominięcie pamięci podręcznej lub spowodować błąd strony. Implementacja listy oparta na prostych tablicach może być znacznie szybsza ze względu na lepsze buforowanie i mniejszą liczbę błędów strony nawet — co pozwala na to, że tablica będzie trudniejsza do rozwiania, nadal może być szybsza.

- Tabele mieszania, które używają dynamicznie przydzielonych połączonych list, mogą obniżać wydajność. W związku z tym tabele mieszania, które używają dynamicznie przydzielonych połączonych list do przechowywania ich zawartości, mogą działać znacznie gorzej. W rzeczywistości w końcowej analizie proste wyszukiwanie liniowe za pomocą tablicy może być w rzeczywistości szybsze (w zależności od okoliczności). Tabele skrótów oparte na tablicy (tak zwane "zamknięte mieszanie") to często pomijana implementacja, która często ma doskonałą wydajność.

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a>Sortowanie i wyszukiwanie

Sortowanie jest z natury czasochłonne w porównaniu do wielu typowych operacji. Najlepszym sposobem uniknięcia niepotrzebnego spowolnienia jest unikanie sortowania w krytycznych momentach. Możesz być w stanie:

- Oderwij sortowanie do czasu, gdy nie ma krytycznego czasu.

- Sortuj dane we wcześniejszym, krytycznym czasie niesakrie.

- Sortuj tylko tę część danych, która naprawdę wymaga sortowania.

Czasami można utworzyć listę w kolejności posortowane. Należy zachować ostrożność, ponieważ jeśli trzeba wstawić dane w kolejności posortowanej, może wymagać bardziej skomplikowanej struktury danych ze słabą lokalizacja odwołania, co prowadzi do braków w pamięci podręcznej i błędów strony. Nie ma podejścia, które działa we wszystkich przypadkach. Wypróbuj kilka podejść i zmierz różnice.

Oto kilka ogólnych wskazówek dotyczących sortowania:

- Użyj sortowania zapasów, aby zminimalizować błędy.

- Każda praca, którą możesz wcześniej wykonać, aby zmniejszyć złożoność tego rodzaju, jest opłacalna. Jeśli jednorazowe przekazanie danych upraszcza porównania i zmniejsza sortowanie z O(n log n) do O(n), prawie na pewno wyjdziesz z wyprzedzeniem.

- Pomyśl o lokalizacji odwołania algorytmu sortowania i danych, które można oczekiwać, aby uruchomić na.

Istnieje mniej alternatyw dla wyszukiwań niż do sortowania. Jeśli wyszukiwanie ma krytyczne znaczenie czasowe, wyszukiwanie binarne lub wyszukiwanie tabeli skrótów jest prawie zawsze najlepsze, ale podobnie jak w przypadku sortowania, należy pamiętać o lokalizacji. Wyszukiwanie liniowe za pośrednictwem małej tablicy może być szybsze niż wyszukiwanie binarne za pomocą struktury danych z dużą ilością wskaźników, które powodują błędy strony lub braki w pamięci podręcznej.

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a>Biblioteki MFC i klas

Microsoft Foundation Classes (MFC) może znacznie uprościć kod pisania. Podczas pisania kodu krytycznego czas, należy pamiętać o obciążenie związane z niektórych klas. Sprawdź kod MFC, który używa kodu krytycznego czas, aby sprawdzić, czy spełnia wymagania dotyczące wydajności. Poniższa lista identyfikuje klasy MFC i funkcje, o których należy pamiętać:

- `CString`MFC wywołuje bibliotekę wyłowienia C, aby dynamicznie przydzielać pamięć dla [CString.](../atl-mfc-shared/reference/cstringt-class.md) Ogólnie rzecz biorąc, jest tak wydajny, `CString` jak każdy inny ciąg alokacji dynamicznie. Podobnie jak w przypadku każdego dynamicznie przydzielonego ciągu, ma obciążenie związane z alokacją dynamiczną i wydaniem. Często prosta `char` tablica na stosie może służyć temu samemu celowi i jest szybsza. Nie używaj `CString` a do przechowywania stałego ciągu. Zamiast tego użyj polecenia cmdlet `const char *`. Każda operacja, którą `CString` wykonujesz za pomocą obiektu, ma pewne obciążenie. Korzystanie z funkcji [ciągu](../c-runtime-library/string-manipulation-crt.md) biblioteki w czasie wykonywania może być szybsze.

- `CArray`[CArray](../mfc/reference/carray-class.md) zapewnia elastyczność, że regularne tablicy nie, ale program może nie być potrzebny. Jeśli znasz określone limity dla tablicy, możesz użyć globalnej stałej tablicy. W przypadku `CArray`użycia `CArray::SetSize` programu służy do ustalenia jego rozmiaru i określenia liczby elementów, o które rośnie, gdy konieczna jest ponowna alokacja. W przeciwnym razie dodawanie elementów może spowodować, że tablica ma być często ponownie przydzielane i kopiowane, co jest nieefektywne i można fragment pamięci. Należy również pamiętać, że jeśli wstawisz element do tablicy, `CArray` przenosi kolejne elementy w pamięci i może być konieczne zwiększenie tablicy. Te akcje mogą powodować błędy w pamięci podręcznej i błędy strony. Jeśli przejrzysz kod, który używa MFC, może się okazać, że można napisać coś bardziej konkretnego do scenariusza w celu zwiększenia wydajności. Ponieważ `CArray` jest szablonem, na przykład `CArray` można podać specjalizacje dla określonych typów.

- `CList`[CList](../mfc/reference/clist-class.md) jest podwójnie połączone listy, więc wstawianie elementu jest szybki na`POSITION`czele, ogon, i w znanej pozycji ( ) na liście. Wyszukiwanie elementu według wartości lub indeksu wymaga sekwencyjnego wyszukiwania, jednak, które mogą być powolne, jeśli lista jest długa. Jeśli kod nie wymaga podwójnie połączonej listy, warto `CList`ponownie rozważyć użycie programu . Za pomocą pojedynczo połączonej listy zapisuje obciążenie aktualizacji dodatkowy wskaźnik dla wszystkich operacji, jak również pamięci dla tego wskaźnika. Dodatkowa pamięć nie jest świetna, ale jest to kolejna okazja do pominięcia pamięci podręcznej lub błędów strony.

- `IsKindOf`Ta funkcja może generować wiele wywołań i uzyskać dostęp do dużej ilości pamięci w różnych obszarach danych, co prowadzi do złej lokalizacji odwołania. Jest to przydatne dla kompilacji debugowania (w assert wywołania, na przykład), ale należy unikać używania go w kompilacji wydania.

- `PreTranslateMessage`Użyj, `PreTranslateMessage` gdy określone drzewo systemu Windows wymaga różnych akceleratorów klawiatury lub gdy należy wstawić obsługę wiadomości do pompy wiadomości. `PreTranslateMessage`zmienia komunikaty o wysyłaniu MFC. W przypadku `PreTranslateMessage`zastąpienia, zrób to tylko na wymaganym poziomie. Na przykład nie jest konieczne zastąpienie, `CMainFrame::PreTranslateMessage` jeśli jesteś zainteresowany tylko wiadomości będzie do dzieci określonego widoku. Zamiast tego `PreTranslateMessage` zastądnikuj dla klasy widoku.

   Nie należy obchodzić normalnej ścieżki `PreTranslateMessage` wysyłki przy użyciu do obsługi wiadomości wysłanych do dowolnego okna. Użyj [procedur okna](../mfc/registering-window-classes.md) i mapy komunikatów MFC w tym celu.

- `OnIdle`Bezczynne zdarzenia mogą wystąpić w czasie, którego `WM_KEYDOWN` nie `WM_KEYUP` oczekujesz, na przykład między i zdarzenia. Czasomierze mogą być bardziej efektywnym sposobem wyzwalania kodu. Nie zmuszaj `OnIdle` do wielokrotnego wywoływania przez generowanie `TRUE` fałszywych wiadomości lub `OnIdle`zawsze zwracając z zastąpienia , które nigdy nie pozwoli wątku do uśpienia. Ponownie czasomierz lub oddzielny wątek może być bardziej odpowiednie.

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a>Biblioteki udostępnione

Ponowne użycie kodu jest pożądane. Jeśli jednak zamierzasz użyć kodu innej osoby, upewnij się, że wiesz dokładnie, co robi w tych przypadkach, gdy wydajność jest dla Ciebie krytyczna. Najlepszym sposobem, aby to zrozumieć, jest przechodzenie przez kod źródłowy lub pomiar za pomocą narzędzi, takich jak PView lub Monitor wydajności.

## <a name="heaps"></a><a name="_core_heaps"></a>Stert

Używaj wielu stert z dyskrecją. Dodatkowe sterty utworzone `HeapCreate` `HeapAlloc` z i umożliwiają zarządzanie, a następnie usuwanie powiązanego zestawu alokacji. Nie poświęć zbyt wiele pamięci. Jeśli używasz wielu stert, należy zwrócić szczególną uwagę na ilość pamięci, która jest początkowo zatwierdzona.

Zamiast wielu stert, można użyć funkcji pomocnika do interfejsu między kodem a domyślną stertą. Funkcje pomocnika ułatwiają niestandardowe strategie alokacji, które mogą poprawić wydajność aplikacji. Na przykład jeśli często wykonujesz małe alokacje, można zlokalizować te alokacje do jednej części domyślnego stosu. Można przydzielić duży blok pamięci, a następnie użyć funkcji pomocnika do suballocate z tego bloku. Jeśli to zrobisz, nie będzie mieć dodatkowe sterty z nieużywaną pamięcią, ponieważ alokacja wychodzi z domyślnej sterty.

W niektórych przypadkach jednak przy użyciu domyślnego stosu można zmniejszyć lokalizacja odwołania. Użyj Process Viewer, Spy ++ lub Monitor wydajności do pomiaru skutków przenoszenia obiektów ze sterty do sterty.

Zmierz sterty, dzięki czemu można uwzględnić dla każdej alokacji na stercie. Użyj [c procedury sterty debugowania](/visualstudio/debugger/crt-debug-heap-details) w czasie wykonywania do punktu kontrolnego i zrzutu sterty. Dane wyjściowe można odczytać w programie arkusza kalkulacyjnego, takim jak Microsoft Excel, i używać tabel przestawnych do wyświetlania wyników. Zanotuj całkowitą liczbę, rozmiar i rozkład alokacji. Porównaj je z rozmiarem zestawów roboczych. Spójrz również na klastrowanie obiektów o powiązanych rozmiarach.

Liczniki wydajności można również używać do monitorowania użycia pamięci.

## <a name="threads"></a><a name="_core_threads"></a>Wątków

W przypadku zadań w tle efektywna bezczynna obsługa zdarzeń może być szybsza niż przy użyciu wątków. Łatwiej jest zrozumieć lokalizacja odwołania w programie jednowątkowym.

Dobrą zasadą jest użycie wątku tylko wtedy, gdy powiadomienie systemu operacyjnego, które można zablokować, znajduje się w katalogu głównym pracy w tle. Wątki są najlepszym rozwiązaniem w takim przypadku, ponieważ jest niepraktyczne, aby zablokować główny wątek na zdarzenie.

Wątki przedstawiają również problemy z komunikacją. Należy zarządzać łącze komunikacyjne między wątkami, z listą wiadomości lub przydzielając i przy użyciu pamięci współużytkowanej. Zarządzanie łączem komunikacyjnym zwykle wymaga synchronizacji, aby uniknąć warunków wyścigu i problemów z zakleszczeniem. Ta złożoność może łatwo przekształcić się w błędy i problemy z wydajnością.

Aby uzyskać więcej informacji, zobacz [Przetwarzanie pętli bezczynnej](../mfc/idle-loop-processing.md) i [wielowątkowe](../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="small-working-set"></a><a name="_core_small_working_set"></a>Mały zestaw roboczy

Mniejsze zestawy robocze oznaczają lepszą lokalizacja odwołania, mniejszą liczbę błędów stron i więcej trafień pamięci podręcznej. Zestaw roboczy procesu jest najbliższą metryką, która system operacyjny bezpośrednio zapewnia pomiar lokalizacji referencyjnej.

- Aby ustawić górną i dolną granicę zestawu roboczego, użyj [funkcji SetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize).

- Aby uzyskać górne i dolne granice zestawu roboczego, użyj [getprocessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize).

- Aby wyświetlić rozmiar zestawu roboczego, użyj Spy++.

## <a name="see-also"></a>Zobacz też

[Optymalizacja kodu](optimizing-your-code.md)
