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
ms.openlocfilehash: 081c8b46d03abf8257cc9bea642db93918f97429
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536945"
---
# <a name="tips-for-improving-time-critical-code"></a>Wskazówki dotyczące poprawiania kodu wrażliwego na czas

Pisanie kodu szybkiego wymaga zrozumienia wszystkich aspektów aplikacji i sposób jej interakcji z systemu. W tym temacie sugeruje alternatywy dla niektórych bardziej oczywisty technik kodowania, które pomagają zagwarantować pomyślnie wykonać czas ma istotne znaczenie fragmenty kodu.

Aby podsumować, poprawiania kodu wrażliwego na czas wymaga, aby użytkownik:

- Znać części programu, które muszą być szybko.

- Wiadomo, rozmiar i prędkość kodu.

- Wiadomo, koszt nowych funkcji.

- Wiadomo, minimalna pracy wymaganej do wykonania zadania.

Aby zebrać informacje na temat wydajności kodu, można użyć Monitora wydajności (perfmon.exe).

## <a name="sections-in-this-article"></a>Sekcje w tym artykule

- [Chybienia w pamięci podręcznej i błędów stron](#_core_cache_hits_and_page_faults)

- [Sortowanie i wyszukiwanie](#_core_sorting_and_searching)

- [MFC i bibliotek klas](#_core_mfc_and_class_libraries)

- [Biblioteki udostępnione](#vcovrsharedlibraries)

- [Stert](#_core_heaps)

- [Wątki](#_core_threads)

- [Rozmiar zestawu roboczego małych](#_core_small_working_set)

##  <a name="_core_cache_hits_and_page_faults"></a> Chybienia w pamięci podręcznej i błędów stron

Pominięte trafień w pamięci podręcznej, w obu wewnętrznych i zewnętrznych pamięci podręcznej, a także błędów strony (zgodnie z ruchem do magazynu pomocniczego dla danych i instrukcje programu) spowolnienie działania programu.

Trafienie w pamięci podręcznej Procesora mogą kosztować program 10-20 cykli zegara. Trafienie w pamięci podręcznej zewnętrznych mogą kosztować cykle zegara 20 – 40. Błąd strony mogą kosztować cykle zegara jeden milion (zakładając, że procesora, który obsługuje 500 milionów instrukcje na sekundę i czas 2 milisekund błąd strony). Dlatego jest w najlepszym interesie wykonywania programu, aby napisać kod, który spowoduje zmniejszenie liczby trafień w pamięci podręcznej brakujących i błędów stron.

Jednym z powodów powolne programów jest wykonać więcej błędów stron lub przeoczyć pamięci podręcznej częściej niż to konieczne. Aby tego uniknąć, należy używać struktury danych z dobrą miejscowości odwołania, co oznacza, że elementy powiązane ze sobą. Czasami struktury danych, która wygląda bardzo okaże się horrible ze względu na słabe miejscowość odwołania, a następnie czasem odwrotna ma wartość true. Poniżej przedstawiono dwa przykłady:

- Przydzielany dynamicznie połączonej listy może zmniejszyć wydajność programu, ponieważ podczas wyszukiwania elementu lub przechodzenie przez listę do końca, każde łącze pominięto można pamięci podręcznej pominąć lub spowodować błąd strony. Implementacja list, oparte na macierzach proste faktycznie może być znacznie szybciej ze względu na lepsze buforowania i mniej błędów stron nawet — zezwalanie na fakt, że tablicy byłoby trudniejsze rozwoju, nadal może być szybsze.

- Tabel skrótów, które używają przydzielany dynamicznie połączonej listy mogą obniżyć wydajność. Przy użyciu rozszerzenia, tabele zbędnych danych, korzystające z dynamicznie przydzielonego połączonej listy do przechowywania ich zawartość mogą wykonywać znacznie niższa. W rzeczywistości w ostatecznym rozrachunku prostego wyszukiwania liniowego tablicy może mieć w rzeczywistości szybciej (w zależności od sytuacji). Tabele na podstawie tablicy skrótów (tak zwane "zamknięte wyznaczania wartości skrótu") jest często pomijane wdrożenia, który często ma doskonałą wydajność.

##  <a name="_core_sorting_and_searching"></a> Sortowanie i wyszukiwanie

Sortowanie jest natury dużo czasu w porównaniu do wielu typowych operacji. Najlepszym sposobem uniknięcia spowolnienia niepotrzebne jest uniknąć sortowania przez czas krytycznych. Może mieć możliwość:

- Odrocz sortowanie do czasu niekrytyczne — wydajność.

- Sortowanie danych w momencie wcześniej, niż newralgicznym dla wydajności.

- Sortowanie tylko część danych, które naprawdę potrzebuje sortowania.

Czasami możesz utworzyć listę w kolejności posortowanej. Ostrożność, ponieważ jeśli potrzebujesz wstawić dane w kolejności posortowanej, mogą wymagać bardziej złożone struktury danych z niską miejscowość odniesienia, co prowadzi do chybień pamięci podręcznej i błędów stron. Nie istnieje żadne podejście, które działa we wszystkich przypadkach. Wypróbuj różne podejścia i mierzyć różnice.

Poniżej przedstawiono pewne ogólne porady dotyczące sortowania:

- Użyj standardowych sortowania, aby zminimalizować błędy.

- Wszelkie prace, które można wykonać wcześniej uproszczeniu sortowania jest cenna. Jeśli jednorazowe — dostęp próbny danych upraszcza porównania i zmniejsza sortowanie od O (n log n), aby O(n), należy prawie na pewno pojawią wyprzedzeniem.

- Pomyśl o miejscowość odwołania do algorytmu sortowania i danych, jego uruchomienie na oczekiwane.

Istnieją mniej alternatyw wyszukuje niż sortowanie. W przypadku wrażliwego na czas wyszukiwania binarnego wyszukiwania tabeli wyszukiwania lub skrót prawie zawsze najlepiej jest, ale podobnie jak w przypadku sortowania, miejscowość muszą należy pamiętać. Wykonywanie wyszukiwania liniowego za pośrednictwem małą tablicę mogą być szybciej niż binarny przeszukiwania struktury danych z dużą wskaźników, która powoduje występowanie błędów stron lub liczba chybień pamięci podręcznej.

##  <a name="_core_mfc_and_class_libraries"></a> MFC i bibliotek klas

Microsoft Foundation Classes (MFC) znacznie ułatwia pisanie kodu. Podczas pisania kodu wrażliwego na czas, należy pamiętać o obciążenie związane z niektórych klas. Sprawdź kod MFC, który używa kodu wrażliwego na czas, aby sprawdzić, czy spełnia ono wymagań dotyczących wydajności. Poniższa lista zawiera klasy MFC i funkcje, których należy wiedzieć:

- `CString` MFC wywołuje bibliotekę wykonawczą C można przydzielić pamięci dla [CString](../../atl-mfc-shared/reference/cstringt-class.md) dynamicznie. Ogólnie rzecz biorąc `CString` jest wydajne niż inny ciąg przydzielany dynamicznie. Podobnie jak w przypadku dowolnego dynamicznie przydzielonej ciągu ma obciążenie dynamicznej alokacji i wydania. Często prostego `char` tablicy na stosie może obsługiwać ten sam cel i jest szybsze. Nie używaj `CString` do przechowywania stałym ciągiem. Zamiast nich należy używać słów kluczowych `const char *`. Wszelkie operacje, możesz wykonać za pomocą `CString` obiekt ma pewne nadmiarowe obciążenie. Za pomocą biblioteki wykonawczej [ciągów funkcji](../../c-runtime-library/string-manipulation-crt.md) może przebiegać szybciej.

- `CArray` A [CArray](../../mfc/reference/carray-class.md) zapewnia elastyczność nie regularne tablicy, że program nie może być potrzebna. Jeśli znasz określone limity dla tablicy, możesz zamiast tego użyj globalnej tablicy stały. Jeśli używasz `CArray`, użyj `CArray::SetSize` jej rozmiaru i określ liczbę elementów, według których rośnie, gdy konieczne jest ponowne przydzielenie. W przeciwnym razie dodanie elementów może spowodować macierz często ponownie przydzielane i skopiowana, który jest nieefektywne i może fragmentu pamięci. Należy także zauważyć, że jeśli Wstawianie elementu do tablicy, `CArray` przenosi kolejnych elementów w pamięci i może być konieczne zwiększenie tablicy. Te akcje może spowodować Chybienia pamięci podręcznej i błędów stron. Podczas przeglądania przez kod, który używa MFC, może zostać wyświetlony, można napisać bardziej szczegółowa do danego scenariusza, aby zwiększyć wydajność. Ponieważ `CArray` jest szablonem, na przykład można określić `CArray` specjalizacje dla określonych typów.

- `CList` [CList](../../mfc/reference/clist-class.md) jest podwójnie połączoną listą, więc szybko na czele, wstawianie elementu uchwyt, a pozycja znanych (`POSITION`) na liście. Trwa wyszukiwanie elementu według wartości lub indeksu wymaga sekwencyjne wyszukiwania, jednak może być powolne, jeśli lista jest długa. Jeśli Twój kod nie wymaga podwójnie połączoną listą warto powierzeniem `CList`. Za pomocą pojedynczo połączoną listą zapisuje obciążenie aktualizowania dodatkowe wskaźnik dla wszystkich operacji, a także pamięci dla tego wskaźnika. Dodatkowa pamięć nie jest doskonały, ale jest inny możliwość Chybienia pamięci podręcznej lub błędów stron.

- `IsKindOf` Ta funkcja może wygenerować wiele wywołań i dostęp do dużej ilości pamięci w obszarach danych, co prowadzi do miejscowość nieprawidłowe odwołania. Jest przydatne w przypadku kompilacji debugowania (w wywołaniu POTWIERDZEŃ, na przykład), ale Staraj się unikać korzystania z niego w kompilacji wydania.

- `PreTranslateMessage` Użyj `PreTranslateMessage` podczas określonego drzewa systemu windows wymaga różnych klawiszy skrótów lub należy wstawić obsługi wiadomości do "pompy komunikatów". `PreTranslateMessage` Zmienia MFC wysyłania wiadomości. Jeśli zastąpisz `PreTranslateMessage`, więc tylko na poziomie potrzebne. Na przykład nie jest konieczne zastąpić `CMainFrame::PreTranslateMessage` Jeśli interesuje Cię tylko komunikaty przechodzące z określonym widokiem elementami podrzędnymi. Zastąp `PreTranslateMessage` widoku klasy zamiast tego.

   Obchodzi ścieżki normalne wysyłania za pomocą `PreTranslateMessage` każdy komunikat wysyłany do dowolnego okna obsługi. Użyj [procedury okna](../../mfc/registering-window-classes.md) i mapy wiadomości MFC do tego celu.

- `OnIdle` Zdarzenia bezczynności może wystąpić w czasie nie będzie, takie jak między `WM_KEYDOWN` i `WM_KEYUP` zdarzenia. Czasomierze może być bardziej efektywne sposobem wyzwalać Twój kod. Nie wymuszaj `OnIdle` wywoływany wielokrotnie, generując fałszywe komunikaty lub zawsze zwracając `TRUE` z zastąpieniem `OnIdle`, co umożliwiłoby wątek w stan uśpienia. Ponownie czasomierz lub w oddzielnym wątku może być bardziej odpowiednie.

##  <a name="vcovrsharedlibraries"></a> Biblioteki udostępnione

Ponowne wykorzystanie kodu jest pożądane. Jednak jeśli zamierzasz użyć kodu innej osoby, powinien upewnij się, że wiesz, że dokładnie co robi w przypadkach, gdzie wydajność ma kluczowe znaczenie, do Ciebie. Najlepszym sposobem zrozumienia to jest poprzez krokowe wykonywanie kodu źródłowego lub przez dokonywanie pomiarów przy użyciu narzędzi, takich jak PView lub monitora wydajności.

##  <a name="_core_heaps"></a> Stert

Za pomocą wielu sterty na własne ryzyko. Dodatkowe stosów utworzonych za pomocą `HeapCreate` i `HeapAlloc` umożliwiają zarządzanie, a następnie usunąć powiązany zestaw alokacji. Nie należy zatwierdzić zbyt dużej ilości pamięci. Jeśli używasz wielu sterty, należy zwrócić szczególną uwagę na ilość pamięci, która jest początkowo zatwierdzone.

Zamiast kilku stert można użyć funkcji pomocnika interfejsu między kodu i domyślnej sterty. Funkcje pomocnicze ułatwienia strategii alokacji niestandardowych, które może poprawić wydajność aplikacji. Na przykład jeśli alokacje małych często wykonywane, może być do zlokalizowania tych środków do jednej części stosu domyślnego. Można przydzielić dużych bloków pamięci, a następnie użyj funkcji pomocnika do podrzędnej z tego bloku. Jeśli to zrobisz, nie będziesz mieć dodatkowe stert za pomocą nieużywanej pamięci, ponieważ alokacja wystawała z domyślnej sterty.

W niektórych przypadkach jednak przy użyciu domyślnej sterty można zmniejszyć miejscowość odwołania. Użyj podglądu procesu, narzędzie Spy ++ lub monitora wydajności do mierzenia wpływ przenoszenia obiektów sterty sterty.

Zmierz swojej sterty, więc konta na potrzeby każdej alokacji, na stosie. Użyj środowiska wykonawczego języka C [procedury stosu debugowania](/visualstudio/debugger/crt-debug-heap-details) do punktu kontrolnego i zrzutu swojej sterty. Może odczytywać dane wyjściowe do arkusza kalkulacyjnego programu, np. Microsoft Excel i użyj tabele przestawne, aby wyświetlić wyniki. Należy pamiętać, łączna liczba, rozmiar i dystrybucji alokacji. Porównaj je z rozmiarem zestawów roboczych. Również Sprawdź klastra o rozmiarze powiązanych obiektów.

Liczniki wydajności można również użyć do monitorowania wykorzystania pamięci.

##  <a name="_core_threads"></a> Wątki

Zadania w tle skutecznego bezczynności obsługi zdarzeń może być szybsza niż przy użyciu wątków. Jest to łatwiejsze do zrozumienia miejscowość odwołania w programie apartamentem.

Regułą jest użycie wątku, tylko wtedy, gdy wiadomość z powiadomieniem systemu operacyjnego, który możesz zablokować na głównym pracę w tle. Wątki są najlepszym rozwiązaniem w takiej sytuacji, ponieważ jest to niepraktyczne blokowania wątku głównego na zdarzenie.

Wątki także prezentować problemy z komunikacją. Można zarządzać łącza komunikacyjnego między wątki, za pomocą listy komunikatów lub przydzielając i używanie udostępnionej pamięci. Zarządzanie łącza komunikacyjnego, zwykle wymaga synchronizacji, aby uniknąć wyścigu i zakleszczenie problemów. Tę złożoność można łatwo przekształcić usterki i problemy z wydajnością.

Aby uzyskać więcej informacji, zobacz [przetwarzanie pętli bezczynności](../../mfc/idle-loop-processing.md) i [wielowątkowość](../../parallel/multithreading-support-for-older-code-visual-cpp.md).

##  <a name="_core_small_working_set"></a> Rozmiar zestawu roboczego małych

Mniejszych zestawów roboczych oznacza miejscowość lepsze odwołania, mniejszą liczbę błędów stron i więcej trafień w pamięci podręcznej. Zestaw roboczy procesu to najbliższy metryki, udostępnia systemu operacyjnego bezpośrednio do pomiaru miejscowość odwołania.

- Aby ustawić górny i dolny limit zestawu roboczego, użyj [SetProcessWorkingSetSize](/windows/desktop/api/winbase/nf-winbase-getprocessworkingsetsize).

- Aby uzyskać górny i dolny limit zestawu roboczego, użyj [GetProcessWorkingSetSize](/windows/desktop/api/winbase/nf-winbase-setprocessworkingsetsize).

- Aby wyświetlić rozmiar zestawu roboczego, użyj programu Spy ++.

## <a name="see-also"></a>Zobacz też

[Optymalizacja kodu](../../build/reference/optimizing-your-code.md)