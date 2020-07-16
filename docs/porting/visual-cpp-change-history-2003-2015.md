---
title: Visual C++ — historia zmian w latach 2003–2015
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: 51de46487d85f4b8d7d357a0d1842f3d3192fff7
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404798"
---
# <a name="visual-c-change-history-2003---2015"></a>Visual C++ — historia zmian w latach 2003–2015

W tym artykule opisano wszystkie istotne zmiany z programu Visual Studio 2015 z powrotem do programu Visual Studio 2003, a w tym artykule podano warunki "nowe zachowanie" lub "teraz" odnoszą się do programu Visual Studio 2015 i nowszych. Warunki "stare zachowanie" i "przed" odnoszą się do Visual Studio 2013 i wcześniejszych wersji.

Aby uzyskać informacje o najnowszej wersji programu Visual Studio, zobacz [Nowości dotyczące Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodności w Visual C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

> [!NOTE]
> Między programem Visual Studio 2015 i Visual Studio 2017 nie są istotne żadne zmiany binarne.

Po uaktualnieniu do nowej wersji programu Visual Studio mogą wystąpić błędy kompilacji i/lub środowiska uruchomieniowego w kodzie, który został wcześniej skompilowany i prawidłowo uruchomiony. Zmiany w nowej wersji, które powodują takie problemy, są znane jako istotne *zmiany*i zwykle są wymagane przez modyfikacje w standardzie języka C++, podpisy funkcji lub układ obiektów w pamięci.

Aby uniknąć błędów czasu wykonywania, które są trudne do wykrycia i zdiagnozowania, zalecamy, aby nigdy nie łączyć się statycznie z plikami binarnymi skompilowanymi przy użyciu innej wersji kompilatora. Ponadto, gdy uaktualniasz projekt EXE lub DLL, upewnij się, że uaktualniasz również biblioteki, z którymi się on łączy. Nie należy przekazywać typów CRT (C Runtime) ani standardowej biblioteki C++ (standardowa biblioteka C++) między plikami binarnymi, łącznie z bibliotekami DLL, skompilowanymi przy użyciu różnych wersji kompilatora. Aby uzyskać więcej informacji, zobacz [potencjalne błędy podczas przekazywania obiektów CRT między granicami bibliotek DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Nie należy pisać kodu, który zależy od określonego układu dla obiektu, który nie jest interfejsem COM ani obiektem POD. Jeśli jednak piszesz taki kod, upewnij się, że działa po uaktualnieniu. Aby uzyskać więcej informacji, zobacz [przenośność na granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Ponadto ciągłe ulepszenia zgodności kompilatora mogą czasami zmienić sposób, w jaki kompilator rozumie istniejący kod źródłowy. Na przykład można znaleźć nowe lub inne błędy podczas kompilacji, a nawet różnice w zachowaniu kodu, które wcześniej zostały skompilowane i były prawidłowo wykonywane. Chociaż te udoskonalenia nie powodują znaczących zmian, jak te omówione w tym dokumencie, może być konieczne wprowadzenie zmian w kodzie źródłowym w celu rozwiązania tych problemów:

- [Zmiany w bibliotece środowiska uruchomieniowego języka C (CRT)](#BK_CRT)

- [Standardowe zmiany standardowej biblioteki C++ i C++](#BK_STL)

- [Zmiany w przypadku MFC i ATL](#BK_MFC)

- [środowisko uruchomieniowe współbieżności istotne zmiany](#BK_ConcRT)

## <a name="visual-studio-2015-conformance-changes"></a><a name="VC_2015"></a>Zmiany zgodności programu Visual Studio 2015

### <a name="c-runtime-library-crt"></a><a name="BK_CRT"></a>Biblioteka środowiska uruchomieniowego języka C (CRT)

#### <a name="general-changes"></a>Ogólne zmiany

- **Refaktoryzacja plików binarnych**

   Biblioteka CRT została przemieszczona w dwóch różnych plikach binarnych: uniwersalnej CRT (ucrtbase), która zawiera większość standardowych funkcji i bibliotekę środowiska uruchomieniowego VC (vcruntime). Biblioteka vcruntime zawiera funkcje związane z kompilatorem, takie jak obsługa wyjątków i wewnętrzne. Jeśli używasz domyślnych ustawień projektu, ta zmiana nie wpłynie na Ciebie, ponieważ konsolidator automatycznie użyje nowych bibliotek domyślnych. Jeśli ustawisz właściwość **konsolidatora** projektu **Ignoruj wszystkie domyślne biblioteki** na **tak** lub używasz `/NODEFAULTLIB` opcji konsolidatora w wierszu polecenia, musisz zaktualizować listę bibliotek (we właściwościach **dodatkowych zależności** ), aby uwzględnić nowe, odczynnikowe biblioteki. Zastąp starą bibliotekę CRT (libcmt. lib, libcmtd. lib, msvcrt. lib, msvcrtd. lib) przy użyciu równoważnych bibliotek refaktoryzacji. Dla każdej z dwóch bibliotek z replikami są dostępne statyczne (. lib) i dynamiczne (. dll) wersje oraz wydanie (bez sufiksu) i wersje debug (z sufiksem "d"). Wersje dynamiczne mają przyłączone biblioteki importu. Dwie biblioteki refaktoryzacjowe to uniwersalne CRT, w tym ucrtbase.dll, ucrtbase. lib, ucrtbased.dll lub biblioteka ucrtbased. lib oraz biblioteka środowiska uruchomieniowego VC, libvcruntime. lib, vcruntime*Version*. dll, libvcruntimed. lib i vcruntimed*Version*. dll. *Wersja* zarówno programu visual Studio 2015, jak i visual Studio 2017 to 140. Zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

#### \<locale.h>

- **localeconv**

   Funkcja [localeconv](../c-runtime-library/reference/localeconv.md) zadeklarowana w ustawieniach regionalnych. h teraz działa prawidłowo, gdy włączone są [Ustawienia regionalne dla wątku](../parallel/multithreading-and-locales.md) . W poprzednich wersjach biblioteki ta funkcja zwróci `lconv` dane dla globalnych ustawień regionalnych, a nie ustawień regionalnych wątku.

   Jeśli używasz ustawień regionalnych dla wątków, sprawdź, czy używasz programu `localeconv` . Jeśli kod założono, że `lconv` zwrócone dane są dla globalnych ustawień regionalnych, należy je poprawić.

#### \<math.h>

- **Przeciążenia C++ funkcji biblioteki matematycznej**

   W poprzednich wersjach \<math.h> zdefiniowane niektóre, ale nie wszystkie, z przeciążeń języka C++ dla funkcji biblioteki matematycznej. Pozostałe przeciążenia znajdowały się w \<cmath> nagłówku. Tylko dołączony kod \<math.h> może mieć problemy z rozpoznawaniem przeciążenia funkcji. Teraz przeciążenia języka C++ zostały usunięte z programu \<math.h> i są dostępne tylko w \<cmath> .

   Aby rozwiązać błędy, Dołącz \<cmath> do pobrania deklaracji funkcji, z których zostały usunięte \<math.h> . Te funkcje zostały przeniesione:

  - `double abs(double)` i `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float`i `long double` wersje funkcji zmiennoprzecinkowych `acos` , `acosh` ,, `asin` `asinh` `atan` `atanh` `atan2` `cbrt` `ceil` `copysign` `cos` `cosh` `erf` `erfc` `exp` `exp2` `expm1` `fabs` `fdim` `floor` `fma` `fmax` `fmin` `fmod` `frexp` `hypot` `ilogb` `ldexp` `lgamma` `llrint` `llround` `log` `log10` `log1p` `log2` `lrint` `lround` `modf` `nearbyint` `nextafter` `nexttoward` `remainder` `remquo` `rint` `round` `scalbln` `scalbn` `sin` `sinh` `sqrt` `tan` `tanh` ,,,, `tgamma` ,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,,, i`trunc`

  Jeśli masz kod, który używa `abs` dla typu zmiennoprzecinkowego, który zawiera tylko \<math.h> nagłówek, wersje zmiennoprzecinkowe nie będą już dostępne. Wywołanie teraz jest rozpoznawane jako `abs(int)` , nawet w przypadku argumentu zmiennoprzecinkowego, który powoduje błąd:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Poprawka dla tego ostrzeżenia polega na zastępowaniu wywołania do `abs` wersji zmiennoprzecinkowej `abs` , takiej jak `fabs` dla argumentu Double lub `fabsf` argumentu zmiennoprzecinkowego, lub dołączenia \<cmath> nagłówka i nadal używać `abs` .

- **Zgodność zmiennoprzecinkowa**

   Wprowadzono wiele zmian w bibliotece matematycznej w celu poprawienia zgodności z specyfikacjami w języku IEEE-754 i C11, w odniesieniu do specjalnych danych wejściowych przypadku, takich jak NaNs i nieskończoności. Na przykład ciche dane wejściowe NaN, które często były traktowane jako błędy w poprzednich wersjach biblioteki, nie są już traktowane jako błędy. Zobacz [IEEE 754 Standard](https://standards.ieee.org/standard/754-2008.html) i załącznik F [standardu C11](https://www.iso.org/standard/57853.html).

   Te zmiany nie powodują błędów w czasie kompilacji, ale mogą powodować, że programy działają inaczej i bardziej prawidłowo zgodnie ze standardem.

- **FLT_ROUNDS**

   W Visual Studio 2013, makro FLT_ROUNDS rozwinięte na wyrażenie stałe, które było nieprawidłowe, ponieważ tryb zaokrąglania jest konfigurowalny w czasie wykonywania, na przykład przez wywołanie fesetround. Makro FLT_ROUNDS jest teraz dynamiczne i poprawnie odzwierciedla bieżący tryb zaokrąglania.

#### <a name="new-and-newh"></a>\<new> i \<new.h>

- **nowe i Usuń**

   W poprzednich wersjach biblioteki funkcje operatora i usuwania zdefiniowane przez implementację zostały wyeksportowane z biblioteki DLL Biblioteka środowiska uruchomieniowego (na przykład msvcr120.dll). Te funkcje operatorów są teraz zawsze statycznie połączone z danymi binarnymi, nawet w przypadku korzystania z bibliotek DLL biblioteki środowiska uruchomieniowego.

   Nie jest to istotna zmiana dla kodu natywnego lub mieszanego ( `/clr` ), jednak kod skompilowany jako [/CLR: Pure](../build/reference/clr-common-language-runtime-compilation.md), ta zmiana może spowodować niepowodzenie kompilowania kodu. Jeśli kompilujesz kod jako `/clr:pure` , może być konieczne dodanie `#include <new>` lub `#include <new.h>` obejście błędów kompilacji ze względu na tę zmianę. `/clr:pure`Opcja jest przestarzała w programie Visual studio 2015 i nieobsługiwana w programie Visual studio 2017. Kod, który musi być "czysty" należy przenieść do języka C#.

#### \<process.h>

- **_beginthread i _beginthreadex**

   Funkcje [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) i [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) zawierają teraz odwołanie do modułu, w którym procedura wątku jest zdefiniowana na czas trwania wątku. Pozwala to zagwarantować, że moduły nie zostaną zwolnione, dopóki wątek nie zostanie uruchomiony do ukończenia.

#### \<stdarg.h>

- **va_start i typy odwołań**

   Podczas kompilowania kodu w języku C++ [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) teraz sprawdza poprawność w czasie kompilacji, do którego argument przeszedł do nie jest typem referencyjnym. Argumenty typu odwołania są zabronione przez standard C++.

#### <a name="stdioh-and-conioh"></a><a name="stdio_and_conio"></a>\<stdio.h>i\<conio.h>

- **Rodzina funkcji printf i scanf jest teraz zdefiniowana jako wbudowana.**

   Definicje wszystkich `printf` funkcji i zostały `scanf` przeniesione wewnętrznie do \<stdio.h> , \<conio.h> i innych nagłówków CRT. Ta przerwana zmiana prowadzi do błędu konsolidatora (LNK2019, nierozpoznany symbol zewnętrzny) dla wszystkich programów, które deklarują te funkcje lokalnie bez uwzględniania odpowiednich nagłówków CRT. Jeśli to możliwe, należy zaktualizować kod w taki sposób, aby zawierał nagłówki CRT (czyli dodać `#include <stdio.h>` ) i funkcje wbudowane, ale jeśli nie chcesz modyfikować kodu w celu uwzględnienia tych plików nagłówkowych, alternatywnym rozwiązaniem jest dodanie dodatkowej biblioteki do danych wejściowych konsolidatora, legacy_stdio_definitions. lib.

   Aby dodać tę bibliotekę do danych wejściowych konsolidatora w środowisku IDE, otwórz menu kontekstowe dla węzła projektu, wybierz **Właściwości**, a następnie w oknie dialogowym **właściwości projektu** wybierz **konsolidator**i edytuj **dane wejściowe konsolidatora** , aby dodać je `legacy_stdio_definitions.lib` do listy rozdzielanej średnikami.

   Jeśli projekt łączy się z bibliotekami statycznymi, które zostały skompilowane z wersją programu Visual Studio wcześniejszą niż 2015, konsolidator może zgłosić nierozpoznany symbol zewnętrzny. Te błędy mogą odwoływać się do definicji wewnętrznych dla `_iob` , `_iob_func` lub związanych z nimi Importy dla niektórych \<stdio.h> funkcji w postaci _IMP_ \* . Firma Microsoft zaleca, aby ponownie skompilować wszystkie biblioteki statyczne przy użyciu najnowszej wersji kompilatora i bibliotek języka C++ podczas uaktualniania projektu. Jeśli biblioteka jest biblioteką innej firmy, dla której źródło nie jest dostępne, należy zażądać zaktualizowanego pliku binarnego od innej firmy lub hermetyzować użycie tej biblioteki w oddzielnym pliku DLL, który można skompilować przy użyciu starszej wersji kompilatora i bibliotek.

    > [!WARNING]
    > W przypadku łączenia się z Windows SDK 8,1 lub starszymi można napotkać nierozwiązane błędy symboli zewnętrznych. W takim przypadku należy rozwiązać ten problem, dodając legacy_stdio_definitions. lib do danych wejściowych konsolidatora zgodnie z wcześniejszym opisem.

   Aby rozwiązać problemy z nierozwiązanymi błędami symboli, można spróbować użyć [dumpbin.exe](../build/reference/dumpbin-reference.md) , aby sprawdzić symbole zdefiniowane w danych binarnych. Spróbuj użyć następującego wiersza polecenia, aby wyświetlić symbole zdefiniowane w bibliotece.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **Pobiera i _getws**

   Funkcje [Get](../c-runtime-library/gets-getws.md) i [_getws](../c-runtime-library/gets-getws.md) zostały usunięte. Funkcja Get została usunięta z standardowej biblioteki języka C w C11, ponieważ nie można jej użyć bezpiecznie. Funkcja _getws była rozszerzeniem firmy Microsoft, które było równoważne pobieraniu, ale dla szerokich ciągów. Jako alternatywy dla tych funkcji Rozważ użycie [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md)i [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets i _cgetws**

   Funkcje [_cgets](../c-runtime-library/cgets-cgetws.md) i [_cgetws](../c-runtime-library/cgets-cgetws.md) zostały usunięte. Jako alternatywy dla tych funkcji Rozważ użycie [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) i [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Nieskończoność i NaN — formatowanie**

   W poprzednich wersjach nieskończoności i NaNs zostałyby sformatowane przy użyciu zestawu ciągów wskaźnikowych specyficznych dla MSVC.

  - Nieskończoność: 1. #INF

  - Cichy NaN: 1. #QNAN

  - Sygnalizowanie NaN: 1. #SNAN

  - Nieokreślony NaN: 1. #IND

  Wszystkie te formaty mogły być poprzedzone znakiem i mogą być sformatowane nieco inaczej w zależności od szerokości pola i precyzji (czasami z nietypowymi skutkami, na przykład `printf("%.2f\n", INFINITY)` wydrukować 1. #J, ponieważ #INF być "zaokrąglona" do 2-cyfrową precyzją). C99 wprowadził nowe wymagania dotyczące sposobu formatowania nieskończoności i NaNs. Implementacja MSVC jest teraz zgodna z tymi wymaganiami. Nowe ciągi są następujące:

  - Nieskończoność: inf

  - Cichy NaN: NaN

  - Sygnalizowanie NaN: NaN (sNaN)

  - Nieokreślony NaN: NaN (IND)

  Dowolne z nich może być poprzedzone znakiem. Jeśli jest używany specyfikator formatu wielką literą (% F zamiast% f), ciągi są drukowane w postaci wersalików ( `INF` zamiast `inf` ), zgodnie z potrzebami.

  Funkcje [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) zostały zmodyfikowane w celu przeanalizowania tych nowych ciągów, więc te ciągi są teraz rundy `printf` i `scanf` .

- **Formatowanie zmiennoprzecinkowe i analizowanie**

   Wprowadzono nowe algorytmy formatowania i analizy zmiennoprzecinkowe w celu poprawienia poprawności. Ta zmiana ma wpływ na rodzinę [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkcji, a także funkcje, takie jak [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Starego algorytmu formatowania spowoduje wygenerowanie tylko ograniczonej liczby cyfr, a następnie wypełnienie pozostałych miejsc dziesiętnych wartością zero. Zazwyczaj mogą generować ciągi, które będą przenoszone z powrotem do pierwotnej wartości zmiennoprzecinkowej, ale nie były wspaniałe, jeśli potrzebujesz dokładnej wartości (lub najbliższej reprezentacji dziesiętnej). Nowe algorytmy formatowania generują dowolną liczbę cyfr, ile jest wymaganych do reprezentowania wartości (lub aby wypełnić określoną precyzję). Przykładem ulepszeń; należy wziąć pod uwagę wyniki podczas drukowania dużej mocy dwóch:

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   Stare dane wyjściowe:

    ```Output
    1208925819614629200000000
    ```

   Nowe dane wyjściowe:

    ```Output
    1208925819614629174706176
    ```

   Stare algorytmy analizy uwzględniają maksymalnie 17 cyfr znaczących z ciągu wejściowego i odrzucają resztę cyfr. To podejście jest wystarczające do wygenerowania bliskiego przybliżenia wartości reprezentowanej przez ciąg, a wynik jest zwykle blisko prawidłowo zaokrąglonego wyniku. Nowa implementacja traktuje wszystkie obecne cyfry i generuje prawidłowo zaokrąglony wynik dla wszystkich danych wejściowych (długość do 768 cyfr). Ponadto te funkcje mają teraz zastosowanie do trybu zaokrąglania (kontrolowanego przez fesetround).  Jest to potencjalnie nieprzerwana zmiana zachowania, ponieważ funkcje te mogą wyprowadzać różne wyniki. Nowe wyniki są zawsze poprawne niż stare wyniki.

- **Analizowanie liczb zmiennoprzecinkowych szesnastkowych i nieskończonych**

   Algorytmy analizy zmiennoprzecinkowej teraz analizują szesnastkowe ciągi zmiennoprzecinkowe (takie jak wygenerowane przez specyfikatory formatu% a i% printf) oraz wszystkie ciągi nieskończoności i NaN, które są generowane przez `printf` funkcje, zgodnie z powyższym opisem.

- **% A i% dopełnienia zero**

   Specyfikatory formatu% a i% A są sformatowane jako liczba zmiennoprzecinkowa jako szesnastkowy mantysy i binarny wykładnik. W poprzednich wersjach `printf` funkcje byłyby nieprawidłowo wypełnianymi ciągami. Na przykład program `printf("%07.0a\n", 1.0)` drukuje 00x1p + 0, gdzie powinien drukować 0x01p + 0. Ten problem został rozwiązany.

- **% A i% a precyzja**

   Domyślna precyzja% A i% specyfikatorów formatu była 6 we wcześniejszych wersjach biblioteki. Domyślna precyzja to teraz 13 dla zgodności ze standardem C.

   Jest to zachowanie w czasie wykonywania w danych wyjściowych dowolnej funkcji, która używa ciągu formatu z% A lub% a. W starym zachowaniu dane wyjściowe przy użyciu specyfikatora% A mogą być "1.1 A2B3Cp + 111". Teraz dane wyjściowe o tej samej wartości to "1.1 A2B3C4D5E6F7p + 111". Aby uzyskać stare zachowanie, można określić precyzję, na przykład%. 6A. Zobacz [specyfikację precyzji](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Specyfikator% F**

   Format% F/specyfikator konwersji jest teraz obsługiwany. Jest on funkcjonalnie równoważny specyfikatorowi formatu% f, z tą różnicą, że nieskończoności i NaNs są formatowane przy użyciu wielkich liter.

   W poprzednich wersjach implementacja użyta do analizy modyfikatorów F i N AS. To zachowanie z powrotem do wieku segmentów przestrzeni adresowej: Modyfikatory długości zostały użyte do wskazania blisko i zbliżonych wskaźników odpowiednio, jak w przypadku elementu% FP lub% NS. To zachowanie zostało usunięte. Jeśli napotkano element% F, jest on teraz traktowany jako specyfikator formatu% F; w przypadku napotkania elementu% N jest on teraz traktowany jako nieprawidłowy parametr.

- **Formatowanie wykładnika**

   Specyfikatory formatu% e i% E formatują liczbę zmiennoprzecinkową w postaci dziesiętnej mantysy i wykładnika. Specyfikatory formatu% g i% G również formatują cyfry w tym formularzu w niektórych przypadkach. W poprzednich wersjach, CRT zawsze generuje ciągi z wykładnikami z trzema cyframi. Na przykład `printf("%e\n", 1.0)` 1.000000 e + 000, co było nieprawidłowe. C wymaga, aby w przypadku reprezentacji wykładnika przy użyciu tylko jednej lub dwóch cyfr, wydrukować tylko dwie cyfry.

   W programie Visual Studio 2005 dodano przełącznik globalny zgodności: [_set_output_format](../c-runtime-library/set-output-format.md). Program może wywołać tę funkcję z argumentem _TWO_DIGIT_EXPONENT, aby włączyć zgodne drukowanie wykładnika. Zachowanie domyślne zostało zmienione na tryb drukowania wykładnika zgodnego ze standardami.

- **Sprawdzanie poprawności ciągu formatu**

   W poprzednich wersjach `printf` funkcje i w sposób `scanf` dyskretny akceptują wiele nieprawidłowych ciągów formatu, czasami z nietypowymi skutkami. Na przykład% hlhlhld będzie traktowany jako% d. Wszystkie nieprawidłowe ciągi formatu są teraz traktowane jako nieprawidłowe parametry.

- **Sprawdzanie poprawności ciągu trybu fopen**

   W poprzednich wersjach `fopen` Rodzina funkcji w sposób dyskretny zaakceptował kilka nieprawidłowych ciągów trybów, takich jak `r+b+` . Nieprawidłowe ciągi trybu są teraz wykrywane i traktowane jako nieprawidłowe parametry.

- **Tryb _O_U8TEXT**

   Funkcja [_setmode](../c-runtime-library/reference/setmode.md) teraz prawidłowo raportuje tryb dla strumieni otwartych in_O_U8TEXT tryb. W poprzednich wersjach biblioteki może zgłosić takie strumienie jako otwarte w _O_WTEXT.

   Jest to istotna zmiana, jeśli kod interpretuje tryb _O_WTEXT dla strumieni, w których kodowanie to UTF-8. Jeśli aplikacja nie obsługuje UTF_8, należy rozważyć dodanie obsługi tego coraz typowego kodowania.

- **snprintf i vsnprintf**

   Funkcje [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) i [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) są teraz zaimplementowane. Starszy kod często udostępnia definicje wersje makr tych funkcji, ponieważ nie zostały zaimplementowane przez bibliotekę CRT, ale nie są już potrzebne w nowszych wersjach. Jeśli [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) lub [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) jest zdefiniowane jako makro przed dołączeniem \<stdio.h> , kompilacja kończy się niepowodzeniem z błędem wskazującym, gdzie zostało zdefiniowane makro.

   Zwykle rozwiązanie tego problemu polega na usunięciu wszelkich deklaracji `snprintf` lub `vsnprintf` w kodzie użytkownika.

- **tmpnam generuje użyteczne nazwy plików**

   W poprzednich wersjach `tmpnam` `tmpnam_s` funkcje i wygenerowały nazwy plików w katalogu głównym dysku (na przykład \sd3c.). Te funkcje teraz generują użyteczne ścieżki nazw plików w katalogu tymczasowym.

- **Hermetyzacja pliku**

   W poprzednich wersjach pełny typ pliku został zdefiniowany publicznie w \<stdio.h> , więc możliwe jest, aby kod użytkownika mógł dotrzeć do pliku i zmodyfikować jego wewnętrzne elementy. Biblioteka została zmieniona w celu ukrycia szczegółów implementacji. W ramach tej zmiany plik zdefiniowany w programie \<stdio.h> jest teraz typem nieprzezroczystym, a jego elementy członkowskie są niedostępne z zewnątrz samego CRT.

- **_outp i _inp**

   Funkcje [_outp](../c-runtime-library/outp-outpw-outpd.md), [_outpw](../c-runtime-library/outp-outpw-outpd.md), [_outpd](../c-runtime-library/outp-outpw-outpd.md), [_inp](../c-runtime-library/inp-inpw-inpd.md), [_inpw](../c-runtime-library/inp-inpw-inpd.md)i [_inpd](../c-runtime-library/inp-inpw-inpd.md) zostały usunięte.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>, \<malloc.h> i\<sys/stat.h>

- **strtof i wcstof**

   `strtof`Funkcja and `wcstof` nie `errno` została ustawiona na ERANGE, gdy wartość nie była reprezentacja jako zmiennoprzecinkowa. Ten błąd jest specyficzny dla tych dwóch funkcji; `strtod` `wcstod` `strtold` nie dotyczy to funkcji,,, i `wcstold` . Ten problem został rozwiązany i jest to zmiana w czasie wykonywania.

- **Wyrównane funkcje alokacji**

   W poprzednich wersjach, wyrównane funkcje alokacji ( `_aligned_malloc` `_aligned_offset_malloc` itp.) byłyby w trybie dyskretnym akceptowane żądania dla bloku z wyrównaniem 0. Wymagane wyrównanie musi być potęgą liczby dwa, która nie jest równa zero. Żądane wyrównanie wartości 0 jest teraz traktowane jako nieprawidłowy parametr. Ten problem został rozwiązany i jest to zmiana w czasie wykonywania.

- **Funkcje sterty**

   `_heapadd`Funkcje, `_heapset` i `_heapused` zostały usunięte. Te funkcje nie działały od czasu zaktualizowania CRT do korzystania z sterty systemu Windows.

- **smallheap**

   `smallheap`Opcja Link została usunięta. Zobacz [Opcje łącza](../c-runtime-library/link-options.md).

#### \<string.h>

- **wcstok**

   Podpis funkcji został zmieniony tak, `wcstok` aby odpowiadał wymaganiom standardu języka C. W poprzednich wersjach biblioteki podpis tej funkcji był następujący:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Używa wewnętrznego kontekstu dla wątku do śledzenia stanu dla wywołań, tak jak zostało to zrobione `strtok` . Funkcja ma teraz sygnaturę `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)` i wymaga, aby obiekt wywołujący przeszedł jako trzeci argument do funkcji.

   Dodano nową `_wcstok` funkcję ze starym podpisem w celu ułatwienia przenoszenia. Podczas kompilowania kodu w języku C++ jest również wbudowane Przeciążenie o `wcstok` starym podpisie. To przeciążenie jest zadeklarowane jako przestarzałe. W kodzie języka C define_CRT_NON_CONFORMING_WCSTOK może `_wcstok` być używany zamiast `wcstok` .

#### \<time.h>

- **zegar**

   W poprzednich wersjach funkcja [Clock](../c-runtime-library/reference/clock.md) została zaimplementowana przy użyciu interfejsu API systemu Windows [GetSystemTimeAsFileTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). W tej implementacji funkcja Clock była wrażliwa na czas systemowy i w rezultacie nie monotoniczny. Funkcja Clock została ponownie zaimplementowana w warunkach [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) i jest teraz monotoniczny.

- **fstat i _utime**

   W poprzednich wersjach funkcje [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)i [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) obsłużą nieprawidłowy czas letni. Przed Visual Studio 2013 wszystkie te funkcje zostały nieprawidłowo dostosowane do standardowego czasu, tak jakby były w czasie letnim.

   W Visual Studio 2013 problem został rozwiązany w **_statej** części funkcji, ale podobne problemy w rodzinach **fstat** i **_utime** funkcji nie zostały naprawione. Ta częściowa poprawka prowadzi do problemów z powodu niespójności między funkcjami. Rodziny **fstat** i **_utime** funkcje zostały już naprawione, więc wszystkie te funkcje teraz obsługują odpowiednio czas letni i spójny.

- **asctime**

   W poprzednich wersjach funkcja [asctime](../c-runtime-library/reference/asctime-wasctime.md) przystąpi jednocyfrowe dni z zerem wiodącym, na przykład: `Fri Jun 06 08:00:00 2014` . Specyfikacja wymaga, aby te dni były uzupełnione o początkowe miejsce, jak w `Fri Jun  6 08:00:00 2014` . Ten problem został rozwiązany.

- **strftime i wcsftime**

   `strftime`Funkcje i `wcsftime` obsługują teraz% C,% D,% e,% F,% g,% g,% h,% n,% r,% r,% t,% t,% u i specyfikatorów formatu% V. Ponadto Modyfikatory E i O są analizowane, ale ignorowane.

   Specyfikator formatu% c został określony jako generowanie "odpowiedniej daty i godziny przedstawienia" dla bieżących ustawień regionalnych. W ustawieniach regionalnych języka C ta reprezentacja musi być taka sama jak w przypadku `%a %b %e %T %Y` programu, który jest tworzony przez `asctime` . W poprzednich wersjach specyfikator formatu% c jest niepoprawnie sformatowany razy przy użyciu `MM/DD/YY HH:MM:SS` reprezentacji. Ten problem został rozwiązany.

- **timespec i TIME_UTC**

   \<time.h>Nagłówek definiuje teraz `timespec` Typ i `timespec_get` funkcję ze standardu C11. Ponadto makro TIME_UTC, do użytku z `timespec_get` funkcją, jest teraz zdefiniowane. Ta aktualizacja jest istotną zmianą dla kodu, który ma sprzeczną definicję dla dowolnego z tych identyfikatorów.

- **CLOCKS_PER_SEC**

   Makro CLOCKS_PER_SEC jest teraz rozwijane do liczby całkowitej typu `clock_t` , zgodnie z wymaganiami języka C.

#### <a name="c-standard-library"></a><a name="BK_STL"></a>Standardowa biblioteka języka C++

Aby włączyć nowe optymalizacje i kontrole debugowania, implementacja standardowej biblioteki C++ w Visual Studio celowo łamie zgodność binarną między wersjami. W związku z tym gdy używana jest standardowa biblioteka C++, pliki obiektowe i biblioteki statyczne, które są kompilowane przy użyciu różnych wersji, nie mogą być mieszane w jednym pliku binarnym (EXE lub DLL), a obiekty standardowej biblioteki C++ nie mogą być przekazywane między plikami binarnymi, które są kompilowane przy użyciu różnych wersji. Takie mieszanie powoduje błędy konsolidatora dotyczące niezgodności _MSC_VER. (_MSC_VER to makro zawierające wersję główną kompilatora, na przykład 1800 dla Visual Studio 2013.) Ten test nie może wykryć mieszania DLL i nie może wykryć mieszania, które obejmuje program Visual Studio 2008 lub jego wcześniejszą.

- **Pliki dołączane do standardowej biblioteki C++**

   Wprowadzono pewne zmiany w strukturze include w nagłówkach standardowej biblioteki języka C++. Nagłówki standardowej biblioteki języka C++ mogą zawierać siebie nawzajem w nieokreślony sposób. Ogólnie rzecz biorąc, należy napisać swój kod, tak aby uważnie uwzględniał wszystkie nagłówki, których potrzebuje, zgodnie ze standardem C++, i nie polega na tym, które nagłówki standardowej biblioteki C++ obejmują inne nagłówki standardowej biblioteki C++. Sprawia to, że kod jest przenośny między wersjami i platformami. Co najmniej dwie zmiany nagłówka w programie Visual Studio 2015 wpływają na kod użytkownika. Po pierwsze, \<string> nie zawiera już \<iterator> . Druga, \<tuple> teraz deklaruje `std::array` bez uwzględniania wszystkich elementów \<array> , które mogą przerwać kod za pośrednictwem następującej kombinacji konstrukcji kodu: kod ma zmienną o nazwie "Array" i masz dyrektywę Using "używającą przestrzeni nazw std;" i dołączysz nagłówek standardowej biblioteki języka C++ (na przykład), który \<functional> zawiera \<tuple> , który teraz deklaruje `std::array` .

- **steady_clock**

   \<chrono>Implementacja [steady_clock](../standard-library/steady-clock-struct.md) została zmieniona w taki sposób, aby spełniała standardowe wymagania języka C++ dotyczące stałego i monotonicity. `steady_clock`jest teraz oparta na [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) i `high_resolution_clock` jest teraz elementem TypeDef dla `steady_clock` . W związku z tym, w programie Visual Studio `steady_clock::time_point` jest teraz elementem TypeDef dla, `chrono::time_point<steady_clock>` jednak nie jest to konieczne w przypadku innych implementacji.

- **przydzielenie i stała**

   Teraz wymagane jest porównujenie równości/nierówności alokatora, aby akceptować argumenty const po obu stronach. Jeśli Twoje przypisania definiują te operatory w taki sposób,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   Następnie należy je zaktualizować i zadeklarować jako składowe const:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **elementy const**

   Standard C++ zawsze zabrania kontenerów elementów stałych (takich jak Vector \<const T> lub Set \<const T> ). Visual Studio 2013 i wcześniej zaakceptowali takie kontenery. W bieżącej wersji nie można skompilować takich kontenerów.

- **std:: Alokator::d eallocate**

   W Visual Studio 2013 i starszej `std::allocator::deallocate(p, n)` Ignorowanie argumentu przekazaną dla *n*.  Standard C++ zawsze wymagał, aby *n* musi być równy wartości przekazana jako pierwszy argument wywołania, `allocate` które zwróciło *p*. Jednak w bieżącej wersji jest sprawdzana wartość *n* . Kod, który przekazuje argumenty dla *n* , które różnią się od tego, jakie wymagania standardowe mogą ulec awarii w czasie wykonywania.

- **hash_map i hash_set**

   Niestandardowe pliki nagłówkowe \<hash_map> i \<hash_set> są przestarzałe w programie Visual Studio 2015 i zostaną usunięte w przyszłej wersji. Użyj polecenia \<unordered_map> i \<unordered_set> .

- **komparatorów i operator ()**

   Kontenery asocjacyjne ( \<map> rodzina) wymagają teraz, aby ich komparatorów miały operatory wywołania funkcji z wartością stałą. Kompilowanie następującego kodu w deklaracji klasy komparator teraz nie powiodło się:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Aby rozwiązać ten problem, zmień deklarację funkcji na:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **cechy typu**

   Stare nazwy cech typu ze starszej wersji wersji Standard języka C++ zostały usunięte. Zostały one zmienione w języku C++ 11 i zostały zaktualizowane do wartości języka C++ 11 w programie Visual Studio 2015. W poniższej tabeli przedstawiono stare i nowe nazwy.

   |Stara nazwa|Nowa nazwa|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **Uruchom:: any i Launch:: Sync zasad**

   Niestandardowe `launch::any` i `launch::sync` zasady zostały usunięte. Zamiast tego, `launch::any` Użyj `launch:async | launch:deferred` . Dla programu `launch::sync` , użyj `launch::deferred` . Zobacz [Uruchamianie wyliczania](../standard-library/future-enums.md#launch).

#### <a name="mfc-and-atl"></a><a name="BK_MFC"></a>MFC i ATL

- **Microsoft Foundation Classes (MFC)**

   nie jest już uwzględniony w "typowej" instalacji programu Visual Studio z powodu jego dużego rozmiaru. Aby zainstalować MFC, wybierz opcję instalacji **niestandardowej** w Instalatorze programu Visual Studio 2015. Jeśli masz już zainstalowany program Visual Studio 2015, możesz zainstalować MFC, uruchamiając ponownie Instalatora **programu Visual Studio** . Wybierz opcję Instalacja **niestandardowa** , a następnie wybierz **Microsoft Foundation Classes**. Instalację **programu Visual Studio** można uruchomić z poziomu **Panelu sterowania** **programy i funkcje**lub z nośnika instalacyjnego programu.

   Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.

#### <a name="concurrency-runtime"></a><a name="BK_ConcRT"></a>środowisko uruchomieniowe współbieżności

- **Nadaje makro z systemu Windows. h powodujące konflikt z elementem concurrency:: Context:: Yield**

   Środowisko uruchomieniowe współbieżności poprzednio używany `#undef` do dedefiniowania makra Yield, aby uniknąć konfliktów między makrom Yield zdefiniowanym w systemie Windows. h h i `concurrency::Context::Yield` funkcją. Ten `#undef` element został usunięty i dodano nowe niepowodujące konfliktu wywołanie metody [concurrency:: Context:: YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) . Aby obejść konflikty z wynikiem Yield, można zaktualizować kod, aby wywołać `YieldExecution` funkcję, lub ująć `Yield` nazwę funkcji z nawiasami w miejscach wywołania, jak w poniższym przykładzie:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Ulepszenia zgodności kompilatora w programie Visual Studio 2015

Podczas uaktualniania kodu z poprzednich wersji, można również napotkać błędy kompilatora, które wynikają z ulepszeń zgodności wykonanych w programie Visual Studio 2015. Te udoskonalenia nie łamią zgodności binarnej z wcześniejszych wersji programu Visual Studio, ale mogą generować błędy kompilatora, gdy żadne z nich nie zostało emitowane wcześniej. Aby uzyskać więcej informacji, zobacz [Visual C++ nowości od 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

W programie Visual Studio 2015 ciągłe ulepszenia zgodności kompilatora mogą czasami zmienić sposób, w jaki kompilator rozumie istniejący kod źródłowy. W związku z tym mogą wystąpić nowe lub inne błędy podczas kompilacji, a nawet różnice w kodzie, które wcześniej zostały skompilowane i były prawidłowo wykonywane.

Na szczęście te różnice mają niewielki wpływ na większość kodu źródłowego. Gdy kod źródłowy lub inne zmiany są konieczne w celu rozwiązania tych różnic, poprawki będą małe i proste do przodu. Dodaliśmy wiele przykładów wcześniej akceptowalnego kodu źródłowego, który może wymagać zmiany *(przed)* i poprawek w celu ich skorygowania *(po)*.

Chociaż różnice te mogą mieć wpływ na kod źródłowy lub inne artefakty kompilacji, nie wpływają na zgodność binarną między aktualizacjami wersji programu Visual Studio. Istotna *zmiana* jest bardziej poważniejsza i może mieć wpływ na zgodność binarną, ale te rodzaje binarnych podziałów zgodności występują tylko między głównymi wersjami programu Visual Studio, na przykład między Visual Studio 2013 i Visual Studio 2015. Aby uzyskać informacje na temat istotnych zmian, które wystąpiły między Visual Studio 2013 a programem Visual Studio 2015, zobacz [zmiany zgodności programu Visual studio 2015](#VC_2015).

- [Ulepszenia zgodności w programie Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodności w aktualizacji Update 1](#VS_Update1)

- [Ulepszenia zgodności w aktualizacji Update 2](#VS_Update2)

- [Ulepszenia zgodności w aktualizacji Update 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a>Ulepszenia zgodności w programie Visual Studio 2015

- /Zc: forScope — opcja

   Opcja kompilatora `/Zc:forScope-` jest przestarzała i zostanie usunięta w przyszłej wersji.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Zazwyczaj ta opcja została użyta w celu zezwalania na niestandardowy kod, który używa zmiennych pętli po punkcie, gdzie, zgodnie ze standardem, powinny znajdować się poza zakresem. Jest to konieczne tylko wtedy, gdy skompilowano z `/Za` opcją, ponieważ bez `/Za` , użycie dla zmiennej pętli for jest zawsze dozwolone. Jeśli nie chcesz zachować zgodności ze standardami (na przykład jeśli kod nie jest przeznaczony do użytku przenośnego z innymi kompilatorami), możesz wyłączyć `/Za` opcję (lub ustawić właściwość **Wyłącz rozszerzenia językowe** na wartość **nie**). Jeśli chcesz zadbać o pisanie kodu przenośnego, zgodnego ze standardami, należy ponownie napisać kod, aby był zgodny ze standardem poprzez przeniesienie deklaracji takich zmiennych do punktu poza pętlą.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg`Opcja kompilatora

   `/Zg`Opcja kompilatora (Generuj prototypy funkcji) nie jest już dostępna. Ta opcja kompilatora była wcześniej przestarzała.

- Nie można już uruchamiać testów jednostkowych przy użyciu języka C++/CLI z wiersza polecenia z mstest.exe. Zamiast tego należy użyć vstest.console.exe. Zobacz [VSTest.Console.exe opcje wiersza polecenia](/visualstudio/test/vstest-console-options).

- **mutable — słowo kluczowe**

   Specyfikator klasy magazynu **modyfikowalnego** nie jest już dozwolony w miejscach, w których poprzednio został skompilowany bez błędu. Teraz kompilator daje Błąd C2071 (niedozwolona Klasa magazynu). Zgodnie ze standardem, specyfikator **modyfikowalny** może być stosowany tylko do nazw składowych danych klasy i nie można go stosować do nazw zadeklarowanych jako const lub static i nie można go stosować do elementów członkowskich odwołania.

   Rozważmy na przykład następujący kod:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Poprzednie wersje kompilatora zaakceptowali ten problem, ale teraz kompilator nadaje następujący błąd:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Aby naprawić ten błąd, Usuń nadmiarowe słowo kluczowe **mutable** .

- **char_16_t i char32_t**

   Nie można już używać `char16_t` lub `char32_t` jako aliasów w elemencie **typedef**, ponieważ te typy są teraz traktowane jako wbudowane. Była wspólna dla użytkowników i autorów bibliotek, aby definiować `char16_t` `char32_t` odpowiednio aliasy `uint16_t` i `uint32_t` .

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   Aby zaktualizować kod, Usuń deklaracje **typedef** i Zmień nazwy innych identyfikatorów, które kolidują z tymi nazwami.

- **Parametry szablonu bez typu**

   Pewien kod, który obejmuje parametry szablonu bez typu, jest teraz poprawnie sprawdzony pod kątem zgodności typów, gdy podajesz jawne argumenty szablonu. Na przykład poniższy kod został skompilowany bez błędu w poprzednich wersjach programu Visual Studio.

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   Bieżący kompilator prawidłowo podaje błąd, ponieważ typ parametru szablonu nie jest zgodny z argumentem szablonu (parametr jest wskaźnikiem do składowej const, ale funkcja f nie jest stałą):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Aby rozwiązać ten błąd w kodzie, upewnij się, że typ argumentu szablonu jest zgodny z zadeklarowanym typem parametru szablonu.

- **__declspec (Wyrównaj)**

   Kompilator nie akceptuje już `__declspec(align)` funkcji. Ta konstrukcja była zawsze ignorowana, ale teraz generuje błąd kompilatora.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracji funkcji. Ponieważ nie ma żadnego skutku, usunięcie go nie zmienia niczego.

- **Obsługa wyjątków**

   Istnieje kilka zmian w obsłudze wyjątków. Najpierw obiekty wyjątków muszą mieć możliwość kopiowania lub Movable. Poniższy kod został skompilowany w Visual Studio 2013, ale nie kompiluje się w programie Visual Studio 2015:

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Problem polega na tym, że Konstruktor kopiujący jest prywatny, dlatego nie można skopiować obiektu w normalnym czasie obsługi wyjątku. Ta sama zasada ma zastosowanie, gdy Konstruktor kopiujący jest zadeklarowany jako **jawny**.

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   Aby zaktualizować swój kod, upewnij się, że Konstruktor kopiujący dla obiektu wyjątku jest **publiczny** i nie jest oznaczony jako **jawny**.

   Przechwycenie wyjątku przez wartość wymaga również, aby obiekt wyjątku mógł być kopiowany. Poniższy kod został skompilowany w Visual Studio 2013, ale nie kompiluje się w programie Visual Studio 2015:

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   Możesz rozwiązać ten problem, zmieniając typ parametru dla **catch** do Reference.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Literały ciągu, po których następuje makra**

   Kompilator obsługuje teraz literały zdefiniowane przez użytkownika. W związku z tym literały ciągów, po których następuje makro bez żadnych spacji, są interpretowane jako literały zdefiniowane przez użytkownika, co może spowodować błędy lub nieoczekiwane wyniki. Na przykład w poprzednich kompilatorach pomyślnie skompilowano następujący kod:

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   Kompilator interpretuje ten kod jako literał ciągu "Hello", po którym następuje makro, które jest rozwinięte w "tam", a następnie dwa literały ciągu zostały połączone w jeden. W programie Visual Studio 2015 kompilator interpretuje tę sekwencję jako literał zdefiniowany przez użytkownika, ale ponieważ nie ma zdefiniowanego zgodnego literału zdefiniowanego przez użytkownika `_x` , występuje błąd.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Aby rozwiązać ten problem, Dodaj spację między literałem ciągu a makrem.

- **Sąsiadujące literały ciągu**

   Podobnie jak w poprzednim, ze względu na powiązane zmiany w analizie ciągów, sąsiadujące literały ciągu (literały ciągów szerokich lub wąskich) nie mogą być interpretowane jako jeden ciąg połączony w poprzednich wersjach Visaul C++. W programie Visual Studio 2015 musisz teraz dodać odstęp między dwoma ciągami. Na przykład należy zmienić następujący kod:

    ```cpp
    char * str = "abc""def";
    ```

   Aby rozwiązać ten problem, Dodaj odstęp między dwoma ciągami:

    ```cpp
    char * str = "abc" "def";
    ```

- **Umieszczanie nowych i usuwanie**

   Wprowadzono zmiany w operatorze **delete** w celu zapewnienia zgodności ze standardem c++ 14. Szczegóły zmiany ze standardami można znaleźć w [dealokacji rozmiaru C++](https://isocpp.org/files/papers/n3778.html). Zmiany dodają postać globalnego operatora **usuwania** , który pobiera parametr size. Istotna zmiana polega na tym, że jeśli wcześniej użyto operatora **delete** z tym samym podpisem (w celu odłożenia operatora **umieszczania** ), zostanie wyświetlony błąd kompilatora (C2956, który występuje w punkcie, w którym jest używane nowe miejsce umieszczania), ponieważ jest to pozycja w kodzie, gdzie kompilator próbuje zidentyfikować odpowiedni pasujący operator **delete** ).

   Funkcja `void operator delete(void *, size_t)` była operatorem **usuwania umieszczania** odpowiadającym **nowej funkcji umieszczania** `void * operator new(size_t, size_t)` w języku c++ 11. W przypadku cofnięcia alokacji o rozmiarze w języku C++ 14 ta funkcja usuwania jest teraz *zwykłą funkcją* cofania alokacji (operatorem **delete** globalnym). Standard wymaga, aby Jeśli użycie położenia nowego wyszukuje odpowiednią funkcję usuwania i odnajdzie zwykłą funkcję dealokacji, program jest źle sformułowany.

   Załóżmy na przykład, że kod definiuje zarówno **położenie nowe** , jak i **usuwanie położenia**:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   Problem występuje z powodu dopasowania w sygnaturach funkcji między zdefiniowanym operatorem **usuwania rozmieszczenia** i nowym operatorem **usuwania** rozmiaru globalnego. Należy rozważyć, czy można użyć innego typu innego niż `size_t` w przypadku wszystkich innych operatorów **umieszczania** i **usuwania** . Typ elementu `size_t` **typedef** jest zależny od kompilatora; jest to **element typedef** dla **niepodpisanej liczby całkowitej** w MSVC. Dobrym rozwiązaniem jest użycie typu wyliczeniowego, takiego jak:

    ```cpp
    enum class my_type : size_t {};
    ```

   Następnie Zmień definicję **umieszczania nowe** i **Usuń** , aby użyć tego typu jako drugiego argumentu zamiast `size_t` . Należy również zaktualizować wywołania do umieszczania nowe, aby przekazać nowy typ (na przykład za pomocą `static_cast<my_type>` do konwersji z wartości całkowitej) i zaktualizować definicję funkcji **New** i **delete** , aby rzutować z powrotem na typ Integer. Nie musisz używać **wyliczenia** dla tego elementu; Typ klasy z `size_t` elementem członkowskim również będzie działał.

   Alternatywne rozwiązanie polega na tym, że można całkowicie wyeliminować **nowe rozmieszczenie** . Jeśli kod używa funkcji **umieszczania New** w celu zaimplementowania puli pamięci, w której argument umieszczania jest rozmiarem obiektu, który jest przydzielany lub usuwany, funkcja cofania alokacji o określonym rozmiarze może być odpowiednia do zastąpienia własnego niestandardowego kodu puli pamięci i można wycofać funkcje umieszczania i po prostu użyć własnego operatora **usuwania** dwuargumentowego zamiast funkcji umieszczania.

   Jeśli nie chcesz natychmiast aktualizować kodu, możesz przywrócić stare zachowanie przy użyciu opcji kompilatora `/Zc:sizedDealloc-` . Jeśli używasz tej opcji, funkcje usuwania z dwoma argumentami nie istnieją i nie spowodują konfliktu z operatorem **usuwania umieszczania** .

- **Składowe danych Union**

   Elementy członkowskie danych Unii nie mogą już mieć typów referencyjnych. Poniższy kod został pomyślnie skompilowany w Visual Studio 2013, ale generuje błąd w programie Visual Studio 2015.

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   Poprzedni kod generuje następujące błędy:

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Aby rozwiązać ten problem, Zmień typy odwołań na wskaźnik lub wartość. Zmiana typu wskaźnika wymaga wprowadzenia zmian w kodzie, który używa pola Union. Zmiana kodu na wartość spowoduje zmianę danych przechowywanych w Unii, co wpływa na inne pola, ponieważ pola w typach Unii współużytkują tę samą pamięć. W zależności od rozmiaru wartości może również zmienić rozmiar związku.

- Anonimowe Unii są teraz bardziej zgodne ze standardem. Poprzednie wersje kompilatora wygenerowały jawny Konstruktor i destruktor dla Unii anonimowych. Te funkcje generowane przez kompilator są usuwane w programie Visual Studio 2015.

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   Poprzedni kod generuje następujący błąd w programie Visual Studio 2015:

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Aby rozwiązać ten problem, należy podać własne definicje konstruktora i/lub destruktora.

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **Unii z anonimowymi strukturami**

   Aby zapewnić zgodność ze standardem, zachowanie środowiska uruchomieniowego zostało zmienione dla elementów członkowskich struktur anonimowych w Unii. Konstruktor dla elementów członkowskich struktury anonimowej w Unii nie jest już wywoływany niejawnie podczas tworzenia takiego związku. Ponadto destruktor dla elementów członkowskich struktury anonimowej w Unii nie jest już niejawnie wywoływany, gdy Unia wykracza poza zakres. Rozważmy następujący kod, w którym Unia U zawiera anonimową strukturę, która zawiera nazwaną strukturę elementu członkowskiego, która ma destruktor.

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   W Visual Studio 2013 Konstruktor dla S jest wywoływany, gdy Unia zostanie utworzona, i destruktor dla S jest wywoływany, gdy stos funkcji f zostanie oczyszczony. Jednak w programie Visual Studio 2015 Konstruktor i destruktor nie są wywoływane. Kompilator wyświetla ostrzeżenie dotyczące zmiany tego zachowania.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Aby przywrócić oryginalne zachowanie, nadaj strukturze anonimowej nazwę. Zachowanie środowiska uruchomieniowego struktur nieanonimowych jest takie samo, niezależnie od wersji kompilatora.

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Alternatywnie możesz spróbować przenieść Konstruktor i destruktor do nowych funkcji i dodać wywołania tych funkcji z konstruktora i destruktora dla Unii.

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **Rozwiązanie szablonu**

   Wprowadzono zmiany w rozpoznawaniu nazw dla szablonów. W języku C++, podczas rozważania kandydatów do rozpoznawania nazw, może być to przypadek, że co najmniej jedna nazwa, pod którą uważa się, że jest to potencjalne dopasowanie, tworzy wystąpienie nieprawidłowego szablonu. Te nieprawidłowe wystąpienia zwykle nie powodują błędów kompilatora, a zasada znana jako SFINAE (niepowodzenie podstawiania nie jest błędem).

   Teraz, Jeśli SFINAE wymaga kompilatora, aby utworzyć wystąpienie specjalizacji szablonu klasy, wówczas wszystkie błędy występujące w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator zignoruje takie błędy. Rozważmy na przykład następujący kod:

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   Jeśli kompilujesz za pomocą bieżącego kompilatora, zostanie wyświetlony następujący błąd:

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   Jest to spowodowane tym, że w punkcie pierwszego wywołania is_base_of Klasa `D` nie została jeszcze zdefiniowana.

   W takim przypadku poprawka ma nie używać takich cech typu, dopóki Klasa nie zostanie zdefiniowana. Jeśli przeniesiesz definicje `B` i `D` na początek pliku kodu, błąd zostanie rozwiązany. Jeśli definicje znajdują się w plikach nagłówkowych, sprawdź kolejność instrukcji include dla plików nagłówkowych, aby upewnić się, że wszystkie definicje klas zostały skompilowane przed użyciem nieproblematycznych szablonów.

- **Kopiuj konstruktory**

   W obu Visual Studio 2013 i w programie Visual Studio 2015 kompilator generuje Konstruktor kopiujący dla klasy, jeśli ta klasa ma zdefiniowany przez użytkownika Konstruktor przenoszący, ale nie ma zdefiniowanego przez użytkownika konstruktora kopiującego. W Dev14, ten niejawnie wygenerowany Konstruktor kopiujący jest również oznaczony jako "= Delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **Główne zadeklarowane jako extern "C" teraz wymaga typu zwracanego.**

   Poniższy kod generuje teraz C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Aby naprawić ten błąd, Dodaj zwracany typ:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **Nazwa typu jest niedozwolona w inicjatorze składowej**

   Poniższy kod generuje teraz C2059:

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   Aby naprawić ten błąd, Usuń `typename` z inicjatora:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **Klasa magazynu dla jawnych specjalizacji jest ignorowana.**

   W poniższym kodzie specyfikator statycznej klasy magazynu jest ignorowany

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **Stała użyta w static_assert wewnątrz szablonu klasy zawsze zakończy się niepowodzeniem.**

   Poniższy kod powoduje, że `static_assert` zawsze kończy się niepowodzeniem:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Aby obejść ten problem, zawiń wartość w **strukturze**:

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **Reguły wymuszone dla deklaracji do przodu. (Dotyczy tylko C).**

   Poniższy kod generuje teraz C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Aby rozwiązać ten problem, Dodaj odpowiednie deklaracje przesyłania dalej:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Bardziej spójne wymuszanie typów wskaźników funkcji**

   Poniższy kod generuje teraz C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Niejednoznaczne wywołania przeciążonych funkcji**

   Poniższy kod generuje teraz C266: "N:: bind": niejednoznaczne wywołanie przeciążonej funkcji

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   Aby naprawić ten błąd, można w pełni zakwalifikować wywołanie do `bind: N::bind(...)` . Jeśli jednak ta zmiana jest manifestem za pośrednictwem niezadeklarowanego identyfikatora (C2065), może być odpowiednie rozwiązanie tego problemu przy użyciu deklaracji **using** .

   Ten wzorzec występuje często z ComPtr i innymi typami w `Microsoft::WRL` przestrzeni nazw.

- **Popraw niepoprawny adres**

   Poniższy kod generuje teraz C2440: ' = ': nie można konwertować z ' Type * ' na ' Type '. Aby naprawić ten błąd, Zmień wartość & (typ) na (typ) i (&f ()) na (f ()).

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **Literał ciągu jest tablicą stałą**

   Poniższy kod generuje teraz C2664: "void f (void *)": nie można skonwertować argumentu 1 z "const char (*) [2]" na "void *"

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Aby naprawić ten błąd, Zmień typ parametru funkcji na `const void*` lub zmień treść, `h` tak aby wyglądał jak w tym przykładzie:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **Ciągi UDL języka c++ 11**

   Poniższy kod generuje teraz błąd C3688: nieprawidłowy sufiks literału "L"; nie znaleziono operatora literału lub szablonu operatora literału "L"

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Aby naprawić ten błąd, Zmień kod, aby dodać odstęp:

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   W powyższym przykładzie `MACRO` nie jest już analizowane jako dwa tokeny (ciąg, po którym następuje makro). Teraz jest ona analizowana jako pojedynczy token UDL. To samo dotyczy L "" L "", który został przeanalizowany wcześniej jako L "" i L "" i jest teraz analizowany jako L "" L i "".

   Reguły łączenia ciągów zostały również dostosowane do zgodności ze standardem, co oznacza, że L "a" "b" jest odpowiednikiem L "AB". Poprzednie wersje programu Visual Studio nie akceptują łączenia ciągów z inną szerokością znaków.

- **Pusty znak języka c++ 11 został usunięty**

   Poniższy kod generuje teraz błąd C2137: pustą stałą znaku

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Aby naprawić ten błąd, Zmień kod w celu jawnego określenia wartości null:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Nie można przechwycić wyjątków MFC przez wartość, ponieważ nie są one możliwe do kopiowania**

   Następujący kod w aplikacji MFC powoduje teraz wystąpienie błędu C2316: 'D ': nie można przechwycić, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub usunięte

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   Aby naprawić kod, można zmienić blok catch na, `catch (const D &)` ale lepszym rozwiązaniem jest zwykle użycie makr try/catch MFC.

- **alignof jest teraz słowem kluczowym**

   Poniższy kod generuje teraz błąd C2332: "Class": Brak nazwy tagu. Aby naprawić kod, należy zmienić nazwę klasy lub, jeśli klasa wykonuje te same działania co **alignof**, wystarczy zamienić klasę na słowo kluczowe New.

    ```cpp
    class alignof{}
    ```

- **wyrażenie constexpr jest teraz słowem kluczowym**

   Poniższy kod generuje teraz błąd C2059: błąd składniowy: ') '. Aby naprawić kod, należy zmienić nazwy wszelkich nazw funkcji lub zmiennych, które są nazywane "constexpr".

    ```cpp
    int constexpr() {return 1;}
    ```

- **Typy ruchome nie mogą być stałe**

   Gdy funkcja zwraca typ, który jest przeznaczony do przeniesienia, jego typ zwracany nie powinien być **stałą**.

- **Usunięte konstruktory kopiowania**

   Poniższy kod tworzy teraz C2280:: S (S &&) ': próba odwołania do usuniętej funkcji:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Aby naprawić ten błąd, użyj bezpośredniej inicjalizacji dla `S2` :

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Konwersja wskaźnika funkcji jest generowana tylko w przypadku braku przechwytywania lambda**

   Poniższy kod generuje C2664 w programie Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Aby naprawić ten błąd, Usuń `=` z listy przechwytywania.

- **Niejednoznaczne wywołania obejmujące operatory konwersji**

   Poniższy kod generuje teraz błąd C2440: "Type CAST": nie można konwertować z 2 "na" 1 ":

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   Aby naprawić ten błąd, jawnie Wywołaj Operator konwersji:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Poniższy kod generuje teraz błąd C2593: "operator =" jest niejednoznaczny:

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   Aby naprawić ten błąd, jawnie Wywołaj Operator konwersji:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Napraw nieprawidłowe inicjalizacje kopiowania w inicjalizacji niestatycznej składowej danych (NSDMI)**

   Poniższy kod jest teraz wytwarzany błąd C2664:1:: S1 (S1 &&) ': nie można skonwertować argumentu 1 z "bool" na "const S1 &":

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Aby naprawić ten błąd, użyj bezpośredniej inicjalizacji:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Uzyskiwanie dostępu do konstruktorów wewnątrz instrukcji decltype**

   Poniższy kod generuje teraz C2248:: S ': nie można uzyskać dostępu do prywatnej składowej zadeklarowanej w klasie ':

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   Aby naprawić ten błąd, Dodaj deklarację zaprzyjaźnioną dla elementu `S2` w `S` :

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Domyślny ctor elementów lambda został niejawnie usunięty**

   Poniższy kod generuje teraz błąd C3497: nie można skonstruować wystąpienia wyrażenia lambda:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Aby naprawić ten błąd, Usuń konieczność wywołania domyślnego konstruktora. Jeśli wyrażenie lambda nie przechwytuje niczego, można je rzutować na wskaźnik funkcji.

- **Wyrażenie lambda z usuniętym operatorem przypisania**

   Poniższy kod generuje teraz błąd C2280:

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   Aby naprawić ten błąd, zastąp wyrażenie lambda klasą Funktor lub Usuń konieczność użycia operatora przypisania.

- **Podjęto próbę przeniesienia obiektu z usuniętym konstruktorem kopiującym**

   Poniższy kod generuje teraz błąd C2280: "ruchome:: ruchome (const ruchome &)": próba odwołująca się do usuniętej funkcji

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   Aby naprawić ten błąd, użyj `std::move` zamiast tego:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Klasa lokalna nie może odwoływać się do innej klasy lokalnej zdefiniowanej dalej w tej samej funkcji**

   Poniższy kod generuje teraz błąd C2079: "używa niezdefiniowanej struktury" Main:: S2 "

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   Aby naprawić ten błąd, Przenieś w górę definicję `S2` :

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **W treści pochodnej elementu ctor nie można wywołać chronionego elementu ctor Base.**

   Poniższy kod tworzy teraz błąd C2248: "1:: S1": nie można uzyskać dostępu do chronionej składowej zadeklarowanej w klasie 1 "

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   Aby naprawić ten błąd, w polu `S2` Usuń wywołanie do `S1()` z konstruktora i w razie potrzeby umieść go w innej funkcji.

- **{}uniemożliwia konwersję na wskaźnik**

   Poniższy kod generuje teraz C2439::p ': nie można zainicjować składowej

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Aby naprawić ten błąd, Usuń nawiasy klamrowe z dookoła `0` lub else Użyj **nullptr** zamiast tego, jak pokazano w poniższym przykładzie:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Nieprawidłowa definicja makra i użycie z nawiasami**

   Poniższy przykład tworzy teraz błąd C2008: '; ': nieoczekiwany w definicji makra

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Aby rozwiązać ten problem, Zmień górny wiersz na`#define A();`

   Poniższy kod generuje błąd C2059: błąd składniowy: ') '

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Aby naprawić kod, Usuń spację między a i ().

   Poniższy kod generuje błąd C2091: funkcja zwraca funkcję:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Aby naprawić ten błąd, Usuń nawiasy po ZADEKLAROWANiu w S: `DECLARE;` .

   Poniższy kod generuje błąd C2062: nieoczekiwany typ "int"

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Aby rozwiązać ten problem, zdefiniuj `A` następujący:

    ```cpp
    #define A int
    ```

- **Dodatkowe parens w deklaracjach**

   Poniższy kod generuje błąd C2062: nieoczekiwany typ "int"

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Aby naprawić ten błąd, Usuń nawiasy `j` . Jeśli nawiasy są niezbędne do przejrzystości, użyj elementu **typedef**.

- **Konstruktory i __declspec generowane przez kompilator (notablicę)**

   W programie Visual Studio 2015 istnieje zwiększone prawdopodobieństwo, że wygenerowane przez kompilator wbudowane konstruktory klas abstrakcyjnych z wirtualnymi klasami podstawowymi mogą uwidaczniać niewłaściwe użycie `__declspec(novtable)` w połączeniu z `__declspec(dllimport)` .

- **Funkcja autowypełnia pojedyncze wyrażenie w ramach inicjalizacji listy bezpośredniej**

   Poniższy kod generuje teraz błąd C3518: "testPositions": w kontekście bezpośredniego inicjowania listy Typ dla "Auto" można wywnioskować tylko na podstawie pojedynczego wyrażenia inicjatora

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Aby naprawić ten błąd, jedną z możliwości jest zainicjowanie `testPositions` w następujący sposób:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Sprawdzanie typów a wskaźniki do typów dla is_convertible**

   Poniższy kod powoduje, że potwierdzenie statyczne kończy się niepowodzeniem.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Aby naprawić ten błąd, Zmień wartość `static_assert` tak, aby porównuje wskaźniki z `D` i `B2` :

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **deklaracje __declspec (notablicę) muszą być zgodne**

   `__declspec`deklaracje muszą być spójne we wszystkich bibliotekach. Poniższy kod spowoduje teraz wygenerowanie naruszenia reguły z jedną definicją (ODR):

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

### <a name="conformance-improvements-in-update-1"></a><a name="VS_Update1"></a>Ulepszenia zgodności w aktualizacji Update 1

- **Prywatne wirtualne klasy bazowe i dziedziczenie pośrednie**

   Poprzednie wersje kompilatora pozwoliły klasie pochodnej na wywoływanie funkcji Członkowskich jego pośrednio pochodnych `private virtual` klas podstawowych. To stare zachowanie było nieprawidłowe i nie jest zgodne ze standardem C++. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia błąd kompilatora C2280 w wyniku.

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   Przykład (przed)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   Przykład (po)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \-oraz

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Przeciążony operator new i operator delete**

   Poprzednie wersje kompilatora umożliwiły **operatorowi** nienależącemu do elementu członkowskiego nowe i nieskładowe **, które mają** być zadeklarowane jako statyczne i mogą być deklarowane w przestrzeniach nazw innych niż globalna przestrzeń nazw.  To stare zachowanie spowodowało ryzyko, że program nie wywoła implementacji operatora **New** lub **delete** , który jest przeznaczony dla programisty, co skutkuje nieprawidłowym zachowaniem środowiska uruchomieniowego. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia C2323 błąd kompilatora.

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   Przykład (przed)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   Przykład (po)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   Ponadto mimo że kompilator nie daje określonej diagnostyki, wbudowany operator **New** jest traktowany jako źle sformułowany.

- **Wywoływanie "operator *Type*()" (konwersja zdefiniowana przez użytkownika) dla typów niebędących klasami**

   W poprzednich wersjach kompilatora dozwolone jest wywoływanie " *Typ*operatora ()" dla typów niebędących klasami, podczas gdy jest on dyskretnie ignorowany. To stare zachowanie spowodowało ryzyko pominięcia nieprawidłowego generowania kodu, co skutkuje nieprzewidywalnym zachowaniem środowiska uruchomieniowego. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia C2228 błąd kompilatora.

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   Przykład (przed)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   Przykład (po)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **Nadmiarowa nazwa elementu TypeName w wypracowanych specyfikatorach typu**

   Poprzednie wersje **kompilatora dozwolone w** specyfikatorze typu złożonego, ale kod pisany w ten sposób jest semantycznie niepoprawny. Kompilator nie akceptuje już kodu pisanego w ten sposób i wystawia C3406 błąd kompilatora.

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   Przykład (przed)

    ```cpp
    template <typename class T>
    class container;
    ```

   Przykład (po)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **Typ odejmowania tablic z listy inicjatorów**

   Poprzednie wersje kompilatora nie obsługiwały odejmowania typów tablic z listy inicjatorów. Kompilator obsługuje teraz tę formę odejmowania typu, a w rezultacie wywołania szablonów funkcji korzystających z list inicjatorów mogą teraz być niejednoznaczne lub można wybrać inne Przeciążenie niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program musi teraz jawnie określić Przeciążenie, którego zaplanowano programista.

   Gdy to nowe zachowanie powoduje rozwiązanie przeciążenia w celu uwzględnienia dodatkowego kandydata, który jest równie dobry, jak kandydat historyczny, wywołanie stanie się niejednoznaczne i kompilator wystawia błąd kompilatora C2668 w wyniku.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Przykład 1: niejednoznaczne wywołanie przeciążonej funkcji (przed)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   Przykład 1: niejednoznaczne wywołanie przeciążonej funkcji (po)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   Gdy to nowe zachowanie powoduje rozwiązanie przeciążenia w celu uwzględnienia dodatkowego kandydata, który jest lepszym rozwiązaniem niż kandydat historyczny, wywołanie jest rozpoznawane w sposób niejednoznaczny dla nowego kandydata, powodując zmianę zachowania programu, które prawdopodobnie różni się od programisty zamierzone.

   Przykład 2: zmiana rozdzielczości przeciążenia (przed)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   Przykład 2: zmiana rozdzielczości przeciążenia (po)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **Przywracanie ostrzeżeń instrukcji switch**

   Poprzednia wersja kompilatora usunęła niektóre ostrzeżenia dotyczące instrukcji **Switch** ; te ostrzeżenia zostały teraz przywrócone. Kompilator wystawia teraz przywrócone ostrzeżenia i ostrzeżenia związane z określonymi przypadkami (w tym przypadkiem domyślnym) są teraz wydawane w wierszu zawierającym przypadek, w którym występują problemy, a nie na ostatnim wierszu instrukcji switch. W wyniku wydawania tych ostrzeżeń w różnych wierszach niż w przeszłości ostrzeżenia poprzednio pomijane za pomocą nie `#pragma warning(disable:####)` mogą być już pomijane jako zamierzone. Aby pominąć te ostrzeżenia zgodnie z oczekiwaniami, może być konieczne przeniesienie `#pragma warning(disable:####)` dyrektywy do wiersza powyżej pierwszego wystąpienia. Przywrócone ostrzeżenia są następujące:

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   Przykład C4063 (przed)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   Przykład C4063 (po)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   Przykłady innych przywróconych ostrzeżeń znajdują się w dokumentacji.

- **#include: Użyj specyfikatora katalogu nadrzędnego ".." w nazwie ścieżki** (dotyczy tylko `/Wall` `/WX` )

   Poprzednie wersje kompilatora nie wykryły użycia specyfikatora katalogu nadrzędnego ".." w nazwie ścieżki `#include` dyrektyw. Kod zapisany w ten sposób jest zwykle przeznaczony do uwzględniania nagłówków istniejących poza projektem przez nieprawidłowe użycie ścieżek względnych dla projektu. To stare zachowanie polega na tym, że program może zostać skompilowany przez dołączenie innego pliku źródłowego niż programista lub ścieżki względne nie zostaną przenośne do innych środowisk kompilacji. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i generuje opcjonalne Ostrzeżenie kompilatora C4464, jeśli jest włączone.

    ```Output
    warning C4464: relative include path contains '..'
    ```

   Przykład (przed)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   Przykład (po)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   Ponadto mimo że kompilator nie zapewnia określonej diagnostyki, zalecamy również, aby specyfikator katalogu nadrzędnego ".." nie był używany do określania katalogów dołączanych projektu.

- **#pragma Optymalizuj () wykracza poza koniec pliku nagłówka** (dotyczy tylko `/Wall` `/WX` )

   Poprzednie wersje kompilatora nie wykryły zmian w ustawieniach flagi optymalizacji, które wyłączają plik nagłówka w jednostce translacji. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i wystawia opcjonalne Ostrzeżenie kompilatora C4426 w lokalizacji problemu `#include` , jeśli jest włączone. To ostrzeżenie jest wysyłane tylko wtedy, gdy zmiany powodują konflikt z flagami optymalizacji ustawionymi przez argumenty wiersza polecenia do kompilatora.

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   Przykład (przed)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   Przykład (po)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **Niezgodność #pragma warning (push)** i **#pragma warning (pop)** (dotyczy tylko `/Wall` `/WX` )

   Poprzednie wersje kompilatora nie wykryły `#pragma warning(push)` zmian stanu sparowanych ze `#pragma warning(pop)` zmianami stanu w innym pliku źródłowym, co jest rzadko zamierzone. To stare zachowanie spowodowało ryzyko, że program został skompilowany z innym zestawem ostrzeżeń włączonym od programisty, prawdopodobnie z powodu nieprawidłowego zachowania środowiska uruchomieniowego. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i wystawia opcjonalne Ostrzeżenie kompilatora C5031 w lokalizacji dopasowania `#pragma warning(pop)` , jeśli jest włączone. To ostrzeżenie zawiera uwagę odwołującą się do lokalizacji odpowiadającego #pragma ostrzeżenia (push).

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   Przykład (przed)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   Przykład (po)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   Chociaż nietypowy, kod pisany w ten sposób jest czasami celowo. Kod zapisany w ten sposób jest wrażliwy na zmiany w `#include` kolejności; jeśli to możliwe, zalecamy, aby pliki kodu źródłowego zarządzać stanem ostrzegawczym w sposób samodzielny.

- **Niedopasowane #pragma ostrzeżenie (push)** (dotyczy tylko `/Wall` `/WX` )

   Poprzednie wersje kompilatora nie wykryły niedopasowanych `#pragma warning(push)` zmian stanu na końcu jednostki tłumaczenia. Kompilator wykrywa teraz i powiadamia programistę o kodzie zapisanym w ten sposób i wystawia opcjonalne Ostrzeżenie kompilatora C5032 w lokalizacji niedopasowanego `#pragma warning(push)` , jeśli jest włączone. To ostrzeżenie jest wysyłane tylko wtedy, gdy w jednostce tłumaczenia nie występują błędy kompilacji.

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   Przykład (przed)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   Przykład (po)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **Dodatkowe ostrzeżenia mogą być wydawane w wyniku ulepszonego śledzenia stanu ostrzeżenia #pragma**

   Poprzednie wersje kompilatora prześledzone #pragma zmiany stanu ostrzegawczego niewystarczająco dobrze, aby wystawić wszystkie zamierzone ostrzeżenia. To zachowanie spowodowało utworzenie ryzyka, że niektóre ostrzeżenia byłyby skutecznie pomijane w okolicznościach innych niż programista. Kompilator teraz śledzi `#pragma warning` stan bardziej niezawodnie — szczególnie powiązane ze `#pragma warning` zmianami stanu wewnątrz szablonów — i opcjonalnie zgłasza nowe ostrzeżenia C5031 i C5032, które są przeznaczone do ułatwienia programistom lokalizowanie niezamierzonych użycia `#pragma warning(push)` i `#pragma warning(pop)` .

   W wyniku ulepszonego `#pragma warning` śledzenia zmian stanu pojawiły się ostrzeżenia dawniej pominięte lub ostrzeżenia związane z problemami, które wcześniej były nieprawidłowo zdiagnozowane, mogą zostać wystawione.

- **Ulepszona identyfikacja nieosiągalnego kodu**

   Standardowa biblioteka języka C++ zmiany i lepsza możliwość wywołań funkcji wbudowanych w porównaniu z poprzednimi wersjami kompilatora może pozwolić kompilatorowi udowodnić, że określony kod jest teraz nieosiągalny. To nowe zachowanie może spowodować nowe i bardziej często wystawione wystąpienia ostrzeżenia C4720.

    ```Output
    warning C4720: unreachable code
    ```

   W wielu przypadkach to ostrzeżenie może zostać wystawione tylko w przypadku kompilowania z włączonymi optymalizacjami, ponieważ optymalizacje mogą zawierać więcej wywołań funkcji, wyeliminować nadmiarowy kod lub w inny sposób określić, że określony kod jest nieosiągalny. Zaobserwowano, że nowe wystąpienia ostrzeżenia C4720 często występowały w blokach **try/catch** , szczególnie w odniesieniu do użycia klasy [std:: find](../standard-library/algorithm-functions.md#find).

   Przykład (przed)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   Przykład (po)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

### <a name="conformance-improvements-in-update-2"></a><a name="VS_Update2"></a>Ulepszenia zgodności w aktualizacji Update 2

- **Dodatkowe ostrzeżenia i błędy mogą być wydawane w wyniku częściowego wsparcia dla SFINAE wyrażeń**

   Poprzednie wersje kompilatora nie przeanalizują niektórych rodzajów wyrażeń wewnątrz specyfikatorów **decltype** ze względu na brak obsługi wyrażenia SFINAE. To stare zachowanie było nieprawidłowe i nie jest zgodne ze standardem C++. Kompilator analizuje teraz te wyrażenia i ma częściową obsługę wyrażenia SFINAE z powodu bieżących ulepszeń zgodności. W związku z tym kompilator wystawia ostrzeżenia i błędy Znalezione w wyrażeniach, których poprzednie wersje kompilatora nie zostały przeanalizowane.

   Gdy to nowe zachowanie analizuje wyrażenie **decltype** , które zawiera typ, który nie został jeszcze zadeklarowany, kompilator wystawia błąd kompilatora C2039 w wyniku.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Przykład 1: użycie niezadeklarowanego typu (przed)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   Przykład 1 (po)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   Gdy to nowe zachowanie analizuje wyrażenie **decltype** , w którym brakuje niepotrzebnego użycia słowa kluczowego **TypeName** , aby określić, że nazwa zależna jest typem, kompilator wystawia ostrzeżenia kompilatora C4346 razem z błędem kompilatora C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Przykład 2: Nazwa zależna nie jest typem (przed)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   Przykład 2 (po)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- `volatile`**zmienne składowe uniemożliwiają niejawnie zdefiniowane konstruktory i operatory przypisania**

   Poprzednie wersje kompilatora umożliwiły klasie, która ma zmienne składowe **lotne** , aby mieć domyślne konstruktory kopiowania/przenoszenia oraz automatyczne generowanie operatorów przypisania kopiowania/przenoszenia. To stare zachowanie było nieprawidłowe i nie jest zgodne ze standardem C++. Kompilator traktuje teraz klasę, która ma zmienne składowe **lotne** , aby mieć nieuproszczone operatory konstrukcji i przypisania, które uniemożliwiają automatyczne generowanie domyślnych implementacji tych operatorów. Gdy taka Klasa jest członkiem Unii (lub anonimowej Unii wewnątrz klasy), konstruktory kopiowania/przenoszenia oraz operatory przypisania kopiowania/przenoszenia Unii (lub klasy zawierającej Unię anonimową) zostaną niejawnie zdefiniowane jako usunięte. Podjęto próbę skonstruowania lub skopiowania Unii (lub klasy zawierającej Unię anonimową) bez jawnego definiowania ich, a kompilator wygeneruje błąd kompilatora C2280 w wyniku.

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   Przykład (przed)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   Przykład (po)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **Statyczne funkcje członkowskie nie obsługują kwalifikatorów OKS.**

   Poprzednie wersje programu Visual Studio 2015 dozwolone statyczne funkcje składowe mają kwalifikatory CV. To zachowanie jest spowodowane regresją w programie Visual Studio 2015 i Visual Studio 2015 Update 1. Visual Studio 2013 i poprzednie wersje kompilatora odrzucają kod zapisany w ten sposób. Zachowanie programu Visual Studio 2015 i Visual Studio 2015 Update 1 jest nieprawidłowe i nie jest zgodne ze standardem C++.  Program Visual Studio 2015 Update 2 odrzuca kod zapisany w ten sposób i wystawia C2511 błąd kompilatora.

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   Przykład (przed)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   Przykład (po)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Przekazywanie deklaracji typu enum jest niedozwolone w kodzie WinRT** (dotyczy tylko `/ZW` )

   Kod skompilowany dla środowisko wykonawcze systemu Windows (WinRT) nie zezwala na deklarowanie typów **wyliczeniowych** , podobnie jak w przypadku kompilowania kodu zarządzanego C++ dla programu .NET Framework przy użyciu `/clr` przełącznika kompilatora. Takie zachowanie zapewnia, że rozmiar wyliczenia jest zawsze znany i może być prawidłowo rzutowany na system typów WinRT. Kompilator odrzuca kod zapisany w ten sposób i wystawia błąd kompilatora C2599 razem z błędem kompilatora C3197.

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   Przykład (przed)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   Przykład (po)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **Przeciążony operator, który nie jest elementem członkowskim New i operator delete nie może być zadeklarowany w tekście** (poziom 1 ( `/W1` ) na poziomie domyślnym)

   Poprzednie wersje kompilatora nie generują ostrzeżenia, gdy funkcje operatora Non-member New i operator delete są zadeklarowane w tekście. Kod zapisany w ten sposób jest źle sformułowany (nie jest wymagana żadna Diagnostyka) i może powodować problemy z pamięcią, które wynikają z niedopasowanych operatorów New i Delete (szczególnie w przypadku używania razem z cofnięciem alokacji rozmiaru), które mogą być trudne do zdiagnozowania. Kompilator wystawia teraz ostrzeżenia kompilatora C4595, aby ułatwić zidentyfikowanie kodu w ten sposób.

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   Przykład (przed)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   Przykład (po)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   Naprawianie kodu, który jest pisany w ten sposób, może wymagać, aby definicje operatora były przenoszone poza plik nagłówka i do odpowiedniego pliku źródłowego.

### <a name="conformance-improvements-in-update-3"></a><a name="VS_Update3"></a>Ulepszenia zgodności w aktualizacji Update 3

- **std:: is_convertable teraz wykrywają samodzielne przypisanie** (standardowa biblioteka)

   Poprzednie wersje `std::is_convertable` cech typu nie wykryły prawidłowo samodzielnego przypisania typu klasy, gdy jego Konstruktor kopiujący został usunięty lub jest prywatny. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona **wartość false** w przypadku zastosowania do typu klasy z usuniętym lub prywatnym konstruktorem kopiującym.

   Brak diagnostyki kompilatora skojarzonej z tą zmianą.

   Przykład

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   W poprzednich wersjach kompilatora, statyczne potwierdzenia u dołu tego przykładu są nieprawidłowe, ponieważ `std::is_convertable<>::value` zostały nieprawidłowo ustawione na **wartość true**. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona **wartość false**, co powoduje niepowodzenie potwierdzeń statycznych.

- **Domyślne lub usunięte proste konstruktory kopiujące i przenoszenia respektują specyfikatory dostępu**

   Poprzednie wersje kompilatora nie sprawdzają, czy specyfikator dostępu został domyślnie usunięty, i nie usunięto konstruktorów, a następnie nie można ich wywołać. To stare zachowanie było nieprawidłowe i nie jest zgodne ze standardem C++. W niektórych przypadkach to stare zachowanie spowodowało ryzyko pominięcia nieprawidłowego generowania kodu, co skutkuje nieprzewidywalnym zachowaniem środowiska uruchomieniowego. Kompilator sprawdzi teraz specyfikator dostępu domyślnie, a następnie usunął konstruktory, aby określić, czy można go wywołać, a jeśli nie, wystawia ostrzeżenia kompilatora C2248 w wyniku.

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   Przykład (przed)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   Przykład (po)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **Przestarzała obsługa kodu ATL z atrybutami** (poziom 1 ( `/W1` ) na podstawie wartości domyślnej)

   Poprzednie wersje kompilatora obsługują kod ATL z atrybutami. W następnej fazie usuwania obsługi kodu ATL z atrybutami, który [pojawił się w programie Visual Studio 2008](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008), kod ATL ma atrybut przestarzały. Kompilator wystawia teraz ostrzeżenia kompilatora C4467, aby pomóc w zidentyfikowaniu tego rodzaju przestarzałego kodu.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Jeśli chcesz nadal używać kodu ATL z atrybutami, dopóki nie zostanie usunięta z kompilatora, możesz wyłączyć to ostrzeżenie przez przekazanie `/Wv:18` `/wd:4467` argumentów wiersza polecenia lub do kompilatora lub przez dodanie `#pragma warning(disable:4467)` w kodzie źródłowym.

   Przykład 1 (przed)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Przykład 1 (po)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Czasami może być konieczne lub chcieć utworzyć plik IDL, aby uniknąć używania przestarzałych atrybutów ATL, jak w poniższym przykładzie kodu

   Przykład 2 (przed)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   Najpierw utwórz plik *. idl; wygenerowany plik vc140. idl może służyć do uzyskania \* pliku. idl zawierającego interfejsy i adnotacje.

   Następnie Dodaj krok MIDL do kompilacji, aby upewnić się, że są generowane definicje interfejsu języka C++.

   Przykład 2 IDL (po)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   Następnie użyj biblioteki ATL bezpośrednio w pliku implementacji, jak w poniższym przykładzie kodu.

   Przykład 2 implementacji (po)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **Prekompilowany plik nagłówkowy (pch) i niezgodne dyrektywy #include** (dotyczy tylko `/Wall` `/WX` )

   Poprzednie wersje kompilatora zaakceptowały niezgodne `#include` dyrektywy w plikach źródłowych między `-Yc` i `-Yu` kompilacjami przy użyciu prekompilowanych plików nagłówkowych (pch). Kod zapisany w ten sposób nie jest już akceptowany przez kompilator.   Kompilator wystawia teraz ostrzeżenia kompilatora CC4598, aby ułatwić zidentyfikowanie niezgodnych `#include` dyrektyw podczas korzystania z plików PCH.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Przykład (przed):

   X. cpp (-YCC. h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z. cpp (-Yuc. h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Przykład (po)

   X. cpp (-YCC. h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z. cpp (-Yuc. h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Prekompilowany plik nagłówkowy (pch) i niezgodne katalogi dołączane** (dotyczy tylko `/Wall` `/WX` )

   Poprzednie wersje kompilatora zaakceptowały niezgodne `-I` argumenty wiersza polecenia Include Directory () do kompilatora między `-Yc` i `-Yu` kompilacjami przy użyciu prekompilowanych plików nagłówkowych (pch). Kod zapisany w ten sposób nie jest już akceptowany przez kompilator. Kompilator wystawia teraz ostrzeżenia kompilatora CC4599, aby pomóc w zidentyfikowaniu niezgodnych `-I` argumentów wiersza polecenia Include Directory () podczas korzystania z plików PCH.

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   Przykład (przed)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   Przykład (po)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 zmiany zgodności

### <a name="compiler"></a>Compiler

- Po słowie kluczowym **finalnym** jest generowany błąd nierozpoznanego symbolu, gdzie zostałby skompilowany wcześniej:

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   We wcześniejszych wersjach błąd nie został wystawiony, ponieważ wywołanie było wywołaniem **wirtualnym** ; Niemniej jednak program może ulec awarii w czasie wykonywania. Teraz zostaje zgłoszony błąd konsolidatora, ponieważ wiadomo, że klasa jest ostateczna. W tym przykładzie, aby naprawić błąd, należy połączyć się z obiektem, który zawiera definicję `S2::f` .

- W przypadku używania zaprzyjaźnionych funkcji w przestrzeniach nazw należy ponownie zadeklarować funkcję zaprzyjaźnioną przed odwołaniem do niej lub otrzymać błąd, ponieważ kompilator jest teraz zgodny ze standardem ISO C++. Na przykład ten przykład nie kompiluje się już:

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   Aby poprawić ten kod, zadeklaruj funkcję **zaprzyjaźnioną** :

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- Standard C++ nie zezwala na jawną specjalizację w klasie. Chociaż kompilator języka Microsoft C++ pozwala na to w niektórych przypadkach, w przypadkach, takich jak Poniższy przykład, błąd jest generowany, ponieważ kompilator nie uwzględnia drugiej funkcji jako specjalizacji pierwszej z nich.

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   Aby poprawić ten kod, zmodyfikuj drugą funkcję:

    ```cpp
    template <> void f(char& val);
    ```

- Kompilator nie podejmuje już prób odróżnienia dwóch funkcji w poniższym przykładzie i teraz emituje błąd:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   Aby poprawić ten kod, wyjaśnij wywołanie:

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- Przed podjęciem zgodności kompilatora z ISO C++ 11, poniższy kod zostałby skompilowany i spowodował `x` rozpoznanie typu **int**:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Ten kod jest teraz rozpoznawany jako `x` Typ `std::initializer_list<int>` i powoduje błąd w następnym wierszu, który próbuje przypisać `x` do typu **int**. (Domyślnie nie ma konwersji). Aby poprawić ten kod, użyj **int** , aby **zastąpić**Auto:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Inicjalizacja agregacji nie jest już dozwolona, gdy typ wartości po prawej stronie jest niezgodny z typem wartości po lewej stronie, który jest inicjowany, i jest wystawiany błąd, ponieważ standard ISO C++ 11 wymaga jednolitej inicjalizacji do pracy bez zawężania konwersji. Wcześniej, jeśli jest dostępna konwersja z wąskim poziomem, [Ostrzeżenie kompilatora (poziom 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) zostało wystawione zamiast błędu.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   Aby poprawić ten kod, dodaj jawną konwersję zawężającą:

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- Następująca Inicjalizacja nie jest już dozwolona:

    ```cpp
    void *p = {{0}};
    ```

   Aby poprawić ten kod, użyj którejś z tych postaci:

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- Wyszukiwanie nazw zostało zmienione. Poniższy kod jest rozpoznawany inaczej w kompilatorze języka C++ w programie Visual Studio 2012 i Visual Studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   W programie Visual Studio 2012 `E1` wyrażenie in zostało `E1::b` rozpoznane jako `::E1` w zakresie globalnym. W Visual Studio 2013 `E1` w wyrażeniu jest `E1::b` rozpoznawana jako `typedef E2` Definicja w `main()` i ma typ `::E2` .

- Układ obiektu został zmieniony. W x64, układ obiektu klasy może się zmienić w porównaniu z poprzednimi wydaniami. Jeśli ma funkcję **wirtualną** , ale nie ma klasy bazowej, która ma funkcję **wirtualną** , model obiektów kompilatora wstawia wskaźnik do tabeli funkcji **wirtualnych** po układzie elementu członkowskiego danych. Oznacza to, że układ może nie być optymalny we wszystkich przypadkach. W poprzednich wersjach Optymalizacja dla architektury x64 próbowała ulepszyć układ, ale ponieważ nie działała prawidłowo w złożonych sytuacjach związanych z kodem, została usunięta w Visual Studio 2013. Na przykład, rozważmy ten kod:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- W Visual Studio 2013 wynik `sizeof(S2)` dla architektury x64 to 48, ale w poprzednich wersjach jest on obliczany na 32. Aby ta wartość była Szacowana do 32 w kompilatorze C++ Visual Studio 2013 dla architektury x64, Dodaj fikcyjną klasę bazową, która ma funkcję **wirtualną** :

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Aby znaleźć miejsca w kodzie, które zostały wypróbowane we wcześniejszej wersji, należy użyć kompilatora z tej wersji razem z `/W3` opcją kompilatora i włączyć polecenie Warning C4370. Na przykład:

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Przed Visual Studio 2013 ten kod wyświetla komunikat: "ostrzeżenie C4370:2": układ klasy został zmieniony z poprzedniej wersji kompilatora, ze względu na lepsze pakowanie ".

   Kompilator x86 ma ten sam problem z nieoptymalnym układem we wszystkich wersjach kompilatora. Na przykład, jeśli ten kod jest kompilowany dla architektury x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Wynik `sizeof(S)` wynosi 24. Jednak można je zmniejszyć do 16, jeśli używasz obejścia opisanego dla x64:

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>Standardowa biblioteka

Kompilator języka C++ w Visual Studio 2013 wykrywa niezgodności w _ITERATOR_DEBUG_LEVEL, który został zaimplementowany w programie Visual Studio 2010 i RuntimeLibrary niezgodności. Te niezgodności występują, gdy opcje kompilatora `/MT` (wydanie statyczne), `/MTd` (debugowanie statyczne), `/MD` (wydanie dynamiczne) i `/MDd` (debugowanie dynamiczne) są mieszane.

- Jeśli Twój kod potwierdzi symulowane szablony aliasów poprzedniej wersji, musisz go zmienić. Na przykład zamiast tego należy `allocator_traits<A>::rebind_alloc<U>::other` powiedzieć `allocator_traits<A>::rebind_alloc<U>` . Chociaż `ratio_add<R1, R2>::type` nie jest już konieczne i zalecamy, aby wypowiedzieć `ratio_add<R1, R2>` , że dawniej będzie kompilować, ponieważ `ratio<N, D>` jest wymagany element typedef "Type" dla zredukowanego współczynnika, który będzie tego samego typu, jeśli został już zmniejszony.

- Należy używać `#include <algorithm>` podczas wywoływania `std::min()` lub `std::max()` .

- Jeśli istniejący kod używa symulowanych typów wyliczeniowych w zakresie w poprzednim wydaniu — tradycyjne typy wyliczeniowe nieobjęte zakresem opakowane w przestrzeni nazw — należy je zmienić. Na przykład, jeśli Przywołujesz się do typu `std::future_status::future_status` , teraz musisz powiedzieć `std::future_status` . Jednak większość kodu jest nienaruszona — na przykład `std::future_status::ready` nadal kompiluje.

- `explicit operator bool()`jest bardziej restrykcyjny niż nieokreślony operator-bool-Type (). `explicit operator bool()`zezwala na jawne konwersje na typ bool — na przykład, dane `shared_ptr<X> sp` `static_cast<bool>(sp)` i `bool b(sp)` są prawidłowe — i Boolean-weryfikowalne "Konwersje kontekstowe" na typ bool — na przykład,, `if (sp)` `!sp` `sp &&` niezależnie. Jednakże `explicit operator bool()` zabrania niejawnych konwersji na bool, więc nie można powiedzieć `bool b = sp;` i uzyskać typu zwracanego bool, nie można powiedzieć `return sp` .

- Teraz, gdy szablony wariadyczne są zaimplementowane, _VARIADIC_MAX i powiązane makra nie mają żadnego efektu. Jeśli nadal tworzysz _VARIADIC_MAX, zostanie on zignorowany. Jeśli przyjmiesz nasze rozwiązania makr przeznaczone do wspierania symulowanych szablonów wariadycznych w jakikolwiek inny sposób, musisz zmienić kod.

- Oprócz zwykłych słów kluczowych, nagłówki standardowej biblioteki C++ teraz zabraniają **zastąpienia makra kontekstowych słów kluczowych** i **końcowe**.

- `reference_wrapper`, `ref()` i `cref()` teraz Zabroń powiązania z obiektami tymczasowymi.

- \<random>teraz ściśle wymuszają warunki wstępne czasu kompilacji.

- Różne cechy typu standardowej biblioteki języka C++ mają warunek wstępny "T musi być kompletnym typem". Mimo że kompilator wymusza ten warunek wstępny dokładniej, może nie wymusić go we wszystkich sytuacjach. (Ponieważ naruszenia warunku wstępnego standardowej biblioteki języka C++ wyzwalają niezdefiniowane zachowanie, standard nie gwarantuje wymuszania.)

- Standardowa biblioteka języka C++ nie obsługuje `/clr:oldSyntax` .

- Specyfikacja C++ 11 dla common_type<> miała nieoczekiwane i niepożądane konsekwencje; w szczególności tworzy common_type \<int, int> :: Type Return int&&. W związku z tym kompilator implementuje proponowane rozwiązanie problemu z grupą roboczą biblioteki 2141, co sprawia, że common_type \<int, int=""> :: Type zwraca int.

   W wyniku wprowadzenia tej zmiany przypadek tożsamości nie będzie już działać (common_type \<T> nie zawsze jest wynikiem typu t). To zachowanie jest zgodne z proponowanym rozwiązaniem, ale zrywa każdy kod, który opierał się na poprzednim zachowaniu.

   Jeśli wymagasz cechy typu tożsamości, nie używaj standardu, `std::identity` który jest zdefiniowany w, \<type_traits> ponieważ nie będzie on działał \<void> . Zamiast tego wdróż własną cechę typu tożsamości odpowiednią do własnych potrzeb. Oto przykład:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC i ATL

- **Tylko Visual Studio 2013**: Biblioteka MFC MBCS nie jest dołączona do programu Visual Studio, ponieważ Unicode jest popularne, a korzystanie z MBCS zostało znacznie odrzucone. Ta zmiana podtrzymuje również ściślejszą relację między MFC a Windows SDK. ponieważ wiele nowych kontrolek i komunikatów wymaga Unicode. Jeśli jednak trzeba będzie nadal korzystać z biblioteki MFC MBCS, możesz ją pobrać z centrum pobierania Microsoft w [bibliotece MFC wielobajtowej dla Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770). Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.  (Uwaga: Biblioteka DLL MBCS jest zawarta w składnikach Instalatora języka C++ w programie Visual Studio 2015 i nowszych).

- Ułatwienia dostępu dla wstążki MFC zostały zmienione.  Zamiast architektury jednego poziomu jest teraz architektura hierarchiczna. Można nadal używać starego zachowania przez wywołanie metody `CRibbonBar::EnableSingleLevelAccessibilityMode()` .

- `CDatabase::GetConnect`Metoda jest usuwana. W celu zwiększenia bezpieczeństwa parametry połączenia są teraz przechowywane w postaci zaszyfrowanej i odszyfrowywane tylko w razie potrzeby; nie można jej zwrócić jako zwykłego tekstu.  Ciąg można uzyskać za pomocą `CDatabase::Dump` metody.

- Podpis `CWnd::OnPowerBroadcast` został zmieniony. Sygnatura tego programu obsługi komunikatu została zmieniona, aby przyjąć LPARAM jako drugi parametr.

- Sygnatury są zmieniane w celu obsługi komunikatów. Listy parametrów dla poniższych funkcji zostały zmienione, aby używać nowo dodanych programów obsługi komunikatów ON_WM_*:

  - `CWnd::OnDisplayChange`zmieniono na (UINT, int, int) zamiast (WPARAM, LPARAM), tak aby nowe makro ON_WM_DISPLAYCHANGE może być używane w mapie wiadomości.

  - `CFrameWnd::OnDDEInitiate`zmieniono na (CWnd *, UINT, UNIT) zamiast (WPARAM, LPARAM), tak aby nowe makro ON_WM_DDE_INITIATE może być używane w mapie wiadomości.

  - `CFrameWnd::OnDDEExecute`zmieniono na (CWnd *, dojście) zamiast (WPARAM, LPARAM), tak aby nowe makro ON_WM_DDE_EXECUTE może być używane w mapie wiadomości.

  - `CFrameWnd::OnDDETerminate`zmieniono na (CWnd *) jako parametr zamiast (WPARAM, LPARAM), tak aby nowe makro ON_WM_DDE_TERMINATE może być używane w mapie wiadomości.

  - `CMFCMaskedEdit::OnCut`wartość nie została zmieniona na wartość bez parametrów (WPARAM, LPARAM), tak aby nowe makro ON_WM_CUT może być używane w mapie wiadomości.

  - `CMFCMaskedEdit::OnClear`wartość nie została zmieniona na wartość bez parametrów (WPARAM, LPARAM), tak aby nowe makro ON_WM_CLEAR może być używane w mapie wiadomości.

  - `CMFCMaskedEdit::OnPaste`wartość nie została zmieniona na wartość bez parametrów (WPARAM, LPARAM), tak aby nowe makro ON_WM_PASTE może być używane w mapie wiadomości.

- `#ifdef`dyrektywy w plikach nagłówkowych MFC są usuwane. Liczne `#ifdef` dyrektywy w plikach nagłówkowych MFC związane z nieobsługiwanymi wersjami systemu Windows (winver &lt; 0x0501) są usuwane.

- Biblioteka DLL ATL (atl120.dll) jest usuwana. ATL jest obecnie dostarczany jako nagłówki i biblioteka statyczna (atls.lib).

- Atlsd. lib, atlsn. lib i atlsnd. lib są usuwane. Atls.lib nie ma już zależności zestawu znaków ani kodu, który jest specyficzny dla wersji do debugowania/oficjalnych. Ponieważ działa tak samo dla Unicode/ANSI i wersji do debugowania/oficjalnych, wymagana jest tylko jedna wersja biblioteki.

- Narzędzie śledzenia ATL/MFC jest usuwane razem z biblioteką DLL ATL, a mechanizm śledzenia jest uproszczony. `CTraceCategory`Konstruktor przyjmuje teraz jeden parametr (nazwa kategorii), a makra śledzenia wywołują funkcje raportowania debugowania CRT.

## <a name="visual-studio-2012-breaking-changes"></a>Zmiany w programie Visual Studio 2012

### <a name="compiler"></a>Compiler

- `/Yl`Zmieniono opcję kompilatora. Domyślnie kompilator używa tej opcji, co może prowadzić do LNK2011 błędów w pewnych warunkach. Aby uzyskać więcej informacji, zobacz [/yl (wstrzyknięcie odwołania PCH do biblioteki debugowania)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- W kodzie, który jest kompilowany przy użyciu `/clr` , słowo kluczowe **enum** Class definiuje wyliczenie języka c++ 11, a nie Wyliczenie środowiska uruchomieniowego języka wspólnego (CLR). Aby zdefiniować Wyliczenie CLR, musisz być jawne o dostępności.

- Użyj słowa kluczowego szablonu, aby jawnie odróżnić nazwę zależną (zgodność standardu języka C++). W poniższym przykładzie słowo kluczowe wyróżnionego szablonu jest obowiązkowe, aby usunąć niejednoznaczność. Aby uzyskać więcej informacji, zobacz [rozpoznawanie nazw dla typów zależnych](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Stałe wyrażenie typu float nie jest już dozwolone jako argument szablonu, jak pokazano w poniższym przykładzie.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Kod, który jest kompilowany przy użyciu `/GS` opcji wiersza polecenia i który ma lukę w trybie wyłączności może prowadzić do zakończenia procesu w czasie wykonywania, jak pokazano w poniższym przykładzie pseudokodzie.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Domyślna architektura kompilacji x86 została zmieniona na SSE2; w związku z tym kompilator może emitować instrukcje SSE i używać rejestrów XMM do wykonywania obliczeń zmiennoprzecinkowych. Jeśli chcesz przywrócić poprzednie zachowanie, użyj `/arch:IA32` flagi kompilatora, aby określić architekturę jako ia32.

- Kompilator może wystawić ostrzeżenia [kompilatora ostrzeżeń (poziom 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) i C4701, gdzie wcześniej nie było. Kompilator stosuje silniejsze sprawdzenia do użycia niezainicjowanych zmiennych lokalnych typu wskaźnika.

- Po określeniu nowej flagi konsolidatora `/HIGHENTROPYVA` system Windows 8 zwykle powoduje, że alokacje pamięci będą zwracały adres 64-bitowy. W systemach starszych niż Windows 8 takie przydzielanie często zwracanych adresów, które były mniejsze niż 2 GB. Ta zmiana może ujawnić błędy obcinania wskaźnika w istniejącym kodzie. Domyślnie ten przełącznik jest włączony. Aby wyłączyć to zachowanie, określ `/HIGHENTROPYVA:NO` .

- Zarządzany kompilator (Visual Basic/C#) obsługuje również `/HIGHENTROPYVA` kompilacje zarządzane.  Jednak w tym przypadku `/HIGHENTROPYVAswitch` jest on domyślnie wyłączony.

### <a name="ide"></a>IDE

- Chociaż nie zaleca się tworzenia aplikacji Windows Forms w języku C++/CLI, obsługiwane są konserwacje istniejących aplikacji interfejsu użytkownika języka C++/CLI. Jeśli musisz utworzyć aplikację Windows Forms lub dowolną inną aplikację interfejsu użytkownika platformy .NET, Użyj języka C# lub Visual Basic. Używaj języka C++/CLI tylko do celów współdziałania.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Biblioteka równoległych wzorców i Biblioteka środowisko uruchomieniowe współbieżności

`SchedulerType`Wyliczenie `UmsThreadDefault` jest przestarzałe. Specyfikacja `UmsThreadDefault` zwraca przestarzałe ostrzeżenie i wewnętrznie mapuje z powrotem do `ThreadScheduler` .

### <a name="standard-library"></a>Standardowa biblioteka

- Po rozróżnieniu między standardami C++ 98/03 i C++ 11 przy użyciu jawnych argumentów szablonu do wywołania `make_pair()` — jak w przypadku `make_pair<int, int>(x, y)` — zwykle nie kompiluje się w Visual C++ w programie Visual Studio 2012. Rozwiązaniem jest zawsze wywoływanie `make_pair()` bez jawnych argumentów szablonu — tak jak w przypadku `make_pair(x, y)` . Dostarczanie jawnych argumentów szablonu zakłóca przeznaczenie funkcji. Jeśli potrzebujesz precyzyjnej kontroli nad typem wyniku, użyj `pair` zamiast tego `make_pair` — jako w `pair<short, short>(int1, int2)` .

- Inna nieprzerwana zmiana między standardami C++ 98/03 i C++ 11: gdy program jest niejawnie konwertowany na B i B jest niejawnie konwertowany na C, ale nie jest niejawnie konwertowany na C, C++ 98/03 i Visual Studio 2010 dozwolony `pair<A, X>` do przekonwertowania (niejawnie lub jawnie) do `pair<C, X>` . (Inny typ, X, nie jest interesujący w tym miejscu i nie jest specyficzny dla pierwszego typu pary). Kompilator języka C++ w programie Visual Studio 2012 wykrywa, że nie jest niejawnie konwertowany na C i usuwa konwersję pary z rozpoznawania przeciążenia. Ta zmiana jest dodatnia dla wielu scenariuszy. Na przykład Przeciążenie `func(const pair<int, int>&)` i `func(const pair<string, string>&)` , i wywołanie `func()` with `pair<const char *, const char *>` zostanie skompilowane z tą zmianą. Jednak ta zmiana powoduje przerwanie kodu, który opiera się na przeliczeniu agresywnych par. Taki kod można zazwyczaj naprawić, wykonując jedną część konwersji jawnie — na przykład przez przekazanie `make_pair(static_cast<B>(a), x)` do funkcji, która oczekuje `pair<C, X>` .

- Symulowane szablony wariadyczne programu Visual Studio 2010 — na przykład `make_shared<T>(arg1, arg2, argN)` — do limitu 10 argumentów przez wyczyszczenie przeciążenia i specjalizacji z maszynami preprocesora. W programie Visual Studio 2012 ten limit jest redukowany do pięciu argumentów w celu zwiększenia czasu kompilacji i zużycia pamięci przez kompilator dla większości użytkowników. Można jednak ustawić poprzedni limit, jawnie definiując _VARIADIC_MAX jako 10, cały projekt.

- C++ 11 17.6.4.3.1 [Macro. Names]/2 uniemożliwia zastępowanie makr słowami kluczowymi w przypadku uwzględnienia nagłówków standardowej biblioteki C++. Nagłówki teraz emitują błędy kompilatora, jeśli wykryją słowa kluczowe zastępujące makra. (Definiowanie _ALLOW_KEYWORD_MACROS umożliwia kompilowanie kodu, ale zdecydowanie odradza to użycie). Jako wyjątek, forma makro `new` jest domyślnie dozwolona, ponieważ nagłówki są wszechstronnie obronne przy użyciu `#pragma push_macro("new")` / `#undef new` / `#pragma pop_macro("new")` . Zdefiniowanie _ENFORCE_BAN_OF_MACRO_NEW ma dokładnie znaczenie jego nazwy.

- Aby zaimplementować różne optymalizacje i sprawdzenia debugowania, implementacja standardowej biblioteki języka C++ zacelowo przerywa zgodność binarną między wersjami programu Visual Studio (2005, 2008, 2010, 2012). Gdy standardowa biblioteka języka C++ jest używana, zabrania mieszania plików obiektów i bibliotek statycznych, które są kompilowane przy użyciu różnych wersji w jeden plik binarny (EXE lub DLL) i uniemożliwia przekazywanie obiektów biblioteki standardowej języka C++ między plikami binarnymi, które są kompilowane przy użyciu różnych wersji. Mieszanie plików obiektów i bibliotek statycznych (przy użyciu standardowej biblioteki języka C++, która została skompilowana przy użyciu programu Visual Studio 2010 z tymi, które zostały skompilowane przy użyciu kompilatora języka C++ w programie Visual Studio 2012 emitują błędy konsolidatora dotyczące niezgodności _MSC_VER, gdzie _MSC_VER jest makrem zawierającym wersję główną kompilatora (1700 for Visual C++ w programie Visual Studio 2012). Ten test nie może wykryć mieszania DLL i nie może wykryć mieszania, które obejmuje program Visual Studio 2008 lub jego wcześniejszą.

- Oprócz wykrywania _ITERATOR_DEBUG_LEVEL niezgodności, które zostały zaimplementowane w programie Visual Studio 2010, kompilator języka C++ w programie Visual Studio 2012 wykrywa niezgodności biblioteki środowiska uruchomieniowego. Te niezgodności występują, gdy opcje kompilatora `/MT` (wydanie statyczne), `/MTd` (debugowanie statyczne), `/MD` (wydanie dynamiczne) i `/MDd` (debugowanie dynamiczne) są mieszane.

- `operator<()`, `operator>()` , `operator<=()` , i `operator>=()` były wcześniej dostępne dla `std::unordered_map` i `stdext::hash_map` rodzin kontenerów, chociaż ich implementacje nie były użyteczne. Te operatory niestandardowe zostały usunięte w Visual C++ w programie Visual Studio 2012. Ponadto implementacja programu `operator==()` i `operator!=()` dla `std::unordered_map` rodziny została rozszerzona w celu pokrycia `stdext::hash_map` rodziny. (Zalecamy uniknięcie używania `stdext::hash_map` rodziny w nowym kodzie).

- C++ 11 22.4.1.4 [locale. codecvt] określa, że `codecvt::length()` i `codecvt::do_length()` powinny przyjmować modyfikowalne `stateT&` Parametry, ale program Visual Studio 2010 trwał `const stateT&` . Kompilator języka C++ w programie Visual Studio 2012 przyjmuje `stateT&` zgodnie z zaleceniami Standard. Różnica ta jest istotna dla każdego, kto próbuje zastąpić funkcję wirtualną `do_length()` .

### <a name="crt"></a>CRT

- Sterta środowiska uruchomieniowego języka C (CRT), która jest używana dla nowych i malloc (), nie jest już prywatna. CRT używa teraz sterty procesu. Oznacza to, że sterta nie jest niszczona, gdy biblioteka DLL jest zwolniona, więc biblioteki DLL, które łączą się statycznie z CRT, muszą zapewnić, że pamięć przydzieloną przez kod biblioteki DLL jest czyszczona przed jej wyładowaniem.

- `iscsymf()`Funkcja potwierdza z wartościami ujemnymi.

- `threadlocaleinfostruct`Struktura została zmieniona w celu uwzględnienia zmian w funkcjach regionalnych.

- Funkcje CRT, które mają odpowiednie elementy wewnętrzne, takie jak `memxxx()` , `strxxx()` są usuwane z intrin. h. Jeśli dołączono intrin. h tylko dla tych funkcji, musisz teraz uwzględnić odpowiednie nagłówki CRT.

### <a name="mfc-and-atl"></a>MFC i ATL

- Usunięto obsługę Fusion (afxcomctl32. h); w związku z tym wszystkie metody, które zostały zdefiniowane w programie, zostały \<afxcomctl32.h> usunięte. Pliki nagłówkowe \<afxcomctl32.h> i zostały \<afxcomctl32.inl> usunięte.

- Zmieniono nazwę `CDockablePane::RemoveFromDefaultPaneDividier` na `CDockablePane::RemoveFromDefaultPaneDivider` .

- Zmieniono sygnaturę programu `CFileDialog::SetDefExt` , aby używać LPCTSTR; w związku z tym dotyczy to kompilacji Unicode.

- Usunięto przestarzałe kategorie śledzenia ATL.

- Zmieniono sygnaturę, `CBasePane::MoveWindow` Aby wykonać `const CRect` .

- Zmieniono sygnaturę `CMFCEditBrowseCtrl::EnableBrowseButton` .

- Usunięto właściwości `m_fntTabs` i `m_fntTabsBold` z klasy `CMFCBaseTabCtrl`.

- Dodano parametr do `CMFCRibbonStatusBarPane` konstruktorów. (Jest to domyślny parametr, dlatego nie jest on odporny na źródła).

- Dodano parametr do `CMFCRibbonCommandsListBox` konstruktora. (Jest to domyślny parametr, dlatego nie jest on odporny na źródła).

- Usunięto `AFXTrackMouse` interfejs API (i powiązany z nim proces czasomierza). `TrackMouseEvent`Zamiast tego użyj interfejsu API Win32.

- Dodano parametr do `CFolderPickerDialog` konstruktora. (Jest to domyślny parametr, dlatego nie jest on odporny na źródła).

- `CFileStatus`Zmieniono rozmiar struktury: `m_attribute` element członkowski został zmieniony z Byte na DWORD (aby dopasować wartość zwracaną z `GetFileAttributes` ).

- `CRichEditCtrl`i `CRichEditView` użyj MSFTEDIT_CLASS (formant richedit 4,1), a nie RICHEDIT_CLASS (formant richedit 3,0) w kompilacjach Unicode.

- Usunięte `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` , ponieważ jest zawsze prawdziwe w systemach Windows Vista, Windows 7 i Windows 8.

- Usunięte `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` , ponieważ jest zawsze prawdziwe w systemach Windows Vista, Windows 7 i Windows 8.

- Usunięty `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea` . Wywołaj interfejs API systemu Windows bezpośrednio w systemach Windows Vista, Windows 7 i Windows 8.

- Usunięty `AFX_GLOBAL_DATA::DwmDefWindowProc` . Wywołaj interfejs API systemu Windows bezpośrednio w systemach Windows Vista, Windows 7 i Windows 8.

- Zmieniono nazwę `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` na, `IsDwmCompositionEnabled` Aby wyeliminować kolizję nazw.

- Zmieniono identyfikatory dla wielu wewnętrznych czasomierzy MFC i przeniesiono definicje do plik AFXRES. h (AFX_TIMER_ID_ *).

- Zmieniono sygnaturę `OnExitSizeMove` metody, aby zgadzać się z ON_WM_EXITSIZEMOVE makro:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Zmieniono nazwę i podpis, `OnDWMCompositionChanged` Aby wyrazić zgodę na ON_WM_DWMCOMPOSITIONCHANGED makro:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Zmieniono sygnaturę `OnMouseLeave` metody, aby zgadzać się z ON_WM_MOUSELEAVE makro:

  - `CMFCCaptionBar`

  - `CMFCColorBar`

  - `CMFCHeaderCtrl`

  - `CMFCProperySheetListBox`

  - `CMFCRibbonBar`

  - `CMFCRibbonPanelMenuBar`

  - `CMFCRibbonRichEditCtrl`

  - `CMFCSpinButtonCtrl`

  - `CMFCToolBar`ReplaceThisText

  - `CMFCToolBarComboBoxEdit`

  - `CMFCToolBarEditCtrl`

  - `CMFCAutoHideBar`

- Zmieniono sygnaturę, `OnPowerBroadcast` Aby wyrazić zgodę na ON_WM_POWERBROADCAST makro:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

- Zmieniono sygnaturę, `OnStyleChanged` Aby wyrazić zgodę na ON_WM_STYLECHANGED makro:

  - `CMFCListCtrl`

  - `CMFCStatusBar`

- Zmieniono nazwę metody wewnętrznej `FontFamalyProcFonts` na `FontFamilyProcFonts` .

- Usunięto liczne globalne `CString` obiekty statyczne w celu wyeliminowania przecieków pamięci w niektórych sytuacjach (zamieniono na #defines) i następujących zmiennych składowych klasy:

  - `CKeyBoardManager::m_strDelimiter`

  - `CMFCPropertyGridProperty::m_strFormatChar`

  - `CMFCPropertyGridProperty::m_strFormatShort`

  - `CMFCPropertyGridProperty::m_strFormatLong`

  - `CMFCPropertyGridProperty::m_strFormatUShort`

  - `CMFCPropertyGridProperty::m_strFormatULong`

  - `CMFCPropertyGridProperty::m_strFormatFloat`

  - `CMFCPropertyGridProperty::m_strFormatDouble`

  - `CMFCToolBarImages::m_strPngResType`

  - `CMFCPropertyGridProperty::m_strFormat`

- Zmieniono sygnaturę `CKeyboardManager::ShowAllAccelerators` i usunięto parametr ogranicznika akceleratora.

- Dodano `CPropertyPage::GetParentSheet` i w `CPropertyPage` klasie, wywołaj ją zamiast, `GetParent` Aby uzyskać poprawność okna nadrzędnego arkusza, które może być oknem nadrzędnym lub dziadkem do `CPropertyPage` . Może zajść konieczność zmiany kodu do wywołania `GetParentSheet` zamiast `GetParent` .

- Stałe niezrównoważone #pragma warning (push) w ATLBASE. H, co spowodowało nieprawidłowe wyłączenie ostrzeżeń. Te ostrzeżenia są teraz włączone prawidłowo po ATLBASE. Przeprowadzono analizę H.

- Przeniesiono metody D2D z AFX_GLOBAL_DATA do _AFX_D2D_STATE:

  - `GetDirectD2dFactory`

  - `GetWriteFactory`

  - `GetWICFactory`

  - `InitD2D`

  - `ReleaseD2DRefs`

  - `IsD2DInitialized`

  - `D2D1MakeRotateMatrix`

  - Zamiast wywoływania, na przykład, `afxGlobalData.IsD2DInitialized` Wywołaj `AfxGetD2DState->IsD2DInitialized` .

- Usunięto przestarzałą ATL *. Pliki CPP z folderu \atlmfc\include\

- Przeniesiono `afxGlobalData` inicjalizację na żądanie, a nie w czasie inicjacji CRT, aby spełnić `DLLMain` wymagania.

- Dodano `RemoveButtonByIndex` metodę do `CMFCOutlookBarPane` klasy.

- Poprawiono `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` do `IsFrequentlyUsedCmd` .

- Poprawiono kilka wystąpień `RestoreOriginalstate` do `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)` .

- Usunięto nieużywane metody z `CDockablePane` : `SetCaptionStyle` , `IsDrawCaption` ,, `IsHideDisabledButtons` `GetRecentSiblingPaneInfo` i `CanAdjustLayout` .

- Usunięto `CDockablePane` statyczne zmienne Członkowskie `m_bCaptionText` i `m_bHideDisabledButtons` .

- Dodano metodę przesłonięcia `DeleteString` do `CMFCFontComboBox` .

- Usunięto nieużywane metody z `CPane` : `GetMinLength` i `IsLastPaneOnLastRow` .

- Zmieniono nazwę `CPane::GetDockSiteRow(CDockingPanesRow *)` na `CPane::SetDockSiteRow` .

## <a name="visual-studio-2010-breaking-changes"></a>Zmiany w programie Visual Studio 2010

### <a name="compiler"></a>Compiler

- Słowo **kluczowe "** default" ma nowe domyślne znaczenie. Ze względu na to, że użycie starego znaczenia jest rzadki, ta zmiana nie wpłynie na większość aplikacji.

- Zostanie wprowadzone słowo kluczowe New **static_assert** , co spowoduje konflikt nazw, jeśli istnieje już identyfikator o tej nazwie w kodzie.

- Obsługa nowej notacji lambda wyklucza obsługę kodowania niecytowanego identyfikatora GUID w atrybucie UUID IDL.

- .NET Framework 4 wprowadza koncepcję uszkodzonych wyjątków stanu, które są wyjątkami, które opuszczają proces w nieodwracalnym stanie uszkodzonym. Domyślnie nie można przechwycić wyjątku uszkodzonego stanu, nawet z opcją kompilatora/EHa, która przechwytuje wszystkie inne wyjątki.                 Aby jawnie przechwycić wyjątek uszkodzonego stanu, użyj instrukcji __try- \_ _Except. Lub zastosuj atrybut [HandledProcessCorruptedStateExceptions], aby umożliwić funkcji przechwytywanie wyjątków stanu uszkodzonego.  Ta zmiana dotyczy głównie programistów systemów, którzy mogą potrzebować przechwycić wyjątek uszkodzonego stanu. Osiem wyjątków to STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, STATUS_UNWIND_CONSOLIDATE.                 Aby uzyskać więcej informacji na temat tych wyjątków, zobacz makro [GetExceptionCode](/windows/win32/Debug/getexceptioncode) .

- Poprawiono `/GS` ochronę opcji kompilatora przed przepełnieniem buforu bardziej kompleksowo niż w starszych wersjach. Ta wersja może wstawiać dodatkowe kontrole zabezpieczeń w stosie, które mogą obniżyć wydajność. Użyj `__declspec(safebuffers)` słowa kluczowego new, aby nakazać kompilatorowi niewstawianie kontroli zabezpieczeń dla określonej funkcji.

- Jeśli kompilujesz przy użyciu `/GL` opcji kompilatora (Optymalizacja całego programu) i `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego), `/GL` opcja jest ignorowana. Ta zmiana została wprowadzona ze względu na niewielką korzyść z opcji kompilatora. W wyniku tej zmiany wydajność kompilacji jest ulepszona.

- Domyślnie obsługa trigraphs jest wyłączona w programie Visual Studio 2010. Użyj `/Zc:trigraphs` opcji kompilatora, aby włączyć obsługę trigraphs. Trójznaków składa się z dwóch następujących po sobie znaków zapytania ("??"), po których następuje unikatowy trzeci znak. Kompilator zastępuje trójznaków z odpowiadającym znakiem interpunkcji. Na przykład kompilator zastępuje `??=` trójznaków znakiem "#". Używaj trigraphs w plikach źródłowych języka C, które używają zestawu znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych.

- Konsolidator nie obsługuje już optymalizacji dla systemu Windows 98. `/OPT`Opcja (Optymalizacja) powoduje błąd czasu kompilacji, jeśli określono `/OPT:WIN98` lub `/OPT:NOWIN98` .

- Domyślne opcje kompilatora, które są określone przez właściwości systemu kompilacji RuntimeLibrary i DebugInformationFormat, zostały zmienione. Domyślnie te właściwości kompilacji są określone w projektach, które są tworzone przez Visual C++ wersje 7,0 do 10,0. W przypadku migrowania projektu, który został utworzony przez Visual C++ 6,0, należy rozważyć, czy należy określić wartość tych właściwości.

- W programie Visual Studio 2010, RuntimeLibrary = wielowątkowe ( `/MD` ) i DebugInformationFormat = ProgramDatabase ( `/Zi` ). W Visual C++ 9,0 RuntimeLibrary = wielowątkowe ( `/MT` ) i DebugInformationFormat = Disabled.

### <a name="clr"></a>CLR

- Kompilatory Microsoft C# i Visual Basic mogą teraz tworzyć bez podstawowego zestawu międzyoperacyjnego (bez PIA). Zestaw bez PIA może korzystać z typów COM bez wdrażania odpowiedniego podstawowego zestawu międzyoperacyjnego (PIA). Podczas konsumowania zestawów bez PIA utworzonych przez Visual C# lub Visual Basic, należy odwołać się do zestawu PIA w poleceniu Kompiluj przed odwołaniem do dowolnego zestawu bez PIA, który używa biblioteki.

### <a name="visual-studio-c-projects-and-msbuild"></a>Visual Studio C++ — projekty i MSBuild

- Projekty Visual Studio C++ są teraz oparte na narzędziu MSBuild. W związku z tym pliki projektu używają nowego formatu pliku XML i sufiksu pliku. vcxproj. Program Visual Studio 2010 automatycznie konwertuje pliki projektu z wcześniejszych wersji programu Visual Studio do nowego formatu pliku. Istniejący projekt jest narażony, jeśli zależy od poprzedniego narzędzia kompilacji, VCBUILD.exe lub sufiksu pliku projektu,. vcproj.

- We wcześniejszych wersjach Visual C++ była obsługiwana opóźniona Ocena arkuszy właściwości. Na przykład nadrzędny arkusz właściwości może zaimportować podrzędny arkusz właściwości, a element nadrzędny może użyć zmiennej zdefiniowanej w elemencie podrzędnym, aby zdefiniować inne zmienne. Funkcja późnej oceny włączyła element nadrzędny do używania zmiennej podrzędnej nawet przed zaimportowaniem podrzędnego arkusza właściwości. W programie Visual Studio 2010 zmienna arkusza projektu nie może zostać użyta przed zdefiniowaniem, ponieważ MSBuild obsługuje tylko wczesną ocenę.

### <a name="ide"></a>IDE

- Okno dialogowe zakończenie aplikacji nie kończy już aplikacji. W poprzednich wersjach, gdy `abort()` Funkcja lub `terminate()` zamknął kompilację sprzedaży detalicznej aplikacji, biblioteka uruchomieniowa C wyświetla komunikat zakończenia aplikacji w oknie konsoli lub w oknie dialogowym. Komunikat wymieniony w części "Ta aplikacja zażądała środowiska uruchomieniowego w nietypowy sposób. Aby uzyskać więcej informacji, skontaktuj się z zespołem pomocy technicznej aplikacji ". Komunikat o wygaśnięciu aplikacji został nadmiarowy, ponieważ system Windows wyświetli w tym czasie bieżącą procedurę obsługi zakończenia, która zwykle jest oknem dialogowym Raportowanie błędów systemu Windows (Dr Watson) lub debugerem programu Visual Studio. Począwszy od programu Visual Studio 2010, Biblioteka wykonawcza C nie wyświetla komunikatu. Ponadto środowisko uruchomieniowe uniemożliwia zakończenie działania aplikacji przed uruchomieniem debugera. Jest to istotne zmiany tylko wtedy, gdy zależą od poprzedniego zachowania komunikatu o zakończeniu aplikacji.

- W odniesieniu do programu Visual Studio 2010 funkcja IntelliSense nie działa dla kodu lub atrybutów C++/CLI, funkcja **find all References** nie działa w przypadku zmiennych lokalnych, a model kodu nie pobiera nazw typów z importowanych zestawów ani nie rozpoznaje typów do ich w pełni kwalifikowanych nazw.

### <a name="libraries"></a>Biblioteki

- Klasa SafeInt jest dołączona do Visual C++ i nie jest już w osobnym pobieraniu. Jest to istotna zmiana tylko wtedy, gdy opracowano klasę o nazwie "SafeInt".

- Model wdrażania bibliotek nie używa już manifestów, aby znaleźć określoną wersję biblioteki dołączanej dynamicznie. Zamiast tego, Nazwa każdej biblioteki dołączanej dynamicznie zawiera numer wersji, a ta nazwa jest używana do lokalizowania biblioteki.

- W poprzednich wersjach programu Visual Studio można skompilować biblioteki czasu wykonywania. Program Visual Studio 2010 nie obsługuje już tworzenia własnych kopii plików biblioteki czasu wykonywania języka C.

### <a name="standard-library"></a>Standardowa biblioteka

- \<iterator>Nagłówek nie jest już automatycznie dołączany przez wiele innych plików nagłówkowych. Zamiast tego należy jawnie dołączyć ten nagłówek, jeśli wymagana jest obsługa iteratorów autonomicznych zdefiniowanych w nagłówku. Istniejący projekt jest narażony, jeśli zależy od poprzedniego narzędzia kompilacji, VCBUILD.exe lub sufiksu pliku projektu,. vcproj. iterator.

- W \<algorithm> nagłówku funkcje checked_ * i unchecked_ \* są usuwane. I w \<iterator> nagłówku> `checked_iterator` Klasa jest usuwana, a `unchecked_array_iterator` Klasa została dodana.

- `CComPtr::CComPtr(int)`Konstruktor jest usuwany. Ten konstruktor zezwolił `CComPtr` obiektowi na skonstruowanie z makra o wartości null, ale był niepotrzebny i dopuszczał bezsensownie konstrukcji z niezerowych liczb całkowitych.

   `CComPtr`Nadal można utworzyć z wartości null, która jest zdefiniowana jako 0, ale nie powiedzie się, jeśli zostanie skonstruowana z liczbą całkowitą inną niż Literal 0. Zamiast tego użyj **nullptr** .

- Następujące `ctype` funkcje członkowskie zostały usunięte: `ctype::_Do_narrow_s` , `ctype::_Do_widen_s` , `ctype::_narrow_s` , `ctype::_widen_s` . Jeśli aplikacja korzysta z jednej z tych funkcji Członkowskich, należy zamienić ją na odpowiadającą jej wersję niebezpieczną: `ctype::do_narrow` , `ctype::do_widen` , `ctype::narrow` , `ctype::widen` .

### <a name="crt-mfc-and-atl-libraries"></a>Biblioteki CRT, MFC i ATL

- Pomoc techniczna została usunięta, aby użytkownicy mogli tworzyć biblioteki CRT, MFC i ATL. Na przykład nie jest dostępny żaden odpowiedni plik NMAKE. Jednak użytkownicy nadal mają dostęp do kodu źródłowego dla tych bibliotek. A dokument opisujący Opcje programu MSBuild, których firma Microsoft używa do kompilowania tych bibliotek, prawdopodobnie zostanie opublikowany w blogu zespołu Visual C++.

- Obsługa biblioteki MFC dla systemu IA64 została usunięta. Jednak nadal jest dostępna obsługa CRT i ATL na IA64.

- Liczby porządkowe nie są już ponownie używane w plikach definicji modułu MFC (. def). Ta zmiana oznacza, że liczby porządkowe nie będą się różnić między wersjami pomocniczymi, a ponadto zostanie ulepszona zgodność binarna z dodatkami Service Pack i krótkimi rozwiązaniami do inżynierów.

- Do klasy została dodana nowa funkcja wirtualna `CDocTemplate` . Ta nowa funkcja wirtualna jest [klasą CDocTemplate](../mfc/reference/cdoctemplate-class.md). Poprzednia wersja `OpenDocumentFile` ma dwa parametry. Nowa wersja ma trzy parametry. Aby zapewnić obsługę Menedżera ponownego uruchamiania, każda klasa pochodna `CDocTemplate` musi implementować wersję, która ma trzy parametry. Nowy parametr to `bAddToMRU` .

### <a name="macros-and-environment-variables"></a>Makra i zmienne środowiskowe

- Zmienna środowiskowa __MSVCRT_HEAP_SELECT nie jest już obsługiwana. Ta zmienna środowiskowa jest usuwana i nie ma żadnych zastąpień.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

- Kilka dyrektyw zostało usuniętych z kompilatora odwołania asemblera makr firmy Microsoft. Dyrektywy usunięte to,,,,, `.186` `.286` `.286P` `.287` `.8086` `.8087` i `.NO87` .

## <a name="visual-studio-2008-breaking-changes"></a>Zmiany w programie Visual Studio 2008

### <a name="compiler"></a>Compiler

- Platformy Windows 95, Windows 98, Windows ME i Windows NT nie są już obsługiwane. Te systemy operacyjne zostały usunięte z listy platform dokierowanych.

- Kompilator nie obsługuje już wielu atrybutów, które zostały bezpośrednio skojarzone z serwerem ATL. Następujące atrybuty nie są już obsługiwane:

  - perf_counter

  - perf_object

  - monitora wydajności

  - request_handler

  - soap_handler

  - soap_header

  - soap_method

  - tag_name

### <a name="visual-studio-c-projects"></a>Projekty Visual Studio C++

- Podczas uaktualniania projektów z poprzednich wersji programu Visual Studio może zajść potrzeba zmodyfikowania makra WINVER i _WIN32_WINNT w taki sposób, aby były większe lub równe 0x0500.

- Począwszy od programu Visual Studio 2008, Kreator nowego projektu nie ma opcji tworzenia projektu programu C++ SQL Server. Projekty SQL Server utworzone przy użyciu wcześniejszej wersji programu Visual Studio będą nadal kompilowane i działały prawidłowo.

- Plik nagłówkowy interfejsu API systemu Windows Winable. h został usunięty. Zamiast tego Dołącz Winuser. h.

- Biblioteka interfejsu API systemu Windows Rpcndr. lib została usunięta. Zamiast tego Połącz z rpcrt4. lib.

### <a name="crt"></a>CRT

- System Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4,0 został usunięty.

- Następujące zmienne globalne zostały usunięte:

  - _osplatform

  - _osver

  - _winmajor

  - _winminor

  - _winver

- Następujące funkcje zostały usunięte. Zamiast tego użyj funkcji interfejsu API systemu Windows `GetVersion` `GetVersionEx` :

  - _get_osplatform

  - _get_osver

  - _get_winmajor

  - _get_winminor

  - _get_winver

- Składnia adnotacji SAL została zmieniona. Aby uzyskać więcej informacji, zobacz [Adnotacje sal](../c-runtime-library/sal-annotations.md).

- Filtr IEEE obsługuje teraz zestaw instrukcji SSE 4,1. Aby uzyskać więcej informacji, zobacz [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Biblioteki wykonawcze C dostarczane z programem Visual Studio nie są już zależne od msvcrt.dll systemowej biblioteki DLL.

### <a name="standard-library"></a>Standardowa biblioteka

- System Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4,0 został usunięty.

- Podczas kompilowania w trybie debugowania z _HAS_ITERATOR_DEBUGGING zdefiniowanych (zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po wystąpieniu programu Visual Studio 2010) aplikacja zostanie teraz potwierdzona, gdy ITERATOR próbuje zwiększyć lub zmniejszyć poza granice bazowego kontenera.

- Zmienna elementu członkowskiego c klasy stosu jest teraz zadeklarowana jako chroniona. Wcześniej ta zmienna członkowska została zadeklarowana jako publiczna.

- Zachowanie `money_get::do_get` zostało zmienione. Wcześniej podczas analizowania kwoty pieniężnej o większej liczbie ułamków niż jest to wywołane przez `frac_digits` , `do_get` używane do korzystania z nich. Teraz można `do_get` zatrzymać analizowanie po użyciu najwyżej `frac_digits` znaków.

### <a name="atl"></a>ATL

- Nie można skompilować biblioteki ATL bez zależności w CRT. We wcześniejszych wersjach programu Visual Studio można użyć ATL_MIN_CRT #define, aby projekt ATL był minimalny zależny od CRT. W programie Visual Studio 2008 wszystkie projekty ATL są w minimalnym stopniu zależne od CRT, niezależnie od tego, czy ATL_MIN_CRT jest zdefiniowany.

- Baza kodu ATL Server została wydana jako udostępniony projekt źródłowy w programie CodePlex i nie jest zainstalowana jako część programu Visual Studio. Klasy kodowania i dekodowania danych z atlenc. h i funkcje narzędzi oraz klasy z atlutil. h i atlpath. h zostały zachowane i są teraz częścią biblioteki ATL. Kilka plików skojarzonych z serwerem ATL nie jest już częścią programu Visual Studio.

- Niektóre funkcje nie są już zawarte w bibliotece DLL. Nadal znajdują się one w bibliotece importu. Nie ma to wpływu na kod, który używa funkcji statycznie. Będzie to miało wpływ tylko na kod, który używa tych funkcji dynamicznie.

- Makra PROP_ENTRY i PROP_ENTRY_EX zostały wycofane i zastąpione makrami PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX ze względów bezpieczeństwa.

### <a name="atlmfc-shared-classes"></a>Klasy współdzielone ATL/MFC

- Nie można skompilować biblioteki ATL bez zależności w CRT. We wcześniejszych wersjach programu Visual Studio można użyć, `#define ATL_MIN_CRT` Aby Projekt ATL był minimalny zależny od CRT. W programie Visual Studio 2008 wszystkie projekty ATL są w minimalnym stopniu zależne od CRT, niezależnie od tego, czy ATL_MIN_CRT jest zdefiniowany.

- Baza kodu ATL Server została wydana jako udostępniony projekt źródłowy w programie CodePlex i nie jest zainstalowana jako część programu Visual Studio. Klasy kodowania i dekodowania danych z atlenc. h i funkcje narzędzi oraz klasy z atlutil. h i atlpath. h zostały zachowane i są teraz częścią biblioteki ATL. Kilka plików skojarzonych z serwerem ATL nie jest już częścią programu Visual Studio.

- Niektóre funkcje nie są już zawarte w bibliotece DLL. Nadal znajdują się one w bibliotece importu. Nie ma to wpływu na kod, który używa funkcji statycznie. Będzie to miało wpływ tylko na kod, który używa tych funkcji dynamicznie.

### <a name="mfc"></a>MFC

- `CTime`Klasa: `CTime` Klasa akceptuje daty zaczynające się od 1/1/1900 0001 zamiast 1/1/1970 0001

- Kolejność tabulacji kontrolek w oknach dialogowych MFC: poprawna kolejność tabulacji w oknie dialogowym MFC jest zakłócona, jeśli formant ActiveX MFC zostanie wstawiony w kolejności tabulacji. Ta zmiana rozwiązuje ten problem.

   Na przykład Utwórz aplikację okna dialogowego MFC z kontrolką ActiveX i kilkoma kontrolkami edycji. Umieść formant ActiveX w środku kolejności tabulacji w kontrolkach edycji. Uruchom aplikację, kliknij kontrolkę Edycja, której kolejność tabulacji jest późniejsza od kontrolki ActiveX, a następnie kartę. przed tą zmianą fokus został przeszedł do kontrolki edycji po kontrolce ActiveX zamiast następnej kontrolki edycji w kolejności tabulacji.

- `CFileDialog`Klasa: nie można automatycznie przenieść szablonów niestandardowych dla `CFileDialog` klasy do systemu Windows Vista. Nadal można korzystać z nich, ale nie będą one mieć dodatkowych możliwości ani wyglądu okien dialogowych stylów systemu Windows Vista.

- `CWnd`Klasa i `CFrameWnd` Klasa: `CWnd::GetMenuBarInfo` Metoda została usunięta.

   `CFrameWnd::GetMenuBarInfo`Metoda jest teraz metodą niewirtualną. Aby uzyskać więcej informacji, zobacz **Funkcja GetMenuBarInfo** w Windows SDK.

- Obsługa interfejsu ISAPI MFC: MFC nie obsługuje już kompilowania aplikacji przy użyciu interfejsu programowania aplikacji (ISAPI) serwera internetowego. Jeśli chcesz skompilować aplikację ISAPI, wywołaj rozszerzenia ISAPI bezpośrednio.

- Przestarzałe interfejsy API ANSI: wersje ANSI kilku metod MFC są przestarzałe. Używaj wersji Unicode tych metod w przyszłych aplikacjach. Aby uzyskać więcej informacji, zobacz **wymagania dotyczące kompilacji dla wspólnych kontrolek systemu Windows Vista**.

## <a name="visual-studio-2005-breaking-changes"></a>Zmiany w programie Visual Studio 2005

### <a name="crt"></a>CRT

- Wiele funkcji jest przestarzałych. Zobacz **przestarzałe funkcje CRT**.

- Wiele funkcji sprawdza teraz poprawność swoich parametrów i zatrzymuje wykonywanie, jeśli podano nieprawidłowe parametry. Ta Walidacja może spowodować uszkodzenie kodu, który przekazuje nieprawidłowe parametry i polega na tym, że pomija on funkcję lub po prostu zwróci kod błędu. Zobacz **Walidacja parametrów**.

- Plik deskryptora pliku-2 jest teraz używany do wskazania, że `stdout` i `stderr` nie jest dostępny do danych wyjściowych, na przykład w aplikacji systemu Windows, która nie ma okna konsoli. Użyta Poprzednia wartość to-1. Aby uzyskać więcej informacji, zobacz [_fileno](../c-runtime-library/reference/fileno.md).

- Usunięto jednowątkowe biblioteki CRT (libc. lib i libcd. lib). Korzystaj z bibliotek CRT wielowątkowych. `/ML`Flaga kompilatora nie jest już obsługiwana. Niektóre funkcje, które nie zostały zablokować, zostały dodane w przypadkach, gdy różnica wydajności między kodem wielowątkowym a kodem jednowątkowym jest potencjalnie znacząca.

- Przeciążanie pow, podwójne pow (int, int), zostało usunięte w celu lepszego zgodności ze standardem.

- Specyfikator formatu% n nie jest już obsługiwany domyślnie w żadnej z printfch funkcji, ponieważ jest on niezabezpieczony. Jeśli wystąpił błąd% n, domyślnym zachowaniem jest wywołanie procedury obsługi nieprawidłowego parametru. Aby włączyć obsługę% n, użyj `_set_printf_count_output` (również zobacz `_get_printf_count_output` ).

- `sprintf`teraz drukuje znak minus znaku podpisanego zero.

- `swprintf`został zmieniony tak, aby był zgodny ze standardem; teraz wymaga parametru size. Forma `swprintf` bez parametru size jest przestarzała.

- `_set_security_error_handler`został usunięty. Usuń wszystkie wywołania tej funkcji; domyślna procedura obsługi jest znacznie bezpieczniejszym sposobem postępowania z błędami zabezpieczeń.

- `time_t`jest teraz wartością 64-bitową (chyba że _USE_32BIT_TIME_T jest zdefiniowana).

- `_spawn`Funkcje, które `_wspawn` teraz opuszczają `errno` Niepowodzenie, zgodnie z opisem w standardzie C.

- W usłudze RTC są teraz domyślnie stosowane znaki dwubajtowe.

- Funkcje obsługi słów zmiennoprzecinkowych są przestarzałe dla aplikacji skompilowanych za pomocą `/CLR` lub `/CLR:PURE` . Odpowiednie funkcje to,,,,, `_clear87` `_clearfp` `_control87` `_controlfp` `_fpreset` `_status87` `_statusfp` . Można wyłączyć ostrzeżenie o zaniechaniu przez zdefiniowanie _CRT_MANAGED_FP_NO_DEPRECATE, ale używanie tych funkcji w kodzie zarządzanym jest nieprzewidywalne i nieobsługiwane.

- Niektóre funkcje teraz zwracają wskaźniki const. Stare zachowanie niestałe może zostać przywrócone przez zdefiniowanie _CONST_RETURN. Uwzględnione funkcje są

  - memchr, wmemchr

  - strchr, wcschr, _mbschr, _mbschr_l

  - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

  - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

  - strstr, wcsstr, _mbsstr, _mbsstr_l

- Podczas łączenia z setargv. obj lub Wsetargv. obj nie można już pominąć rozszerzania symbolu wieloznacznego w wierszu polecenia, umieszczając go w podwójnych cudzysłowach. Aby uzyskać więcej informacji, zobacz [Rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Biblioteka standardowa (2005)

- Klasa wyjątku (znajdująca się w \<exception> nagłówku) została przeniesiona do `std` przestrzeni nazw. W poprzednich wersjach Ta klasa znajdowała się w globalnej przestrzeni nazw. Aby rozwiązać wszelkie błędy wskazujące, że nie można znaleźć klasy wyjątku, Dodaj następującą instrukcję using do kodu:`using namespace std;`

- Podczas wywoływania `valarray::resize()` , zawartość `valarray` zostanie utracona i zostanie zastąpiona wartościami domyślnymi. `resize()`Metoda ma na celu ponowne zainicjowanie, `valarray` a nie powiększenie, tak jak wektor.

- Iteratory debugowania: Aplikacje skompilowane przy użyciu wersji debugowej biblioteki środowiska uruchomieniowego C i, które niepoprawnie używają iteratorów, mogą zacząć zobaczyć potwierdzenia w czasie wykonywania. Aby wyłączyć te potwierdzenia, należy zdefiniować _HAS_ITERATOR_DEBUGGING (zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po wystąpieniu programu Visual Studio 2010) do 0. Aby uzyskać więcej informacji, zobacz [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Zmiany w Visual C++ .NET 2003

### <a name="compiler"></a>Compiler

- Nawiasy zamykające są teraz wymagane dla zdefiniowanej dyrektywy preprocesora (C2004).

- Jawne specjalizacje nie szukają już parametrów szablonu z szablonu podstawowego ([błąd kompilatora C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Dostęp do chronionej składowej (n) można uzyskać tylko za pośrednictwem funkcji składowej klasy (B), która dziedziczy z klasy (A), z której jest elementem członkowskim ([błąd kompilatora C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Ulepszone sprawdzanie dostępności w kompilatorze wykrywa teraz niedostępne klasy bazowe ([błąd kompilatora C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Nie można przechwycić wyjątku, jeśli destruktor i/lub Konstruktor kopiujący są niedostępne (C2316).

- Domyślne argumenty wskaźników do funkcji, które nie są już dozwolone ([błąd kompilatora C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Nie można zainicjować statycznej składowej danych za pośrednictwem klasy pochodnej ([błąd kompilatora C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- Inicjalizacja **typedef** nie jest dozwolona przez Standard i teraz generuje błąd kompilatora ([błąd kompilatora C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- wartość **logiczna** jest teraz odpowiednim typem ([błąd kompilatora C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- Element UDC może teraz tworzyć niejednoznaczność ze przeciążonymi operatorami ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Więcej wyrażeń jest teraz uważanych za prawidłowe stałe wskaźnika o wartości null ([błąd kompilatora C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- <> szablonu jest teraz wymagane w miejscach, w których kompilator wcześniej go sugeruje ([błąd kompilatora C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Jawna specjalizacja funkcji składowej poza klasą jest nieprawidłowa, jeśli funkcja została już jawnie wyspecjalizowana za pośrednictwem specjalizacji klas szablonu ([błąd kompilatora C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Parametry szablonu bez typu zmiennoprzecinkowego nie są już dozwolone ([błąd kompilatora C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Szablony klas nie są dozwolone jako argumenty typu szablonu (C3206).

- Nazwy funkcji zaprzyjaźnionych nie są już wprowadzane do zawieraj przestrzeni nazw ([błąd kompilatora C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Kompilator nie będzie już akceptować dodatkowych przecinków w makrze (C4002).

- Obiekt typu POD skonstruowane z inicjatorem formularza () zostanie zainicjowany domyślnie (C4345).

- Właściwość TypeName jest teraz wymagana, jeśli nazwa zależna ma być traktowana jako typ ([Ostrzeżenie kompilatora (poziom 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funkcje, które były nieprawidłowo uznawane za specjalizacje szablonu, nie są już uznawane za (C4347).

- Nie można zainicjować statycznych składowych danych za pośrednictwem klasy pochodnej (C4356).

- Specjalizacja szablonu klasy musi być zdefiniowana przed użyciem w zwracanym typie ([Ostrzeżenie kompilatora (poziom 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Kompilator teraz raportuje kod nieosiągalny (C4702).

## <a name="see-also"></a>Zobacz też

[Co nowego w Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
