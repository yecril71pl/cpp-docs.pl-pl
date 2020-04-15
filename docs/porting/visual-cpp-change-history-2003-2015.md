---
title: Visual C++ — historia zmian w latach 2003–2015
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: a045b04e5a57e9963b2ad374fbdfdd533bde0a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374169"
---
# <a name="visual-c-change-history-2003---2015"></a>Visual C++ — historia zmian w latach 2003–2015

W tym artykule opisano wszystkie przełomowe zmiany z programu Visual Studio 2015 wracając do programu Visual Studio 2003, a w tym artykule terminy "nowe zachowanie" lub "teraz" odnoszą się do programu Visual Studio 2015 i nowszych. Terminy "stare zachowanie" i "przed" odnoszą się do programu Visual Studio 2013 i wcześniejszych wersji.

Aby uzyskać informacje na temat najnowszej wersji programu Visual Studio, zobacz [Co nowego w programie Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszeniach zgodności w programie Visual C++ w programie Visual Studio.](../overview/cpp-conformance-improvements.md)

> [!NOTE]
> Nie ma żadnych zmian podziału binarnego między programem Visual Studio 2015 i Visual Studio 2017.

Podczas uaktualniania do nowej wersji programu Visual Studio, może wystąpić błędy kompilacji i/lub środowiska wykonawczego w kodzie, który wcześniej skompilowany i uruchomiony poprawnie. Zmiany w nowej wersji, które powodują takie problemy są znane jako *istotne zmiany*, i zazwyczaj są one wymagane przez modyfikacje w standardzie języka C++, podpisy funkcji lub układ obiektów w pamięci.

Aby uniknąć błędów w czasie wykonywania, które są trudne do wykrycia i zdiagnozowania, zaleca się, aby nigdy nie statycznie połączyć się z plikami binarnymi skompilowanymi przy użyciu innej wersji kompilatora. Ponadto, gdy uaktualniasz projekt EXE lub DLL, upewnij się, że uaktualniasz również biblioteki, z którymi się on łączy. Nie przekazuj typów CRT (C Runtime) lub C++ Standard Library (C++ Standard Library) między plikami binarnymi, w tym bibliotekami DLL, skompilowanymi przy użyciu różnych wersji kompilatora. Aby uzyskać więcej informacji, zobacz [Potencjalne błędy przekazywania obiektów CRT przez granice biblioteki DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Nigdy nie należy pisać kodu, który zależy od określonego układu dla obiektu, który nie jest interfejsem COM lub OBIEKT POD. Jeśli jednak piszesz taki kod, upewnij się, że działa po uaktualnieniu. Aby uzyskać więcej informacji, zobacz [Przenośność w granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Ponadto bieżące ulepszenia zgodności kompilatora czasami można zmienić sposób kompilatora rozumie istniejącego kodu źródłowego. Na przykład może się okazać nowe lub różne błędy podczas kompilacji lub nawet różnice behawioralne w kodzie, który wcześniej zbudowany i wydawało się działać poprawnie. Chociaż te ulepszenia nie są istotne zmiany, takie jak te omówione w tym dokumencie, może być konieczne wprowadzenie zmian w kodzie źródłowym, aby rozwiązać te problemy:

- [C Zmiany podziału biblioteki środowiska wykonawczego (CRT)](#BK_CRT)

- [Standardowe zmiany w bibliotece standardowej w językach C++ i C++](#BK_STL)

- [Zmiany w przerwach WIFC i ATL](#BK_MFC)

- [Zmiany podziału środowiska uruchomieniowego współbieżności](#BK_ConcRT)

## <a name="visual-studio-2015-conformance-changes"></a><a name="VC_2015"></a>Zmiany zgodności programu Visual Studio 2015

### <a name="c-runtime-library-crt"></a><a name="BK_CRT"></a>Biblioteka środowiska wykonawczego C (CRT)

#### <a name="general-changes"></a>Zmiany ogólne

- **Refaktoryzowane pliki binarne**

   Biblioteka CRT została przekształcona w dwa różne pliki binarne: uniwersalny CRT (ucrtbase), który zawiera większość standardowych funkcji, oraz bibliotekę wykonawczą VC (vcruntime). Biblioteka vcruntime zawiera funkcje związane z kompilatorem, takie jak obsługa wyjątków i wewnętrzne. Jeśli używasz domyślnych ustawień projektu, ta zmiana nie ma wpływu na Ciebie, ponieważ konsolidator automatycznie użyje nowych bibliotek domyślnych. Jeśli właściwość **konsoli dostępu** projektu została ustawiona na **Wartość Ignoruj** `/NODEFAULTLIB` **wszystkie biblioteki domyślne** projektu na Tak lub używasz opcji konsolidatora w wierszu polecenia, należy zaktualizować listę bibliotek (we właściwości **Dodatkowe zależności),** aby uwzględnić nowe, refaktoryzowane biblioteki. Zastąp starą bibliotekę CRT (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib) równoważnymi bibliotekami refaktoryzowanymi. Dla każdej z dwóch refaktoryzowanych bibliotek istnieją wersje statyczne (lib) i dynamiczne (.dll) oraz wersja release (bez sufiksu) i debugowania (z sufiksem "d"). Wersje dynamiczne mają bibliotekę importu, z którą nawiązujesz połączenie. Dwie regenerowane biblioteki to Universal CRT, w szczególności ucrtbase.dll lub ucrtbase.lib, ucrtbased.dll lub ucrtbased.lib oraz biblioteka środowiska wykonawczego VC, libvcruntime.lib, vcruntime*version*.dll, libvcruntimed.lib i vcruntimed*version*.dll. *Wersja* w programie Visual Studio 2015 i Visual Studio 2017 jest 140. Zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<>

- **localeconv**

   Funkcja [localeconv](../c-runtime-library/reference/localeconv.md) zadeklarowana w locale.h działa teraz poprawnie, gdy włączone są [ustawienia regionalne dla wątku.](../parallel/multithreading-and-locales.md) W poprzednich wersjach biblioteki ta `lconv` funkcja zwraca dane dla ustawień regionalnych globalnego, a nie ustawień regionalnych wątku.

   Jeśli używasz ustawień regionalnych dla wątku, `localeconv`należy sprawdzić użycie programu . Jeśli kod zakłada, `lconv` że zwrócone dane są dla ustawień regionalnych globalnych, należy go poprawić.

#### <a name="mathh"></a>\<> math.h

- **Przeciążenia funkcji biblioteki matematycznej w języku C++**

   W poprzednich \<wersjach math.h> zdefiniował niektóre, ale nie wszystkie, przeciążenia C++ dla funkcji biblioteki matematycznej. Reszta przeciążeń była w \<nagłówku cmath>. Kod, który \<zawierał tylko> math.h, może mieć problemy z rozdzielczością przeciążenia funkcji. Teraz przeciążenia C++ zostały \<usunięte z> math.h i \<znajdują się tylko w cmath>.

   Aby rozwiązać problemy, \<należy uwzględnić cmath>, aby uzyskać deklaracje \<funkcji, które zostały usunięte z math.h>. Te funkcje zostały przeniesione:

  - `double abs(double)` i `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float`i `long double` `acos`wersje funkcji zmiennoprzecinkowych `atan2` `cbrt`, `ceil` `copysign` `cos` `cosh` `erf` `erfc` `exp` `exp2` `expm1` `fabs` `sqrt` `tan` `tanh` `tgamma`, `log10`, `log1p` `log2` `lrint` `lround` `modf` `nearbyint` `nextafter` `nexttoward` `log` `atan` `atanh` `acosh` `asin` `asinh` `scalbln`, , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , , `fdim` `floor` `fma` `fmax` `fmin` `fmod` `frexp` `hypot` `ilogb` `ldexp` `lgamma` `llrint` `llround` `remainder` `remquo` `rint` `round` `scalbn` `sin` `sinh``trunc`

  Jeśli masz kod, `abs` który używa z typu zmiennoprzecinkowego, który zawiera tylko \<math.h> nagłówka, wersje zmiennoprzecinkowe nie będą już dostępne. Wywołanie jest teraz `abs(int)`rozpoznawane, nawet z argumentem zmiennoprzecinkowym, który generuje błąd:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Poprawka dla tego ostrzeżenia polega na `abs` zastąpieniu wywołania `abs`zmiennoprzecinkową wersją , na przykład `fabs` dla podwójnego argumentu lub `fabsf` argumentu float, lub \<dołączenie nagłówka cmath> i dalsze używanie `abs`.

- **Zgodność zmiennoprzecinkową**

   Wprowadzono wiele zmian w bibliotece matematycznej w celu poprawy zgodności ze specyfikacjami IEEE-754 i C11 annex F w odniesieniu do specjalnych danych wejściowych, takich jak NaN i bezokoliczności. Na przykład ciche dane wejściowe NaN, które często były traktowane jako błędy w poprzednich wersjach biblioteki, nie są już traktowane jako błędy. Patrz [norma IEEE 754](https://standards.ieee.org/standard/754-2008.html) i załącznik F [normy C11](https://www.iso.org/standard/57853.html).

   Te zmiany nie powodują błędów w czasie kompilacji, ale mogą powodować programy zachowywać się inaczej i bardziej poprawnie zgodnie ze standardem.

- **FLT_ROUNDS**

   W programie Visual Studio 2013 FLT_ROUNDS makro rozwinięte do wyrażenia stałego, które było niepoprawne, ponieważ tryb zaokrąglania można skonfigurować w czasie wykonywania, na przykład przez wywołanie fesetround. Makro FLT_ROUNDS jest teraz dynamiczne i poprawnie odzwierciedla bieżący tryb zaokrąglania.

#### <a name="new-and-newh"></a>\<nowych> i \<> new.h

- **nowe i usuń**

   W poprzednich wersjach biblioteki operator zdefiniowany implementacją nowe i delete funkcje zostały wyeksportowane z biblioteki wykonawczej biblioteki wykonawczej biblioteki DLL (na przykład msvcr120.dll). Te funkcje operatora są teraz zawsze statycznie połączone z plikami binarnymi, nawet podczas korzystania z bibliotek biblioteki dll biblioteki wykonawczej.

   Nie jest to zmiana podziału dla kodu`/clr`macierzystego lub mieszanego ( ), jednak dla kodu skompilowanego jako [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md), ta zmiana może spowodować, że kod nie powiedzie się skompilować. Jeśli skompilować `/clr:pure`kod jako , `#include <new>` `#include <new.h>` może być konieczne dodanie lub obejść błędy kompilacji z powodu tej zmiany. Opcja`/clr:pure` jest przestarzała w programie Visual Studio 2015 i nie jest obsługiowana w programie Visual Studio 2017. Kod, który musi być "czysty" powinien zostać przeniesiony do języka C#.

#### <a name="processh"></a>\<> proces.h

- **_beginthread i _beginthreadex**

   Funkcje [_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) i [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) posiadają teraz odwołanie do modułu, w którym procedura wątku jest zdefiniowana na czas trwania wątku. Pomaga to zapewnić, że moduły nie są zwalniane, dopóki wątek nie został uruchomiony do zakończenia.

#### <a name="stdargh"></a>\<>

- **typy va_start i referencyjne**

   Podczas kompilowania kodu C++ [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) teraz sprawdza poprawność w czasie kompilacji, że argument przekazany do niego nie jest typu odwołania. Argumenty typu odwołania są zabronione przez standard C++.

#### <a name="stdioh-and-conioh"></a><a name="stdio_and_conio"></a>\<stdio.h> i \<conio.h>

- **Printf i scanf rodziny funkcji są teraz zdefiniowane w linii.**

   Definicje `printf` wszystkich funkcji i `scanf` funkcji zostały przeniesione \<w wierszu do stdio.h>, \<conio.h> i innych nagłówków CRT. Ta zmiana podziału prowadzi do błędu konsolidatora (LNK2019, nierozwiązany symbol zewnętrzny) dla wszystkich programów, które zadeklarowały te funkcje lokalnie bez uwzględnienia odpowiednich nagłówków CRT. Jeśli to możliwe, należy zaktualizować kod, aby uwzględnić nagłówki `#include <stdio.h>`CRT (czyli dodaj) i wbudowane funkcje, ale jeśli nie chcesz modyfikować kodu w celu uwzględnienia tych plików nagłówkowych, alternatywnym rozwiązaniem jest dodanie dodatkowej biblioteki do wprowadzania konsolidatora, legacy_stdio_definitions.lib.

   Aby dodać tę bibliotekę do danych wejściowych konsolidatora w ide, otwórz menu kontekstowe węzła projektu, wybierz **polecenie Właściwości**, a następnie w oknie dialogowym **Właściwości projektu** wybierz pozycję **Linker**i edytuj **dane wejściowe konsolidatora,** aby dodać `legacy_stdio_definitions.lib` je do listy oddzielonych średnikami.

   Jeśli łącza projektu z bibliotek statycznych, które zostały skompilowane z wydaniem programu Visual Studio wcześniej niż 2015, konsolidator może zgłosić nierozwiązany symbol zewnętrzny. Błędy te mogą odwoływać `_iob`się `_iob_func`do wewnętrznych definicji \<dla , lub powiązanych importu dla niektórych stdio.h> funkcji w postaci _imp_\*. Firma Microsoft zaleca ponowne skompilowanie wszystkich bibliotek statycznych z najnowszą wersją kompilatora języka C++ i bibliotek podczas uaktualniania projektu. Jeśli biblioteka jest biblioteką innej firmy, dla której źródło nie jest dostępne, należy zażądać zaktualizowanego pliku binarnego od innej firmy lub hermetyzować użycie tej biblioteki w osobnej bibliotece DLL, która jest kompilowana ze starszą wersją kompilatora i bibliotek.

    > [!WARNING]
    > Jeśli łączysz się z zestawem Windows SDK 8.1 lub starszym, mogą wystąpić te nierozwiązane błędy symboli zewnętrznych. W takim przypadku należy rozwiązać ten błąd, dodając legacy_stdio_definitions.lib do danych wejściowych konsolidatora, jak opisano wcześniej.

   Aby rozwiązać problemy z nierozwiązanymi błędami symboli, można spróbować użyć [pliku dumpbin.exe](../build/reference/dumpbin-reference.md) w celu zbadania symboli zdefiniowanych w pliku binarnym. Spróbuj użyć następującego wiersza polecenia, aby wyświetlić symbole zdefiniowane w bibliotece.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **dostaje i _getws**

   Funkcje [pobiera](../c-runtime-library/gets-getws.md) i [_getws](../c-runtime-library/gets-getws.md) zostały usunięte. Funkcja gets została usunięta z biblioteki standardowej języka C11, ponieważ nie można jej bezpiecznie używać. Funkcja _getws była rozszerzeniem firmy Microsoft, które było równoważne pobiera, ale dla szerokich ciągów. Jako alternatywę dla tych funkcji, należy rozważyć użycie [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws](../c-runtime-library/reference/fgets-fgetws.md), [gets_s](../c-runtime-library/reference/gets-s-getws-s.md)i [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets i _cgetws**

   Funkcje [_cgets](../c-runtime-library/cgets-cgetws.md) i [_cgetws](../c-runtime-library/cgets-cgetws.md) zostały usunięte. Jako alternatywę dla tych funkcji, należy rozważyć użycie [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) i [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Formatowanie nieskończoności i nan**

   W poprzednich wersjach ciągów infinities i NaN będą formatowane przy użyciu zestawu ciągów wartownika specyficznych dla msvc.

  - Nieskończoność: 1,#INF

  - Cicha NaN: 1.#QNAN

  - Sygnalizacja NaN: 1.#SNAN

  - Nieokreślony NaN: 1.#IND

  Każdy z tych formatów mógł być poprzedzony znakiem i mógł być sformatowany nieco inaczej w zależności `printf("%.2f\n", INFINITY)` od szerokości i precyzji pola (czasami z nietypowymi efektami, na przykład drukowanie 1,#J, ponieważ #INF będzie "zaokrąglona" do 2-cyfrowej precyzji). C99 wprowadziło nowe wymagania dotyczące sposobu formatowania nieprawidłowości i sieci nan. Implementacja MSVC jest teraz zgodna z tymi wymaganiami. Nowe ciągi są następujące:

  - Nieskończoność: inf

  - Cichy NaN: nan

  - Sygnalizacja NaN: nan(snan)

  - Nieokreślony NaN: nan(ind)

  Każdy z nich może być poprzedzony znakiem. Jeśli używany jest specyfikator formatu pisanego wielkimi literami (%F zamiast %f), ciągi są drukowane wielkimi literami (`INF` zamiast ), zgodnie z `inf`wymaganiami.

  Funkcje [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) zostały zmodyfikowane w celu przeanalizowania tych nowych ciągów, `printf` więc `scanf`te ciągi teraz w obie strony i .

- **Formatowanie i analizowanie zmiennoprzecinkowe**

   Wprowadzono nowe algorytmy formatowania zmiennoprzecinkowego i analizowania w celu poprawy poprawności. Ta zmiana wpływa na [rodziny printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkcji, a także funkcje, takie jak [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Stare algorytmy formatowania wygenerowałyby tylko ograniczoną liczbę cyfr, a następnie wypełniłyby pozostałe miejsca dziesiętne zerem. Zazwyczaj mogą generować ciągi, które będą w obie strony z powrotem do oryginalnej wartości zmiennoprzecinkowej, ale nie były świetne, jeśli chcesz dokładną wartość (lub najbliższą ich reprezentację dziesiętną). Nowe algorytmy formatowania generują tyle cyfr, ile jest wymaganych do reprezentowania wartości (lub wypełnienia określonej precyzji). Jako przykład poprawy; należy wziąć pod uwagę wyniki podczas drukowania dużej mocy dwóch:

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   Stare wyjście:

    ```Output
    1208925819614629200000000
    ```

   Nowe wyjście:

    ```Output
    1208925819614629174706176
    ```

   Stare algorytmy analizowania będzie uwzględniać tylko do 17 cyfr znaczących z ciągu wejściowego i będzie odrzucić pozostałe cyfry. Takie podejście jest wystarczające do wygenerowania zbliżonego przybliżenia wartości reprezentowanej przez ciąg, a wynik jest zwykle bardzo blisko poprawnie zaokrąglonego wyniku. Nowa implementacja uwzględnia wszystkie obecne cyfry i daje poprawnie zaokrąglony wynik dla wszystkich wejść (do 768 cyfr długości). Ponadto funkcje te są teraz zgodne z trybem zaokrąglania (sterowanym za pośrednictwem fesetround).  Jest to potencjalnie zmiana zachowania przerwania, ponieważ te funkcje mogą wyprowadzać różne wyniki. Nowe wyniki są zawsze bardziej poprawne niż stare wyniki.

- **Analizowanie szesnastkowe i nieskończoności/nan zmiennoprzecinkowe**

   Algorytmy analizowania zmiennoprzecinkowego będą teraz analizować szesnastkowe ciągi zmiennoprzecinkowe (takie jak te generowane przez specyfikatory formatu `printf` %a i %A) oraz wszystkie ciągi nieskończoności i NaN generowane przez funkcje, jak opisano powyżej.

- **%A i %dopełnienie zerowe**

   Specyfikatory formatu %a i %A formatują liczbę zmiennoprzecinkowa jako szesnastkową mantysię i wykładnik binarny. W poprzednich wersjach `printf` funkcje niepoprawnie zero-pad ciągów. Na przykład `printf("%07.0a\n", 1.0)` można wydrukować 00x1p + 0, gdzie należy wydrukować 0x01p + 0. Ta wada została naprawiona.

- **%A i %a precyzja**

   Domyślna dokładność specyfikatorów formatu %A i %a wynosiła 6 w poprzednich wersjach biblioteki. Domyślna precyzja wynosi teraz 13 dla zgodności ze standardem C.

   Jest to zmiana zachowania środowiska uruchomieniowego w danych wyjściowych dowolnej funkcji, która używa ciągu formatu z %A lub %a. W starym zachowaniu dane wyjściowe przy użyciu specyfikatora %A mogą być "1.1A2B3Cp+111". Teraz wyjście dla tej samej wartości to "1.1A2B3C4D5E6F7p+111". Aby uzyskać stare zachowanie, można określić dokładność, na przykład %.6A. Zobacz [Specyfikacja precyzji](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Specyfikator %F**

   Specyfikator formatu/konwersji %F jest teraz obsługiwany. Jest funkcjonalnie odpowiednikiem specyfikatora formatu %f, z tą różnicą, że wyrazy i sieci NaN są formatowane przy użyciu wielkich liter.

   W poprzednich wersjach implementacji używane do analizować F i N jako modyfikatory długości. To zachowanie datowane na wiek segmentowanych przestrzeni adresowych: te modyfikatory długości były używane do wskazywania wskaźników położonych odpowiednio daleko i blisko, jak w %Fp lub %Ns. To zachowanie zostało usunięte. Jeśli wystąpi %F, jest teraz traktowany jako specyfikator formatu %F; Jeśli wystąpi %N, jest teraz traktowany jako nieprawidłowy parametr.

- **Formatowanie wykładnikowe**

   Specyfikatory formatu %e i %E formatują liczbę zmiennoprzecinkowa jako dziesiętną modliscę i wykładnik. Specyfikatory formatu %g i %G również formatuje liczby w tym formularzu w niektórych przypadkach. W poprzednich wersjach CRT zawsze generować ciągi z wykładników trzycyfrowych. Na przykład `printf("%e\n", 1.0)` można wydrukować 1.000000e + 000, który był niepoprawny. C wymaga, aby jeśli wykładnik jest reprezentowany przy użyciu tylko jednej lub dwóch cyfr, należy wydrukować tylko dwie cyfry.

   W programie Visual Studio 2005 dodano globalny przełącznik zgodności: [_set_output_format](../c-runtime-library/set-output-format.md). Program może wywołać tę funkcję z argumentem _TWO_DIGIT_EXPONENT, aby włączyć zgodne wykładnik drukowania. Domyślne zachowanie zostało zmienione na zgodny ze standardami tryb drukowania wykładnik.

- **Sprawdzanie poprawności ciągu formatu**

   W poprzednich wersjach `scanf` i funkcje po cichu `printf` akceptować wiele nieprawidłowych ciągów formatu, czasami z nietypowych efektów. Na przykład %hlhlhld będzie traktowany jako %d. Wszystkie nieprawidłowe ciągi formatu są teraz traktowane jako nieprawidłowe parametry.

- **sprawdzanie poprawności ciągu w trybie fopen**

   W poprzednich wersjach `fopen` rodzina funkcji po cichu akceptowała `r+b+`niektóre nieprawidłowe ciągi trybu, takie jak . Nieprawidłowe ciągi trybu są teraz wykrywane i traktowane jako nieprawidłowe parametry.

- **tryb _O_U8TEXT**

   Funkcja [_setmode](../c-runtime-library/reference/setmode.md) poprawnie informuje o trybie strumieni otwartych in_O_U8TEXT trybie. W poprzednich wersjach biblioteki raport y takie strumienie jako otwierane w _O_WTEXT.

   Jest to zmiana podziału, jeśli kod interpretuje tryb _O_WTEXT dla strumieni, gdzie kodowanie jest UTF-8. Jeśli aplikacja nie obsługuje UTF_8, należy rozważyć dodanie obsługi tego coraz bardziej powszechne kodowanie.

- **snprintf i vsnprintf**

   Funkcje [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) i [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) są teraz implementowane. Starszy kod często dostarczał definicje wersji makr tych funkcji, ponieważ nie zostały zaimplementowane przez bibliotekę CRT, ale nie są już potrzebne w nowszych wersjach. Jeśli [snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) lub [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) jest zdefiniowany jako makro przed dołączeniem \<stdio.h>, kompilacja kończy się niepowodzeniem z błędem wskazującym, gdzie zdefiniowano makro.

   Zwykle rozwiązaniem tego problemu jest usunięcie wszelkich deklaracji `snprintf` `vsnprintf` lub w kodzie użytkownika.

- **tmpnam generuje użyteczne nazwy plików**

   W poprzednich `tmpnam` wersjach `tmpnam_s` i funkcje generowane nazwy plików w katalogu głównym dysku (takich jak \sd3c.). Te funkcje generują teraz użyteczne ścieżki nazw plików w katalogu tymczasowym.

- **Hermetyzacja pliku**

   W poprzednich wersjach kompletny typ pliku \<został zdefiniowany publicznie w> stdio.h, dzięki czemu kod użytkownika mógł dotrzeć do pliku i zmodyfikować jego wewnętrzne. Biblioteka została zmieniona, aby ukryć szczegóły implementacji. W ramach tej zmiany plik \<zdefiniowany w stdio.h> jest teraz typem nieprzezroczystym, a jego członkowie są niedostępni spoza samego CRT.

- **_outp i _inp**

   Funkcje [_outp,](../c-runtime-library/outp-outpw-outpd.md) [_outpw,](../c-runtime-library/outp-outpw-outpd.md) [_outpd,](../c-runtime-library/outp-outpw-outpd.md) [_inp,](../c-runtime-library/inp-inpw-inpd.md) [_inpw](../c-runtime-library/inp-inpw-inpd.md)i [_inpd](../c-runtime-library/inp-inpw-inpd.md) zostały usunięte.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<>, \<> i \<sys/stat.h>

- **strtof i wcstof**

   I `strtof` `wcstof` funkcje nie `errno` można ustawić na ERANGE, gdy wartość nie była reprezentowana jako float. Ten błąd był specyficzny dla tych dwóch funkcji; , i `wcstold` funkcje pozostały nienaruszone. `strtod` `wcstod` `strtold` Ten problem został rozwiązany i jest zmianą przerywania środowiska uruchomieniowego.

- **Wyrównane funkcje alokacji**

   W poprzednich wersjach wyrównane`_aligned_malloc`funkcje alokacji ( , `_aligned_offset_malloc`itp.) po cichu akceptowały żądania bloku z wyrównaniem 0. Żądane wyrównanie musi być potęgą dwóch, która nie jest prawdziwa zero. Żądane wyrównanie 0 jest teraz traktowane jako nieprawidłowy parametr. Ten problem został rozwiązany i jest zmianą przerywania środowiska uruchomieniowego.

- **Funkcje sterty**

   I `_heapadd` `_heapset` `_heapused` funkcje zostały usunięte. Te funkcje były niefunkcjonalne od crt został zaktualizowany do korzystania ze sterty systemu Windows.

- **mała**

   Opcja `smallheap` łącza została usunięta. Zobacz [Opcje łącza](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   Podpis funkcji `wcstok` został zmieniony tak, aby odpowiadał wymaganą przez standard C. W poprzednich wersjach biblioteki podpis tej funkcji wynosił:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   Użyto wewnętrznego kontekstu na gwint do śledzenia stanu `strtok`w wywołaniach, tak jak to ma miejsce w przypadku . Funkcja ma teraz `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)`podpis i wymaga od wywołującego przekazania kontekstu jako trzeciego argumentu do funkcji.

   Dodano `_wcstok` nową funkcję ze starym podpisem, aby ułatwić przenoszenie. Podczas kompilowania kodu C++ istnieje również przeciążenie wbudowane, `wcstok` które ma stary podpis. To przeciążenie jest zadeklarowane jako przestarzałe. W kodzie C możesz define_CRT_NON_CONFORMING_WCSTOK spowodować, że `_wcstok` będzie `wcstok`używany zamiast pliku .

#### <a name="timeh"></a>\<> time.h

- **clock**

   W poprzednich wersjach funkcja [zegara](../c-runtime-library/reference/clock.md) została zaimplementowana przy użyciu interfejsu API systemu Windows [GetSystemTimeAsFileTime](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). Dzięki tej implementacji funkcja zegara była wrażliwa na czas systemowy, a zatem niekoniecznie była monotonna. Funkcja zegara została ponownie zaimplementowana pod względem [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) i jest teraz monotoniczna.

- **fstat i _utime**

   W poprzednich wersjach funkcje [_stat](../c-runtime-library/reference/stat-functions.md), [fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)i [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) niepoprawnie obsługują czas letni. Przed Visual Studio 2013 wszystkie te funkcje niepoprawnie dostosowane czasy standardowe, tak jakby były w czasie dziennym.

   W programie Visual Studio 2013 problem został rozwiązany w **_stat** rodziny funkcji, ale podobne problemy w **fstat** i **_utime** rodzin funkcji nie zostały rozwiązane. Ta częściowa poprawka doprowadziła do problemów z powodu niespójności między funkcjami. **Fstat** i **_utime** rodziny funkcji zostały już naprawione, więc wszystkie te funkcje obsługują teraz czas letni poprawnie i konsekwentnie.

- **asctime (czas na szemoc**

   W poprzednich wersjach funkcja [asctime](../c-runtime-library/reference/asctime-wasctime.md) będzie pad jednocyfrowe dni `Fri Jun 06 08:00:00 2014`z zerem wiodącym, na przykład: . Specyfikacja wymaga, aby takie dni były wyściełane wiodącą przestrzenią, jak w `Fri Jun  6 08:00:00 2014`. Ten problem został rozwiązany.

- **strftime i wcsftime**

   `strftime` Funkcje `wcsftime` i funkcje obsługują teraz specyfikatory formatu %C, %D, %e, %F, %g, %h, %n, %r, %R, %t, %T, %u i %V. Ponadto modyfikatory E i O są analizowane, ale ignorowane.

   Specyfikator formatu %c jest określony jako tworzący "odpowiednią reprezentację daty i godziny" dla bieżących ustawień regionalnych. W ustawieniach regionalnych C reprezentacja ta musi `%a %b %e %T %Y`być taka sama jak `asctime`, w tym samym formularzu, który jest produkowany przez . W poprzednich wersjach specyfikator formatu %c niepoprawnie sformatował czasy za pomocą `MM/DD/YY HH:MM:SS` reprezentacji. Ten problem został rozwiązany.

- **timespec i TIME_UTC**

   Nagłówek \<> time.h definiuje teraz `timespec` typ i `timespec_get` funkcję ze standardu C11. Ponadto makro TIME_UTC, do użytku z funkcją, `timespec_get` jest teraz zdefiniowane. Ta aktualizacja jest przełomową zmianą dla kodu, który ma sprzeczną definicję dla każdego z tych identyfikatorów.

- **CLOCKS_PER_SEC**

   Makro CLOCKS_PER_SEC rozwija się teraz do liczby całkowitej `clock_t`typu, zgodnie z wymaganiami języka C.

#### <a name="c-standard-library"></a><a name="BK_STL"></a>Standardowa biblioteka języka C++

Aby włączyć nowe optymalizacje i kontrole debugowania, implementacja standardowej biblioteki C++ w Visual Studio celowo łamie zgodność binarną między wersjami. W związku z tym gdy używana jest standardowa biblioteka C++, pliki obiektowe i biblioteki statyczne, które są kompilowane przy użyciu różnych wersji, nie mogą być mieszane w jednym pliku binarnym (EXE lub DLL), a obiekty standardowej biblioteki C++ nie mogą być przekazywane między plikami binarnymi, które są kompilowane przy użyciu różnych wersji. Takie mieszanie powoduje błędy konsolidatora dotyczące niezgodności _MSC_VER. (_MSC_VER jest makro, które zawiera wersję główną kompilatora — na przykład 1800 dla programu Visual Studio 2013.) Ten czek nie może wykryć mieszania biblioteki DLL i nie można wykryć mieszania, które obejmuje program Visual Studio 2008 lub wcześniej.

- **Standardowa biblioteka języka C++ zawiera pliki**

   Wprowadzono pewne zmiany w strukturze dołączania w nagłówkach biblioteki standardowej języka C++. Nagłówki biblioteki standardowej języka C++ mogą zawierać się wzajemnie w nieokreślony sposób. Ogólnie rzecz biorąc należy napisać kod, tak aby starannie zawiera wszystkie nagłówki, które potrzebuje zgodnie ze standardem C++ i nie polegać na które nagłówki biblioteki standardowej języka C++ zawierają inne nagłówki biblioteki standardowej języka C++.In general, you should write your code so that it carefully includes all of the headers that it needs according to the C++ standard standard standard, and doesn't rely on which C++ Standard Library headers include which other C++ Standard Library headers. Dzięki temu kod przenośny między wersjami i platformami. Co najmniej dwie zmiany nagłówka w programie Visual Studio 2015 wpływają na kod użytkownika. Po \<pierwsze> ciąg nie \<zawiera już> iteratora. Po \<drugie, krotka> `std::array` teraz deklaruje \<bez uwzględnienia wszystkich> tablic, które mogą rozbić kod przez następującą kombinację konstrukcji kodu: kod ma zmienną o nazwie "tablica", a masz using-dyrektywy \<"przy użyciu std obszaru nazw;", a następnie dołącza nagłówek biblioteki standardowej C++ (takich jak> funkcjonalne), który zawiera \<krotki>, który teraz deklaruje `std::array`.

- **steady_clock**

   Chrono \<> wdrożenie [steady_clock](../standard-library/steady-clock-struct.md) został zmieniony, aby spełnić wymagania standardu C++ dotyczące stabilności i monotonności. `steady_clock`jest teraz oparty na [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) i `high_resolution_clock` `steady_clock`jest teraz typedef dla . W rezultacie w programie `steady_clock::time_point` Visual Studio jest `chrono::time_point<steady_clock>`teraz typedef for ; jednak nie musi to być w przypadku innych implementacji.

- **alokatory i const**

   Teraz wymagamy porównania równości/nierówności alokatora, aby zaakceptować argumenty const po obu stronach. Jeśli alokatory definiują te operatory w ten sposób,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   następnie należy je zaktualizować i zadeklarować je jako const członków:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **const elementy**

   Standard C++ zawsze zabronione pojemniki const elementów (takich jak wektor\<const\<T> lub zestaw const T>). Visual Studio 2013 i wcześniej zaakceptowane takie kontenery. W bieżącej wersji takie kontenery nie można skompilować.

- **std::alokator::dlokalizuj**

   W programie Visual Studio 2013 i wcześniejszych `std::allocator::deallocate(p, n)` zignorowano argument przekazany dla *n*.  Standard C++ zawsze wymagał, aby *n* było równe wartości przekazanej jako pierwszy `allocate` argument do wywołania, którego zwrócone *p*. Jednak w bieżącej wersji wartość *n* jest kontrolowana. Kod, który przekazuje argumenty dla *n,* które różnią się od tego, co wymaga standard może ulec awarii w czasie wykonywania.

- **hash_map i hash_set**

   Niestandardowe pliki nagłówkowe \<hash_map> i \<hash_set> są przestarzałe w programie Visual Studio 2015 i zostaną usunięte w przyszłej wersji. Zamiast \<tego użyj>> \<unordered_map unordered_set i unordered_set.

- **komparatory i operator()**

   Kontenery zespolone \<(> rodziny map) wymagają teraz, aby ich komparatory miały operatory wywołania funkcji const-callable. Następujący kod w deklaracji klasy porównawczej nie można teraz skompilować:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Aby rozwiązać ten błąd, zmień deklarację funkcji na:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **cechy typu**

   Stare nazwy cech typu z wcześniejszej wersji wzorca wersji C++ zostały usunięte. Zostały one zmienione w języku C++ 11 i zostały zaktualizowane do wartości C++ 11 w programie Visual Studio 2015. W poniższej tabeli przedstawiono stare i nowe nazwy.

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

- **uruchamianie::dowolne i uruchamianie::zasady synchronizacji**

   Niestandardowe `launch::any` zasady `launch::sync` i zasady zostały usunięte. Zamiast tego, `launch::any`dla `launch:async | launch:deferred`, użyj . Dla `launch::sync`, `launch::deferred`użyj . Zobacz [uruchom Wyliczenie](../standard-library/future-enums.md#launch).

#### <a name="mfc-and-atl"></a><a name="BK_MFC"></a>MFC i ATL

- **Microsoft Foundation Classes (MFC)**

   nie jest już uwzględniony w "Typowe" zainstalować visual studio ze względu na jego duży rozmiar. Aby zainstalować MFC, wybierz opcję **Instalacja niestandardowa** w instalatorze programu Visual Studio 2015. Jeśli masz już zainstalowany program Visual Studio 2015, możesz zainstalować MFC, ponownie uruchamiając instalator **programu Visual Studio.** Wybierz opcję **Instalacja niestandardowa,** a następnie wybierz pozycję **Microsoft Foundation Classes**. Konfigurację **programu Visual Studio** można uruchomić za ć na podstawie panelu sterowania **Programami i funkcjami** **panelu** sterowania lub z nośnika instalacyjnego.

   Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.

#### <a name="concurrency-runtime"></a><a name="BK_ConcRT"></a>Środowisko uruchomieniowe współbieżności

- **Makro wydajności z systemu Windows.h jest sprzeczne z współbieżnością::Kontekst::Yield**

   Współbieżność runtime wcześniej używane `#undef` do undefine yield makra, aby uniknąć konfliktów między yield `concurrency::Context::Yield` makro zdefiniowane w systemie Windows.h h i funkcji. To `#undef` zostało usunięte i nowy odpowiednik współbieżności wywołania interfejsu API nie powodujące [konfliktu::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) został dodany. Aby obejść konflikty z Yield, można zaktualizować `YieldExecution` kod, aby zamiast `Yield` tego wywołać funkcję, lub otoczyć nazwę funkcji nawiasami w witrynach wywołań, jak w poniższym przykładzie:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Ulepszenia zgodności kompilatora w programie Visual Studio 2015

Podczas uaktualniania kodu z poprzednich wersji, może również wystąpić błędy kompilatora, które są spowodowane ulepszenia zgodności wprowadzone w programie Visual Studio 2015. Te ulepszenia nie powodują przerwania zgodności binarnej z wcześniejszych wersji programu Visual Studio, ale mogą powodować błędy kompilatora, w których żadne nie zostały wyemitowane wcześniej. Aby uzyskać więcej informacji, zobacz [Visual C++ What's New 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

W programie Visual Studio 2015 bieżące ulepszenia zgodności kompilatora można czasami zmienić sposób, w jaki kompilator rozumie istniejący kod źródłowy. W rezultacie może wystąpić nowe lub różne błędy podczas kompilacji lub nawet różnice behawioralne w kodzie, który wcześniej zbudowany i wydawało się działać poprawnie.

Na szczęście te różnice mają niewielki lub żaden wpływ na większość kodu źródłowego. Gdy kod źródłowy lub inne zmiany są potrzebne do rozwiązania tych różnic, poprawki wydają się być małe i proste do przodu. Zamieściliśmy wiele przykładów wcześniej akceptowalnego kodu źródłowego, który może wymagać zmiany *(wcześniej)* oraz poprawki, aby je poprawić *(po)*.

Mimo że te różnice mogą mieć wpływ na kod źródłowy lub inne artefakty kompilacji, nie wpływają one na zgodność binarną między aktualizacjami wersji programu Visual Studio. *Zmiana podziału* jest bardziej dotkliwe i może mieć wpływ na zgodność binarną, ale tego rodzaju podziały zgodności binarnej występują tylko między głównymi wersjami programu Visual Studio, na przykład między programem Visual Studio 2013 i Visual Studio 2015. Aby uzyskać informacje na temat zmian podziału, które wystąpiły między programami Visual Studio 2013 i Visual Studio 2015, zobacz [Visual Studio 2015 Zmiany zgodności.](#VC_2015)

- [Ulepszenia zgodności w programie Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodności w aktualizacji 1](#VS_Update1)

- [Ulepszenia zgodności w aktualizacji 2](#VS_Update2)

- [Ulepszenia zgodności w aktualizacji 3](#VS_Update3)

### <a name="conformance-improvements-in-visual-studio-2015"></a><a name="VS_RTM"></a>Ulepszenia zgodności w programie Visual Studio 2015

- /Zc:forScope- opcja

   Opcja `/Zc:forScope-` kompilatora jest przestarzała i zostanie usunięta w przyszłej wersji.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Zazwyczaj ta opcja została użyta w celu umożliwienia niestandardowego kodu, który używa zmiennych pętli po punkcie, w którym, zgodnie ze standardem, powinny one wyjść poza zakres. Było to konieczne tylko wtedy, `/Za` gdy skompilowano z opcją, ponieważ bez `/Za`, użycie zmiennej pętli for po zakończeniu pętli jest zawsze dozwolone. Jeśli nie dbasz o zgodność ze standardami (na przykład, jeśli kod nie jest przeznaczony do `/Za` przenoszenia do innych kompilatorów), możesz wyłączyć tę opcję (lub ustawić właściwość **Wyłącz rozszerzenia języka** na **Nie).** Jeśli zależy Ci na pisaniu przenośnego kodu zgodnego ze standardami, należy przepisać kod, tak aby był zgodny ze standardem, przenosząc deklarację takich zmiennych do punktu poza pętlą.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg`kompilator, opcja

   Opcja `/Zg` kompilatora (Generowanie prototypów funkcji) nie jest już dostępna. Ta opcja kompilatora została wcześniej przestarzała.

- Nie można już uruchamiać testów jednostkowych za pomocą języka C++/CLI z wiersza polecenia z mstest.exe. Zamiast tego należy użyć vstest.console.exe. Zobacz [opcje wiersza polecenia VSTest.Console.exe](/visualstudio/test/vstest-console-options).

- **słowa kluczowe modyfikowalne**

   Specyfikator klasy **magazynu modyfikowatej** nie jest już dozwolony w miejscach, w których wcześniej skompilowano bez błędu. Teraz kompilator daje błąd C2071 (klasa nielegalnego magazynu). Zgodnie ze standardem **modyfikowalny** specyfikator może być stosowany tylko do nazw elementów członkowskich danych klasy i nie może być stosowany do nazw zadeklarowanych const lub static i nie może być stosowany do elementów członkowskich odwołania.

   Rozważmy na przykład następujący kod:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Poprzednie wersje kompilatora zaakceptował to, ale teraz kompilator daje następujący błąd:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Aby naprawić błąd, usuń zbędne słowo kluczowe **modyfikowalne.**

- **char_16_t i char32_t**

   Nie można już `char16_t` `char32_t` używać ani jako aliasów w **typedef**, ponieważ te typy są teraz traktowane jako wbudowane. Użytkownicy i autorzy bibliotek `char16_t` często `char32_t` definiują `uint16_t` i `uint32_t`jako aliasy i , odpowiednio.

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

   Aby zaktualizować kod, usuń deklaracje **typedef** i zmień nazwę innych identyfikatorów, które zderzają się z tymi nazwami.

- **Parametry szablonu bez typu**

   Niektóre kody, które obejmuje parametry szablonu nie typu jest teraz poprawnie sprawdzane pod kątem zgodności typu po podaniu jawne argumenty szablonu. Na przykład następujący kod skompilowany bez błędu w poprzednich wersjach programu Visual Studio.

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

   Bieżący kompilator poprawnie podaje błąd, ponieważ typ parametru szablonu nie pasuje do argumentu szablonu (parametr jest wskaźnikiem do elementu członkowskiego const, ale funkcja f nie jest zgodna z const):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Aby rozwiązać ten błąd w kodzie, upewnij się, że typ argumentu szablonu, którego używasz, jest zgodny z zadeklarowanym typem parametru szablonu.

- **__declspec(wyrównywanie)**

   Kompilator nie akceptuje `__declspec(align)` już funkcji. Ta konstrukcja była zawsze ignorowana, ale teraz generuje błąd kompilatora.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Aby rozwiązać ten `__declspec(align)` problem, usuń z deklaracji funkcji. Ponieważ nie miał żadnego efektu, usunięcie go nic nie zmienia.

- **Obsługa wyjątków**

   Istnieje kilka zmian w obsłudze wyjątków. Po pierwsze, obiekty wyjątków muszą być kopiowane lub ruchome. Następujący kod skompilowany w programie Visual Studio 2013, ale nie jest kompilowany w programie Visual Studio 2015:

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

   Problem polega na tym, że konstruktor kopii jest prywatny, więc obiektu nie można skopiować, jak to się dzieje w normalnym przebiegu obsługi wyjątku. To samo dotyczy sytuacji, gdy konstruktor kopii jest zadeklarowany **jawnie.**

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

   Aby zaktualizować kod, upewnij się, że konstruktor kopii dla obiektu wyjątku jest **publiczny** i nie jest **oznaczony jako jawny.**

   Przechwytywanie wyjątku przez wartość wymaga również obiekt wyjątku do kopiowania. Następujący kod skompilowany w programie Visual Studio 2013, ale nie jest kompilowany w programie Visual Studio 2015:

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

   Ten problem można rozwiązać, zmieniając typ parametru dla **catch** na odwołanie.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Literały ciągów, po których następowały makra**

   Kompilator obsługuje teraz literały zdefiniowane przez użytkownika. W konsekwencji literały ciągów, po których następują makra bez interweniujących odstępów, są interpretowane jako literały zdefiniowane przez użytkownika, co może powodować błędy lub nieoczekiwane wyniki. Na przykład w poprzednich kompilatorach następujący kod został pomyślnie skompilowany:

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

   Kompilator zinterpretował ten kod jako literał ciągu "hello", po którym następuje makro, które jest rozwijane do "tam", a następnie dwa literały ciągu zostały połączone w jeden. W programie Visual Studio 2015 kompilator interpretuje tę sekwencję jako literał zdefiniowany przez `_x` użytkownika, ale ponieważ nie ma żadnych dopasowujących zdefiniowanych literału zdefiniowanych przez użytkownika, daje błąd.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Aby rozwiązać ten problem, dodaj spację między literału ciągu a makro.

- **Sąsiednie literały ciągów**

   Podobnie jak w poprzednim, ze względu na powiązane zmiany w analizowaniu ciągów, sąsiednie literały ciągu (literały ciągów szerokich lub wąskich) bez żadnych odstępów były interpretowane jako pojedynczy ciąg łączony w poprzednich wersjach Visaul C++. W programie Visual Studio 2015 należy teraz dodać odstępy między dwoma ciągami. Na przykład należy zmienić następujący kod:

    ```cpp
    char * str = "abc""def";
    ```

   Aby rozwiązać ten problem, dodaj spację między dwoma ciągami:

    ```cpp
    char * str = "abc" "def";
    ```

- **Umieszczanie nowych i usuwanie**

   Wprowadzono zmianę **w** delete operator w celu dostosowania go do standardu C++14. Szczegółowe informacje na temat zmiany standardów można znaleźć na [stronie C++ Sized Deallocation](https://isocpp.org/files/papers/n3778.html). Zmiany dodać formę globalnego operatora **usuwania,** który przyjmuje parametr rozmiaru. Przełomowa zmiana polega na tym, że jeśli wcześniej używano operatora **delete** z tym samym podpisem (aby odpowiadać nowemu operatorowi **umieszczania),** zostanie wyświetlony błąd kompilatora (C2956, który występuje w punkcie, w którym jest używane nowe miejsce docelowe, ponieważ jest to pozycja w kodzie, w której kompilator próbuje zidentyfikować odpowiedni pasujący operator **usuwania).**

   Funkcja `void operator delete(void *, size_t)` była **operatorem usuwania miejsc docelowych** odpowiadającym **umieszczeniu nowej** funkcji `void * operator new(size_t, size_t)` w języku C++11. Z C + + 14 wielkości deallocation, ta funkcja usuwania jest teraz *zwykłą funkcją alokacji (operator* **usuwania** globalnego). Standard wymaga, aby jeśli użycie nowego miejsca docelowego wyszukuje odpowiednią funkcję usuwania i znajdzie zwykłą funkcję lokalizowania, program jest źle sformułowany.

   Załóżmy na przykład, że kod definiuje zarówno **umieszczenie nowe,** jak i **usunięcie miejsca docelowego:**

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   Ten problem występuje z powodu dopasowania w podpisach funkcji między zdefiniowanym operatorem **usuwania miejsca docelowego** a nowym operatorem **usuwania** o rozmiarze globalnym. Należy wziąć pod uwagę, czy `size_t` można użyć innego typu niż dla dowolnego **miejsca nowego** i **delete** operatorów. Typ `size_t` **typedef** jest zależny od kompilatora; jest **typedef** dla **niepodpisanych int** w MSVC. Dobrym rozwiązaniem jest użycie wyliczonego typu, takiego jak ten:

    ```cpp
    enum class my_type : size_t {};
    ```

   Następnie zmień definicję **umieszczania i** **usuń,** aby użyć tego `size_t`typu jako drugiego argumentu zamiast . Należy również zaktualizować wywołania do umieszczenia nowy, aby przekazać nowy `static_cast<my_type>` typ (na przykład za pomocą konwersji z wartości całkowitej) i zaktualizować definicję **nowych** i **usunąć,** aby rzutować z powrotem do typu liczby całkowitej. Nie musisz używać do tego **wyliczenia;** typ klasy z `size_t` członkiem również będzie działać.

   Alternatywnym rozwiązaniem jest to, że może być w stanie całkowicie wyeliminować **umieszczenie nowe.** Jeśli kod używa **umieszczania nowy** do zaimplementowania puli pamięci, gdzie argument umieszczania jest rozmiar obiektu są przydzielane lub usuwane, a następnie wielkości funkcji dezalokacji może być odpowiedni do zastąpienia własnego kodu puli pamięci niestandardowej i można pozbyć się funkcji umieszczania i po prostu użyć własnego dwuarzyscowego delete operatora zamiast funkcji umieszczania. **delete**

   Jeśli nie chcesz natychmiast aktualizować kodu, możesz przywrócić stare zachowanie przy użyciu `/Zc:sizedDealloc-`opcji kompilatora . Jeśli użyjesz tej opcji, funkcje usuwania dwóch argumentów nie istnieją i nie powodują konfliktu z operatorem **usuwania miejsca docelowego.**

- **Unijni członkowie danych**

   Elementy członkowskie danych związków nie mogą już mieć typów odwołań. Poniższy kod został pomyślnie skompilowany w programie Visual Studio 2013, ale generuje błąd w programie Visual Studio 2015.

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

   Aby rozwiązać ten problem, zmień typy odwołań na wskaźnik lub wartość. Zmiana typu na wskaźnik wymaga zmian w kodzie, który używa pola unii. Zmiana kodu na wartość spowoduje zmianę danych przechowywanych w unii, co wpływa na inne pola, ponieważ pola w typach unii współużytkują tę samą pamięć. W zależności od rozmiaru wartości może również zmienić rozmiar unii.

- Anonimowe związki są teraz bardziej zgodne ze standardem. Poprzednie wersje kompilatora generowane jawne konstruktora i destruktora dla związków anonimowych. Te funkcje generowane przez kompilator są usuwane w programie Visual Studio 2015.

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

   Aby rozwiązać ten problem, podaj własne definicje konstruktora i/lub destruktora.

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

- **Związki zawodowe z anonimowymi strukturami**

   Aby zapewnić zgodność ze standardem, zachowanie środowiska uruchomieniowego uległo zmianie dla członków struktur anonimowych w związkach. Konstruktor dla członków struktury anonimowej w związku nie jest już niejawnie wywoływane podczas tworzenia takiej unii. Ponadto destruktor dla członków struktury anonimowej w unii nie jest już niejawnie wywoływane, gdy związek wykracza poza zakres. Należy wziąć pod uwagę następujący kod, w którym unia U zawiera strukturę anonimową, która zawiera nazwany struktury elementu członkowskiego S, który ma destruktora.

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

   W programie Visual Studio 2013 konstruktor dla S jest wywoływany podczas tworzenia unii, a destruktor dla S jest wywoływany, gdy stos dla funkcji f jest czyszczony. Ale w programie Visual Studio 2015 konstruktora i destruktora nie są wywoływane. Kompilator daje ostrzeżenie o tej zmianie zachowania.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Aby przywrócić oryginalne zachowanie, nadaj strukturze anonimowej nazwę. Zachowanie środowiska wykonawczego struktur nieanonimowych jest taka sama, niezależnie od wersji kompilatora.

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

   Alternatywnie spróbuj przenieść kod konstruktora i destruktora do nowych funkcji i dodać wywołania do tych funkcji z konstruktora i destruktora dla unii.

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

- **Rozdzielczość szablonu**

   Wprowadzono zmiany w rozpoznawaniu nazw szablonów. W języku C++, rozważając kandydatów do rozwiązania nazwy, może być tak, że jedna lub więcej nazw pod uwagę jako potencjalne dopasowania tworzy nieprawidłowe wystąpienie szablonu. Te nieprawidłowe wystąpienia zwykle nie powodują błędów kompilatora, zasada znana jako SFINAE (błąd podstawiania nie jest błędem).

   Teraz jeśli SFINAE wymaga kompilatora do wystąpienia specjalizacji szablonu klasy, następnie wszelkie błędy, które występują podczas tego procesu są błędy kompilatora. W poprzednich wersjach kompilator ignoruje takie błędy. Rozważmy na przykład następujący kod:

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

   Jeśli kompilujesz z bieżącym kompilatorem, pojawia się następujący błąd:

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

   Dzieje się tak, ponieważ w punkcie pierwszego wywołania is_base_of `D` klasa nie została jeszcze zdefiniowana.

   W takim przypadku poprawka nie jest użycie takich cech typu, dopóki klasa została zdefiniowana. Jeśli przeniesiesz definicje `B` `D` i na początek pliku kodu, błąd zostanie rozwiązany. Jeśli definicje znajdują się w plikach nagłówkowych, sprawdź kolejność zestawienia dla plików nagłówkowych, aby upewnić się, że wszystkie definicje klas są kompilowane przed użyciem problematycznych szablonów.

- **Konstruktory kopiowania**

   W programie Visual Studio 2013 i Visual Studio 2015 kompilator generuje konstruktora kopii dla klasy, jeśli ta klasa ma konstruktora przenoszenia zdefiniowane przez użytkownika, ale nie konstruktora kopiowania zdefiniowanego przez użytkownika. W dev14 ten niejawnie wygenerowany konstruktor kopii jest również oznaczony "= delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **main zadeklarowane jako extern "C" teraz wymaga typu zwrotu.**

   Poniższy kod tworzy teraz C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Aby naprawić błąd, dodaj typ zwracany:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **nazwa typu nie jest dozwolona w inicjatorze elementu członkowskiego**

   Poniższy kod tworzy teraz C2059:

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

   Aby naprawić błąd, `typename` usuń z inicjatora:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **Klasa magazynu na jawne specjalizacje jest ignorowana.**

   W poniższym kodzie specyfikator klasy magazynu statycznego jest ignorowany

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

- **Stała używana w static_assert wewnątrz szablonu klasy zawsze zakończy się niepowodzeniem.**

   Poniższy kod `static_assert` powoduje, że zawsze zakończy się niepowodzeniem:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Aby obejść ten problem, zawiń wartość w **strukturę:**

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

- **Reguły wymuszane dla deklaracji przesyłania dalej. (Dotyczy tylko C.)**

   Poniższy kod tworzy teraz C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Aby rozwiązać ten problem, dodaj odpowiednie deklaracje do przodu:

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

   Poniższy kod tworzy teraz C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Niejednoznaczne wywołania przeciążonych funkcji**

   Poniższy kod tworzy teraz C266: 'N::bind': niejednoznaczne wywołanie przeciążonej funkcji

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

   Aby naprawić błąd, można w pełni `bind: N::bind(...)`zakwalifikować wywołanie do . Jednak jeśli ta zmiana jest manifestowana za pośrednictwem niezadeklarowanego identyfikatora (C2065), a następnie może być właściwe, aby rozwiązać ten problem za **pomocą** using deklaracji zamiast.

   Ten wzorzec występuje często z ComPtr i innych typów w obszarze `Microsoft::WRL` nazw.

- **Napraw nieprawidłowy adres**

   Poniższy kod tworzy teraz C2440: '=': nie można przekonwertować z 'type *' na 'type'. Aby naprawić błąd, zmień &(type) na (type) i (&f()) na (f()).

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

   Poniższy kod tworzy teraz C2664: 'void f(void *)': nie można przekonwertować argumentu 1 z 'const char (*)[2]' na 'void *'

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Aby naprawić błąd, zmień typ `const void*`parametru funkcji na `h` , lub zmień treść, aby wyglądać jak w tym przykładzie:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **Ciągi UDL języka C++11**

   Poniższy kod generuje teraz błąd C3688: nieprawidłowy sufiks literał "L"; Nie znaleziono dosłownego operatora lub dosłownego szablonu operatora 'operator "L'.

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Aby naprawić błąd, zmień kod, aby dodać spację:

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

   W powyższym `MACRO` przykładzie nie jest już analizowany jako dwa tokeny (ciąg następuje makro). Teraz jest analizowany jako pojedynczy token UDL. To samo dotyczy L""L", który był wcześniej analizowany jako L"" i L",", a teraz jest analizowany jako L""L i "".

   Reguły łączenia ciągów zostały również doprowadzone do zgodności ze standardem, co oznacza, że L"a" "b" jest odpowiednikiem L"ab". Poprzednie wersje programu Visual Studio nie akceptowały łączenia ciągów o różnej szerokości znaków.

- **C++11 pusty znak usunięty**

   Poniższy kod generuje teraz błąd C2137: pusta stała znaków

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Aby naprawić błąd, zmień kod, aby null jawne:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Wyjątków MFC nie można złapać przez wartość, ponieważ nie można ich kopiować**

   Poniższy kod w aplikacji MFC powoduje teraz błąd C2316: "D": nie można złapać, ponieważ destruktor i/lub konstruktor kopii są niedostępne lub usunięte

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

   Aby naprawić kod, można zmienić `catch (const D &)` catch bloku, ale lepszym rozwiązaniem jest zwykle użycie makr MFC TRY/CATCH.

- **alignof jest teraz słowem kluczowym**

   Poniższy kod generuje teraz błąd C2332: 'class': missing tag name. Aby naprawić kod należy zmienić nazwę klasy lub, jeśli klasa wykonuje taką samą pracę jak **alignof**, wystarczy zastąpić klasę z nowym słowem kluczowym.

    ```cpp
    class alignof{}
    ```

- **constexpr jest teraz słowem kluczowym**

   Poniższy kod generuje teraz błąd C2059: błąd składni: ')'. Aby naprawić kod, należy zmienić nazwę dowolnej funkcji lub nazwy zmiennych, które są nazywane "constexpr".

    ```cpp
    int constexpr() {return 1;}
    ```

- **Ruchome typy nie mogą być const**

   Gdy funkcja zwraca typ, który ma zostać przeniesiony, jego typ powrotu nie powinien być **const**.

- **Usunięte konstruktory kopii**

   Poniższy kod tworzy teraz C2280 'S::S(S &&)': próbuje odwołać się do usuniętej funkcji:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Aby naprawić błąd, użyj inicjowania bezpośredniego dla: `S2`

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Konwersja do wskaźnika funkcji generowane tylko wtedy, gdy nie lambda przechwytywania**

   Poniższy kod tworzy C2664 w programie Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Aby naprawić błąd, `=` usuń go z listy przechwytywania.

- **Niejednoznaczne wywołania z udziałem operatorów konwersji**

   Poniższy kod generuje teraz błąd C2440: "type cast": nie można przekonwertować z 'S2' na 'S1':

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

   Aby naprawić błąd, należy jawnie wywołać operator konwersji:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Poniższy kod generuje teraz błąd C2593: 'operator =' jest niejednoznaczny:

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

   Aby naprawić błąd, należy jawnie wywołać operator konwersji:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Napraw nieprawidłowe inicjowanie kopiowania podczas inicjowania elementu członkowskiego danych niestatycznych (NSDMI)**

   Następujący kod generuje teraz błąd C2664: 'S1::S1(S1 &&)': nie można przekonwertować argumentu 1 z 'bool' na 'const S1 &':

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Aby naprawić błąd, użyj inicjowania bezpośredniego:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Uzyskiwanie dostępu do konstruktorów wewnątrz instrukcji odznaczania**

   Poniższy kod tworzy teraz C2248: "S::S": nie można uzyskać dostępu do prywatnego elementu członkowskiego zadeklarowane w klasie "S":

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

   Aby naprawić błąd, dodaj deklarację znajomego w `S2` : `S`

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Domyślny ctor lambda jest niejawnie usuwany**

   Poniższy kod generuje teraz błąd C3497: nie można skonstruować wystąpienia lambda:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Aby naprawić błąd, należy usunąć konieczność wywołania domyślnego konstruktora. Jeśli lambda nie przechwytuje niczego, a następnie może być rzut oddanych do wskaźnika funkcji.

- **Lambdas z usuniętym operatorem przypisania**

   Następujący kod generuje teraz błąd C2280:

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

   Aby naprawić błąd, należy zastąpić lambda klasy functor lub usunąć konieczność korzystania z operatora przypisania.

- **Próba przeniesienia obiektu z usuniętym konstruktorem kopii**

   Następujący kod generuje teraz błąd C2280: 'moveable::moveable(const moveable &)": próba odwołania się do usuniętej funkcji

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

   Aby naprawić błąd, `std::move` użyj zamiast tego:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Klasa lokalna nie może odwoływać się do innych klas lokalnych zdefiniowanych później w tej samej funkcji**

   Poniższy kod generuje teraz błąd C2079: 's' używa niezdefiniowanej struktury 'main::S2'

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

   Aby naprawić błąd, przesuń w górę definicję `S2`:

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

- **Nie można wywołać chronionego ctor podstawy w treści ctor pochodne.**

   Poniższy kod generuje teraz błąd C2248: "S1::S1": nie może uzyskać dostępu do chronionego elementu członkowskiego zadeklarowanego w klasie 'S1'

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

   Aby naprawić błąd, `S2` w remove `S1()` wywołanie z konstruktora i w razie potrzeby umieścić go w innej funkcji.

- **{}zapobiega konwersji na wskaźnik**

   Poniższy kod generuje teraz C2439 "S::p": nie można zainicjować elementu członkowskiego

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Aby naprawić błąd, usuń nawiasy `0` klamrowe z całego lub zamiast tego użyj **nullptr,** jak pokazano w tym przykładzie:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Niepoprawna definicja makra i użycie z nawiasami**

   Poniższy przykład powoduje teraz błąd C2008: ';': nieoczekiwany w definicji makra

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Aby rozwiązać ten problem, zmień górną linię na`#define A();`

   Następujący kod generuje błąd C2059: błąd składni: ')'

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Aby naprawić kod, usuń odstęp między A i ().

   Następujący kod generuje błąd C2091: funkcja zwraca funkcję:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Aby naprawić błąd, usuń nawiasy po DECLARE `DECLARE;`w S: .

   Następujący kod generuje błąd C2062: wpisz "int" nieoczekiwane

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Aby rozwiązać ten `A` problem, zdefiniuj w ten sposób:

    ```cpp
    #define A int
    ```

- **Dodatkowe parens w deklaracjach**

   Następujący kod generuje błąd C2062: wpisz "int" nieoczekiwane

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Aby naprawić błąd, usuń nawiasy `j`wokół . Jeśli nawiasy są potrzebne do jasności, należy użyć **typedef**.

- **Konstruktory generowane przez kompilator i __declspec(novtable)**

   W programie Visual Studio 2015 istnieje zwiększone prawdopodobieństwo, że kompilator generowane wbudowane konstruktory klas abstrakcyjnych z wirtualnych klas podstawowych może narazić niewłaściwe `__declspec(novtable)` użycie, gdy jest używany w połączeniu z `__declspec(dllimport)`.

- **auto wymaga pojedynczego wyrażenia w inicjalizacji listy bezpośredniej**

   Poniższy kod generuje teraz błąd C3518: 'testPositions': w kontekście inicjowania listy bezpośredniej typ "auto" można wywnioskować tylko z pojedynczego wyrażenia inicjatora

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Aby naprawić błąd, jedną z możliwości `testPositions` jest zainicjowanie w następujący sposób:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Sprawdzanie typów a wskaźników do typów dla is_convertible**

   Poniższy kod powoduje teraz, że twierdzenie statyczne zakończy się niepowodzeniem.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Aby naprawić błąd, `static_assert` zmień wskaźnik, aby `D` porównać `B2`wskaźniki i:

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **__declspec(novtable) deklaracje muszą być spójne**

   `__declspec`deklaracje muszą być spójne we wszystkich bibliotekach. Poniższy kod spowoduje teraz naruszenie reguły jednej definicji (ODR):The following code will now produce a one-definition rule (ODR) violation:

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

### <a name="conformance-improvements-in-update-1"></a><a name="VS_Update1"></a>Ulepszenia zgodności w aktualizacji 1

- **Prywatne wirtualne klasy podstawowe i dziedziczenie pośrednie**

   Poprzednie wersje kompilatora dozwolone klasy pochodnej do wywoływania funkcji `private virtual` członkowskich jego pośrednio pochodnych klas podstawowych. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. Kompilator nie akceptuje już kodu napisanego w ten sposób i generuje błąd kompilatora C2280 w wyniku.

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

   \-lub -

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Przeciążony operator nowy i usunięcie operatora**

   Poprzednie wersje kompilatora dozwolone operator niebędący elementami **elementów członkowskich usunięcie nowego** i innego elementu **członkowskiego,** które mają być zadeklarowane jako statyczne i zadeklarowane w przestrzeniach nazw innych niż globalna przestrzeń nazw.  To stare zachowanie stworzyło ryzyko, że program nie będzie wywoływać **nowej** lub **usuwać** implementacji operatora, że programista przeznaczone, co powoduje ciche złe zachowanie środowiska uruchomieniowego. Kompilator nie akceptuje już kodu napisanego w ten sposób i zamiast tego generuje błąd kompilatora C2323.

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

   Ponadto mimo że kompilator nie daje określonej diagnostyki, wbudowany operator **nowy** jest uważany za nieuformowany.

- **Wywoływanie *"typu*operatora ()" (konwersja zdefiniowana przez użytkownika) w typach innych niż klasy**

   Poprzednie wersje kompilatora dozwolone *"typ*operatora ()" być wywoływane na typy innych klas, podczas gdy dyskretnie ignorując go. To stare zachowanie stworzyło ryzyko generowania cichego złego kodu, co spowodowało nieprzewidywalne zachowanie środowiska uruchomieniowego. Kompilator nie akceptuje już kodu napisanego w ten sposób i zamiast tego generuje błąd kompilatora C2228.

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

- **Nadmiarowa nazwa typu w opracowanych specyfikatorach typu**

   Poprzednie wersje kompilatora dozwolone **nazwa typu** w specyfikatora typu opracowanego, ale kod napisany w ten sposób jest semantycznie niepoprawne. Kompilator nie akceptuje już kodu napisanego w ten sposób i zamiast tego generuje błąd kompilatora C3406.

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

- **Typ odliczanie tablic z listy inicjatora**

   Poprzednie wersje kompilatora nie obsługiwały odliczeń typów tablic z listy inicjatorów. Kompilator obsługuje teraz tę formę dedukcji typu i w rezultacie wywołania szablonów funkcji przy użyciu list inicjatora może być teraz niejednoznaczne lub może być wybrane inne przeciążenie niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program musi teraz jawnie określić przeciążenie, które programista przeznaczone.

   Gdy to nowe zachowanie powoduje, że rozwiązanie przeciążenia do rozważenia dodatkowego kandydata, który jest równie dobry jak kandydat historyczny, wywołanie staje się niejednoznaczne i kompilatora problemy kompilatora błąd C2668 w wyniku.

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   Przykład 1: Niejednoznaczne wywołanie przeciążonej funkcji (przed)

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

   Gdy to nowe zachowanie powoduje, że rozwiązanie przeciążenia do rozważenia dodatkowego kandydata, który jest lepiej dopasowane niż historycznego kandydata, wywołanie rozwiązuje jednoznacznie do nowego kandydata, powodując zmianę zachowania programu, który prawdopodobnie różni się od programisty przeznaczone.

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

- **Przywracanie ostrzeżeń instrukcji przełącznika**

   Poprzednia wersja kompilatora usunęła niektóre ostrzeżenia związane z **instrukcjami switch;** ostrzeżenia te zostały przywrócone. Kompilator teraz wystawia przywrócone ostrzeżenia i ostrzeżenia związane z określonymi przypadkami (w tym przypadek domyślny) są teraz wydawane w wierszu zawierającym przypadek naruszający, a nie w ostatnim wierszu instrukcji switch. W wyniku wydawania tych ostrzeżeń w różnych liniach niż w przeszłości `#pragma warning(disable:####)` ostrzeżenia wcześniej tłumione za pomocą mogą nie być dłużej tłumione zgodnie z przeznaczeniem. Aby pominąć te ostrzeżenia zgodnie z przeznaczeniem, może być konieczne przeniesienie `#pragma warning(disable:####)` dyrektywy do wiersza powyżej pierwszego przypadku przestępstwa. Poniżej znajdują się przywrócone ostrzeżenia:

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

   Przykłady innych przywróconych ostrzeżeń znajdują się w ich dokumentacji.

- **#include: użycie specyfikatora katalogu nadrzędnego '..' w nazwach ścieżek** `/Wall` `/WX`(dotyczy tylko)

   Poprzednie wersje kompilatora nie wykryły użycia specyfikatora katalogu nadrzędnego '.' w ścieżce `#include` dyrektyw. Kod napisany w ten sposób jest zwykle przeznaczony do uwzględnienia nagłówków, które istnieją poza projektem przez niepoprawnie przy użyciu ścieżek względnych projektu. To stare zachowanie stworzyło ryzyko, że program może zostać skompilowany przez dołączenie innego pliku źródłowego niż programista przeznaczony lub że te ścieżki względne nie będą przenośne do innych środowisk kompilacji. Kompilator teraz wykrywa i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora C4464, jeśli jest włączone.

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

   Ponadto chociaż kompilator nie daje określonej diagnostyki, zaleca się również, że specyfikator katalogu nadrzędnego ".." nie powinien być używany do określania katalogów dołączanych projektu.

- **#pragma optimize() rozciąga się na koniec minionego końca pliku nagłówka** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora nie wykryły zmian w ustawieniach flagi optymalizacji, które unikną pliku nagłówka zawartego w jednostce tłumaczenia. Kompilator wykrywa teraz i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora `#include`C4426 w lokalizacji naruszającego , jeśli jest włączone. To ostrzeżenie jest wydawane tylko wtedy, gdy zmiany są w konflikcie z flagami optymalizacji ustawionymi przez argumenty wiersza polecenia do kompilatora.

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

- **Niedopasowane #pragma ostrzeżenie (push)** i **#pragma warning(pop)** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora `#pragma warning(push)` nie wykryły `#pragma warning(pop)` zmian stanu sparowanych ze zmianami stanu w innym pliku źródłowym, który rzadko jest przeznaczony. To stare zachowanie stworzyło ryzyko, że program zostanie skompilowany z włączonym innym zestawem ostrzeżeń niż programista, co może spowodować ciche złe zachowanie środowiska uruchomieniowego. Kompilator wykrywa teraz i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora C5031 w lokalizacji pasującego `#pragma warning(pop)`, jeśli jest włączone. Ostrzeżenie to zawiera notatkę odwołującą się do lokalizacji odpowiedniego #pragma ostrzeżenie (wypychanie).

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

   Choć niezbyt często, kod napisany w ten sposób jest czasami zamierzone. Kod napisany w ten sposób jest `#include` wrażliwy na zmiany w kolejności; Jeśli to możliwe, zaleca się, aby pliki kodu źródłowego zarządzały stanem ostrzeżenia w sposób samodzielny.

- **Niezrównane ostrzeżenie #pragma (push)** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora nie wykryły niedopasowanych `#pragma warning(push)` zmian stanu na końcu jednostki tłumaczenia. Kompilator wykrywa teraz i powiadamia programistę kodu napisanego w ten sposób i generuje opcjonalne ostrzeżenie kompilatora C5032 w lokalizacji niedopasowanego `#pragma warning(push)`, jeśli jest włączona. To ostrzeżenie jest wydawane tylko wtedy, gdy w jednostce tłumaczenia nie występują błędy kompilacji.

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

- **Dodatkowe ostrzeżenia mogą zostać wydane w wyniku poprawy śledzenia stanu #pragma**

   Poprzednie wersje kompilatora śledzone #pragma stan ostrzeżenia zmienia się niewystarczająco dobrze, aby wydać wszystkie zamierzone ostrzeżenia. To zachowanie stworzyło ryzyko, że niektóre ostrzeżenia będą skutecznie pomijane w okolicznościach innych niż programista przeznaczony. Kompilator śledzi `#pragma warning` teraz stan bardziej solidnie `#pragma warning` - szczególnie związane ze zmianami stanu wewnątrz szablonów - i opcjonalnie wydaje nowe ostrzeżenia C5031 i C5032, które mają pomóc programisty zlokalizować niezamierzone zastosowania `#pragma warning(push)` i `#pragma warning(pop)`.

   W wyniku poprawy `#pragma warning` śledzenia zmian stanu, ostrzeżenia wcześniej nieprawidłowo pomijane lub ostrzeżenia związane z problemami wcześniej błędnie mogą być wydawane.

- **Ulepszona identyfikacja nieosiągalnego kodu**

   C++ Standard Library zmiany i ulepszone możliwości wywołania funkcji wbudowanych w poprzednich wersjach kompilatora może umożliwić kompilator udowodnić, że niektóre kod jest teraz nieosiągalny. To nowe zachowanie może spowodować nowe i częściej wystawiane wystąpienia ostrzeżenia C4720.

    ```Output
    warning C4720: unreachable code
    ```

   W wielu przypadkach to ostrzeżenie może być wydawane tylko podczas kompilowania z włączonymi optymalizacjami, ponieważ optymalizacje mogą wywołać więcej funkcji, wyeliminować nadmiarowy kod lub w inny sposób umożliwić ustalenie, że określony kod jest nieosiągalny. Zaobserwowaliśmy, że nowe przypadki ostrzegania C4720 często występowały w blokach **typu try/catch,** szczególnie w odniesieniu do stosowania [std::find](../standard-library/algorithm-functions.md#find).

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

### <a name="conformance-improvements-in-update-2"></a><a name="VS_Update2"></a>Ulepszenia zgodności w aktualizacji 2

- **Dodatkowe ostrzeżenia i błędy mogą być wydawane w wyniku częściowej obsługi wyrażenia SFINAE**

   Poprzednie wersje kompilatora nie analizować niektórych rodzajów wyrażeń wewnątrz **specyfikatorów decltype** ze względu na brak obsługi wyrażenia SFINAE. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. Kompilator analizuje teraz te wyrażenia i ma częściową obsługę wyrażenia SFINAE ze względu na trwające ulepszenia zgodności. W rezultacie kompilator teraz wydaje ostrzeżenia i błędy znalezione w wyrażeniach, które poprzednie wersje kompilatora nie analizował.

   Gdy to nowe zachowanie analizuje wyrażenie **decltype,** który zawiera typ, który nie został jeszcze zadeklarowany, kompilator generuje błąd kompilatora C2039 w wyniku.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Przykład 1: użycie typu niezadeklarowanego (przed)

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

   Gdy to nowe zachowanie analizuje wyrażenie **decltype,** którego brakuje niezbędnego użycia słowa kluczowego **nazwa typu,** aby określić, że nazwa zależna jest typem, kompilator wydaje ostrzeżenie kompilatora C4346 wraz z błędem kompilatora C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Przykład 2: nazwa zależna nie jest typem (przed)

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

- `volatile`**zmienne członkowskie zapobiegają niejawnie zdefiniowanym konstruktorom i operatorom przypisania**

   Poprzednie wersje kompilatora zezwalały na automatyczne generowanie klasy, która ma **zmienne zmienne nietrwałe** elementów członkowskich. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. Kompilator teraz uważa, że klasa, która ma **zmienne zmienne nietrwałe** elementów członkowskich, mają nietrywialne operatory konstrukcji i przypisania, co uniemożliwia automatyczne implementacje tych operatorów są generowane automatycznie. Gdy taka klasa jest członkiem unii (lub unii anonimowej wewnątrz klasy), konstruktory kopiowania/przenoszenia i operatorów przypisania kopiowania/przenoszenia unii (lub klasy zawierającej związek anonimowy) zostaną niejawnie zdefiniowane jako usunięte. Próba skonstruowania lub skopiowania unii (lub klasy zawierającej związek anonimowy) bez jawnego zdefiniowania ich jest błędem, a w rezultacie kompilator wydaje błąd kompilatora C2280.

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

- **Statyczne funkcje członkowskie nie obsługują kwalifikatorów cv.**

   Poprzednie wersje programu Visual Studio 2015 zezwalały na statyczne funkcje członkowskie, które miały kwalifikacje cv. To zachowanie jest spowodowane regresji w programie Visual Studio 2015 i Visual Studio 2015 Update 1; Visual Studio 2013 i poprzednie wersje kompilatora odrzuca kod napisany w ten sposób. Zachowanie visual studio 2015 i Visual Studio 2015 Update 1 jest niepoprawna i nie jest zgodna ze standardem C++.  Visual Studio 2015 Update 2 odrzuca kod napisany w ten sposób i problemalizuje błąd kompilatora C2511 zamiast.

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

   Przykład(po)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Forward deklaracja wyliczenia nie jest dozwolone w kodzie WinRT** (dotyczy `/ZW`tylko)

   Kod skompilowany dla środowiska wykonawczego systemu Windows (WinRT) nie zezwala na przekazywanie typów **wyliczeni,** podobnie jak `/clr` wtedy, gdy zarządzany kod C++ jest kompilowany dla programu .Net Framework przy użyciu przełącznika kompilatora. To zachowanie zapewnia, że rozmiar wyliczenia jest zawsze znany i może być poprawnie rzutowane do systemu typu WinRT. Kompilator odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2599 wraz z błędem kompilatora C3197.

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

- **Przeciążony operator niebędący członkiem nowy i usunięcie operatora nie może być zadeklarowany w linii wbudowanej** (poziom 1 (`/W1`) domyślnie)

   Poprzednie wersje kompilatora nie wydają ostrzeżenia, gdy operator niebędący elementem członkowskim nowe i operator delete funkcje są zadeklarowane wbudowane. Kod napisany w ten sposób jest źle sformułowany (nie wymaga diagnostyki) i może powodować problemy z pamięcią wynikające z niedopasowanych operatorów nowych i delete (szczególnie gdy są używane razem z rozmiarem dezlokacji), które mogą być trudne do zdiagnozowania. Kompilator teraz generuje ostrzeżenie kompilatora C4595, aby pomóc zidentyfikować kod napisany w ten sposób.

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

   Kod naprawiania, który jest napisany w ten sposób może wymagać, aby definicje operatora zostały przeniesione z pliku nagłówka i do odpowiedniego pliku źródłowego.

### <a name="conformance-improvements-in-update-3"></a><a name="VS_Update3"></a>Ulepszenia zgodności w aktualizacji 3

- **std::is_convertable wykrywa teraz samoadowanie** (standardowa biblioteka)

   Poprzednie wersje `std::is_convertable` cechy typu nie wykrywały poprawnie samoadowania typu klasy, gdy jego konstruktor kopii zostanie usunięty lub prywatny. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona na **false** po zastosowaniu do typu klasy z konstruktorem usunięte lub kopii prywatnej.

   Z tą zmianą nie jest skojarzona żadna diagnostyka kompilatora.

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

   W poprzednich wersjach kompilatora statyczne potwierdzenia w dolnej `std::is_convertable<>::value` części tego przykładu przebiegają, ponieważ został niepoprawnie ustawiony na **true**. Teraz `std::is_convertable<>::value` jest poprawnie ustawiona na **false**, powodując nie powiodło się potwierdzenia statyczne.

- **Domyślnie lub usunięte trywialne konstruktory kopiowania i przenoszenia respektują specyfikatory dostępu**

   Poprzednie wersje kompilatora nie sprawdzały specyfikatora dostępu domyślnie lub usunięte trywialne kopiowanie i przenoszenie konstruktorów przed zezwoleniem na ich wywołanie. To stare zachowanie było niepoprawne i nie jest zgodne ze standardem C++. W niektórych przypadkach to stare zachowanie stworzyło ryzyko generowania cichego złego kodu, co spowodowało nieprzewidywalne zachowanie środowiska uruchomieniowego. Kompilator sprawdza teraz specyfikator dostępu domyślnie lub usunięte trywialne kopiowanie i przenoszenie konstruktorów, aby ustalić, czy można go wywołać, a jeśli nie, problemy kompilator ostrzeżenie C2248 w wyniku.

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

- **Wycofanie obsługi kodu przypisanego ATL** (poziom`/W1`1 ( ) domyślnie)

   Poprzednie wersje kompilatora obsługiwane przypisany kod ATL. Jako następna faza usuwania obsługi przypisanego kodu ATL, który [rozpoczął się w programie Visual Studio 2008,](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008)przypisany kod ATL został przestarzały. Kompilator teraz generuje ostrzeżenie kompilatora C4467, aby pomóc zidentyfikować tego rodzaju przestarzały kod.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Jeśli chcesz nadal używać przypisanego kodu ATL, dopóki obsługa nie zostanie usunięta `/Wv:18` `/wd:4467` z kompilatora, możesz wyłączyć `#pragma warning(disable:4467)` to ostrzeżenie, przekazując argumenty wiersza polecenia do kompilatora lub dodając w kodzie źródłowym.

   Przykład 1 (przed)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Przykład 1 (po)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Czasami może być konieczne lub chcesz utworzyć plik IDL, aby uniknąć użycia przestarzałych atrybutów ATL, jak w poniższym przykładowym kodzie

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

   Najpierw utwórz plik *.idl; wygenerowany plik vc140.idl może służyć \*do uzyskania pliku .idl zawierającego interfejsy i adnotacje.

   Następnie dodaj krok MIDL do kompilacji, aby upewnić się, że definicje interfejsu języka C++ są generowane.

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

   Następnie należy użyć ATL bezpośrednio w pliku implementacji, jak w poniższym przykładzie kodu.

   Przykład 2 Implementacja (po)

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

- **Wstępnie skompilowane pliki nagłówka (PCH) i niedopasowane dyrektywy** `/Wall` `/WX`#include (dotyczy tylko)

   Poprzednie wersje kompilatora akceptowały `#include` niedopasowane dyrektywy `-Yc` w `-Yu` plikach źródłowych między i kompilacje podczas korzystania z plików nagłówka wstępnie skompilowanego (PCH). Kod napisany w ten sposób nie jest już akceptowany przez kompilator.   Kompilator generuje teraz ostrzeżenie kompilatora CC4598, aby ułatwić identyfikowanie niedopasowanych `#include` dyrektyw podczas korzystania z plików PCH.

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   Przykład (przed):

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   Przykład (po)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **Wstępnie skompilowane pliki nagłówka (PCH) i niedopasowane katalogi dołączania** (dotyczy `/Wall` `/WX`tylko)

   Poprzednie wersje kompilatora akceptowane niedopasowane obejmują`-I`katalog ( ) argumenty wiersza polecenia do kompilatora między `-Yc` i `-Yu` kompilacji podczas korzystania z wstępnie skompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest już akceptowany przez kompilator. Kompilator generuje teraz ostrzeżenie kompilatora CC4599, aby`-I`pomóc w identyfikacji niezgodnych argumentów wiersza polecenia () podczas korzystania z plików PCH.

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

## <a name="visual-studio-2013-conformance-changes"></a>Zmiany zgodności programu Visual Studio 2013

### <a name="compiler"></a>Kompilator

- **Ostateczne** słowo kluczowe generuje teraz nierozwiązany błąd symbolu, w którym wcześniej zostałby skompilowany:

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

   We wcześniejszych wersjach błąd nie został wystawiony, ponieważ wywołanie było wywołaniem **wirtualnym;** niemniej jednak program uległby awarii w czasie wykonywania. Teraz zostaje zgłoszony błąd konsolidatora, ponieważ wiadomo, że klasa jest ostateczna. W tym przykładzie, aby naprawić błąd, należy połączyć się `S2::f`z obj, który zawiera definicję .

- Podczas korzystania z funkcji znajomych w przestrzeniach nazw, należy ponownie zadeklarować funkcję znajomego przed odniesieniem się do niego lub pojawi się błąd, ponieważ kompilator jest teraz zgodny ze standardem ISO C++. Na przykład w tym przykładzie nie jest już kompilowana:

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

   Aby poprawić ten kod, zadeklaruj funkcję **znajomego:**

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

- Standard Języka C++ nie zezwala na jawną specjalizację w klasie. Chociaż kompilator Języka Microsoft C++ zezwala na to w niektórych przypadkach, w przypadkach, takich jak poniższy przykład, błąd jest teraz generowany, ponieważ kompilator nie uważa drugiej funkcji za specjalizację pierwszej.

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

- Kompilator nie próbuje już rozróżnić dwie funkcje w poniższym przykładzie, a teraz emituje błąd:

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

- Zanim kompilator został zgodny z normą ISO C++11, `x` następujący kod został skompilowany i spowodował, aby rozwiązać, aby wpisać **int:**

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Ten kod jest `x` teraz rozpoznawany jako typ `std::initializer_list<int>` i powoduje błąd `x` w następnym wierszu, który próbuje przypisać do wpisania **int**. (Domyślnie nie ma konwersji). Aby poprawić ten kod, użyj **int,** aby zastąpić **auto:**

    ```cpp
    int x = {0};
    int y = x;
    ```

- Inicjowanie agregacji nie jest już dozwolone, gdy typ wartości po prawej stronie nie jest zgodny z typem zainicjowanej wartości lewej strony i jest wystawiany błąd, ponieważ norma ISO C++11 wymaga jednoliczenia do pracy bez zawężania konwersji. Wcześniej, jeśli konwersja zawężenia była dostępna, ostrzeżenie [kompilatora (poziom 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) ostrzeżenie zostałoby wydane zamiast błędu.

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   Aby poprawić ten kod, dodaj jawną konwersję zawężającą:

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- Następujące inicjowanie nie jest już dozwolone:

    ```cpp
    void *p = {{0}};
    ```

   Aby poprawić ten kod, użyj którejś z tych postaci:

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- Odnośnik nazw został zmieniony. Następujący kod jest rozpoznawany inaczej w kompilatorze języka C++ w programie Visual Studio 2012 i visual studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   W programie Visual Studio 2012 `E1` wyrażenie `::E1` `E1::b` w języku rozszerzonym w zakresie globalnym. W programie Visual Studio `E1` 2013 w wyrażeniu `::E2` `E1::b` jest rozpoznawana definicja `typedef E2` w `main()` i ma typ .

- Układ obiektu został zmieniony. W x64, układ obiektu klasy może się zmienić w porównaniu z poprzednimi wydaniami. Jeśli ma funkcję **wirtualną,** ale nie ma klasy podstawowej, która ma funkcję **wirtualną,** model obiektu kompilatora wstawia wskaźnik do tabeli funkcji **wirtualnych** po układzie elementu członkowskiego danych. Oznacza to, że układ może nie być optymalny we wszystkich przypadkach. W poprzednich wersjach optymalizacji dla x64 będzie próbował poprawić układ dla Ciebie, ale ponieważ nie działa poprawnie w sytuacjach złożonych kodu, został usunięty w programie Visual Studio 2013. Na przykład, rozważmy ten kod:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- W programie Visual Studio 2013 wynik `sizeof(S2)` na x64 jest 48, ale w poprzednich wersjach, ocenia do 32. Aby to ocenić do 32 w visual studio 2013 C++ kompilator dla x64, dodaj atrapę klasy podstawowej, która ma funkcję **wirtualną:**

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

   Aby znaleźć miejsca w kodzie, które wcześniej wersji próbował zoptymalizować, należy użyć `/W3` kompilatora z tej wersji wraz z opcją kompilatora i włączyć ostrzeżenie C4370. Przykład:

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

   Przed Visual Studio 2013 ten kod wyprowadza ten komunikat: "ostrzeżenie C4370: 'S2': układ klasy zmienił się z poprzedniej wersji kompilatora z powodu lepszego pakowania".

   Kompilator x86 ma ten sam problem z układem nieoptymalnym we wszystkich wersjach kompilatora. Na przykład, jeśli ten kod jest kompilowany dla architektury x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Wynik `sizeof(S)` jest 24. Jednak można go zmniejszyć do 16, jeśli używasz obejścia wspomnianego dla x64:

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

Kompilator języka C++ w programie Visual Studio 2013 wykrywa niezgodności w _ITERATOR_DEBUG_LEVEL, które zostały zaimplementowane w programie Visual Studio 2010 i niezgodności z przebiegiem pracy. Te niezgodności występują, gdy `/MT` opcje kompilatora (zwolnienie statyczne), `/MTd` (debugowanie statyczne), `/MD` (wersja dynamiczna) i `/MDd` (debugowanie dynamiczne) są mieszane.

- Jeśli kod potwierdza szablony symulowanych aliasów poprzedniej wersji, musisz go zmienić. Na przykład, zamiast `allocator_traits<A>::rebind_alloc<U>::other`, teraz trzeba `allocator_traits<A>::rebind_alloc<U>`powiedzieć . Chociaż `ratio_add<R1, R2>::type` nie jest już konieczne i `ratio_add<R1, R2>`teraz zalecamy, aby `ratio<N, D>` powiedzieć , były nadal skompilować, ponieważ jest wymagane, aby mieć "type" typedef dla obniżonego współczynnika, który będzie tego samego typu, jeśli jest już zmniejszona.

- Należy użyć `#include <algorithm>` podczas `std::min()` połączenia `std::max()`lub .

- Jeśli istniejący kod używa symulowanych wyliczenia o określonym zakresie poprzedniej wersji — tradycyjnych wyliczeniach nieskopowanych zawiniętych w przestrzenie nazw — należy je zmienić. Na przykład, jeśli mowa `std::future_status::future_status`o typie , `std::future_status`teraz trzeba powiedzieć . Jednak większość kodu pozostaje nienaruszona — `std::future_status::ready` na przykład nadal kompiluje.

- `explicit operator bool()`jest surowsza niż operator nieokreślony-bool-type(). `explicit operator bool()`pozwala na jawne konwersje na `shared_ptr<X> sp`bool `static_cast<bool>(sp)` `bool b(sp)` — na przykład podane , oba i są ważne — i "konwersje kontekstowe" sprawdzane przez wartość logiczną na bool `if (sp)`— na przykład , `!sp` `sp &&` cokolwiek. Jednak `explicit operator bool()` zabrania niejawne konwersje do bool, więc `bool b = sp;` nie można powiedzieć i biorąc pod `return sp`uwagę typ zwrotu bool, nie można powiedzieć .

- Teraz, gdy implementowane są rzeczywiste szablony variadic, _VARIADIC_MAX i powiązane makra nie mają wpływu. Jeśli nadal definiujesz _VARIADIC_MAX, jest to ignorowane. Jeśli przyjmiesz nasze rozwiązania makr przeznaczone do wspierania symulowanych szablonów wariadycznych w jakikolwiek inny sposób, musisz zmienić kod.

- Oprócz zwykłych słów kluczowych nagłówki biblioteki standardowej języka C++ zabraniają teraz zastępowania makr słów kluczowych **kontekstowych** i **końcowych**.

- `reference_wrapper`, `ref()`a `cref()` teraz zabronić wiązania z obiektami tymczasowymi.

- \<losowe> teraz ściśle egzekwuje swoje warunki wstępne w czasie kompilacji.

- Różne cechy typu biblioteki standardowej języka C++ mają warunek wstępny "T musi być typem kompletnym". Chociaż kompilator teraz wymusza ten warunek wstępny bardziej rygorystycznie, może nie wymusić go we wszystkich sytuacjach. (Ponieważ naruszenia zasad warunku wstępnego biblioteki standardowej języka C++ wyzwalają niezdefiniowane zachowanie, standard nie gwarantuje wymuszania).

- Standardowa biblioteka języka C++ nie obsługuje `/clr:oldSyntax`.

- Specyfikacja C++11 dla common_type<> miała nieoczekiwane i niepożądane konsekwencje; w szczególności sprawia, że\<common_type int, int>::type return int&&. W związku z tym kompilator implementuje proponowane rozwiązanie dla biblioteki grupy roboczej\<problem 2141, który sprawia, że common_type int, int="">::type return int.

   Jako efekt uboczny tej zmiany przypadek tożsamości nie działa już\<(common_type T> nie zawsze powoduje typ T). To zachowanie jest zgodne z proponowanym rozwiązaniem, ale łamie każdy kod, który opierał się na poprzednim zachowaniu.

   Jeśli potrzebujesz cechy typu tożsamości, nie używaj niestandardowej, `std::identity` która \<jest zdefiniowana w type_traits>, ponieważ \<nie będzie działać w przypadku> void. Zamiast tego wdróż własną cechę typu tożsamości odpowiednią do własnych potrzeb. Oto przykład:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC i ATL

- **Tylko visual studio 2013:** Biblioteka MBCS MFC nie jest uwzględniona w programie Visual Studio, ponieważ unicode jest tak popularny, a użycie MBCS znacznie spadło. Ta zmiana podtrzymuje również ściślejszą relację między MFC a Windows SDK. ponieważ wiele nowych kontrolek i komunikatów wymaga Unicode. Jeśli jednak musisz nadal korzystać z biblioteki MBCS MFC, możesz ją pobrać z Centrum pobierania MSDN w [bibliotece MFC Multibyte dla programu Visual Studio 2013.](https://www.microsoft.com/download/details.aspx?id=40770) Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.  (Uwaga: Biblioteka DLL MBCS jest uwzględniona w składnikach konfiguracji języka C++ w programie Visual Studio 2015 i nowszych).

- Dostępność dla wstążki MFC zostanie zmieniona.  Zamiast architektury jednopoziomowej istnieje teraz hierarchiczna architektura. Stare zachowanie można nadal używać, wywołując program `CRibbonBar::EnableSingleLevelAccessibilityMode()`.

- `CDatabase::GetConnect`zostanie usunięta. Aby zwiększyć bezpieczeństwo, parametry połączenia są teraz przechowywane zaszyfrowane i są odszyfrowywane tylko w razie potrzeby; nie można go zwrócić jako zwykłego tekstu.  Ciąg można uzyskać za `CDatabase::Dump` pomocą metody.

- Podpis `CWnd::OnPowerBroadcast` jest zmieniony. Sygnatura tego programu obsługi komunikatu została zmieniona, aby przyjąć LPARAM jako drugi parametr.

- Podpisy są zmieniane w celu uwzględnienia programów obsługi wiadomości. Listy parametrów dla poniższych funkcji zostały zmienione, aby używać nowo dodanych programów obsługi komunikatów ON_WM_*:

  - `CWnd::OnDisplayChange`zmieniono na (UINT, int, int) zamiast (WPARAM, LPARAM), aby można było użyć nowego makra ON_WM_DISPLAYCHANGE na mapie wiadomości.

  - `CFrameWnd::OnDDEInitiate`zmieniono na (CWnd*, UINT, UNIT) zamiast (WPARAM, LPARAM), aby można było użyć nowego makra ON_WM_DDE_INITIATE na mapie wiadomości.

  - `CFrameWnd::OnDDEExecute`zmieniono na (CWnd*, HANDLE) zamiast (WPARAM, LPARAM), aby można było użyć nowego makra ON_WM_DDE_EXECUTE na mapie wiadomości.

  - `CFrameWnd::OnDDETerminate`zmieniono na (CWnd*) jako parametr zamiast (WPARAM, LPARAM), aby można było użyć nowego makra ON_WM_DDE_TERMINATE na mapie wiadomości.

  - `CMFCMaskedEdit::OnCut`zmieniono na brak parametrów zamiast (WPARAM, LPARAM), tak aby można było użyć nowego makra ON_WM_CUT na mapie wiadomości.

  - `CMFCMaskedEdit::OnClear`zmieniono na brak parametrów zamiast (WPARAM, LPARAM), tak aby można było użyć nowego makra ON_WM_CLEAR na mapie wiadomości.

  - `CMFCMaskedEdit::OnPaste`zmieniono na brak parametrów zamiast (WPARAM, LPARAM), tak aby można było użyć nowego makra ON_WM_PASTE na mapie wiadomości.

- `#ifdef`w plikach nagłówkowych MFC. Liczne `#ifdef` dyrektywy w plikach nagłówkowych MFC związane z nieobsługiwały wersje systemu Windows (WINVER &lt; 0x0501) są usuwane.

- Biblioteka DLL ATL (atl120.dll) zostanie usunięta. ATL jest obecnie dostarczany jako nagłówki i biblioteka statyczna (atls.lib).

- Atlsd.lib, atlsn.lib i atlsnd.lib są usuwane. Atls.lib nie ma już zależności zestawu znaków ani kodu, który jest specyficzny dla wersji do debugowania/oficjalnych. Ponieważ działa tak samo dla Unicode/ANSI i wersji do debugowania/oficjalnych, wymagana jest tylko jedna wersja biblioteki.

- Narzędzie ŚLEDZENIA ATL/MFC jest usuwane razem z biblioteką DLL ATL, a mechanizm śledzenia jest uproszczony. Konstruktor `CTraceCategory` przyjmuje teraz jeden parametr (nazwę kategorii), a makra TRACE wywołują funkcje raportowania debugowania CRT.

## <a name="visual-studio-2012-breaking-changes"></a>Przełomowe zmiany w programie Visual Studio 2012

### <a name="compiler"></a>Kompilator

- Zmieniono `/Yl` opcję kompilatora. Domyślnie kompilator używa tej opcji, co może prowadzić do błędów LNK2011 pod pewnymi warunkami. Aby uzyskać więcej informacji, zobacz [/Yl (Inject PCH Reference for Debug Library)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- W kodzie, który jest `/clr`kompilowany przy użyciu , **enum** class — słowo kluczowe definiuje wyliczenia C++11, a nie wyliczenia wspólnego środowiska wykonawczego języka (CLR). Aby zdefiniować wyliczenia CLR, należy jawić jego dostępność.

- Użyj słowa kluczowego szablonu, aby jawnie odróżnić nazwę zależną (zgodność ze standardem języka C++). W poniższym przykładzie wyróżnione słowo kluczowe szablonu jest obowiązkowe, aby rozwiązać niejednoznaczność. Aby uzyskać więcej informacji, zobacz [Rozpoznawanie nazw dla typów zależnych](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Stałe wyrażenie typu float nie jest już dozwolone jako argument szablonu, jak pokazano w poniższym przykładzie.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Kod, który jest kompilowany przy użyciu opcji `/GS` wiersza polecenia i który ma lukę w zabezpieczeniach typu "od jednego" może prowadzić do zakończenia procesu w czasie wykonywania, jak pokazano w poniższym przykładzie pseudokodu.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Domyślna architektura kompilacji x86 została zmieniona na SSE2; w związku z tym kompilator może emitować instrukcje SSE i użyje rejestrów XMM do wykonywania obliczeń zmiennoprzecinkowych. Jeśli chcesz przywrócić poprzednie zachowanie, użyj `/arch:IA32` flagi kompilatora, aby określić architekturę jako IA32.

- Kompilator może wydawać ostrzeżenia [Ostrzeżenie kompilatora (poziom 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) i C4701, gdzie wcześniej nie. Kompilator stosuje silniejsze kontrole użycia niezainicjowanych zmiennych lokalnych typu wskaźnika.

- Po określeniu `/HIGHENTROPYVA` nowej flagi konsolidatora system Windows 8 zazwyczaj powoduje, że alokacje pamięci zwracają adres 64-bitowy. (Przed windows 8 takie alokacje częściej zwracały adresy, które były mniejsze niż 2 GB). Ta zmiana może uwidaczniać błędy obcinania wskaźnika w istniejącym kodzie. Domyślnie ten przełącznik jest włączony. Aby wyłączyć to `/HIGHENTROPYVA:NO`zachowanie, należy określić .

- Kompilator zarządzany (Visual Basic/C#) obsługuje `/HIGHENTROPYVA` również kompilacje zarządzane.  Jednak w tym przypadku `/HIGHENTROPYVAswitch` jest domyślnie wyłączony.

### <a name="ide"></a>IDE

- Mimo że zaleca się, aby nie tworzyć aplikacji Windows Forms w języku C++/CLI, obsługa istniejących aplikacji interfejsu użytkownika języka C++/CLI jest obsługiwana. Jeśli musisz utworzyć aplikację Windows Forms lub dowolną inną aplikację interfejsu użytkownika platformy .NET, należy użyć języka C# lub Visual Basic. Należy używać języka C++/CLI wyłącznie do celów współdziałania.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Biblioteka wzorców równoległych i biblioteka wykonawcza współbieżności

Wyliczenie `SchedulerType` `UmsThreadDefault` jest przestarzałe. Specyfikacja `UmsThreadDefault` generuje przestarzałe ostrzeżenie i wewnętrznie mapuje z powrotem do . `ThreadScheduler`

### <a name="standard-library"></a>Standardowa biblioteka

- Po przełomowej zmiany między standardami C++ 98/03 i C++11, przy użyciu jawnych argumentów szablonu do wywołania `make_pair()` — jak w `make_pair<int, int>(x, y)` — zazwyczaj nie kompiluje się w programie Visual C++ w programie Visual Studio 2012. Rozwiązaniem jest zawsze `make_pair()` wywoływanie bez jawnych `make_pair(x, y)`argumentów szablonu — jak w . Dostarczanie jawnych argumentów szablonu pokonuje cel funkcji. Jeśli wymagana jest precyzyjna kontrola nad `pair` typem `make_pair` wynikowym, użyj zamiast — jak w `pair<short, short>(int1, int2)`.

- Kolejna przełomowa zmiana między standardami C++98/03 i C++11: Gdy A jest niejawnie konwertowana na B i B, jest niejawnie konwertowana na C, ale `pair<A, X>` A nie jest niejawnie konwertowana na C, C++98/03 i Visual Studio 2010 dozwolone do konwersji (w sposób dorozumiany lub jawny) na `pair<C, X>`. (Inny typ, X, nie jest tutaj interesujący i nie jest specyficzny dla pierwszego typu w parze). Kompilator Języka C++ w programie Visual Studio 2012 wykrywa, że A nie jest niejawnie konwertowany na C i usuwa konwersję pary z rozpoznawania przeciążenia. Ta zmiana jest pozytywna dla wielu scenariuszy. Na przykład `func(const pair<int, int>&)` przeciążenie `func(const pair<string, string>&)`i `func()` , `pair<const char *, const char *>` i wywołanie z będzie kompilować z tej zmiany. Jednak ta zmiana przerywa kod, który opierał się na konwersjach par agresywnych. Taki kod można zazwyczaj naprawić, wykonując jedną część konwersji jawnie `make_pair(static_cast<B>(a), x)` — na przykład `pair<C, X>`przechodząc do funkcji, która oczekuje .

- Visual Studio 2010 symulowane szablony variadic — na przykład `make_shared<T>(arg1, arg2, argN)`— do limitu 10 argumentów, przez wybijanie przeciążenia i specjalizacje z preprocesor maszyn. W programie Visual Studio 2012 ten limit jest zredukowany do pięciu argumentów, aby poprawić czas kompilacji i zużycie pamięci kompilatora dla większości użytkowników. Można jednak ustawić poprzedni limit, wyraźnie definiując _VARIADIC_MAX jako 10 w całym projekcie.

- C++11 17.6.4.3.1 [macro.names]/2 zabrania zastępowania słów kluczowych makr podczas uwzględniania nagłówków biblioteki standardowej języka C++. Nagłówki emitują teraz błędy kompilatora, jeśli wykryją słowa kluczowe zastąpione makrami. (Definiowanie _ALLOW_KEYWORD_MACROS umożliwia skompilowanie takiego kodu, ale zdecydowanie odradzamy to użycie). Jako `new` wyjątek forma makra jest domyślnie dozwolona, ponieważ nagłówki kompleksowo bronią się za pomocą programu `#pragma push_macro("new")` / `#undef new` / `#pragma pop_macro("new")`. Definiowanie _ENFORCE_BAN_OF_MACRO_NEW robi dokładnie to, co sugeruje jego nazwa.

- Aby zaimplementować różne optymalizacje i debugowanie kontroli, implementacja biblioteki standardowej języka C++ celowo przerywa zgodność binarną między wersjami programu Visual Studio (2005, 2008, 2010, 2012). Gdy biblioteka standardowa języka C++ jest używana, zabrania mieszania plików obiektów i bibliotek statycznych, które są kompilowane przy użyciu różnych wersji w jeden plik binarny (EXE lub DLL) i zabrania przekazywania obiektów biblioteki standardowej języka C++ między plikami binarnymi, które są kompilowane przy użyciu różnych wersji. Mieszanie plików obiektów i bibliotek statycznych (przy użyciu standardowej biblioteki C++, które zostały skompilowane przy użyciu programu Visual Studio 2010 z plikami, które zostały skompilowane przy użyciu kompilatora C++ w programie Visual Studio 2012 emituje błędy konsolidatora dotyczące niezgodności _MSC_VER, gdzie _MSC_VER jest makrem zawierającym główną wersję kompilatora (1700 dla programu Visual C++ w programie Visual Studio 2012). Ten czek nie może wykryć mieszania biblioteki DLL i nie można wykryć mieszania, które obejmuje program Visual Studio 2008 lub wcześniej.

- Oprócz wykrywania niezgodności _ITERATOR_DEBUG_LEVEL, który został zaimplementowany w programie Visual Studio 2010 kompilator C++ w programie Visual Studio 2012 wykrywa niezgodności biblioteki wykonawczej. Te niezgodności występują, gdy opcje `/MT` kompilatora `/MTd` (zwolnienie statyczne), (debugowanie statyczne), `/MD` (wersja dynamiczna) i `/MDd` (debugowanie dynamiczne) są mieszane.

- `operator<()`, `operator>()` `operator<=()`, `operator>=()` i były wcześniej `std::unordered_map` dostępne `stdext::hash_map` dla i rodzin kontenerów, chociaż ich implementacje nie były przydatne. Te niestandardowe operatory zostały usunięte w programie Visual C++ w programie Visual Studio 2012. Dodatkowo, realizacja `operator==()` i `operator!=()` dla `std::unordered_map` rodziny została rozszerzona `stdext::hash_map` na pokrycie rodziny. (Zaleca się unikanie używania `stdext::hash_map` rodziny w nowym kodzie).

- C++11 22.4.1.4 [locale.codecvt] `codecvt::length()` określa, że `codecvt::do_length()` `stateT&` i powinny przyjmować modyfikowalne `const stateT&`parametry, ale Visual Studio 2010 wziął . Kompilator C++ w programie Visual Studio `stateT&` 2012 przyjmuje zgodnie z wymaganiami standardu. Różnica ta jest istotna dla każdego, kto próbuje `do_length()`zastąpić funkcję wirtualną .

### <a name="crt"></a>CRT

- Sterta środowiska wykonawczego C (CRT), która jest używana dla nowych i malloc(), nie jest już prywatna. CRT teraz używa sterty procesu. Oznacza to, że sterty nie jest niszczony, gdy biblioteka DLL jest zwalniana, więc biblioteki DLL, które łączą się statycznie z CRT musi zapewnić pamięć, która jest przydzielana przez kod biblioteki DLL jest czyszczone przed jego rozładowania.

- Funkcja `iscsymf()` potwierdza z wartościami ujemnymi.

- Struktura `threadlocaleinfostruct` została zmieniona, aby uwzględnić zmiany w funkcjach ustawień regionalnych.

- Funkcje CRT, które mają odpowiednie `memxxx()`funkcje wewnętrzne, takie jak , `strxxx()` są usuwane z intrin.h. Jeśli intrin.h został dołączony tylko dla tych funkcji, należy teraz dołączyć odpowiednie nagłówki CRT.

### <a name="mfc-and-atl"></a>MFC i ATL

- Usunięto wsparcie Fusion (afxcomctl32.h); w związku z tym wszystkie \<metody zdefiniowane w afxcomctl32.h> zostały usunięte. Pliki \<nagłówkowe afxcomctl32.h> \<i afxcomctl32.inl> zostały usunięte.

- Zmieniono nazwę `CDockablePane::RemoveFromDefaultPaneDividier` `CDockablePane::RemoveFromDefaultPaneDivider`na .

- Zmieniono podpis `CFileDialog::SetDefExt` do używania LPCTSTR; w związku z tym Unicode kompilacje są zagrożone.

- Usunięto przestarzałe kategorie śledzenia ATL.

- Zmieniono podpis `CBasePane::MoveWindow` na `const CRect`.

- Zmieniono podpis `CMFCEditBrowseCtrl::EnableBrowseButton`.

- Usunięto właściwości `m_fntTabs` i `m_fntTabsBold` z klasy `CMFCBaseTabCtrl`.

- Dodano parametr do `CMFCRibbonStatusBarPane` konstruktorów. (Jest to parametr domyślny, a więc nie jest podział źródła.)

- Dodano parametr do `CMFCRibbonCommandsListBox` konstruktora. (Jest to parametr domyślny, a więc nie jest podział źródła.)

- Usunięto `AFXTrackMouse` interfejs API (i powiązany czasomierz proc). Zamiast tego użyj `TrackMouseEvent` interfejsu API systemu Win32.

- Dodano parametr do `CFolderPickerDialog` konstruktora. (Jest to parametr domyślny, a więc nie jest podział źródła.)

- `CFileStatus`zmieniono rozmiar `m_attribute` struktury: element członkowski został zmieniony z BYTE na `GetFileAttributes`DWORD (aby dopasować wartość zwróconą z ).

- `CRichEditCtrl`i `CRichEditView` użyj MSFTEDIT_CLASS (RichEdit 4.1 control) zamiast RICHEDIT_CLASS (Formant RichEdit 3.0) w kompilacjach Unicode.

- Usunięto, `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` ponieważ zawsze jest true w systemach Windows Vista, Windows 7 i Windows 8.

- Usunięto, `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` ponieważ zawsze jest true w systemach Windows Vista, Windows 7 i Windows 8.

- Usunięto `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Wywołaj interfejs API systemu Windows bezpośrednio w systemach Windows Vista, Windows 7 i Windows 8.

- Usunięto `AFX_GLOBAL_DATA::DwmDefWindowProc`. Wywołaj interfejs API systemu Windows bezpośrednio w systemach Windows Vista, Windows 7 i Windows 8.

- Zmieniono `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` `IsDwmCompositionEnabled` nazwę, aby wyeliminować kolizji nazw.

- Zmieniono identyfikatory dla wielu wewnętrznych czasomierzy MFC i przeniesiono definicje do afxres.h (AFX_TIMER_ID_*).

- Zmieniono podpis `OnExitSizeMove` metody, aby zgodzić się z ON_WM_EXITSIZEMOVE makra:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Zmieniono nazwę i `OnDWMCompositionChanged` podpis, aby zgodzić się z ON_WM_DWMCOMPOSITIONCHANGED makra:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

  - `CPaneFrameWnd`

- Zmieniono podpis `OnMouseLeave` metody, aby zgodzić się z ON_WM_MOUSELEAVE makra:

  - `CMFCCaptionBar`

  - `CMFCColorBar`

  - `CMFCHeaderCtrl`

  - `CMFCProperySheetListBox`

  - `CMFCRibbonBar`

  - `CMFCRibbonPanelMenuBar`

  - `CMFCRibbonRichEditCtrl`

  - `CMFCSpinButtonCtrl`

  - `CMFCToolBar`Zastąp Ten tekst

  - `CMFCToolBarComboBoxEdit`

  - `CMFCToolBarEditCtrl`

  - `CMFCAutoHideBar`

- Zmieniono `OnPowerBroadcast` podpis, aby zgodzić się z ON_WM_POWERBROADCAST makra:

  - `CFrameWndEx`

  - `CMDIFrameWndEx`

- Zmieniono `OnStyleChanged` podpis, aby zgodzić się z ON_WM_STYLECHANGED makra:

  - `CMFCListCtrl`

  - `CMFCStatusBar`

- Zmieniono nazwę `FontFamalyProcFonts` metody `FontFamilyProcFonts`wewnętrznej na .

- Usunięto `CString` wiele globalnych obiektów statycznych w celu wyeliminowania przecieków pamięci w niektórych sytuacjach (zastąpionych #defines) i następujących zmiennych elementów członkowskich klasy:

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

- Zmieniono podpis `CKeyboardManager::ShowAllAccelerators` i usunięto parametr ogranicznika akceleratora.

- Dodano `CPropertyPage::GetParentSheet`, a `CPropertyPage` w klasie, wywołać go zamiast uzyskać poprawne okno arkusza nadrzędnego, `GetParent` który `CPropertyPage`może być nadrzędnym lub dziadkiem okno do . Może być konieczna zmiana `GetParentSheet` kodu, `GetParent`aby zadzwonić zamiast .

- Naprawiono niezrównoważone ostrzeżenie #pragma (push) w ATLBASE. H, co spowodowało nieprawidłowe wyłączenie ostrzeżeń. Te ostrzeżenia są teraz poprawnie włączone po ATLBASE. H został przeanalizowany.

- Przeniesiono metody związane z D2D z AFX_GLOBAL_DATA do _AFX_D2D_STATE:

  - `GetDirectD2dFactory`

  - `GetWriteFactory`

  - `GetWICFactory`

  - `InitD2D`

  - `ReleaseD2DRefs`

  - `IsD2DInitialized`

  - `D2D1MakeRotateMatrix`

  - Zamiast dzwonić, na `afxGlobalData.IsD2DInitialized`przykład, `AfxGetD2DState->IsD2DInitialized`zadzwoń .

- Usunięto przestarzałe ATL*. pliki CPP z folderu \atlmfc\include\.

- Przeniesiono `afxGlobalData` inicjalizację na żądanie, a nie na `DLLMain` czas inicjowania CRT, aby spełnić wymagania.

- Dodano `RemoveButtonByIndex` metodę do `CMFCOutlookBarPane` klasy.

- Poprawiono `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` `IsFrequentlyUsedCmd`do .

- Poprawiono kilka `RestoreOriginalstate` wystąpień `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`do .

- Usunięto `CDockablePane`nieużywane `GetRecentSiblingPaneInfo`metody `CanAdjustLayout`z : `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, i .

- Usunięto `CDockablePane` `m_bCaptionText` statyczne zmienne członkowskie i `m_bHideDisabledButtons`.

- Dodano metodę zastępowania `DeleteString` `CMFCFontComboBox`do .

- Usunięto `CPane`nieużywane metody z : `GetMinLength` i `IsLastPaneOnLastRow`.

- Zmieniono `CPane::GetDockSiteRow(CDockingPanesRow *)` `CPane::SetDockSiteRow`nazwę na .

## <a name="visual-studio-2010-breaking-changes"></a>Przełomowe zmiany w programie Visual Studio 2010

### <a name="compiler"></a>Kompilator

- Słowo kluczowe **auto** ma nowe domyślne znaczenie. Ponieważ użycie starego znaczenia jest rzadkie, większość aplikacji nie będzie miała wpływu na tę zmianę.

- Wprowadzono nowe **static_assert** słowo kluczowe, które spowoduje konflikt nazw, jeśli w kodzie znajduje się już identyfikator o tej nazwie.

- Obsługa nowego notacji lambda wyklucza obsługę kodowania niecytowanego identyfikatora GUID w atrybucie Uuid IDL.

- .NET Framework 4 wprowadza pojęcie uszkodzonych wyjątków stanu, które są wyjątkami, które pozostawiają proces w nieodwracalnym stanie uszkodzonym. Domyślnie nie można złapać wyjątek stanu uszkodzony, nawet z /EHa kompilatora opcji, która połowy wszystkich innych wyjątków.                 Aby jawnie złapać wyjątek stanu uszkodzonego,\_należy użyć instrukcji __try- _except. Lub zastosuj atrybut [HandledProcessCorruptedStateExceptions], aby włączyć funkcję, aby wychwytywać wyjątki stanu uszkodzonych.  Ta zmiana dotyczy przede wszystkim programistów systemu, którzy mogą mieć do połowu wyjątek stanu uszkodzony. Osiem wyjątków to STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, STATUS_UNWIND_CONSOLIDATE.                 Aby uzyskać więcej informacji na temat tych wyjątków, zobacz [GetExceptionCode](/windows/win32/Debug/getexceptioncode) makra.

- Poprawiona `/GS` opcja kompilatora chroni przed przepełnienia buforu bardziej kompleksowo niż we wcześniejszych wersjach. Ta wersja może wstawić dodatkowe kontrole zabezpieczeń w stosie, które mogą zmniejszyć wydajność. Użyj nowego `__declspec(safebuffers)` słowa kluczowego, aby poinstruować kompilatora, aby nie wstawić kontroli zabezpieczeń dla określonej funkcji.

- Jeśli kompilujesz z `/GL` opcjami kompilatora (Optymalizacja całego programu) `/clr` i `/GL` (Kompilacja środowiska wykonawczego języka wspólnego), opcja ta jest ignorowana. Ta zmiana została wniesiena, ponieważ połączenie opcji kompilatora pod warunkiem niewielkie korzyści. W wyniku tej zmiany wydajność kompilacji jest lepsza.

- Domyślnie obsługa trygrafów jest wyłączona w programie Visual Studio 2010. Użyj `/Zc:trigraphs` opcji kompilatora, aby włączyć obsługę trygrafów. Trygraf składa się z dwóch kolejnych znaków zapytania ("??"), po których następuje unikalny trzeci znak. Kompilator zastępuje trygraf odpowiednim znakiem interpunkcyjnym. Na przykład kompilator zastępuje `??=` trygraf znakiem "#". Użyj trygrafów w plikach źródłowych języka C, które używają zestawu znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych.

- Konsolidator nie obsługuje już optymalizacji dla systemu Windows 98. Opcja `/OPT` (Optymalizacje) generuje błąd czasu kompilacji, `/OPT:WIN98` `/OPT:NOWIN98`jeśli określisz lub .

- Domyślne opcje kompilatora, które są określone przez RuntimeLibrary i DebugInformationFormat właściwości systemu kompilacji zostały zmienione. Domyślnie te właściwości kompilacji są określone w projektach, które są tworzone przez visual c++ zwalnia od 7.0 do 10.0. W przypadku migracji projektu, który został utworzony przez visual C++ 6.0, należy rozważyć, czy określić wartość dla tych właściwości.

- W programie Visual Studio 2010, RuntimeLibrary`/MD`= MultiThreaded ( ) i DebugInformationFormat = ProgramDatabase (`/Zi`). W programie Visual C++ 9.0, RuntimeLibrary`/MT`= MultiThreaded ( ) i DebugInformationFormat = Wyłączone.

### <a name="clr"></a>CLR

- Kompilatory Microsoft C# i Visual Basic mogą teraz tworzyć nie podstawowy zestaw interop (no-PIA). Zestaw no-PIA może używać typów COM bez wdrażania odpowiedniego podstawowego zestawu międzyoperacyjnego (PIA). Podczas korzystania z zestawów no-PIA produkowanych przez visual C# lub Visual Basic, należy odwołać się do zestawu PIA w komendzie polecenia przed odwołaniem się do dowolnego zestawu no-PIA, który używa biblioteki.

### <a name="visual-studio-c-projects-and-msbuild"></a>Projekty programu Visual Studio C++ i MSBuild

- Projekty programu Visual Studio C++ są teraz oparte na narzędziu MSBuild. W związku z tym pliki projektu używają nowego formatu pliku XML i sufiksu pliku .vcxproj. Program Visual Studio 2010 automatycznie konwertuje pliki projektu z wcześniejszych wersji programu Visual Studio na nowy format pliku. Istniejący projekt ma wpływ, jeśli zależy od poprzedniego narzędzia kompilacji, VCBUILD.exe lub sufiks pliku projektu, .vcproj.

- We wcześniejszych wersjach visual C++ obsługiwane późnej oceny arkuszy właściwości. Na przykład arkusz właściwości nadrzędnej może zaimportować arkusz właściwości podrzędnych, a element nadrzędny może użyć zmiennej zdefiniowanej w podrzędnym do definiowania innych zmiennych. Późna ocena umożliwiła elementowi nadrzędnemu użycie zmiennej podrzędnej jeszcze przed zaimportowanym arkuszem właściwości podrzędnych. W programie Visual Studio 2010 nie można użyć zmiennej arkusza projektu przed jej zdefiniowaniem, ponieważ MSBuild obsługuje tylko wczesną ocenę.

### <a name="ide"></a>IDE

- Okno dialogowe zakończenia aplikacji nie kończy już aplikacji. W poprzednich wersjach, gdy `abort()` lub `terminate()` funkcja zamknęła kompilację sieci sprzedaży aplikacji, biblioteka czasu wykonywania C wyświetlała komunikat o zakończeniu aplikacji w oknie konsoli lub w oknie dialogowym. Komunikat powiedział w części"Ta aplikacja zażądała środowiska wykonawczego, aby zakończyć go w nietypowy sposób. Aby uzyskać więcej informacji, skontaktuj się z zespołem pomocy technicznej aplikacji." Komunikat zakończenia aplikacji był zbędny, ponieważ system Windows następnie wyświetlał bieżący program obsługi zakończenia, który był zwykle w oknie dialogowym Raportowanie błędów systemu Windows (Dr Watson) lub debugerem programu Visual Studio. Począwszy od programu Visual Studio 2010, biblioteka czasu wykonywania języka C nie wyświetla komunikatu. Ponadto środowisko wykonawcze uniemożliwia zakończenie aplikacji przed uruchomieniem debugera. Jest to zmiana podziału tylko wtedy, gdy zależy od poprzedniego zachowania komunikatu zakończenia aplikacji.

- W szczególności dla programu Visual Studio 2010 IntelliSense nie działa dla kodu C++/CLI lub atrybutów **Znajdź wszystkie odwołania** nie działa dla zmiennych lokalnych, a model kodu nie pobiera nazw typów z importowanych zestawów ani nie rozpoznaje typów do ich w pełni kwalifikowanych nazw.

### <a name="libraries"></a>Biblioteki

- SafeInt Klasa jest uwzględniony w języku Visual C++ i nie jest już w osobnym download. Jest to przełomowa zmiana tylko wtedy, gdy masz rozwiniętą klasę o nazwie "SafeInt".

- Model wdrażania bibliotek nie używa już manifestów do znajdowania określonej wersji biblioteki łączy dynamicznych. Zamiast tego nazwa każdej biblioteki łączy dynamicznych zawiera jego numer wersji i używasz tej nazwy, aby zlokalizować bibliotekę.

- W poprzednich wersjach programu Visual Studio można było odbudować biblioteki czasu wykonywania. Visual Studio 2010 nie obsługuje już tworzenia własnych kopii plików biblioteki czasu wykonywania języka C.

### <a name="standard-library"></a>Standardowa biblioteka

- Nagłówek \<> iteratora nie jest już automatycznie uwzględniany przez wiele innych plików nagłówkowych. Zamiast tego należy uwzględnić ten nagłówek jawnie, jeśli wymagana jest obsługa autonomicznych iteratorów zdefiniowanych w nagłówku. Dotyczy to istniejącego projektu, jeśli zależy ono od poprzedniego narzędzia kompilacji, VCBUILD.exe lub sufiksu pliku projektu, .vcproj.iterator.

- W \<nagłówku> algorytmu\* są usuwane funkcje checked_* i unchecked_. I w \<nagłówku>> iteratora `checked_iterator` klasa jest `unchecked_array_iterator` usuwana, a klasa została dodana.

- `CComPtr::CComPtr(int)` Konstruktor zostanie usunięty. Ten konstruktor `CComPtr` zezwolił na konstruowanie obiektu z makra NULL, ale był niepotrzebny i zezwalał na bezsensowne konstrukcje z liczb całkowitych niezerowych.

   A `CComPtr` nadal mogą być konstruowane z NULL, który jest zdefiniowany jako 0, ale zakończy się niepowodzeniem, jeśli skonstruowane z liczby całkowitej innej niż literału 0. Zamiast tego użyj **nullptr.**

- Usunięto `ctype` następujące `ctype::_Do_narrow_s` `ctype::_Do_widen_s`funkcje członkowskie: , , `ctype::_narrow_s`, `ctype::_widen_s`. Jeśli aplikacja korzysta z jednej z tych funkcji członkowskich, należy ją `ctype::do_narrow`zastąpić `ctype::do_widen` `ctype::narrow`odpowiednią `ctype::widen`wersją niezabezpieczoną: , , , .

### <a name="crt-mfc-and-atl-libraries"></a>Biblioteki CRT, MFC i ATL

- Obsługa została usunięta dla użytkowników do tworzenia bibliotek CRT, MFC i ATL. Na przykład nie podano odpowiedniego pliku NMAKE. Jednak użytkownicy nadal mają dostęp do kodu źródłowego dla tych bibliotek. I dokument, który opisuje opcje MSBuild, które firma Microsoft używa do tworzenia tych bibliotek prawdopodobnie zostaną opublikowane w visual C++ Team Blog.

- Obsługa MFC dla IA64 została usunięta. Jednak obsługa CRT i ATL na IA64 jest nadal dostępna.

- Liczba porządkowa nie jest już ponownie używana w plikach mfc z definicją modułu (def). Ta zmiana oznacza, że liczby porządkowe nie będą się różnić między wersjami pomocniczymi, a zgodność binarna dodatków Service Pack i szybkie poprawki wersje inżynieryjne zostaną ulepszone.

- Nowa funkcja wirtualna została `CDocTemplate` dodana do klasy. Ta nowa funkcja wirtualna to [klasa CDocTemplate](../mfc/reference/cdoctemplate-class.md). Poprzednia wersja `OpenDocumentFile` miała dwa parametry. Nowa wersja ma trzy parametry. Aby obsługiwać menedżera ponownego uruchamiania, każda klasa pochodząca z `CDocTemplate` musi zaimplementować wersję, która ma trzy parametry. Nowym parametrem `bAddToMRU`jest .

### <a name="macros-and-environment-variables"></a>Makra i zmienne środowiskowe

- Zmienna środowiskowa __MSVCRT_HEAP_SELECT nie jest już obsługiwana. Ta zmienna środowiskowa jest usuwana i nie ma zamiennika.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

- Kilka dyrektyw zostały usunięte z kompilatora odwołania akcesora makr firmy Microsoft. Usunięte dyrektywy to `.186` `.286`, `.286P` `.287`, `.8086` `.8087`, `.NO87`, , i .

## <a name="visual-studio-2008-breaking-changes"></a>Przełomowe zmiany w programie Visual Studio 2008

### <a name="compiler"></a>Kompilator

- Platformy Windows 95, Windows 98, Windows ME i Windows NT nie są już obsługiwane. Te systemy operacyjne zostały usunięte z listy platform docelowych.

- Kompilator nie obsługuje już wielu atrybutów, które były bezpośrednio skojarzone z serwerem ATL. Następujące atrybuty nie są już obsługiwane:

  - perf_counter

  - perf_object

  - Perfmon

  - request_handler

  - soap_handler

  - soap_header

  - soap_method

  - tag_name

### <a name="visual-studio-c-projects"></a>Projekty programu Visual Studio W++

- Podczas uaktualniania projektów z poprzednich wersji programu Visual Studio może być konieczne zmodyfikowanie makr WINVER i _WIN32_WINNT, tak aby były większe lub równe 0x0500.

- Począwszy od programu Visual Studio 2008, nowy kreator projektu nie ma opcji, aby utworzyć projekt programu SQL Server języka C++. Projekty programu SQL Server utworzone przy użyciu wcześniejszej wersji programu Visual Studio będą nadal kompilować i działać poprawnie.

- Plik nagłówka interfejsu API systemu Windows Winable.h został usunięty. Dołącz Winuser.h zamiast.

- Biblioteka interfejsu API systemu Windows Rpcndr.lib została usunięta. Zamiast tego łącz się z rpcrt4.lib.

### <a name="crt"></a>CRT

- Usunięto obsługę systemów Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4.0.

- Usunięto następujące zmienne globalne:

  - _osplatform

  - _osver

  - _winmajor

  - _winminor

  - _winver

- Następujące funkcje zostały usunięte. Użyj funkcji `GetVersion` interfejsu `GetVersionEx` API systemu Windows lub zamiast tego:

  - _get_osplatform

  - _get_osver

  - _get_winmajor

  - _get_winminor

  - _get_winver

- Składnia adnotacji SAL została zmieniona. Aby uzyskać więcej informacji, zobacz [Annotacje SAL](../c-runtime-library/sal-annotations.md).

- Filtr IEEE obsługuje teraz zestaw instrukcji SSE 4.1. Aby uzyskać więcej informacji, zobacz [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Biblioteki w czasie wykonywania języka C dostarczane z programem Visual Studio nie są już zależne od pliku MSVCRT.dll systemu DLL.

### <a name="standard-library"></a>Standardowa biblioteka

- Usunięto obsługę systemów Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4.0.

- Podczas kompilowania w trybie debugowania z _HAS_ITERATOR_DEBUGGING zdefiniowane (zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010), aplikacja będzie teraz potwierdzać, gdy iterator próbuje przyrost lub dekrementacji poza granice kontenera źródłowego.

- Zmienna elementu członkowskiego c klasy stosu jest teraz zadeklarowana jako chroniona. Wcześniej ta zmienna elementu członkowskiego została ogłoszona publiczna.

- Zachowanie uległo `money_get::do_get` zmianie. Wcześniej, podczas analizowania kwoty pieniężnej z większą ilością cyfr `frac_digits` `do_get` ułamkowych, niż jest to wymagane przez , używane do spożywania ich wszystkich. Teraz `do_get` przestaje parsować po `frac_digits` spożyciu co najwyżej znaków.

### <a name="atl"></a>ATL

- Atl nie można zbudować bez zależności od CRT. We wcześniejszych wersjach programu Visual Studio można użyć #define ATL_MIN_CRT, aby projekt ATL minimalnie zależne od CRT. W programie Visual Studio 2008 wszystkie projekty ATL są minimalnie zależne od CRT, niezależnie od tego, czy ATL_MIN_CRT jest zdefiniowany.

- Baza kodu serwera ATL została wydana jako udostępniony projekt źródłowy w usłudze CodePlex i nie jest zainstalowana jako część programu Visual Studio. Klasy kodowania i dekodowania danych z atlenc.h oraz funkcje i klasy narzędziowe z atlutil.h i atlpath.h zostały zachowane i są obecnie częścią biblioteki ATL. Kilka plików skojarzonych z usługą ATL Server nie jest już częścią programu Visual Studio.

- Niektóre funkcje nie są już zawarte w dll. Nadal znajdują się one w bibliotece importu. Nie wpłynie to na kod, który używa funkcji statycznie. Wpłynie to tylko na kod, który korzysta z tych funkcji dynamicznie.

- Makra PROP_ENTRY i PROP_ENTRY_EX zostały przestarzałe i zastąpione makrami PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX ze względów bezpieczeństwa.

### <a name="atlmfc-shared-classes"></a>Klasy współdzielone ATL/MFC

- Atl nie można zbudować bez zależności od CRT. We wcześniejszych wersjach programu Visual `#define ATL_MIN_CRT` Studio można użyć do projektu ATL minimalnie zależne od CRT. W programie Visual Studio 2008 wszystkie projekty ATL są minimalnie zależne od CRT, niezależnie od tego, czy ATL_MIN_CRT jest zdefiniowany.

- Baza kodu serwera ATL została wydana jako udostępniony projekt źródłowy w usłudze CodePlex i nie jest zainstalowana jako część programu Visual Studio. Klasy kodowania i dekodowania danych z atlenc.h oraz funkcje i klasy narzędziowe z atlutil.h i atlpath.h zostały zachowane i są obecnie częścią biblioteki ATL. Kilka plików skojarzonych z usługą ATL Server nie jest już częścią programu Visual Studio.

- Niektóre funkcje nie są już zawarte w dll. Nadal znajdują się one w bibliotece importu. Nie wpłynie to na kod, który używa funkcji statycznie. Wpłynie to tylko na kod, który korzysta z tych funkcji dynamicznie.

### <a name="mfc"></a>MFC

- `CTime`Klasa: `CTime` Klasa akceptuje teraz daty zaczynające się od 1/1/1900 C.E. zamiast 1/1/1970 C.E.

- Kolejność kontrolek tabulatorów w oknach dialogowych MFC: Prawidłowa kolejność tabulatorów wielu formantów w oknie dialogowym MFC jest zaburzona, jeśli kontrolka MFC ActiveX zostanie wstawiona w kolejności tabulacji. Ta zmiana poprawia ten problem.

   Na przykład utwórz aplikację okna dialogowego MFC, która ma formant ActiveX i kilka formantów edycji. Umieść kontrolkę ActiveX na środku kolejności tabulacji formantów edycji. Uruchom aplikację, kliknij formant edycji, którego kolejność tabulacji jest po formancie ActiveX, a następnie kartę.

- `CFileDialog`Klasa: Szablony niestandardowe `CFileDialog` dla klasy nie mogą być automatycznie przenoszone do systemu Windows Vista. Są one nadal użyteczne, ale nie będą miały dodatkowych funkcji lub wyglądu okien dialogowych stylu systemu Windows Vista.

- `CWnd`Klasa `CFrameWnd` i klasa: Metoda `CWnd::GetMenuBarInfo` została usunięta.

   Metoda `CFrameWnd::GetMenuBarInfo` jest teraz metodą niewirtua, która jest metodą niewirtua. Aby uzyskać więcej informacji, zobacz **Funkcja GetMenuBarInfo** w programie Windows SDK.

- Obsługa interfejsu ISAPI MFC: MFC nie obsługuje już tworzenia aplikacji za pomocą interfejsu ISAPI (Internet Server Application Programming Interface). Jeśli chcesz utworzyć aplikację ISAPI, należy wywołać rozszerzenia ISAPI bezpośrednio.

- Przestarzałe interfejsy API ANSI: wersje ANSI kilku metod MFC są przestarzałe. Użyj wersji Unicode tych metod w przyszłych aplikacjach. Aby uzyskać więcej informacji, zobacz **Wymagania dotyczące kompilacji dla wspólnych formantów systemu Windows Vista**.

## <a name="visual-studio-2005-breaking-changes"></a>Przełomowe zmiany w programie Visual Studio 2005

### <a name="crt"></a>CRT

- Wiele funkcji zostało przestarzałych. Zobacz **przestarzałe funkcje CRT**.

- Wiele funkcji sprawdza teraz ich parametry, zatrzymując wykonanie, jeśli podane nieprawidłowe parametry. To sprawdzanie poprawności może przerwać kod, który przekazuje nieprawidłowe parametry i opiera się na funkcji ignorując je lub po prostu zwraca kod błędu. Zobacz **Sprawdzanie poprawności parametrów**.

- Wartość deskryptora pliku -2 jest `stdout` teraz `stderr` używana do wskazania, że i nie są dostępne dla danych wyjściowych, na przykład w aplikacji systemu Windows, która nie ma okna konsoli. Poprzednia użyta wartość to -1. Aby uzyskać więcej informacji, zobacz [_fileno](../c-runtime-library/reference/fileno.md).

- Jednowątkowa biblioteka CRT (libc.lib i libcd.lib) zostały usunięte. Użyj bibliotek CRT wielowątkowych. Flaga `/ML` kompilatora nie jest już obsługiwana. Nieblokujące wersje niektórych funkcji zostały dodane w przypadkach, gdy różnica w wydajności między kodem wielowątkowym a kodem jednowątkowym jest potencjalnie znacząca.

- Przeciążenie pow, podwójne pow (int, int), został usunięty, aby lepiej zgodne ze standardem.

- Specyfikator formatu %n nie jest już domyślnie obsługiwany w żadnej z rodziny funkcji printf, ponieważ jest z natury niezabezpieczona. Jeśli wystąpi %n, domyślnym zachowaniem jest wywołanie nieprawidłowego programu obsługi parametrów. Aby włączyć obsługę %n, użyj (zobacz `_set_printf_count_output` również `_get_printf_count_output`).

- `sprintf`teraz drukuje ujemny znak podpisanego zera.

- `swprintf`został zmieniony w celu dostosowania go do normy; teraz wymaga parametru rozmiaru. Forma parametru `swprintf` bez rozmiaru została przestarzała.

- `_set_security_error_handler`został usunięty. Usuń wszelkie wywołania tej funkcji; domyślny program obsługi jest znacznie bezpieczniejszym sposobem radzenia sobie z błędami zabezpieczeń.

- `time_t`jest teraz wartością 64-bitową (chyba że zdefiniowano _USE_32BIT_TIME_T).

- Funkcje `_spawn`teraz `errno` pozostawić nietknięte na sukces, zgodnie z określonymi przez standard C. `_wspawn`

- RTC używa teraz domyślnie szerokich znaków.

- Funkcje obsługi słów sterowania zmiennoprzecinowego zostały `/CLR` przestarzałe dla aplikacji skompilowanych z programem . `/CLR:PURE` Dostępne funkcje `_clear87`to `_clearfp` `_control87`, `_controlfp` `_fpreset`, `_status87` `_statusfp`, , , , . Ostrzeżenie o deprekacji można wyłączyć, definiując _CRT_MANAGED_FP_NO_DEPRECATE, ale użycie tych funkcji w kodzie zarządzanym jest nieprzewidywalne i nieobsługiwało się.

- Niektóre funkcje zwracają teraz wskaźniki const. Stare, non-const zachowanie można przywrócić przez zdefiniowanie _CONST_RETURN. Zagrożone funkcje są

  - memchr, wmemchr

  - strchr, wcschr, _mbschr, _mbschr_l

  - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

  - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

  - strstr, wcsstr, _mbsstr, _mbsstr_l

- Podczas łączenia z plikami Setargv.obj lub Wsetargv.obj nie można już pominąć rozwinięcie symbolu wieloznacznego w wierszu polecenia, otaczając go w cudzysłowie. Aby uzyskać więcej informacji, zobacz [Rozwijanie argumentów symboli wieloznacznych](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Biblioteka standardowa (2005)

- Klasa wyjątku (znajdująca się w nagłówku wyjątku \< `std`>) została przeniesiona do obszaru nazw. W poprzednich wersjach ta klasa była w globalnej przestrzeni nazw. Aby rozwiązać wszelkie błędy wskazujące, że nie można odnaleźć klasy wyjątku, dodaj do kodu następującą instrukcję using:`using namespace std;`

- Podczas `valarray::resize()`wywoływania zawartość `valarray` zostanie utracona i zostanie zastąpiona wartościami domyślnymi. Metoda `resize()` ma na celu ponowne `valarray` zainicjowanie, a nie rozwijanie go dynamicznie jak wektor.

- Iteratory debugowania: Aplikacje utworzone za pomocą wersji debugowania biblioteki środowiska wykonawczego C i niepoprawnie korzystające z iteratorów mogą zacząć widzieć potwierdzenia w czasie wykonywania. Aby wyłączyć te potwierdzenia, należy zdefiniować _HAS_ITERATOR_DEBUGGING (zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po visual studio 2010) do 0. Aby uzyskać więcej informacji, zobacz [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Zmiany w programie Visual C++ .NET 2003

### <a name="compiler"></a>Kompilator

- Nawiasy zamykające są teraz wymagane dla zdefiniowanej dyrektywy preprocesora (C2004).

- Jawne specjalizacje nie znajdują już parametrów szablonu z szablonu podstawowego ([Błąd kompilatora C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Chroniony element członkowski (n) jest dostępny tylko za pośrednictwem funkcji elementu członkowskiego klasy (B), która dziedziczy z klasy (A), której (n) jest członkiem ([Błąd kompilatora C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Ulepszone kontrole dostępności w kompilatorze wykrywają teraz niedostępne klasy podstawowe[(Błąd kompilatora C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Nie można złapać wyjątku, jeśli destruktor i/lub konstruktor kopii jest niedostępny (C2316).

- Domyślne argumenty na wskaźnikach do funkcji nie są już dozwolone ([Błąd kompilatora C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Nie można zainicjować elementu członkowskiego danych statycznych za pomocą klasy pochodnej ([Błąd kompilatora C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- Inicjowanie **typedef** nie jest dozwolone przez standard, a teraz generuje błąd kompilatora ([Błąd kompilatora C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- **bool** jest teraz właściwym typem[(Błąd kompilatora C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- UDC może teraz tworzyć niejednoznaczność z przeciążonymi operatorami ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Więcej wyrażeń jest teraz uznawanych za prawidłowe stałe wskaźnika zerowego[(Błąd kompilatora C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- szablon<> jest teraz wymagany w miejscach, w których kompilator wcześniej sugerowałby[(Błąd kompilatora C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Jawna specjalizacja funkcji elementu członkowskiego poza klasą nie jest prawidłowa, jeśli funkcja została już jawnie wyspecjalizowana za pośrednictwem specjalizacji klasy szablonu ([Błąd kompilatora C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Parametry szablonu nienapłytowego zmiennoprzecinkowe nie są już dozwolone[(Błąd kompilatora C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Szablony klas nie są dozwolone jako argumenty typu szablonu (C3206).

- Nazwy funkcji znajomego nie są już wprowadzane do zawierającego obszaru nazw[(Błąd kompilatora C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Kompilator nie będzie już akceptował dodatkowych przecinków w makrze (C4002).

- Obiekt typu POD skonstruowany za pomocą inicjatora formularza () zostanie zainicjowany domyślnie (C4345).

- nazwa typu jest teraz wymagana, jeśli nazwa zależna ma być traktowana jako typ ([Ostrzeżenie kompilatora (poziom 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funkcje, które zostały niepoprawnie uznane za specjalizacje szablonów nie są już tak traktowane (C4347).

- Nie można zainicjować elementów członkowskich danych statycznych za pośrednictwem klasy pochodnej (C4356).

- Specjalizacja szablonu klasy musi zostać zdefiniowana, zanim zostanie użyta w typie zwracanym ([Ostrzeżenie kompilatora (poziom 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Kompilator zgłasza teraz nieosiągalny kod (C4702).

## <a name="see-also"></a>Zobacz też

[Co nowego w programie Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
