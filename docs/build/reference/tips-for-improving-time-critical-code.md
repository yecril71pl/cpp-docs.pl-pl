---
title: Wskazówki dotyczące poprawiania kodu wrażliwego na czas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69e05d0aa49a895a9632b07fe07bf38d9e6d4d6b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379513"
---
# <a name="tips-for-improving-time-critical-code"></a>Wskazówki dotyczące poprawiania kodu wrażliwego na czas
Pisanie kodu szybkiego wymaga opis wszystkich aspektów aplikacji i sposób interakcji z systemu. W tym temacie sugeruje alternatywy dla niektórych bardziej oczywistymi technik kodowania w celu zapewnienia pomyślnie wykonać wrażliwego na czas fragmentów kodu.  
  
 Podsumowując, poprawiania kodu wrażliwego na czas wymaga, aby użytkownik:  
  
-   Sprawdzić, które części programu szybkie.  
  
-   Znać rozmiaru i prędkości kodu.  
  
-   Znać koszt nowych funkcji.  
  
-   Znać minimalna pracy wymaganej do wykonania zadania.  
  
 Aby zbierać informacje o wydajności kodu, można użyć Monitora wydajności (perfmon.exe).  
  
## <a name="sections-in-this-article"></a>Sekcje w tym artykule  
  
-   [Chybienia pamięci podręcznej i błędów stron](#_core_cache_hits_and_page_faults)  
  
-   [Sortowanie i wyszukiwanie](#_core_sorting_and_searching)  
  
-   [MFC i biblioteki klas](#_core_mfc_and_class_libraries)  
  
-   [Biblioteki udostępnione](#vcovrsharedlibraries)  
  
-   [Stert](#_core_heaps)  
  
-   [Wątki](#_core_threads)  
  
-   [Zestaw roboczy małe](#_core_small_working_set)  
  
##  <a name="_core_cache_hits_and_page_faults"></a> Chybienia pamięci podręcznej i błędów stron  
 Pominięte trafień w pamięci podręcznej, w obu wewnętrznych i zewnętrznych pamięci podręcznej, a także błędów stron (przechodzi do magazynu pomocniczego dla danych i instrukcje programu) spowolnienie działania programu.  
  
 Trafienie w pamięci podręcznej Procesora koszt program 10-20 cykle zegara. Trafień pamięci podręcznej zewnętrzne mogą kosztem cykle zegara 20-40. Błąd strony mogą kosztem cykle zegara milion (przy założeniu, procesora, które obsługuje 500 milionów instrukcje na sekundę i czas 2 milisekund błąd strony). Dlatego jest w najlepszym odsetek wykonywania programu do pisania kodu, który zmniejsza liczbę trafień w pamięci podręcznej brakujących i błędów stron.  
  
 Jedną z przyczyn powolne programów jest zająć więcej błędów stron lub pominąć pamięci podręcznej częściej niż to konieczne. Aby tego uniknąć, należy użyć struktur danych z dobrym miejscowości odwołania, co oznacza grupowanie powiązanych elementów. Czasami struktury danych, która wygląda bardzo okaże się horrible z powodu słabej miejscowości odwołania, a czasami odwrotnej ma wartość true. Poniżej przedstawiono dwa przykłady:  
  
-   Dynamicznie przydzielonego list połączonych może zmniejszyć wydajność programu, ponieważ podczas wyszukiwania elementu lub przechodzenie listę do końca, każde łącze zostało pominięte, można pominąć pamięci podręcznej lub spowodować błąd strony. Implementacja listy, na podstawie tablic proste faktycznie może być znacznie szybsze ze względu na lepsze buforowania i mniej błędów stron nawet — zezwalanie na fakt, że tablicy może być trudniejsza zwiększa się, nadal może być szybsze.  
  
-   Tabele hash, korzystających z dynamicznie przydzielane połączonej listy może obniżyć wydajność. Przez rozszerzenie, może wykonać tabel wyznaczania wartości skrótu, które używają list połączone dynamicznie przydzielonego do przechowywania ich zawartość znacznie gorszą. W rzeczywistości w ostatecznym rozrachunku proste wyszukiwanie liniowe za pomocą tablicy może mieć w rzeczywistości szybsze (w zależności od sytuacji). Tabel na podstawie tablicy skrótów (tak zwane "zamknięte wyznaczania wartości skrótu") jest często pomijane implementacji, który często ma lepszą wydajność.  
  
##  <a name="_core_sorting_and_searching"></a> Sortowanie i wyszukiwanie  
 Sortowanie jest z założenia czasochłonne w porównaniu do wielu typowych operacji. Najlepszym sposobem uniknięcia spowolnienia niepotrzebne jest uniknąć sortowania w czasie krytyczne. Może mieć możliwość:  
  
-   Odroczenie sortowanie wydajności niekrytyczne czasu.  
  
-   Sortowanie danych w czasie wcześniej, wydajności niekrytyczne.  
  
-   Sortowanie tylko część danych wymagających naprawdę sortowania.  
  
 Czasami należy utworzyć listę posortowane. Należy zachować ostrożność, ponieważ do wstawiania danych posortowane należy może wymagać bardziej skomplikowane struktury danych, z niską miejscowości odwołania, co może prowadzić do Chybienia pamięci podręcznej i błędów stron. Brak nie metody, która działa we wszystkich przypadkach. Spróbuj różne podejścia i zmierzyć różnice.  
  
 Poniżej przedstawiono pewne ogólne porady dotyczące sortowania:  
  
-   Użyj standardowych sortowania, aby zminimalizować usterki.  
  
-   Pracę, należy wcześniej uproszczeniu sortowania jest rozważyć. Jeśli jednorazowe przekazywanym przez dane upraszcza porównanie i zmniejsza sortowanie od O (dziennika n n) do O(n), będzie prawie na pewno NAS wyprzedzeniem.  
  
-   Zastanów się odwołania algorytm sortowania i danych spodziewasz się go w tej lokalizacji.  
  
 Brak mniej alternatyw wyszukuje niż sortowanie. W przypadku wrażliwego na czas wyszukiwania binarne wyszukiwania tabeli wyszukiwania lub skrótu jest prawie zawsze najlepsze, ale tak jak w przypadku sortowania, miejscowości musi należy pamiętać. Wyszukiwanie liniowe za pośrednictwem mała tablica może być szybsze niż wyszukiwanie binarne za pośrednictwem struktury danych z dużą wskaźników, która powoduje występowanie błędów stron lub liczba chybień pamięci podręcznej.  
  
##  <a name="_core_mfc_and_class_libraries"></a> MFC i biblioteki klas  
 Biblioteka Microsoft Foundation Classes (MFC) znacznie ułatwia pisanie kodu. Podczas pisania kodu wrażliwego na czas, należy zwrócić uwagę koszty związane z niektórych klas. Sprawdź kod MFC, który używa kodu wrażliwego na czas, aby sprawdzić, czy spełnia on wymagań dotyczących wydajności. Poniższa lista zawiera klasy MFC i funkcje, które należy zwrócić uwagę:  
  
-   `CString` Biblioteki wykonawcze języka C można przydzielić pamięci dla wywołania MFC [cstring —](../../atl-mfc-shared/reference/cstringt-class.md) dynamicznie. Ogólnie rzecz biorąc `CString` jest efektywne dowolnego dynamicznie przydzielane ciągu. Podobnie jak w przypadku dowolnego dynamicznie przydzielonego ciągu ma obciążenie dynamiczne przydzielanie i wersji. Często prostą `char` tablicy na stosie, może obsługiwać te same funkcje i jest szybsze. Nie używaj `CString` do przechowywania ciągiem stałym. Zamiast nich należy używać słów kluczowych `const char *`. Każde działanie wykonywane z `CString` obiekt ma pewne nadmiarowe obciążenie. Przy użyciu biblioteki wykonawczej [ciągu funkcji](../../c-runtime-library/string-manipulation-crt.md) może przebiegać szybciej.  
  
-   `CArray` A [carray —](../../mfc/reference/carray-class.md) zapewnia elastyczność nie regularne tablicy, że program może nie być konieczne który. Jeśli znasz określone limity dla tablicy można globalne tablicy o ustalonym zamiast tego. Jeśli używasz `CArray`, użyj `CArray::SetSize` jego rozmiar i określ liczbę elementów, które rozwoju, gdy konieczne jest ponowne przydzielenie. W przeciwnym razie dodanie elementów może spowodować tablica przydzielić często i kopiować, który jest nieefektywne i można fragmentu pamięci. Należy także zauważyć, że po wstawieniu elementu do tablicy, `CArray` przenosi kolejnych elementów w pamięci i może być konieczne wzrostu tablicy. Te działania mogą powodować Chybienia pamięci podręcznej i błędów stron. Jeśli Przejrzyj kod, który używa MFC, mogą pojawić się, czy możesz zapisywać bardziej szczegółowa do danego scenariusza, aby zwiększyć wydajność. Ponieważ `CArray` jest szablonem, na przykład można określić `CArray` specjalizacje dla określonego typu.  
  
-   `CList` [Clist —](../../mfc/reference/clist-class.md) jest podwójnie połączonej listy, tak aby element wstawiania przy head, tail, a w pozycji znane (`POSITION`) na liście. Wyszukiwanie elementu według wartości lub indeks wymaga sekwencyjnych wyszukiwania, jednak może być wolne, jeśli lista jest długa. Jeśli kod nie wymaga podwójnie połączonej listy może zajść potrzeba powierzeniem `CList`. Przy użyciu pojedynczo połączonej listy zapisuje koszty aktualizowania dodatkowe wskaźnika dla wszystkich operacji, a także pamięci dla tego wskaźnika. Dodatkowej pamięci nie jest doskonałym, ale jest możliwość innego Chybienia pamięci podręcznej lub błędów stron.  
  
-   `IsKindOf` Tej funkcji można wygenerować wiele wywołań i dużej ilości pamięci w obszarach danych, co prowadzi do lokalizacji zły odwołania dostępu. Jest przydatne w przypadku kompilacji debugowania (w wywołaniu ASSERT, na przykład), ale należy unikać używania go w kompilacji wydania.  
  
-   `PreTranslateMessage` Użyj `PreTranslateMessage` drzewa systemu windows wymaga innej klawiszy skrótów lub po wstawieniu komunikat — Obsługa na przekazywanie komunikatów. `PreTranslateMessage` Zmienia MFC wysyłania wiadomości. Jeśli można zastąpić `PreTranslateMessage`, dlatego tylko na poziomie potrzebne. Na przykład nie jest konieczne zastąpić `CMainFrame::PreTranslateMessage` Jeśli interesuje Cię tylko komunikatów do podrzędnych określonego widoku. Zastąpienie `PreTranslateMessage` widoku zamiast klasy.  
  
     Nie stanowi obejścia ścieżki normalne wysyłania za pomocą `PreTranslateMessage` wszystkie wiadomości wysyłane do dowolnego okna obsługi. Użyj [procedury okna](../../mfc/registering-window-classes.md) i mapy wiadomości MFC do tego celu.  
  
-   `OnIdle` Zdarzenia bezczynności może wystąpić w czasie nie będzie, takich jak między `WM_KEYDOWN` i `WM_KEYUP` zdarzenia. Czasomierze może być bardziej wydajny sposób, aby wyzwolić kodu. Nie wymuszaj `OnIdle` wywoływanie wielokrotnie, generując false wiadomości lub zawsze zwracając `TRUE` z zastępująca `OnIdle`, które umożliwiałyby z wątku w stan uśpienia. Ponownie czasomierz lub oddzielnym wątku mogą być bardziej odpowiednie.  
  
##  <a name="vcovrsharedlibraries"></a> Biblioteki udostępnione  
 Ponowne użycie kodu jest pożądane. Jednak jeśli zamierzasz użyć do kogoś innego kodu, powinien upewnij się, że znasz dokładnie działanie w przypadkach, gdy ma kluczowe znaczenie dla Ciebie. Aby to zrozumieć najlepiej krokowe wykonywanie kodu źródłowego lub poprzez pomiar z narzędzi, takich jak PView lub monitora wydajności.  
  
##  <a name="_core_heaps"></a> Stert  
 Użyj wielu stosów na własne ryzyko. Dodatkowe stosów utworzone za pomocą `HeapCreate` i `HeapAlloc` umożliwiają zarządzanie, a następnie usuwa powiązany zestaw alokacji. Nie należy zatwierdzić zbyt dużej ilości pamięci. Jeśli używasz wielu stosów należy zwrócić szczególną uwagę na ilość pamięci, która jest początkowo zatwierdzone.  
  
 Zamiast wielu stosów możesz użyć funkcji pomocnika interfejs między kodu i domyślnej sterty. Funkcje pomocy ułatwiają strategii alokacji niestandardowych, które może poprawić wydajność aplikacji. Na przykład często wykonywane małych alokacji, możesz lokalizowanie tych przydziałów do domyślnej sterty części. Można Przydziel dużych bloków pamięci, a następnie użyć funkcji pomocnika do podrzędnej z tego bloku. Jeśli to zrobisz, nie będzie mieć dodatkowe stosów z nieużywanej pamięci, ponieważ alokacja wystawała domyślnej sterty.  
  
 W niektórych przypadkach jednak przy użyciu domyślnej sterty można zmniejszyć miejscowości odwołania. Używać procesu podglądu, narzędzie Spy ++ lub monitora wydajności do mierzenia skutków przenoszenie obiektów sterty stosu.  
  
 Zmierz Twojej stosów tak można konta dla każdej operacji przydzielenia pamięci na stercie. Użyj C-run-time [procedury sterty debugowania](/visualstudio/debugger/crt-debug-heap-details) do punktu kontrolnego i zrzutu stosu sieci. Można odczytywać dane wyjściowe do programu arkusza kalkulacyjnego, takich jak program Microsoft Excel i używać tabele przestawne, aby wyświetlić wyniki. Należy pamiętać, łączna liczba, rozmiar i dystrybucji alokacji. Porównaj je z rozmiarem zestawów roboczych. Też przyjrzeć klastra o rozmiarze powiązane obiekty.  
  
 Umożliwia także liczniki wydajności do monitorowania użycia pamięci.  
  
##  <a name="_core_threads"></a> Wątki  
 Dla zadania w tle skutecznego bezczynności obsługi zdarzeń może być szybsza niż przy użyciu wątków. Jest łatwiejsze do zrozumienia miejscowości odwołania w programie jednowątkowy.  
  
 Regułą polega na użyciu wątku, tylko wtedy, gdy wiadomość z powiadomieniem systemu operacyjnego, który zostanie zablokowany na jest w katalogu głównym Praca w tle. Wątki są najlepsze rozwiązania w takim przypadku, ponieważ jest niemożliwe do blokowania wątku głównego na zdarzenia.  
  
 Wątki stanowi również problemy z komunikacją. Należy zarządzać łącza komunikacyjnego między wątkami, na listę komunikatów lub przydzielając i przy użyciu pamięci współużytkowanej. Zarządzanie łącza komunikacyjnego zwykle wymaga synchronizacji, aby uniknąć wyścigu i zakleszczenie problemów. Ta złożoności można łatwo przekształcić błędy i problemy z wydajnością.  
  
 Aby uzyskać więcej informacji, zobacz [przetwarzanie pętli bezczynności](../../mfc/idle-loop-processing.md) i [Multithreading](../../parallel/multithreading-support-for-older-code-visual-cpp.md).  
  
##  <a name="_core_small_working_set"></a> Zestaw roboczy małe  
 Mniejszych zestawów roboczych oznaczają lepszą miejscowości odwołania, mniejszej liczby błędów stron i więcej trafień w pamięci podręcznej. Zestaw roboczy procesu to najbliższego metrykę, które bezpośrednio zapewnia system operacyjny do pomiaru miejscowości odwołania.  
  
-   Aby ustawić górny i dolny limit zestawu roboczego, użyj [SetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms683226.aspx).  
  
-   Aby uzyskać górny i dolny limit zestawu roboczego, użyj [GetProcessWorkingSetSize](http://msdn.microsoft.com/library/windows/desktop/ms686234.aspx).  
  
-   Aby wyświetlić rozmiar zestawu roboczego, użyj narzędzia Spy ++.  
  
## <a name="see-also"></a>Zobacz też  
 [Optymalizacja kodu](../../build/reference/optimizing-your-code.md)