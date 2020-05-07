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

Szybkie pisanie kodu wymaga poznania wszystkich aspektów aplikacji oraz sposobu, w jaki współdziała z systemem. W tym temacie przedstawiono alternatywy dla niektórych bardziej oczywistych technik kodowania, które ułatwiają zapewnienie, że krytyczne fragmenty kodu działają prawidłowo.

Aby podsumować, poprawić kod krytyczny czasu wymaga:

- Sprawdź, które części programu muszą być szybkie.

- Poznaj rozmiar i szybkość kodu.

- Poznaj koszt nowych funkcji.

- Zapoznaj się z minimalną ilością pracy wymaganej do wykonania zadania.

Aby zebrać informacje o wydajności kodu, można użyć Monitora wydajności (Perfmon. exe).

## <a name="sections-in-this-article"></a>Sekcje w tym artykule

- [Chybienia w pamięci podręcznej i błędy stron](#_core_cache_hits_and_page_faults)

- [Sortowanie i wyszukiwanie](#_core_sorting_and_searching)

- [MFC i biblioteki klas](#_core_mfc_and_class_libraries)

- [Biblioteki udostępnione](#vcovrsharedlibraries)

- [Sterty](#_core_heaps)

- [Wątki](#_core_threads)

- [Mały zestaw roboczy](#_core_small_working_set)

## <a name="cache-misses-and-page-faults"></a><a name="_core_cache_hits_and_page_faults"></a>Chybienia w pamięci podręcznej i błędy stron

Nieodebrane trafienia pamięci podręcznej, zarówno wewnętrzna, jak i zewnętrzna pamięć podręczna, a także błędy stron (przechodzenie do magazynu pomocniczego w celu uzyskania instrukcji i danych programu) spowalniają wydajność programu.

Trafienie pamięci podręcznej procesora CPU może obsłużyć cykl zegara programu w programie 10-20. Trafienie zewnętrznej pamięci podręcznej może mieć koszt 20-40 cykli zegara. Błąd strony może mieć koszt 1 000 000 cykli zegara (przy założeniu, że procesor obsługuje 500 000 000 instrukcje/sekundę i czas 2 milisekundy dla błędu strony). W związku z tym najlepszym rozwiązaniem jest wykonanie programu w celu napisania kodu, który zmniejszy liczbę nieodebranych trafień pamięci podręcznej i błędów stron.

Jedną z przyczyn wolnych programów jest to, że przestają one więcej błędów stron lub nie trafią pamięci podręcznej częściej niż to konieczne. Aby tego uniknąć, ważne jest używanie struktur danych z dobrą cechą referencyjną, co oznacza, że są one powiązane ze sobą. Czasami struktura danych, która wygląda doskonale, Horrible z powodu słabej lokalizacji odniesienia i czasami odwrócenia jest prawdziwa. Poniżej przedstawiono dwa przykłady:

- Dynamicznie przydzielane listy połączone mogą zmniejszyć wydajność programu, ponieważ podczas wyszukiwania elementu lub przechodzenia na listę na końcu każde pominięte łącze może pominąć pamięć podręczną lub spowodować błąd strony. Implementacja listy oparta na prostych tablicach może być rzeczywiście znacznie szybsza ze względu na lepszą buforowanie i mniejszą liczbę błędów stron, co pozwala na fakt, że rozmiar tablicy będzie trudniejszy do poszerzenia, wciąż może być szybszy.

- Tabele skrótów korzystające z dynamicznie przyznanych list połączonych mogą obniżyć wydajność. Dzięki rozszerzeniu tabele skrótów korzystające z dynamicznie przydzielonej listy połączonej do przechowywania ich zawartości mogą działać znacząco gorsze. W rzeczywistości w ostatniej analizie proste wyszukiwanie liniowe za pomocą tablicy może być w praktyce szybsze (w zależności od okoliczności). Tablice skrótów oparte na tablicach (tak zwane "zamknięte mieszanie") to często powtarzające się implementacje, które często mają wyższą wydajność.

## <a name="sorting-and-searching"></a><a name="_core_sorting_and_searching"></a>Sortowanie i wyszukiwanie

Sortowanie jest nieodłącznie czasochłonne w porównaniu z wieloma typowymi operacjami. Najlepszym sposobem uniknięcia niepotrzebnego spowolnienia jest uniknięcie sortowania w przypadku krytycznych czasów. Możliwe jest:

- Odłóż sortowanie do czasu niekrytycznego dla wydajności.

- Posortuj dane na wcześniejszym czas niekrytyczny dla wydajności.

- Sortuj tylko część danych, które naprawdę wymagają sortowania.

Czasami można utworzyć listę w kolejności sortowania. Należy zachować ostrożność, ponieważ jeśli chcesz wstawić dane w sortowanej kolejności, możesz wymagać bardziej skomplikowanej struktury danych z niską ilością odwołania, co prowadzi do chybień w pamięci podręcznej i błędów stron. Nie ma podejścia, które działa we wszystkich przypadkach. Wypróbuj kilka metod i zmierz różnice.

Poniżej przedstawiono niektóre ogólne porady dotyczące sortowania:

- Użyj sortowania giełdowego, aby zminimalizować błędy.

- Każda z zadań, które można wcześniej wykonać, aby zmniejszyć złożoność sortowania, to wartościowa. Jeśli jednorazowe przekazywanie danych upraszcza porównania i zmniejsza sortowanie od O (n log n) do O (n), niemal zostanie to przeprowadzone.

- Zastanów się na miejscowość odwołania do algorytmu sortowania oraz dane, które oczekują na jego uruchomienie.

Wyszukiwanie jest mniejsze niż w przypadku wyszukiwania. Jeśli wyszukiwanie ma krytyczne znaczenie dla czasu, wyszukiwanie binarne lub wyszukiwanie w tabeli skrótów jest niemal zawsze najlepsze, ale podobnie jak w przypadku sortowania, należy pamiętać o lokalizacji lokalnej. Wyszukiwanie liniowe przez małą tablicę może być szybsze niż wyszukiwanie binarne przez strukturę danych z dużą ilością wskaźników, które powodują błędy stron lub Chybienia w pamięci podręcznej.

## <a name="mfc-and-class-libraries"></a><a name="_core_mfc_and_class_libraries"></a>MFC i biblioteki klas

Microsoft Foundation Classes (MFC) może znacznie uprościć pisanie kodu. Podczas pisania kodu o kluczowym znaczeniu należy zwrócić uwagę na obciążenie związane z niektórymi z klas. Sprawdź kod MFC używany przez kod krytyczny czasu, aby sprawdzić, czy spełnia on wymagania dotyczące wydajności. Poniższa lista zawiera klasy MFC i funkcje, z którymi należy się zapoznać:

- `CString`MFC wywołuje bibliotekę wykonawczą C w celu dynamicznego przydzielania pamięci dla [CString](../atl-mfc-shared/reference/cstringt-class.md) . Ogólnie mówiąc, `CString` jest tak wydajny jak każdy inny dynamicznie przydzielony ciąg. Podobnie jak w przypadku dowolnego dynamicznego przydzielonego ciągu, ma to narzuty dynamiczne przydzielanie i wydanie. Często prosta `char` tablica na stosie może służyć do tego samego celu i jest szybsza. Nie należy używać `CString` do przechowywania stałej postaci ciągu. Zamiast tego użyj polecenia cmdlet `const char *`. Każda operacja wykonywana z `CString` obiektem ma pewne narzuty. Korzystanie z [funkcji ciągu](../c-runtime-library/string-manipulation-crt.md) biblioteki wykonawczej może być szybsze.

- `CArray`[CArray](../mfc/reference/carray-class.md) zapewnia elastyczność, że zwykła tablica nie jest, ale program może nie potrzebować tego. Jeśli znasz określone limity dla tablicy, możesz zamiast tego użyć globalnej stałej tablicy. Jeśli używasz `CArray`, użyj `CArray::SetSize` , aby ustalić jego rozmiar i określić liczbę elementów, o których rośnie, gdy konieczne jest ponowne przypisanie. W przeciwnym razie Dodawanie elementów może spowodować, że tablica jest często ponownie przydzielna i kopiowana, co jest niewydajne i może stanowić fragment pamięci. Należy również pamiętać, że w przypadku wstawienia elementu do tablicy program `CArray` przenosi kolejne elementy w pamięci i może wymagać powiększania tablicy. Te akcje mogą spowodować Chybienia w pamięci podręcznej i błędy stron. Jeśli szukasz kodu, który jest używany przez MFC, może się okazać, że można napisać coś bardziej specyficznego dla danego scenariusza, aby zwiększyć wydajność. Ponieważ `CArray` jest to szablon, można na przykład podać `CArray` specjalizacje dla konkretnych typów.

- `CList`[CList](../mfc/reference/clist-class.md) jest połączoną podwójną listą, więc wstawienie elementu jest szybkie na początku, na końcu i na znanej pozycji (`POSITION`) na liście. Wyszukiwanie elementu według wartości lub indeksu wymaga przeszukiwania sekwencyjnego, ale może być wolne, jeśli lista jest długa. Jeśli kod nie wymaga pozostałej listy połączonej, możesz ponownie rozważyć użycie `CList`. Użycie listy połączonej pojedynczo pozwala zaoszczędzić obciążenie związane z aktualizowaniem dodatkowego wskaźnika dla wszystkich operacji, a także pamięci dla danego wskaźnika. Dodatkowa pamięć nie jest świetna, ale jest kolejną okazją dla chybień w pamięci podręcznej lub błędów stron.

- `IsKindOf`Ta funkcja może generować wiele wywołań i uzyskiwać dostęp do dużej ilości pamięci w różnych obszarach danych, co prowadzi do nieprawidłowej lokalizacji referencyjnej. Jest to przydatne w przypadku kompilacji debugowania (na przykład w wywołaniu potwierdzenia), ale spróbuj uniknąć używania jej w kompilacji wydania.

- `PreTranslateMessage`Należy `PreTranslateMessage` używać, gdy określone drzewo systemu Windows wymaga różnych akceleratorów klawiatury lub gdy należy wstawić obsługę komunikatów do pompy komunikatów. `PreTranslateMessage`zmienia komunikaty wysyłania MFC. Jeśli przesłonisz `PreTranslateMessage`, zrób to tylko na żądanym poziomie. Na przykład nie jest konieczne przesłonięcie `CMainFrame::PreTranslateMessage` , Jeśli interesuje się tylko komunikaty przechodzą do elementów podrzędnych określonego widoku. Zamiast `PreTranslateMessage` tego Przesłoń klasę widoku.

   Nie należy omijać normalnej ścieżki wysyłania przy użyciu `PreTranslateMessage` programu w celu obsługi komunikatów wysyłanych do dowolnego okna. Użyj w tym celu [procedur okien](../mfc/registering-window-classes.md) i map komunikatów MFC.

- `OnIdle`Zdarzenia bezczynne mogą wystąpić w godzinach nieoczekiwanych, takich jak `WM_KEYDOWN` między `WM_KEYUP` i zdarzenia. Czasomierze mogą być wydajniejszym sposobem wyzwalania kodu. Nie należy wymuszać `OnIdle` wielokrotnego wywoływania przez generowanie fałszywych komunikatów lub przez zawsze `TRUE` powrót z przesłonięcia `OnIdle`, co nigdy nie zezwoli na wątek do uśpienia. Ponownie czasomierz lub osobny wątek mogą być bardziej odpowiednie.

## <a name="shared-libraries"></a><a name="vcovrsharedlibraries"></a>Biblioteki udostępnione

Wymagane jest ponowne użycie kodu. Jeśli jednak chcesz korzystać z kodu innej osoby, upewnij się, że wiesz dokładnie, co robi w tym przypadku, gdy wydajność ma krytyczne znaczenie dla użytkownika. Najlepszym sposobem na zrozumienie tego jest przechodzenie przez kod źródłowy lub pomiar przy użyciu narzędzi, takich jak PView lub Monitor wydajności.

## <a name="heaps"></a><a name="_core_heaps"></a>Sterty

Używaj wielu stert z opcją uznania. Dodatkowe sterty utworzone w `HeapCreate` programie `HeapAlloc` i umożliwiają zarządzanie, a następnie Usuwanie powiązanego zestawu alokacji. Nie Zatwierdź zbyt dużej ilości pamięci. W przypadku korzystania z wielu stert należy zwrócić szczególną uwagę na ilość pamięci, która jest początkowo zatwierdzona.

Zamiast wielu stert, można używać funkcji pomocnika do interfejsów między kodem i stertą domyślną. Funkcje pomocnika ułatwiają niestandardowe strategie alokacji, które mogą zwiększyć wydajność aplikacji. Jeśli na przykład często wykonujesz małe alokacje, możesz chcieć zlokalizować te przydziały w jednej części sterty domyślnej. Możesz przydzielić duży blok pamięci, a następnie użyć funkcji pomocnika do alokacji z tego bloku. Jeśli to zrobisz, nie będziesz mieć dodatkowych stert z nieużywaną pamięcią, ponieważ alokacja jest wychodząca z sterty domyślnej.

W niektórych przypadkach jednak użycie sterty domyślnej może zmniejszyć liczbę miejsc odwołania. Użyj podglądu procesów, programu Spy + + lub monitora wydajności, aby zmierzyć efekty przeniesienia obiektów ze sterty do sterty.

Zmierz sterty, aby można było uwzględnić każde alokacje na stercie. Użyj [procedur sterty debugowania](/visualstudio/debugger/crt-debug-heap-details) w czasie wykonywania C, aby wypróbować i zrzucić stos. Dane wyjściowe można odczytać do programu arkusza kalkulacyjnego, takiego jak program Microsoft Excel, i użyć tabel przestawnych, aby wyświetlić wyniki. Zwróć uwagę na łączną liczbę, rozmiar i rozkład alokacji. Porównaj je z rozmiarem zestawów roboczych. Zapoznaj się również z klastrowaniem obiektów o powiązanym rozmiarze.

Liczników wydajności można również użyć do monitorowania użycia pamięci.

## <a name="threads"></a><a name="_core_threads"></a>Wątk

W przypadku zadań w tle skuteczna bezczynna obsługa zdarzeń może być szybsza niż przy użyciu wątków. Łatwiej jest zrozumieć zakres odwołań w programie jednowątkowym.

Dobrym warunkiem jest użycie wątku tylko wtedy, gdy powiadomienie systemu operacyjnego, które jest blokowane, znajduje się w katalogu głównym pracy w tle. Wątki są najlepszym rozwiązaniem w takich przypadkach, ponieważ nie ma praktycznego blokowania głównego wątku w zdarzeniu.

Wątki również powodują problemy z komunikacją. Należy zarządzać łączem komunikacyjnym między wątkami, z listą komunikatów lub przez przydzieleniem i użyciem pamięci współdzielonej. Zarządzanie łączem komunikacyjnym zwykle wymaga synchronizacji, aby uniknąć sytuacji wyścigu i problemów z zakleszczeniem. Ta złożoność może łatwo zamienić błędy i problemy z wydajnością.

Aby uzyskać więcej informacji, zobacz [przetwarzanie pętli bezczynności](../mfc/idle-loop-processing.md) i [wielowątkowość](../parallel/multithreading-support-for-older-code-visual-cpp.md).

## <a name="small-working-set"></a><a name="_core_small_working_set"></a>Mały zestaw roboczy

Mniejsze zestawy robocze oznaczają lepszą miejscowość odwołania, mniejsze błędy stron i więcej trafień w pamięci podręcznej. Zestaw roboczy procesu jest najbliższą metryką, którą system operacyjny zapewnia bezpośrednio do mierzenia lokalizacji odniesienia.

- Aby ustawić górny i dolny limit zestawu roboczego, użyj [SetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-getprocessworkingsetsize).

- Aby uzyskać górny i dolny limit zestawu roboczego, użyj [GetProcessWorkingSetSize](/windows/win32/api/winbase/nf-winbase-setprocessworkingsetsize).

- Aby wyświetlić rozmiar zestawu roboczego, użyj programu Spy + +.

## <a name="see-also"></a>Zobacz też

[Optymalizacja kodu](optimizing-your-code.md)
