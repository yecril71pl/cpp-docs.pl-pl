---
title: Visual C++ — Historia latach 2003 – 2015 zmian
ms.date: 08/30/2017
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: a0a13748894880c076f8d32c9c74afde1752504c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448972"
---
# <a name="visual-c-change-history-2003---2015"></a>Visual C++ — Historia latach 2003 – 2015 zmian

W tym artykule opisano wszystkie przełomowe zmiany z programu Visual Studio 2015 po powrocie do programu Visual Studio 2003, a w tym artykule terminy "nowe zachowanie" lub "teraz" odnoszą się do programu Visual Studio 2015 i nowszych. Terminy "stare zachowanie" i "before" odnoszą się do programu Visual Studio 2013 i jego starszych wersji.

Aby uzyskać informacje o najnowszej wersji programu Visual Studio, zobacz [co nowego w języku Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodności w programie Visual C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

> [!NOTE]
> Nie ma żadnych danych binarnych przełomowych zmian między wersjami programu Visual Studio 2015 i Visual Studio 2017.

Po uaktualnieniu do nowej wersji programu Visual Studio, może wystąpić, kompilacji i/lub błędy czasu wykonywania w kodzie, który wcześniej kompilował się i uruchamiał poprawnie. Zmiany w nowej wersji, które powodują takie problemy, są znane jako *istotne zmiany w*, i zazwyczaj są one wymagane przez zmiany w standardzie języka C++, sygnaturach funkcji lub układzie obiektów w pamięci.

Aby uniknąć błędów czasu wykonywania, które są trudne do wykrycia i zdiagnozowania, zalecamy nigdy nie będą statycznie łączyć plików binarnych skompilowanych przy użyciu różnych wersji kompilatora. Ponadto, gdy uaktualniasz projekt EXE lub DLL, upewnij się, że uaktualniasz również biblioteki, z którymi się on łączy. Nie przekazuj CRT (środowisko uruchomieniowe C) lub typów biblioteki standardowej języka C++ (standardowa biblioteka C++) między plikami binarnymi, łącznie z biblioteki dll, które są kompilowane przy użyciu innych wersji kompilatora. Aby uzyskać więcej informacji, zobacz [potencjalne błędy przekazywania CRT obiektów w pliku DLL granicach](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).

Nigdy nie należy napisać kod, który zależy od określonego układu dla obiektu, który nie jest interfejsem COM lub obiektem POD. Jeśli jednak piszesz taki kod, upewnij się, że działa po uaktualnieniu. Aby uzyskać więcej informacji, zobacz [przenośność na granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).

Ponadto najnowsze ulepszenia do zgodności kompilatora czasem zmienić jak kompilator rozpoznaje istniejącego kodu źródłowego. Na przykład może się okazać nowe lub inne błędy podczas kompilacji lub różnice w zachowaniu nawet w kodzie, który wcześniej utworzone i sprawiał by działała poprawnie. Mimo że te ulepszenia nie są istotne zmiany, takie jak te omówionych w tym dokumencie, może być konieczne do wprowadzania zmian w kodzie źródłowym, aby rozwiązać te problemy:

- [Istotne zmiany w Biblioteka środowiska uruchomieniowego (CRT)](#BK_CRT)

- [Standard C++ i standardowej bibliotece C++ fundamentalne zmiany](#BK_STL)

- [MFC i ATL fundamentalne zmiany](#BK_MFC)

- [Zmiany powodujące niezgodność środowiska uruchomieniowego współbieżności](#BK_ConcRT)

## <a name="VC_2015"></a> Visual Studio 2015 Conformance Changes

###  <a name="BK_CRT"></a> Biblioteka środowiska uruchomieniowego języka C (CRT)

#### <a name="general-changes"></a>Ogólne zmiany

- **Wycofanej plików binarnych**

   Biblioteka CRT ma zostały zaprojektowane od nowa w dwóch różnych plików binarnych: Universal CRT (ucrtbase), który zawiera większość standardowych funkcji i Biblioteka środowiska uruchomieniowego VC (vcruntime). Biblioteka vcruntime zawiera funkcje związane z kompilatora, takie jak obsługa wyjątków i funkcje wewnętrzne. Jeśli używane są domyślne ustawienia projektu, następnie ta zmiana nie ma wpływu na możesz ponieważ konsolidator będzie automatycznie używać nowej biblioteki domyślne. Jeśli ustawiono projektu **konsolidatora** właściwość **Ignoruj wszystkie domyślne biblioteki** do **tak** lub używasz `/NODEFAULTLIB` w wierszu polecenia, następnie — opcja konsolidatora należy zaktualizować listę bibliotek (w **dodatkowe zależności** właściwość) do uwzględnienia nowej, wycofanej bibliotek. Zastąp stare biblioteki CRT (libcmt.lib libcmtd.lib, msvcrt.lib, biblioteki msvcrtd.lib) równoważne wycofanej bibliotek. Dla każdego z dwóch bibliotek wycofanej istnieją statyczna (.lib) i wersji dynamicznie (dll) i wersji (nie sufiksem) i wersji debugowania (z sufiksem "d"). Dynamiczne wersje mają biblioteki importowanej, która łączy z. Dwie biblioteki wycofanej są Universal CRT specjalnie ucrtbase.dll lub ucrtbase.lib, bibliotekę ucrtbased.dll lub ucrtbased.lib, a biblioteka środowiska uruchomieniowego VC, libvcruntime.lib, vcruntime*wersji*.dll, libvcruntimed.lib, i vcruntimed*wersji*.dll. *Wersji* zarówno w programie Visual Studio 2015 i Visual Studio 2017 jest 140. Zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

#### <a name="localeh"></a>\<locale.h>

- **localeconv**

   [Localeconv](../c-runtime-library/reference/localeconv.md) funkcja zadeklarowana w locale.h działa teraz poprawnie po [ustawień regionalnych na wątek](../parallel/multithreading-and-locales.md) jest włączona. W poprzednich wersjach biblioteki, ta funkcja zwróci `lconv` dane globalne ustawienia regionalne nie ustawienia regionalne dla wątku.

   Korzystając z ustawień regionalnych na wątek, należy sprawdzić użytkowania `localeconv`. Jeśli w kodzie założono, że `lconv` danych zwracanych dla globalnych ustawień regionalnych, należy go rozwiązać.

#### <a name="mathh"></a>\<math.h>

- **Przeciążenia funkcji bibliotek matematycznych w języku C++**

   W poprzednich wersjach \<math.h > zdefiniowane niektóre, ale nie wszystkie z przeciążeń C++ dla funkcji bibliotek matematycznych. Pozostała część przeciążenia znajdowały się w \<cmath > nagłówka. Kod, który tylko \<math.h > może mieć problemy z Rozpoznanie przeciążenia funkcji. Teraz przeciążeń C++ zostały usunięte z \<math.h > i są dostępne tylko w \<cmath >.

   Aby naprawić błędy, należy dołączyć \<cmath > Aby uzyskać deklaracji funkcji, które zostały usunięte z \<math.h >. Te funkcje zostały przeniesione:

  - `double abs(double)` i `float abs(float)`

  - `double pow(double, int)`, `float pow(float, float)`, `float pow(float, int)`, `long double pow(long double, long double)`, `long double pow(long double, int)`

  - `float` i `long double` wersje pływających punktu funkcje `acos`, `acosh`, `asin`, `asinh`, `atan`, `atanh`, `atan2`, `cbrt`, `ceil`, `copysign`, `cos`, `cosh`, `erf`, `erfc`, `exp`, `exp2`, `expm1`, `fabs`, `fdim`, `floor`, `fma`, `fmax`, `fmin` , `fmod`, `frexp`, `hypot`, `ilogb`, `ldexp`, `lgamma`, `llrint`, `llround`, `log`, `log10`, `log1p`, `log2`, `lrint`, `lround`, `modf`, `nearbyint`, `nextafter`, `nexttoward`, `remainder`, `remquo`, `rint`, `round`, `scalbln`, `scalbn`, `sin`, `sinh`, `sqrt`, `tan`, `tanh`, `tgamma`, i `trunc`

  Jeśli masz kod, który używa `abs` ze swobodnym typu, który zawiera tylko punktu \<math.h > nagłówka, zmiennoprzecinkowej wersji nie będzie już dostępna. Wywołanie teraz jest rozpoznawana jako `abs(int)`, nawet przy użyciu zmiennoprzecinkowy punktu argumentu, który generuje błąd:

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  Poprawkę dotyczącą tego ostrzeżenia jest Zastąp wywołanie `abs` ze swobodnym wersję punktu `abs`, takich jak `fabs` argumentu double lub `fabsf` dla argumentu typu float, lub Uwzględnij \<cmath > nagłówka i w dalszym ciągu używać `abs`.

- **Ruchomy punkt zgodności**

   Wprowadzono wiele zmian do biblioteki matematyczne zwiększyć zgodność IEEE 754 i specyfikacje C11 załączniku F względem specjalnych przypadków dane wejściowe takich jak NaNs i nieskończoności. Na przykład cichy NaN danych wejściowych, które często były traktowane jako błędy w poprzednich wersjach biblioteki, nie są traktowane jako błędy. Zobacz [IEEE 754 standardowa](https://standards.ieee.org/standard/754-2008.html) i załącznika F [C11 Standard](http://www.iso-9899.info/wiki/The_Standard).

   Te zmiany nie będą powodować błędy kompilacji, ale może spowodować programów zachowują się inaczej, właściwie zgodnie ze standardem.

- **FLT_ROUNDS**

   W programie Visual Studio 2013 — makro FLT_ROUNDS rozszerzyć, aby wyrażenie stałe jest niepoprawne, ponieważ można skonfigurować w czasie wykonywania, na przykład przez wywołującego fesetround trybu zaokrąglania. Makro FLT_ROUNDS jest teraz dynamiczny i poprawnie odzwierciedla bieżący tryb zaokrąglania.

#### <a name="new-and-newh"></a>\<Nowy > i \<new.h >

- **nowe i Usuń**

   W poprzednich wersjach biblioteki nowy operator zdefiniowanych w implementacji i funkcje delete musiały zostać wyeksportowane z biblioteki wykonawczej DLL (na przykład msvcr120.dll). Te funkcje operatora są teraz zawsze połączone statycznie do plików binarnych, nawet wtedy, gdy za pomocą biblioteki środowiska uruchomieniowego bibliotek DLL.

   Nie jest to istotną zmianę dla kodu natywnego lub małe i wielkie (`/clr`), ale dla kodu skompilowanego jako [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), ta zmiana może spowodować swój kod, aby kompilacja nie powiedzie się. Jeśli kompilujesz kod jako `/clr:pure`, może być konieczne dodanie `#include <new>` lub `#include <new.h>` w celu obejścia błędy kompilacji z powodu tej zmiany. `/clr:pure` Opcja jest przestarzała w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017. Kod, który ma zostać "czysta" powinny być przenoszone do języka C#.

#### <a name="processh"></a>\<process.h>

- **_beginthread i _beginthreadex**

   [_Beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) i [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) funkcje teraz zawierać odwołanie do modułu, w którym zdefiniowano procedury wątku na czas trwania wątku. Pomaga to zapewnić modułów nie zwolnione, aż wątek ma zostało ukończone.

#### <a name="stdargh"></a>\<stdarg.h>

- **typy va_start i dokumentacja**

   Podczas kompilowania C++ kodu, [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) teraz sprawdza się w czasie kompilacji, który argumentu przekazanego do niej nie jest typu referencyjnego. Argumenty typu odwołania są zabronione przez C++ Standard.

#### <a name="stdioh-and-conioh"></a>\<stdio.h > i \<conio.h >

- **Teraz zdefiniowano printf i scanf rodzinę funkcji wbudowanych.**

   Definicje wszystkich `printf` i `scanf` funkcje zostały wbudowane przenoszony do \<stdio.h >, \<conio.h > i innych nagłówków CRT. Ta zmiana podziału prowadzi do błąd konsolidatora (LNK2019, nierozpoznany symbol zewnętrzny) dla wszystkich programów, które lokalnie zadeklarowane tych funkcji bez uwzględniania odpowiednie nagłówki CRT. Jeśli to możliwe, należy zaktualizować kod o uwzględnieniu nagłówków CRT (oznacza to, Dodaj `#include <stdio.h>`) i funkcje śródwierszowe, ale jeśli chcesz zmodyfikować swój kod, aby uwzględnić te pliki nagłówkowe, alternatywnym rozwiązaniem jest dodanie dodatkowe biblioteki do swoje konsolidatora Input, legacy_stdio_definitions.lib.

   Aby dodać tę bibliotekę dane wejściowe konsolidatora w środowisku IDE, otwórz menu kontekstowe dla węzła projektu, wybierz polecenie **właściwości**, a następnie w obszarze **właściwości projektu** okna dialogowego wybierz **konsolidatora**i edytować **dane wejściowe konsolidatora** dodać `legacy_stdio_definitions.lib` do listy rozdzielanej średnikami naczepa.

   Jeśli projekt łączy się z biblioteki statyczne, które zostały skompilowane przy użyciu programu Visual Studio w wersji wcześniejszej niż 2015, konsolidator może raportować nierozpoznany symbol zewnętrzny. Te błędy mogą odwoływać się do wewnętrznej definicji dla `_iob`, `_iob_func`, lub dla niektórych powiązanych Importy \<stdio.h > funkcje w formie _imp_\*. Firma Microsoft zaleca zrekompilować wszystkie biblioteki statyczne z najnowszą wersją kompilatora języka C++ i bibliotekami po uaktualnieniu projektu. Jeśli biblioteka jest biblioteką innych firm dla źródła, które nie jest dostępna, należy zażądać zaktualizowanego pliku binarnego od innych firm lub hermetyzują użycie tej biblioteki do oddzielnych biblioteki DLL, która skompilować przy użyciu starszej wersji kompilatora i biblioteki .

    > [!WARNING]
    > W przypadku łączenia z Windows SDK 8.1 lub starszym mogą wystąpić następujące błędy nierozpoznany symbol zewnętrzny. W takim przypadku należy rozwiązać problem, dodając legacy_stdio_definitions.lib do konsolidatora, danych wejściowych, zgodnie z wcześniejszym opisem.

   Rozwiązywanie problemów nierozpoznanych symboli, spróbuj użyć [dumpbin.exe](../build/reference/dumpbin-reference.md) zbadanie symbole zdefiniowane w pliku binarnym. Wypróbuj następujący wiersz polecenia w celu wyświetlenia symboli zdefiniowanych w bibliotece.

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **pobiera i _getws —**

   [Pobiera](../c-runtime-library/gets-getws.md) i [_getws —](../c-runtime-library/gets-getws.md) funkcje zostały usunięte. Funkcja pobiera został usunięty z biblioteki standardowej C w C11, ponieważ nie można używać w bezpieczny sposób. _Getws — funkcja została rozszerzeniem firmy Microsoft, który był równoważny pobiera, ale dla szerokiego ciągów. Jako alternatywy dla tych funkcji, rozważ użycie [fgets](../c-runtime-library/reference/fgets-fgetws.md), [fgetws —](../c-runtime-library/reference/fgets-fgetws.md), [gets_s —](../c-runtime-library/reference/gets-s-getws-s.md), i [_getws_s —](../c-runtime-library/reference/gets-s-getws-s.md).

- **_cgets i _cgetws —**

   [_Cgets](../c-runtime-library/cgets-cgetws.md) i [_cgetws —](../c-runtime-library/cgets-cgetws.md) funkcje zostały usunięte. Jako alternatywy dla tych funkcji, rozważ użycie [_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) i [_cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md).

- **Nieskończoności i NaN formatowania**

   W poprzednich wersjach nieskończoności i NaNs będą formatowane przy użyciu zestaw określonych MSVC wartownik ciągów.

  - Infinity: 1.#INF

  - Ciche NaN: 1.#QNAN

  - Sygnalizowanie NaN: 1.#SNAN

  - Nieokreślony NaN: 1.#IND

  Dowolne z tych formatów może być poprzedzona znakiem i może zostać sformatowana nieco inaczej w zależności od szerokość pola i dokładność (czasami z nietypowej skutki, na przykład `printf("%.2f\n", INFINITY)` przetwarzającej 1. #J ponieważ #INF będzie "zaokrąglony" 2-cyfrowy precyzja). C99 wprowadzono nowe wymagania na jak nieskończoności i NaNs powinny być sformatowane. Teraz za pomocą implementacji MSVC jest zgodny z tych wymagań. Nowe parametry są następujące:

  - Infinity: plik inf

  - Quiet NaN: nan

  - Sygnalizowanie NaN: nan(snan)

  - Nieokreślony NaN: nan(ind)

  Dowolny z nich może być poprzedzony znakiem. Jeśli specyfikator formatu wielkimi jest używane (%F zamiast %f), a następnie ciągi są napisane wielkimi literami (`INF` zamiast `inf`), ponieważ jest wymagane.

  [Scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkcje zostały zmodyfikowane w celu analizowania tych nowych parametrów, więc te ciągi, które są teraz obustronne za pośrednictwem `printf` i `scanf`.

- **Liczba zmiennoprzecinkowa formatowanie i analizowanie**

   Nowe zmiennoprzecinkowa formatowania i analizowania algorytmy zostały wprowadzone do poprawy dokładności. Ta zmiana wpływa na [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) rodziny funkcji, a także funkcje, takie jak [strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).

   Stary algorytmy formatowania wygeneruje tylko ograniczoną liczbę cyfr, a następnie zero spowoduje wypełnienie pozostałych miejsc dziesiętnych. Są zazwyczaj może wygenerować ciągów, które będzie obustronne powrót do oryginalnego wartość zmiennoprzecinkową, ale nie zostały wspaniałe, jeżeli chcesz dokładna wartość (lub najbliższy w formie dziesiętnej jej). Nowe algorytmy formatowania Generowanie jako liczbę cyfr, które są wymagane do reprezentowania wartości (lub do wypełnienia określoną dokładność). Na przykład poprawa; Podczas drukowania dużych potęgą liczby dwa, należy wziąć pod uwagę wyniki:

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

   Stary algorytmów analizy zakwalifikowany tylko do 17 cyfr znaczących w ciągu wejściowym i czy odrzucić pozostałe cyfry. To podejście jest wystarczający, aby wygenerować bliskie zbliżenia wartość reprezentowany przez ciąg, a wynik jest zazwyczaj bardzo blisko poprawnie zaokrąglony wynik. Nowa implementacja uwzględnia wszystkie cyfry obecne i daje wynik poprawnie zaokrąglone wszystkich danych wejściowych (maksymalnie 768 znaków długości). Ponadto te funkcje teraz respektują trybu zaokrąglania (sterowane za pośrednictwem fesetround).  Jest to potencjalnie istotną zmianę zachowania, ponieważ te funkcje mogą danych wyjściowych różne wyniki. Nowe wyniki są zawsze prawidłowe niż stare wyniki.

- **Szesnastkowym i zmiennoprzecinkowe nieskończoności/NaN punktu analizy**

   Zmiennoprzecinkowej podczas analizowania algorytmy będą teraz analizy szesnastkowe zmiennoprzecinkowa ciągów (np. tych generowanych przez %a i %A specyfikatorami formatu) i wszystkich nieskończoności i NaN ciągów, które są generowane przez `printf` działa zgodnie z powyższym opisem.

- **%A i dopełnienie %a zero**

   %A i %A format specyfikatory formatu zmiennoprzecinkowy numer punktu jako szesnastkowa mantysy i wykładnika binarnego. W poprzednich wersjach `printf` funkcje czy ciągi niepoprawnie Konsola zero. Na przykład `printf("%07.0a\n", 1.0)` przetwarzającej 00x1p + 0, gdzie powinno drukować 0x01p + 0. Ta luka został rozwiązany.

- **%A i %a dokładności**

   Domyślna dokładność specyfikatorów formatu %A i %a był 6 w poprzednich wersjach biblioteki. Domyślna dokładność jest teraz 13 dla zapewnienia zgodności z C Standard.

   Jest to zmiana zachowania środowiska uruchomieniowego w danych wyjściowych którejkolwiek funkcji korzystającej z ciągiem formatu %A lub %. W stare zachowanie danych wyjściowych za pomocą specyfikatora %A może być "1.1A2B3Cp + 111". Teraz dane wyjściowe dla tej samej wartości to "1.1A2B3C4D5E6F7p + 111". Aby pobrać stare zachowanie, można określić precyzyjnie, na przykład %.6A. Zobacz [Specyfikacja dokładności](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).

- **Specyfikator %F**

   Specyfikator formatu/konwersji %F jest teraz obsługiwane. Jest funkcjonalnie równoważny specyfikatorowi formatu %f, z tą różnicą, że nieskończoności i NaNs są formatowane przy użyciu wielkich liter.

   W poprzednich wersjach, implementacja używany do analizowania F i N jako modyfikatory długości. To zachowanie wydanych powrót do wieku segmentu przestrzeni adresowych: następujące Modyfikatory długość były używane do wskazania daleko i niemal wskaźników, odpowiednio, jak % Fp lub %Ns. To zachowanie zostało usunięte. Jeśli okaże się %F, teraz jest ona traktowana jako specyfikatora formatu %F; Jeśli okaże się %N, teraz jest ona traktowana jako nieprawidłowy parametr.

- **Wykładnik, formatowanie**

   %E i %E format specyfikatory formatu zmiennoprzecinkowy numer punktu jako dziesiętna mantysy i wykładnika. %G i specyfikatorów formatu %G również sformatować liczby, w tym formularzu w niektórych przypadkach. W poprzednich wersjach CRT będzie zawsze Generuj ciągi zawierające trzycyfrowy wykładników. Na przykład `printf("%e\n", 1.0)` przetwarzającej 1.000000e + 000, która była nieprawidłowa. Język C wymaga, że w przypadku stałego, przy użyciu tylko jednej lub dwóch cyfr wykładnika, następnie dwie cyfry są do wydrukowania.

   W programie Visual Studio 2005 został dodany przełącznik globalnego zgodność: [_set_output_format —](../c-runtime-library/set-output-format.md). Program można nazwać tę funkcję z _TWO_DIGIT_EXPONENT argumentu, aby włączyć odpowiadające drukowanie wykładnika. Domyślne zachowanie został zmieniony na zgodne z normami wykładnika trybu drukowania.

- **Sprawdzanie poprawności ciągu formatu**

   W poprzednich wersjach `printf` i `scanf` funkcje dyskretnie będzie akceptować wiele nieprawidłowe formaty ciągów, czasami z nietypowej efekty. Na przykład % hlhlhld będzie traktowane jako %d. Wszystkie ciągi w nieprawidłowym formacie teraz są traktowane jako nieprawidłowe parametry.

- **fopen — tryb ciągu weryfikacji**

   W poprzednich wersjach `fopen` rodzinę funkcji takich jak dyskretnie zaakceptowane niektóre ciągi nieprawidłowy tryb `r+b+`. Nieprawidłowy element mode ciągów są teraz wykryte i traktowany jako nieprawidłowe parametry.

- **Tryb _O_U8TEXT**

   [_Setmode —](../c-runtime-library/reference/setmode.md) funkcja teraz poprawnie zgłasza tryb do strumieni otwieranych w trybie in_O_U8TEXT. W poprzednich wersjach biblioteki go będzie zgłaszać takich strumieni jako właśnie otwierany w _O_WTEXT.

   Jest to istotnej zmiany, jeśli kod interpretuje tryb _O_WTEXT dla strumieni, gdzie jest kodowanie UTF-8. Jeśli aplikacja nie obsługuje UTF_8, należy rozważyć dodanie obsługi coraz bardziej powszechny kodowania.

- **snprintf — i vsnprintf —**

   [Snprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) i [vsnprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) funkcje są teraz zaimplementowane. Starszego kodu często podane definicje makr wersje tych funkcji, ponieważ nie zostały zaimplementowane przez bibliotekę CRT, ale nie są już potrzebne w nowszych wersjach. Jeśli [snprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) lub [vsnprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) jest zdefiniowany jako makro przed dołączeniem \<stdio.h >, teraz kompilacja zakończy się niepowodzeniem z powodu błędu, który wskazuje, gdzie makro zostało zdefiniowane.

   Zwykle rozwiązanie tego problemu polega na usunięciu wszystkie deklaracje `snprintf` lub `vsnprintf` w kodzie użytkownika.

- **tmpnam — generuje można używać nazw plików**

   W poprzednich wersjach `tmpnam` i `tmpnam_s` funkcje wygenerowane nazwy pliku w folderze głównym dysku (na przykład \sd3c.). Te funkcje tworzą teraz można używać nazw ścieżek w katalogu tymczasowym.

- **Hermetyzację plików**

   W poprzednich wersjach kompletnego typu pliku zdefiniowanego publicznie w \<stdio.h >, aby było możliwe, że kod użytkownika dotrzeć do pliku i zmodyfikować jego szczegóły wewnętrzne. Biblioteka został zmieniony na razie ukryć szczegóły implementacji. W ramach tej zmiany, pliku, zgodnie z definicją w \<stdio.h > teraz jest typem nieprzezroczystych i jej składowe są niedostępne z poza CRT, sam.

- **_outp — i _inp —**

   Funkcje [_outp —](../c-runtime-library/outp-outpw-outpd.md), [_outpw —](../c-runtime-library/outp-outpw-outpd.md), [_outpd —](../c-runtime-library/outp-outpw-outpd.md), [_inp —](../c-runtime-library/inp-inpw-inpd.md), [_inpw —](../c-runtime-library/inp-inpw-inpd.md), i [_inpd — ](../c-runtime-library/inp-inpw-inpd.md) zostały usunięte.

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h >, \<malloc.h >, a \<sys/stat.h >

- **strtof — i wcstof —**

   `strtof` i `wcstof` funkcji nie można ustawić `errno` do ERANGE, jeśli wartość nie została stałego jako liczba zmiennoprzecinkowa. Ten błąd był specyficzne dla tych dwóch funkcji; `strtod`, `wcstod`, `strtold`, i `wcstold` nie miała wpływu funkcji. Ten problem został rozwiązany i jest zmianą przerywającą środowiska uruchomieniowego.

- **Funkcje wyrównana Alokacja**

   W poprzednich wersjach, funkcje wyrównana Alokacja (`_aligned_malloc`, `_aligned_offset_malloc`, itp.) dyskretnie będzie akceptować żądania w bloku z wyrównaniem 0. Żądane wyrównanie musi być potęgą liczby dwa, który nie jest spełniony o wartości zero. Żądane wyrównanie 0 teraz jest traktowane jako nieprawidłowy parametr. Ten problem został rozwiązany i jest zmianą przerywającą środowiska uruchomieniowego.

- **Funkcje sterty**

   `_heapadd`, `_heapset`, I `_heapused` funkcje zostały usunięte. Te funkcje zostały prawidłowo, ponieważ CRT zostało zaktualizowane pod kątem korzystania ze stosu Windows.

- **smallheap**

   `smallheap` Opcja link została usunięta. Zobacz [opcje łącza](../c-runtime-library/link-options.md).

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   Podpis `wcstok` funkcji został zmieniony do dopasowania, co jest wymagane przez C Standard. W poprzednich wersjach biblioteki podpis tej funkcji to:

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   On używany do śledzenia stanu przez wywołania, co jest wykonywane na potrzeby wewnętrznych kontekst wątku `strtok`. Funkcja ma teraz podpis `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)`i wymaga obiekt wywołujący, aby przekazać kontekst jako trzeci argument do funkcji.

   Nowy `_wcstok` funkcja została dodana do stary podpis, aby ułatwić przenoszenie. Podczas kompilowania kodu C++, jest również przeciążenia wbudowane `wcstok` zawierający stary podpis. To przeciążenie jest zadeklarowany jako przestarzały. W kodzie C może define_CRT_NON_CONFORMING_WCSTOK spowodować `_wcstok` ma być używany zamiast `wcstok`.

#### <a name="timeh"></a>\<time.h>

- **clock**

   W poprzednich wersjach [zegara](../c-runtime-library/reference/clock.md) funkcja została zaimplementowana za pomocą interfejsu API Windows [GetSystemTimeAsFileTime](/windows/desktop/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime). Ta implementacja clock — funkcja było wrażliwe na czas systemowy i nie jest zatem niekoniecznie monotoniczny. Clock — funkcja ma zostać reimplemented pod względem [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) i teraz jest monotoniczny.

- **fstat — i _utime**

   W poprzednich wersjach [_stat](../c-runtime-library/reference/stat-functions.md), [fstat —](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), i [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) funkcje obsługi niepoprawnie czasu letniego. Przed Visual Studio 2013 wszystkie te funkcje nieprawidłowe ustawienie godzin (czas standardowy), tak, jakby znajdowały się czas letni.

   W programie Visual Studio 2013, problem został rozwiązany w **_stat** rodziny funkcji, ale podobne problemy w **fstat —** i **_utime** rodziny funkcji nie zostały naprawione. Ta poprawka częściowe doprowadziło do problemów ze względu na niespójność między funkcjami. **Fstat —** i **_utime** rodziny funkcji teraz została naprawiona, więc wszystkie te funkcje obsługuje teraz czasu letniego w poprawnej i spójnej.

- **asctime —**

   W poprzednich wersjach [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcja będzie konsoli jednocyfrowych dni z wiodącym zerem, na przykład: `Fri Jun 06 08:00:00 2014`. Specyfikacja wymaga, że takie dni można dopełniana spację, podobnie jak w `Fri Jun  6 08:00:00 2014`. Ten problem został rozwiązany.

- **strftime i wcsftime**

   `strftime` i `wcsftime` functions obsługuje obecnie %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u i %V specyfikatory formatu. Ponadto E oraz O Modyfikatory są analizowane, lecz ignorowane.

   Specyfikator formatu %c jest określana jako tworzenie folderu "odpowiednią datę i czas reprezentacji" dla bieżących ustawień regionalnych. W ustawieniach regionalnych języka C, to reprezentacja musi być taka sama jak `%a %b %e %T %Y`, tworzą takie same, jak jest generowany przez `asctime`. W poprzednich wersjach, specyfikator formatu %c niepoprawnie sformatowana razy, używając `MM/DD/YY HH:MM:SS` reprezentacji. Ten problem został rozwiązany.

- **timespec i TIME_UTC**

   \<Time.h > nagłówka teraz definiuje `timespec` typu i `timespec_get` funkcji ze standardowego C11. Ponadto, makra TIME_UTC, do użytku z programem `timespec_get` funkcji, jest teraz zdefiniowana. Ta aktualizacja jest istotną zmianę dla kodu, który zawiera definicję powodujące konflikt dla dowolnego z tych identyfikatorów.

- **CLOCKS_PER_SEC**

   Makro CLOCKS_PER_SEC rozszerza się teraz na liczbę całkowitą typu `clock_t`, co jest wymagane przez język c.

####  <a name="BK_STL"></a> Standardowa biblioteka C++

Aby włączyć nowe optymalizacje i kontrole debugowania, implementacja standardowej biblioteki C++ w Visual Studio celowo łamie zgodność binarną między wersjami. W związku z tym gdy używana jest standardowa biblioteka C++, pliki obiektowe i biblioteki statyczne, które są kompilowane przy użyciu różnych wersji, nie mogą być mieszane w jednym pliku binarnym (EXE lub DLL), a obiekty standardowej biblioteki C++ nie mogą być przekazywane między plikami binarnymi, które są kompilowane przy użyciu różnych wersji. Takie mieszanie powoduje błędy konsolidatora dotyczące niezgodności _MSC_VER. (_MSC_VER to makro, które zawiera wersję główną kompilatora — na przykład 1800 dla Visual Studio 2013.) To sprawdzenie nie może wykryć mieszania bibliotek DLL i nie może wykryć mieszania, które obejmuje Visual Studio 2008 lub starszy.

- **Pliki dołączane standardowej biblioteki języka C++**

   Niektóre zmiany zostały dokonane do struktury Uwzględnij nagłówki standardowej biblioteki języka C++. Nagłówki standardowej biblioteki języka C++ mogą obejmować siebie nawzajem w sposób nieokreślony. Ogólnie rzecz biorąc należy napisać kod, tak, aby dokładnie obejmuje wszystkie nagłówki, które wymaga zgodnie ze standardem C++ i nie jest zależny od nagłówki standardowej biblioteki języka C++, które obejmują które nagłówki standardowej biblioteki języka C++. To sprawia, że kod przenośny między wersjami i platform. Co najmniej dwie zmiany nagłówka w programie Visual Studio 2015 wpływa na kod użytkownika. Po pierwsze, \<ciągu > nie zawiera już \<iterator >. Drugi \<krotki > teraz deklaruje `std::array` bez wraz ze wszystkimi \<tablicy >, co może przerwać kodu za pomocą następujących kombinacji konstrukcji kodu: kod ma zmienną o nazwie "array", a użytkownik ma dyrektywy using " za pomocą przestrzeni nazw std; ", i dołączyć nagłówek biblioteki standardowej języka C++ (takie jak \<funkcjonalności >) zawierającej \<krotki >, deklaruje, która będzie `std::array`.

- **steady_clock**

   \<Chrono > implementacji [steady_clock](../standard-library/steady-clock-struct.md) został zmieniony w celu spełnienia C++ standardowe wymagania dotyczące opanowanie i monotonicity. `steady_clock` teraz jest oparty na [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) i `high_resolution_clock` jest teraz element typedef dla `steady_clock`. W rezultacie w programie Visual Studio `steady_clock::time_point` jest teraz element typedef dla `chrono::time_point<steady_clock>`; jednak nie jest zawsze w przypadku innych implementacji.

- **alokatorów i const**

   Teraz wymagamy alokatora porównania równości i nierówności, aby przyjmowały argumenty const po obu stronach. Jeśli Twoje buforów zdefiniować te operatory podobny do powyższego,

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   następnie należy zaktualizować je i je zadeklarować jako const elementy członkowskie:

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **elementy const**

   C++ standard zawsze ma zakazany kontenerów elementów stałych (takich jak wektor\<const T > lub ustaw\<const T >). Visual Studio 2013 lub wcześniejszej akceptowane kontenerów tego typu. W bieżącej wersji kontenerów tego typu kompilacja nie powiedzie się.

- **std::allocator::deallocate**

   W programie Visual Studio 2013 lub starszej `std::allocator::deallocate(p, n)` ignorowane przekazanego argumentu *n*.  C++ standard, zawsze wymaga *n* musi być równa wartości przekazane jako pierwszy argument do wywołania elementu `allocate` który zwracany *p*. Jednak w bieżącej wersji, a wartość *n* sprawdzana jest. Kod, który przekazuje argumenty dla *n* które różnią się od co wymaga standard, mogą ulec awarii w czasie wykonywania.

- **hash_map — i hash_set**

   Pliki nagłówkowe niestandardowych \<hash_map > i \<hash_set > są przestarzałe w programie Visual Studio 2015 i zostanie usunięta w przyszłej wersji. Użyj \<unordered_map > i \<unordered_set > zamiast tego.

- **komparatorów i operator()**

   Kontenery asocjacyjne ( \<mapy > rodziny) wymaga ich komparatorów mieć wywołania operatory const wywoływanych funkcji. Poniższy kod w deklaracji klasy komparator jest teraz nie zostanie skompilowany:

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   Aby rozwiązać ten problem, zmień deklarację funkcji do:

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **cechy typu**

   Stare nazwy dla cech typu, ze starszej wersji projektu C++, standardowa, zostały usunięte. Te zostały zmienione w C ++ 11 i C ++ 11 wartości w programie Visual Studio 2015 zostały zaktualizowane. W poniższej tabeli przedstawiono starych i nowych nazw.

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

- **zasady Launch::any i launch::sync**

   Użyto niestandardowego `launch::any` i `launch::sync` zasady zostały usunięte. Katalog wirtualny wskazywał na `launch::any`, użyj `launch:async | launch:deferred`. Aby uzyskać `launch::sync`, użyj `launch::deferred`. Zobacz [launch — wyliczenie](../standard-library/future-enums.md#launch).

####  <a name="BK_MFC"></a> MFC i ATL

- **Microsoft Foundation Classes (MFC)**

   nie jest już umieszczana w "Typowych" Instalacja programu Visual Studio z powodu jego duży rozmiar. Aby zainstalować MFC, wybierz **niestandardowe** opcję instalacji w Instalatorze programu Visual Studio 2015. Jeśli masz już program Visual Studio 2015, możesz zainstalować MFC, korzystając z polecenia **programu Visual Studio** instalację ponownie. Wybierz **niestandardowe** opcję instalacji, a następnie wybierz **Microsoft Foundation Classes**. Możesz uruchomić **programu Visual Studio** Instalatora z **Panelu sterowania** kontroli **programy i funkcje**, lub z nośnika instalacyjnego.

   Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.

####  <a name="BK_ConcRT"></a> Współbieżność środowiska wykonawczego

- **YIELD — makro z Windows.h powodującą konflikt z concurrency::Context::Yield**

   Środowisko uruchomieniowe współbieżności wcześniej używano `#undef` usunięcia definicji makra Yield w celu uniknięcia konfliktów między makro Yield zdefiniowane w Windows.h h i `concurrency::Context::Yield` funkcji. To `#undef` został usunięty i nowe bezkonfliktowe równoważne wywołanie interfejsu API [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) został dodany. Aby uniknąć konfliktów z wydajnością, albo można zaktualizować swój kod, aby wywołać `YieldExecution` zamiast tego funkcji lub przestrzenny `Yield` nazwy funkcji za pomocą nawiasów w wywołaniu witryny, jak w poniższym przykładzie:

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Ulepszenia zgodności kompilatora w programie Visual Studio 2015

Podczas uaktualniania kod z poprzednich wersji, może również wystąpić błędy kompilatora, które są ze względu na ulepszenia zgodności w programie Visual Studio 2015. Te ulepszenia nie przerywają działania zgodność binarną ze starszych wersji programu Visual Studio, ale których brak zostały wyemitowane przed może powodować błędy kompilatora. Aby uzyskać więcej informacji, zobacz [Visual C++ co w nowym roku 2003 do 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).

W programie Visual Studio 2015 najnowsze ulepszenia do zgodności kompilatora czasami można zmienić sposób kompilator rozpoznaje istniejącego kodu źródłowego. W rezultacie mogą wystąpić błędy innym podczas kompilacji lub różnice w zachowaniu nawet w kodzie, który wcześniej utworzone i sprawiał by działała poprawnie.

Na szczęście te różnice mieć niewielkiego lub żadnego wpływu na większość kodu źródłowego. W przypadku kodu źródłowego lub inne zmiany są potrzebne, aby rozwiązać te różnice, poprawki zwykle być mały i proste. Uwzględniliśmy wiele przykładów kodu źródłowego wcześniej dopuszczalne, który może być konieczne, można zmienić *(przed)* i poprawki, aby je rozwiązać *(po)*.

Mimo że te różnice mogą mieć wpływ na kod źródłowy lub inne artefakty kompilacji, nie wpływają na zgodność binarną między aktualizacji do wersji programu Visual Studio. A *zmiana powodująca niezgodność* jest przeprowadzanie bardziej dotkliwych i może mieć wpływ na zgodność binarną, ale te rodzaje zgodność binarną podziały tylko występują między głównej wersji programu Visual Studio, na przykład między Visual Studio 2013 i Visual Studio 2015. Aby uzyskać informacje na temat przełomowych zmian, między programem Visual Studio 2013 i Visual Studio 2015, zobacz [Visual Studio 2015 zgodność zmiany](#VC_2015).

- [Ulepszenia zgodności w programie Visual Studio 2015](#VS_RTM)

- [Ulepszenia zgodności w aktualizacji 1](#VS_Update1)

- [Ulepszenia zgodności Update 2](#VS_Update2)

- [Ulepszenia zgodności aktualizacji 3](#VS_Update3)

###  <a name="VS_RTM"></a> Ulepszenia zgodności w programie Visual Studio 2015

- Opcja /Zc:forScope-

   Opcja kompilatora `/Zc:forScope-` jest przestarzały i zostanie usunięta w przyszłej wersji.

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   Zazwyczaj użyto tę opcję, aby umożliwić kod niestandardowy, który używa pętli zmiennych po punkcie, w którym, zgodnie ze standardem, ich powinien zniknie z zakresu. Konieczne było tylko wtedy, gdy skompilowano z `/Za` opcji, ponieważ bez `/Za`, użycie zmiennej pętli po końcu pętli jest zawsze dozwolona. Jeśli nie dba o zgodność ze standardami (na przykład, jeśli kod nie jest przeznaczona do przenośne na inne kompilatory), możesz całkowicie wyłączyć `/Za` opcja (lub ustaw **Wyłącz rozszerzenia języka** właściwość **nr** ). Jeśli interesujące Cię pisania kodu przenośnego, zgodnych ze standardami, należy napisać ponownie kodu tak, aby jest zgodny ze standardem, przenosząc deklaracji takich zmiennych do punktu poza pętlę.

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg` — Opcja kompilatora

   `/Zg` — Opcja kompilatora (Generuj prototypy funkcji) nie jest już dostępna. Tę opcję kompilatora wcześniej została zakończona.

- Nie można uruchomić testy jednostkowe z C++sposób niezamierzony z wiersza polecenia mstest.exe. Zamiast tego należy użyć vstest.console.exe. Zobacz [opcje wiersza poleceń VSTest.Console.exe](/visualstudio/test/vstest-console-options).

- **Mutable — słowo kluczowe**

   **Mutable** specyfikatora klasy magazynu nie jest już dozwolona w miejscach, w którym, wcześniej skompilowany go bez błędów. Teraz, kompilator wyświetla błąd C2071 (niedozwolona Klasa magazynu). Zgodnie ze standardem **mutable** specyfikator mogą być stosowane tylko do nazwy elementów członkowskich danych klasy, nie można zastosować do nazwy zadeklarowane const lub statyczne i nie można zastosować do odwoływać się do elementów członkowskich.

   Na przykład rozważmy następujący kod:

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   Poprzednie wersje kompilatora zaakceptowane to, ale kompilator zapewnia obecnie następujący błąd:

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   Aby naprawić błąd, Usuń zbędną **mutable** — słowo kluczowe.

- **char_16_t i char32_t**

   Nie można korzystać `char16_t` lub `char32_t` jako aliasów w **typedef**, ponieważ te typy są teraz traktowane jako wbudowane. Było typowe dla użytkowników i autorzy biblioteki, aby zdefiniować `char16_t` i `char32_t` jako aliasy `uint16_t` i `uint32_t`, odpowiednio.

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

   Aby zaktualizować swój kod, należy usunąć **typedef** deklaracje i Zmień nazwę innych identyfikatorów, które kolidują z tych nazw.

- **Parametry szablonu bez typu**

   Pewność, że kod, który obejmuje parametry szablonu bez typu są teraz prawidłowo sprawdzane pod kątem zgodności typów po podaniu jawnych argumentów szablonów. Na przykład poniższy kod kompilowany bez błędów w poprzednich wersjach programu Visual Studio.

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

   Bieżący kompilatora prawidłowo zwraca błąd, ponieważ argument szablonu nie pasuje do typu parametru szablonu (parametr jest wskaźnik do składowej const, ale funkcja f jest niestały):

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   Aby rozwiązać ten błąd w kodzie, należy upewnić się, że typ argumentu szablonu jest zgodny z typem zadeklarowany parametr szablonu.

- **__declspec(align)**

   Kompilator nie będzie akceptował `__declspec(align)` funkcji. Ta konstrukcja zawsze została zignorowana, ale teraz generuje błąd kompilatora.

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracją funkcji. Ponieważ miała żadnego efektu, usuwając go nie wprowadza żadnych zmian.

- **Obsługa wyjątków**

   Istnieje kilka zmian do obsługi wyjątków. Po pierwsze obiekty wyjątków muszą być kopiowania lub przenośne. Poniższy kod skompilowany w programie Visual Studio 2013, ale nie Kompiluj w programie Visual Studio 2015:

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

   Problem polega na tym, że Konstruktor kopiujący jest prywatny, więc nie można skopiować obiektu, ponieważ miało miejsce w trakcie normalnego przebiegu Obsługa wyjątku. To samo dotyczy, gdy Konstruktor kopiujący jest zadeklarowany **jawne**.

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

   Aby zaktualizować swój kod, upewnij się, Konstruktor kopiujący obiektu wyjątku **publicznych** , nie jest oznaczona **jawne**.

   Przechwytywanie wyjątku przez wartość wymaga także obiekt wyjątku do kopiowania. Poniższy kod skompilowany w programie Visual Studio 2013, ale nie Kompiluj w programie Visual Studio 2015:

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

   Możesz rozwiązać ten problem, zmieniając typ parametru dla **catch** do odwołania.

    ```cpp
    catch (D& d)
    {
    }
    ```

- **Literały ciągu, a następnie makra**

   Kompilator obsługuje teraz literały definiowane przez użytkownika. W konsekwencji literałów ciągów następuje makra bez żadnych pośredniczące białe znaki będą interpretowane jako literały definiowane przez użytkownika, które może powodować generowanie błędów lub nieoczekiwane wyniki. Na przykład w poprzednim kompilatory następujący kod został pomyślnie skompilowany:

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

   Kompilator interpretowane ten kod jako ciąg literału "hello", następuje makra podzielonego na "w miejscu", i następnie literałów ciągów dwóch zostały połączone w jedną. W programie Visual Studio 2015, kompilator interpretuje słowa kluczowe tę sekwencję jako literał zdefiniowanych przez użytkownika, ale ponieważ nie ma żadnych pasujących literału zdefiniowanego przez użytkownika `_x` zdefiniowane, powoduje błąd.

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   Aby rozwiązać ten problem, Dodaj odstęp między literałem ciągu i makra.

- **Literały ciągów sąsiadujących**

   Podobnie do poprzedniego, z powodu powiązanych zmian podczas analizowania ciągu, sąsiadujących literałów ciągu (albo literały ciągów znaków szeroki lub wąski) bez żadnych odstępów zostały interpretowane jako pojedynczy ciąg połączonych w poprzednich wersjach Visaul C++. W programie Visual Studio 2015 możesz teraz dodać odstęp między dwa ciągi. Na przykład można zmienić następujący kod:

    ```cpp
    char * str = "abc""def";
    ```

   Aby rozwiązać ten problem, należy dodać spację między dwa ciągi:

    ```cpp
    char * str = "abc" "def";
    ```

- **Położenie nowych i delete**

   Zmiana została wprowadzona do **Usuń** operatora, aby zapewnić zgodność z C ++ 14 standardowych. Szczegółowe informacje o zmianie standardów znajduje się w temacie [cofania alokacji o rozmiarze w języku C++](http://isocpp.org/files/papers/n3778.html). Zmiany dodać formularz globalnego **Usuń** operator, który przyjmuje parametr rozmiaru. Istotną zmianę jest to, że jeśli wcześniej używano operator **Usuń** z tym samym podpisie (z **umieszczania nowych** operator), otrzymasz błąd kompilatora (C2956, który ma miejsce w momencie, gdy nowe położenie jest używana, ponieważ jest pozycja w kodzie, gdzie kompilator próbuje zidentyfikować odpowiednie dopasowania **Usuń** operator).

   Funkcja `void operator delete(void *, size_t)` został **delete umieszczania** operator odpowiadający **umieszczania nowych** funkcji `void * operator new(size_t, size_t)` w C ++ 11. Za pomocą języka C ++ 14 dezalokacji wielkości, ta funkcja usuwania jest obecnie *funkcji dezalokacji zwykle* (globalne **Usuń** operator). Standardowa wymaga użycia nowego miejsca odwołuje się do odpowiednich funkcji usuwania, funkcja dezalokacji zwykle znajduje program źle sformułowane.

   Załóżmy, że Twój kod określa zarówno **umieszczania nowych** i **delete umieszczania**:

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   Występuje problem ze względu na dopasowanie w sygnaturach funkcji między **delete umieszczania** operator zdefiniowany przez użytkownika i nowe globalne, wielkości **Usuń** operatora. Należy wziąć pod uwagę, czy możesz używać innego typu innego niż `size_t` dla każdego **umieszczania nowych** i **Usuń** operatorów. Typ `size_t` **typedef** jest zależna od kompilatora; jest **typedef** dla **unsigned int** w MSVC. Dobrym rozwiązaniem jest używać typu wyliczeniowego, taką jak ta:

    ```cpp
    enum class my_type : size_t {};
    ```

   Następnie zmień definicja **umieszczania nowych** i **Usuń** można użyć tego typu jako drugi argument zamiast `size_t`. Należy również zaktualizować wywołania umieszczania nowych do przekazania nowego typu (na przykład za pomocą `static_cast<my_type>` Aby przekonwertować wartość całkowitą) i aktualizowanie definicji **nowe** i **Usuń** rzutowanie wstecz Typ liczby całkowitej. Nie trzeba używać **wyliczenia** tego; klasa to typ `size_t` Członkowskich również będzie działać.

   Alternatywnym rozwiązaniem jest, że można wyeliminować **umieszczania nowych** całkowicie. Jeśli kod używa **umieszczania nowych** do zaimplementowania puli pamięci, której argument umieszczania jest rozmiar jest obiekt przydzielony lub został usunięty, a następnie funkcja dezalokacji wielkości może być zastąpienie własnego kodu puli pamięci niestandardowe i można pozbyć się funkcji umieszczania i po prostu Użyj własnych dwuargumentową **Usuń** operator zamiast funkcji umieszczania.

   Jeśli nie chcesz natychmiast zaktualizować kod, możesz przywrócić starsze zachowanie za pomocą opcji kompilatora `/Zc:sizedDealloc-`. Jeśli używasz tej opcji, funkcje dwuargumentową delete nie istnieje i nie będzie powodować konfliktu z usługi **delete umieszczania** operator.

- **Elementy członkowskie danych Unii**

   Składowe danych Unii może już typy odwołań. Następujący kod został pomyślnie skompilowany w programie Visual Studio 2013, ale generuje błąd w programie Visual Studio 2015.

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

   Powyższy kod generuje następujące błędy:

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   Aby rozwiązać ten problem, zmień typy odwołań do wskaźnika lub wartość. Zmiana typu do wskaźnika wymaga wprowadzenia zmian w kodzie, który używa pola Unii. Zmiana kodu do wartości zmieniłby danych przechowywanych w Unii, który ma wpływ na inne pola, ponieważ pola w typy Unii udostępnianie tej samej pamięci. W zależności od rozmiaru wartość może on również zmienić rozmiar Unii.

- Związki anonimowe są teraz więcej zgodność ze standardem. Poprzednie wersje kompilatora generowane jawny Konstruktor i destruktor związki anonimowe. Te funkcje generowane przez kompilator są usuwane w programie Visual Studio 2015.

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

   Powyższy kod generuje następujący błąd w programie Visual Studio 2015:

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   Aby rozwiązać ten problem, podaj własne definicje Konstruktor i/lub destruktor.

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

- **Unie przy użyciu struktury anonimowe**

   Aby można było zgodne ze standardem, zachowanie środowiska uruchomieniowego zmienił się dla elementów członkowskich struktury anonimowe w Unii. Konstruktora dla elementów członkowskich struktury anonimowe Unii są nie już wywoływany niejawnie po utworzeniu takiej Unii. Ponadto destruktor dla elementów członkowskich struktury anonimowe Unii nie jest już niejawnie jest wywoływana, gdy Unii wykracza poza zakres. Należy wziąć pod uwagę następujący kod, w której Unii U zawiera anonimowa struktura, która zawiera strukturę nazwanego elementu członkowskiego S, która ma destruktor.

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

   W programie Visual Studio 2013 Konstruktor S jest wywoływana, gdy jest tworzony Unii i destruktor dla S jest wywoływana, gdy stos funkcji f jest czyszczony. Ale w programie Visual Studio 2015, Konstruktor i destruktor nie są wywoływane. Kompilator wyświetla ostrzeżenie dotyczące tej zmiany zachowania.

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   Aby przywrócić oryginalne zachowanie, nazwij anonimowa Struktura. Zachowanie środowiska uruchomieniowego struktury anonimowe są takie same, niezależnie od wersji kompilatora.

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

   Alternatywnie spróbuj przenieść kod Konstruktor i destruktor do nowych funkcji, a następnie dodaj wywołania tych funkcji z Konstruktor i destruktor dla Unii.

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

- **Rozdzielczość szablon**

   Wprowadzono zmiany do rozpoznawania nazw dla szablonów. W języku C++, rozważając kandydatami do rozpoznawania nazw można go tak, że jedną lub więcej nazw pod uwagę jako potencjalny dopasowania tworzy wystąpienia szablonu jest nieprawidłowa. Te nieprawidłowe wystąpień nie normalnie powodują błędy kompilatora, zasady, znane jako SFINAE (podstawienie jest nie błąd).

   Teraz Jeśli SFINAE wymaga kompilatora do utworzenia wystąpienia specjalizacji szablonu klasy, wszelkie błędy, które występują w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator będzie ignorować takie błędy. Na przykład rozważmy następujący kod:

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

   Jeśli kompilujesz z opcją kompilatora bieżącej, zostanie wyświetlony następujący błąd:

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

   Jest to spowodowane punkcie pierwsze wywołanie is_base_of, klasa `D` nie zostało jeszcze zdefiniowana.

   W tym przypadku poprawki ma nie używać tych cech typu, dopóki klasy została zdefiniowana. Jeśli przeniesiesz definicje `B` i `D` na początku pliku kodu błędu nie zostanie rozwiązany. Jeśli definicje znajdują się w plikach nagłówkowych, sprawdź kolejność instrukcje dołączania dla pliki nagłówkowe upewnić się, że wszystkie definicje klas są kompilowane przed szablony problematyczny są używane.

- **Kopiowanie konstruktorów**

   W programie Visual Studio 2013 i Visual Studio 2015 kompilator generuje konstruktora kopiującego dla klasy, jeśli klasa ma Konstruktor przenoszący zdefiniowanych przez użytkownika, ale bez konstruktora kopiującego zdefiniowanego przez użytkownika. W Dev14 to Konstruktor kopiujący niejawnie wygenerowanego jest również oznaczone jako "= delete".

<!--From here to VS_Update1 added 04/21/2017-->

- **główny jest zadeklarowany jako extern "C", teraz wymaga typu zwracanego.**

   Poniższy kod tworzy teraz C4430.

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   Aby naprawić błąd, Dodaj typ zwracany:

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **Nazwa typu nie jest dozwolona w inicjatorze składowej**

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

   Aby naprawić błąd, należy usunąć `typename` z inicjatora:

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **Klasa magazynu na jawne specjalizacje jest ignorowany.**

   W poniższym kodzie specyfikatora klasy magazynu statycznego jest ignorowany

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

- **Stała używane w static_assert wewnątrz szablonu klasy zawsze zakończą się niepowodzeniem.**

   Poniższy kod powoduje, że `static_assert` się zawsze niepowodzeniem:

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   Aby obejść ten problem, opakowywanie wartość **struktury**:

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

- **Reguły wymuszane na deklaracje przechodzenia do przodu. (Dotyczy tylko C.)**

   Poniższy kod generuje teraz C2065:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   Aby rozwiązać ten problem, należy dodać właściwe deklaracje przechodzenia do przodu:

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **Bardziej spójny wymuszanie typów wskaźnika funkcji**

   Poniższy kod generuje teraz C2197:

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **Niejednoznaczny wywołania funkcji przeciążenia**

   Poniższy kod generuje teraz C266: "N::bind": niejednoznaczne wywołanie przeciążonej funkcji

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

   Aby naprawić błąd, możesz pełnej kwalifikacji wywołanie `bind: N::bind(...)`. Jednak jeśli ta zmiana jest manifestu niezadeklarowany identyfikator (C2065), następnie można spróbować rozwiązać za pomocą **przy użyciu** deklaracji zamiast tego.

   Ten wzorzec często wykonywane przy użyciu ComPtr a innymi typami danych w `Microsoft::WRL` przestrzeni nazw.

- **Napraw nieprawidłowy adres**

   Następujący kod teraz generuje C2440: "=": nie można konwertować z ' typ * "do"type". Aby naprawić błąd, Zmień & (typ) na (typ) oraz (& f()) do (f()).

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

- **Literał ciągu jest tablicą stałej**

   Następujący kod teraz generuje C2664: "void f (void *)": nie można przekonwertować argumentu 1 z "const char (*) [2]" na "void *"

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   Aby naprawić błąd, Zmień typ parametru funkcji, aby `const void*`, lub w przeciwnym razie należy zmienić treść funkcji `h` wyglądać następująco:

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **C ++ 11 UDL ciągi znaków**

   Poniższy kod teraz powoduje błąd C3688: nieprawidłowy sufiks literału "L"; operator literału lub szablonu operatora literału "operator" "L" nie znaleziono

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   Aby naprawić błąd, Zmień kod, aby dodać miejsce na:

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

   W powyższym przykładzie `MACRO` już jest analizowany jako dwa tokeny (ciąg następuje makro). Teraz jest analizowany jako pojedynczy UDL tokenu. To samo dotyczy L "" L"", który był wcześniej analizowany jako L""-L "", a teraz jest analizowany jako L "" L i "".

   Reguły konkatenacji ciągów również zostały przeniesione do zgodności ze standardem, co oznacza, że L "a" "b" jest odpowiednikiem L "ab". Poprzednie wersje programu Visual Studio nie zaakceptował łączenia ciągów o szerokości znaków.

- **C ++ 11 pusty usuniętego znaku**

   Poniższy kod teraz powoduje błąd C2137: pusty znak stałej

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   Aby naprawić błąd, Zmień kod, aby wprowadzić jawne wartości null:

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **Wyjątki MFC nie może zostać przechwycony przez wartość, ponieważ nie są możliwe do kopiowania**

   Poniższy kod w aplikacji MFC teraz powoduje błąd C2316: Gdyby ": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub zostały usunięte

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

   Aby naprawić kod, można zmienić blok catch do `catch (const D &)` , ale lepszym rozwiązaniem jest zwykle używanie makr MFC TRY/CATCH.

- **alignof teraz jest słowem kluczowym**

   Poniższy kod teraz powoduje błąd C2332: "class": Brak nazwy tagu. Aby naprawić kod należy zmienić nazwę klasy lub, jeśli klasa wykonuje ten sam pracę jako **alignof**, wystarczy zastąpić klasę za pomocą słowa kluczowego new.

    ```cpp
    class alignof{}
    ```

- **wyrażenia constexpr teraz jest słowem kluczowym**

   Poniższy kod teraz powoduje błąd C2059: błąd składniowy: ")". Aby naprawić kod, należy zmienić nazwę funkcji dowolnej nazwy zmiennych, które są nazywane "constexpr".

    ```cpp
    int constexpr() {return 1;}
    ```

- **Typy ruchome nie mogą być const**

   Gdy funkcja zwraca typ, który jest przeznaczony do przeniesienia, nie należy jej typ zwracany **const**.

- **Konstruktory kopiujące usunięte**

   Poniższy kod generuje teraz firmy C2280:: S(S &&) ": próba odwania do usuniętej funkcji do:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   Aby naprawić błąd, należy użyć inicjalizacji bezpośredniej dla `S2`:

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **Konwersja wskaźnika funkcji tylko generowane, gdy nie przechwytywania lambda**

   Poniższy kod generuje C2664 w programie Visual Studio 2015.

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   Aby naprawić błąd, należy usunąć `=` z listy przechwytywania.

- **Wywołania niejednoznacznego obejmujących operatory konwersji**

   Poniższy kod teraz powoduje błąd C2440: "typ cast": nie można konwertować z "S2" do "S1":

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

   Aby naprawić błąd, należy jawnie wywołać operatora konwersji:

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   Poniższy kod teraz powoduje błąd C2593: "operator =" jest niejednoznaczny:

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

   Aby naprawić błąd, należy jawnie wywołać operatora konwersji:

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **Usuń Inicjalizacja kopiująca nieprawidłowy na inicjowanie składowej danych niestatycznych (NSDMI)**

   Poniższy kod generuje teraz błędu C2664: "S1::S1(S1 &&)": nie można przekonwertować argumentu 1 "bool" na "const S1 &":

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   Aby naprawić błąd, należy użyć inicjalizacji bezpośredniej:

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **Uzyskiwanie dostępu do konstruktorów wewnątrz instrukcji decltype**

   Poniższy kod generuje teraz C2248: "S::S": nie może dostępu prywatnego elementu członkowskiego jest zadeklarowana w klasy ":

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

   Aby naprawić błąd, należy dodać deklaracji elementu zaprzyjaźnionego w taki sposób, aby uzyskać `S2` w `S`:

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **Domyślne ctor lambda niejawnie zostanie usunięty.**

   Poniższy kod teraz powoduje błąd C3497: nie można skonstruować wystąpienia lambdy:

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   Aby naprawić błąd, należy usunąć potrzebę konstruktora domyślnego, który ma zostać wywołana. Jeśli wyrażenie lambda nie przechwytuje niczego, następnie go mogą być rzutowane na wskaźnik funkcji.

- **Wyrażenia lambda z operatorem usunięto przypisanie**

   Poniższy kod teraz generuje błąd C2280:

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

   Aby naprawić błąd, należy zamienić wyrażenia lambda z klasą funktor, lub usunąć trzeba użyć operatora przypisania.

- **Próba przeniesienia obiektu za pomocą konstruktora kopiującego usunięte**

   Poniższy kod teraz powoduje błąd C2280: "ruchoma:: moveable(const moveable &)": próba odwania do usuniętej funkcji do

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

   Aby naprawić błąd, należy użyć `std::move` zamiast tego:

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **Klasy lokalnej nie mogą odwoływać się inne klasy lokalnej, które zostały zdefiniowane w dalszej części tej samej funkcji**

   Poniższy kod teraz powoduje błąd C2079: firmy "używa niezdefiniowane main::S2" struct"

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

   Aby naprawić błąd, Przenieś w górę definicji `S2`:

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

- **Nie można wywołać chroniony Konstruktor podstawowej w treści pochodnej ctor.**

   Poniższy kod teraz generuje błąd C2248: "S1::S1": nie można uzyskać dostępu chroniona składowa zadeklarowana w klasie "S1"

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

   Aby naprawić błąd, w `S2` Usuń wywołanie funkcji `S1()` z konstruktora i jeśli to konieczne umieszczenie go w innej funkcji.

- **{} Zapobiega konwersji do wskaźnika**

   Poniższy kod generuje teraz C2439 "S::p": nie można zainicjować składowej

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   Aby naprawić błąd, Usuń nawiasy klamrowe z całym `0` lub użyj innego **nullptr** zamiast tego, co pokazano w poniższym przykładzie:

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **Definicja makra niepoprawne i użycia za pomocą nawiasów**

   Poniższy przykład powoduje teraz błąd C2008: ';': nieoczekiwany w definicji makra

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   Aby rozwiązać ten problem, zmień górny wiersz, który ma być `#define A();`

   Poniższy kod powoduje błąd C2059: błąd składniowy: ")"

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   Aby naprawić kod, należy usunąć odstęp między A i ().

   Poniższy kod powoduje błąd C2091: funkcja zwraca funkcję:

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   Aby naprawić błąd, Usuń nawiasy po DECLARE w S: `DECLARE;`.

   Poniższy kod generuje błąd C2062: typ "int" Nieoczekiwany

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   Aby rozwiązać ten problem, należy zdefiniować `A` następująco:

    ```cpp
    #define A int
    ```

- **Bardzo parens w deklaracjach**

   Poniższy kod generuje błąd C2062: typ "int" Nieoczekiwany

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   Aby naprawić błąd, należy usunąć nawiasów wokół `j`. Jeśli nawiasy są wymagane w celu uściślenia, należy użyć **typedef**.

- **Konstruktory wygenerowane przez kompilator i __declspec(novtable)**

   W programie Visual Studio 2015 jest zwiększone prawdopodobieństwo wystąpienia generowanych przez kompilator wbudowane konstruktory klas abstrakcyjnych z wirtualnymi klasami bazowymi może narazić niepoprawne użycie `__declspec(novtable)` w połączeniu z `__declspec(dllimport)`.

- **Auto wymaga pojedynczego wyrażenia w bezpośrednich Inicjalizacja listy**

   Poniższy kod teraz powoduje błąd C3518: "testPositions": w kontekście bezpośredniego Inicjalizacja listy typu "Auto" można określić tylko na podstawie pojedynczego wyrażenia inicjatora

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   Aby naprawić błąd, jedną z możliwości, jest zainicjowanie `testPositions` w następujący sposób:

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **Sprawdzanie typów, a wskaźniki do typów is_convertible —**

   Poniższy kod powoduje teraz asercja statyczna nie powiedzie się.

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   Aby naprawić błąd, zmień `static_assert` tak, że porównuje wskaźniki do `D` i `B2`:

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **deklaracje __declspec(novtable) muszą być zgodne**

   `__declspec` deklaracje muszą być spójne we wszystkich bibliotek. Poniższy kod spowodują teraz wygenerowanie naruszenia reguły jednej definicji (ODR):

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

###  <a name="VS_Update1"></a> Ulepszenia zgodności w aktualizacji 1

- **Prywatne wirtualne klasy podstawowe i pośredniego dziedziczenia**

   Poprzednie wersje kompilatora mogą wywołać element członkowski funkcji jego pośrednio pochodnej klasy pochodnej `private virtual` klas bazowych. To zachowanie starej była nieprawidłowa i nie są zgodne ze standardem C++. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C2280 w wyniku.

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

   \- lub —

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **Przeciążony operator nowy i delete — operator**

   Poprzednie wersje kompilatora mogą nieczłonkowskie **nowy operator** i nieczłonkowską **operatora delete** zostać zadeklarowany jako statyczny i być deklarowane w przestrzeni nazw, innym niż globalnej przestrzeni nazw.  To zachowanie starej utworzone ryzyko, że program nie może wywołać **nowe** lub **Usuń** implementacja operatora, zamierzony potwierdzeniu programisty, wynikające zachowanie dyskretnej nieprawidłowe środowisko uruchomieniowe. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C2323 zamiast tego.

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

   Ponadto mimo że kompilator nie zapewnia określonych diagnostyczne, wbudowanego operatora **nowe** uznaje się źle sformułowane.

- **Wywołanie "operator *typu*()" (konwersja zdefiniowana przez użytkownika) dla typów klasy korporacyjnej**

   Poprzednie wersje kompilatora mogą "operator *typu*()" do wywoływania na typach klasy korporacyjnej podczas dyskretnie zostanie zignorowany. To zachowanie starej utworzony ryzyko wygenerowanie dyskretnej złego kodu, co środowisko uruchomieniowe nieprzewidywalne zachowanie. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C2228 zamiast tego.

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

- **Nadmiarowe typename w specyfikatory typów uszczegółowionych**

   Poprzednie wersje kompilatora mogą **typename** w typów uszczegółowionych specyfikator, ale kod napisany w ten sposób jest semantycznie nieprawidłowe. Kompilator nie akceptuje kodu napisanego w ten sposób i generuje błąd kompilatora C3406 zamiast tego.

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

- **Wnioskowanie typu tablic z listy inicjalizatora**

   Poprzednie wersje kompilatora nie obsługuje typ odliczenia magazynowymi pochodzącymi od listy inicjalizatora. Kompilator obsługuje teraz ten formularz wnioskowanie typu i, co w efekcie wywołań szablonów funkcji przy użyciu listy inicjatorów teraz może być niejednoznaczna lub innego przeciążenia mogą zostać wybrane niż w poprzedniej wersji kompilatora. Aby uniknąć tych problemów, program teraz należy jawnie określić przeciążenia, które są przeznaczone na potwierdzeniu programisty.

   To nowe zachowanie powoduje, że funkcja rozpoznawania przeciążeń do rozważenia dodatkowych Release candidate, który jest równie dobrze jako kandydata historycznych, wywołanie staje się niejednoznaczny i dlatego kompilator generuje błąd kompilatora C2668.

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

   Gdy to nowe zachowanie powoduje, że funkcja rozpoznawania przeciążeń do rozważenia dodatkowych Release candidate, który jest lepsze dopasowane niż historyczne Release candidate, wywołanie jest rozpoznawana jako jednoznacznie nowego kandydata; powoduje zmiany w zachowaniu program, który jest prawdopodobnie inna niż programista przeznaczone.

   Przykład 2: zmiany w przeciążeniu rozdzielczości (przed)

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

   Przykład 2: zmiany w przeciążeniu rozdzielczości (po)

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

- **Przywracanie ostrzeżenia instrukcji switch**

   Poprzedniej wersji kompilatora usunięte niektóre ostrzeżenia dotyczące **Przełącz** instrukcji; te ostrzeżenia zostały przywrócone. Kompilator generuje teraz przywróconej ostrzeżenia, a związane z określonych przypadków (w tym przypadku domyślnym) są teraz wyświetlane ostrzeżenia w wierszu zawierającym naruszającym przypadek, a nie w ostatnim wierszu instrukcji switch. W rezultacie teraz wystawiających tych ostrzeżeń w różnych wierszach niż w przeszłości, ostrzeżeń wcześniej pominięty przy użyciu `#pragma warning(disable:####)` nie będzie można pominąć zgodnie z oczekiwaniami. Aby pominąć te ostrzeżenia, zgodnie z oczekiwaniami, może być konieczne przeniesienie `#pragma warning(disable:####)` dyrektywę wiersz powyżej pierwszym przypadku powodujący problemy. Poniżej przedstawiono przywróconej ostrzeżenia:

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

   Przykłady przywróconej ostrzeżeń, które znajdują się w dokumentacji.

- **#include: użycie specyfikatora katalog nadrzędny "." w pathname** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykrył użycie specyfikatora katalog nadrzędny "." w nazwie ścieżki `#include` dyrektywy. Kod napisany w ten sposób jest zwykle przeznaczona do obejmują nagłówki, które istnieją poza projektem za pomocą niepoprawnie ścieżek względnych projektu. To zachowanie starej utworzony ryzyka, że program można kompilować przez dołączenie pliku innego źródła, programista przeznaczone lub że tych ścieżek względnych nie jest przenośny do innych środowisk kompilacji. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia C4464, ostrzeżenia kompilatora, opcjonalnie, jeśli włączona.

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

   Ponadto, mimo że kompilator nie zapewnia określonych diagnostyczne, również zalecamy specyfikator katalogu nadrzędnego "." nie powinny być używane do określania, katalogi dołączane projektu.

- **#pragma optimize() wykracza poza końcem pliku nagłówkowego** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykrył zmiany w ustawieniach flagi optymalizacji, które ucieczki pliku nagłówka, w ramach jednostki translacji. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i problemy z kompilatora opcjonalne ostrzeżenie C4426 w lokalizacji naruszeń `#include`, jeśli jest włączona. To ostrzeżenie zostanie wyświetlone tylko, jeśli konflikt zmiany za pomocą flagi optymalizacji ustawione przez argumenty wiersza polecenia kompilatora.

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

- **Niezgodność #pragma warning(push)** i **#pragma warning(pop)** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykrył `#pragma warning(push)` stan zmieni się on sparowany z `#pragma warning(pop)` stanu zmiany w pliku innego źródła, które rzadko są przeznaczone. To zachowanie starej utworzone ryzyko program będzie skompilowany z innym zestawem ostrzeżenia włączone niż programisty planowano, przez co dyskretnej nieprawidłowe działanie. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia C5031 w lokalizacji odpowiedniego ostrzeżenia kompilatora, opcjonalnie `#pragma warning(pop)`, jeśli jest włączona. To ostrzeżenie zawiera uwagi odwołujące się do lokalizacji odpowiedniego #pragma warning(push).

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

   Chociaż rzadko, kod napisany w ten sposób jest czasami zamierzone. Kod napisany w ten sposób jest wrażliwa na zmiany w `#include` kolejność; Jeśli jest to możliwe, firma Microsoft zaleca, pliki kodu źródłowego, zarządzanie stan ostrzegawczy w sposób niezależny.

- **Niedopasowane #pragma warning(push)** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora nie wykryto niedopasowane `#pragma warning(push)` stanu zmiany na końcu jednostki translacji. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i problemy z kompilatora opcjonalne ostrzeżenie C5032 w lokalizacji niedopasowane `#pragma warning(push)`, jeśli jest włączona. To ostrzeżenie zostanie wyświetlone tylko, jeśli nie ma żadnych błędów kompilacji w jednostce translacji.

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

- **Dodatkowe ostrzeżenia może zostać wygenerowany w wyniku śledzenia stanu ostrzeżenia #pragma ulepszone**

   Poprzednie wersje kompilatora śledzone ostrzeżenia #pragma zmian stanu niewystarczająco również do wystawienia przeznaczone wszystkie ostrzeżenia. To zachowanie utworzony o podwyższonym ryzyku to pewność, że ostrzeżenia będzie efektywnie pomijane w sytuacjach różni się od programisty przeznaczone. Kompilator jest teraz śledzi `#pragma warning` stanu bardziej niezawodnie — szczególnie związane z `#pragma warning` stan zmieni się wewnątrz szablonów — i opcjonalnie wystawia nowe ostrzeżenia C5031 i C5032, które mają na celu pomóc programisty, zlokalizuj niezamierzone zastosowań `#pragma warning(push)` i `#pragma warning(pop)`.

   Na ulepszone `#pragma warning` śledzenia zmian stanu, wcześniej niepoprawnie pominięte ostrzeżenia lub ostrzeżenia dotyczące problemów, które wcześniej misdiagnosed teraz może zostać wygenerowany.

- **Ulepszono proces identyfikacji nieosiągalnego kodu**

   Zmiany standardowej biblioteki języka C++ i ulepszona możliwość wywołania funkcji wbudowanych w porównaniu z poprzednimi wersjami kompilatora może umożliwić kompilatorowi udowodnić, że niektóre kodu jest nieosiągalny. To nowe zachowanie może powodować nowych i innych często wystawione wystąpień ostrzeżenie C4720.

    ```Output
    warning C4720: unreachable code
    ```

   W wielu przypadkach to ostrzeżenie mogą być wystawiane tylko podczas kompilowania z włączonymi optymalizacjami, od optymalizacji mogą wbudowane bardziej wywołaniach funkcji, wyeliminować nadmiarowy kod lub w przeciwnym razie należy można określić, że niektóre kodu jest nieosiągalny. Zauważyliśmy, że nowe wystąpienia ostrzeżenie C4720 często miały miejsce w **bloku try/catch** blokuje, szczególnie w odniesieniu do użytkowania [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).

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

###  <a name="VS_Update2"></a> Ulepszenia zgodności Update 2

- **Dodatkowe ostrzeżenia i błędy, które mogły zostać wydane w wyniku częściowa Obsługa wyrażenie SFINAE**

   Poprzednie wersje kompilatora nie jest przetwarzany niektórych rodzajów wyrażenia wewnątrz **decltype** specyfikatory ze względu na brak obsługi wyrażenie SFINAE. To zachowanie starej była nieprawidłowa i nie są zgodne ze standardem C++. Kompilator teraz analizuje te wyrażenia i ma częściowa Obsługa wyrażenie SFINAE ze względu na ulepszenia trwającą zgodności. W rezultacie kompilator generuje teraz ostrzeżenia i błędy znalezione w wyrażeniach, że poprzednie wersje kompilatora nie jest przetwarzany.

   Gdy to nowe zachowanie analizuje **decltype** wyrażenia zawierającego typ, który nie został zadeklarowany, problemy z kompilatora błąd kompilatora C2039 w wyniku.

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   Przykład 1: Użyj typu Niezadeklarowany (przed)

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

   Po przeanalizowaniu to nowe zachowanie **decltype** wyrażenie, które nie ma potrzeby stosowania **typename** słowo kluczowe, aby określić, że zależna nazwa jest typem, kompilator generuje ostrzeżenia C4346 kompilatora wraz z błąd kompilatora C2923.

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   Przykład 2: zależna nazwa nie jest typem (przed)

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

- `volatile` **zmienne Członkowskie zapobiec niejawnie zdefiniowanych konstruktorów i operatory przypisania**

   Poprzednie wersje kompilatora mogą klasy, która ma **volatile** zmienne Członkowskie mają domyślne konstruktory kopiowania/przenoszenia i domyślne operatory przypisania kopiowania/przenoszenia generowane automatycznie. To zachowanie starej była nieprawidłowa i nie są zgodne ze standardem C++. Kompilator traktuje teraz klasy, która ma **volatile** zmienne Członkowskie nietrywialnymi konstrukcji i operatorów przypisania, które uniemożliwia automatyczne generowanie domyślnej implementacji tych operatorów. Jeśli taka klasa jest elementem członkowskim Unii (lub anonimowej Unii wewnątrz klasy), konstruktorach kopiowania/przenoszenia i operatory przypisania kopiowania/przenoszenia Unii (lub klasy zawierającej anonimowej Unii) będzie można niejawnie zdefiniowany jako usunięty. Próbuje utworzyć lub skopiować Unii (lub klasa zawierająca anonimowej Unii) bez jawne określenie ich jest błędne błąd kompilatora problemów kompilatora C2280 w wyniku.

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

- **Statyczne funkcje Członkowskie nie obsługują kwalifikatory cv.**

   Poprzednie wersje programu Visual Studio 2015 może statyczne funkcje Członkowskie mają kwalifikatory cv. Takie zachowanie wynika z regresji w programie Visual Studio 2015 i Visual Studio 2015 Update 1; Visual Studio 2013 i poprzednie wersje kompilatora odrzucić kodu napisanego w ten sposób. Zachowanie programu Visual Studio 2015 i Visual Studio 2015 Update 1 jest nieprawidłowy i nie są zgodne ze standardem C++.  Visual Studio 2015 Update 2 odrzuca kodu napisanego w ten sposób i generuje błąd kompilatora C2511 zamiast tego.

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

   Example(After)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **Deklaracja wyliczenia jest niedozwolone w kodzie WinRT** (dotyczy tylko `/ZW`)

   Kod kompilowany dla środowiska uruchomieniowego Windows (WinRT) nie zezwala na **wyliczenia** typów do przodu zgłaszane, podobnie jak podczas kompilowania kodu zarządzanego C++ dla programu .net Framework za pomocą `/clr` przełącznika kompilatora. Takie zachowanie gwarantuje, że rozmiar wyliczenie zawsze jest znany i może być poprawnie przekazywany do systemu typów WinRT. Kompilator odrzuca kodu napisanego w ten sposób i generuje błąd kompilatora C2599 wraz z błąd kompilatora C3197.

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

- **Przeciążony operator składowej nowych i operatora delete nie mogą być deklarowane wbudowane** (poziom 1 (`/W1`) na domyślnie)

   Poprzednie wersje kompilatora nie generuje ostrzeżenia, gdy nowy operator składowej i funkcje delete operatora jest zadeklarowana śródwierszowo. Kod napisany w ten sposób jest nieprawidłowo sformułowany (Diagnostyka nie jest wymagane) i może spowodować, że pamięć problemy wynikające z nowych niezgodne i delete — operatory (zwłaszcza gdy jest używany z cofania alokacji o rozmiarze), które mogą być trudne do zdiagnozowania. Kompilator generuje teraz C4595 ułatwiają identyfikację kodu napisanego w ten sposób ostrzeżenia kompilatora.

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

   Naprawianie kodu, który jest zapisywany w ten sposób może wymagać, że definicje operator zostać przeniesiona z pliku nagłówka oraz odpowiadający mu plik źródłowy.

###  <a name="VS_Update3"></a> Ulepszenia zgodności aktualizacji 3

- **STD::is_convertable teraz wykrywa przypisanie własne** (standardowa biblioteka)

   Poprzednie wersje `std::is_convertable` cechy typu niepoprawnie wykrywa przypisanie własne typu klasy, gdy jego Konstruktor kopiujący został usunięty lub prywatnej. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie **false** w przypadku zastosowania do typu klasy za pomocą konstruktora kopiującego usunięty lub jest prywatny.

   Nie ma żadnych diagnostyki kompilatora skojarzone z tą zmianą.

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

   W poprzednich wersjach kompilatora statyczne potwierdzenia w dolnej części w tym przykładzie przekazać, ponieważ `std::is_convertable<>::value` została niepoprawnie ustawiona na **true**. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie **false**, powodując statyczne potwierdzenia nie powiedzie się.

- **Przyjmujące wartości domyślne lub usunął kopię prosta i przenieść specyfikatory dostępu względem konstruktorów**

   Poprzednie wersje kompilatora Sprawdź specyfikator dostępu ustawionych domyślnie lub usuniętych trivial kopii i nie konstruktory przenoszenia przed umożliwieniem do wywołania. To zachowanie starej była nieprawidłowa i nie są zgodne ze standardem C++. W niektórych przypadkach to stare zachowanie utworzony ryzyko wygenerowanie dyskretnej złego kodu, co środowisko uruchomieniowe nieprzewidywalne zachowanie. Kompilator teraz sprawdza specyfikator dostępu ustawionych domyślnie lub usuniętych kopii prosta i przenoszenie konstruktorów w celu ustalenia, czy można wywołać, a jeśli nie, problemy z ostrzeżenia kompilatora, C2248 w wyniku.

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

- **Amortyzacja opartego na atrybutach Obsługa kodu biblioteki ATL** (poziom 1 (`/W1`) na domyślnie)

   Poprzednie wersje kompilatora obsługiwane opartego na atrybutach kodu biblioteki ATL. Jako do następnej fazy Rezygnacja z obsługi ATL z atrybutami kod, który [rozpoczął się w programie Visual Studio 2008](https://msdn.microsoft.com/library/bb384632), opartego na atrybutach kodu biblioteki ATL jest przestarzałe. Kompilator generuje teraz C4467, aby ułatwić zidentyfikowanie tego rodzaju przestarzały kod ostrzeżenia kompilatora.

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   Jeśli chcesz kontynuować korzystanie z atrybutami kodu biblioteki ATL, do momentu usunięcia z kompilatora pomocy technicznej, możesz wyłączyć to ostrzeżenie, przekazując `/Wv:18` lub `/wd:4467` argumenty wiersza polecenia kompilatora lub dodając `#pragma warning(disable:4467)` w kodzie źródłowym.

   Przykład 1 (przed)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   Przykład 1 (po)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   Czasami może być konieczne lub do utworzenia pliku IDL plik, aby uniknąć użycia przestarzałe atrybutów ATL, tak jak poniższego przykładowego kodu

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

   Najpierw utwórz plik *.idl; Plik vc140.idl generowane może służyć do uzyskiwania \*pliku .idl, zawierający interfejsów i adnotacji.

   Następnie dodaj krok MIDL do kompilacji w taki sposób, aby upewnić się, że definicje interfejsu C++ są generowane.

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

   Następnie należy użyć biblioteki ATL, bezpośrednio w pliku implementacji, tak jak poniższego przykładowego kodu.

   Przykład 2 wdrożenia (po)

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

- **Prekompilowanych plików nagłówka (PCH) i niezgodny # dyrektywy include** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora zaakceptowane niezgodny `#include` dyrektywy w plikach źródłowych między `-Yc` i `-Yu` kompilacje, korzystając z prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowana przez kompilator.   Kompilator teraz niezgodny CC4598, aby ułatwić zidentyfikowanie ostrzeżenia kompilatora, problemy z `#include` dyrektywy podczas korzystania z plików PCH.

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

- **Prekompilowanych plików nagłówka (PCH) i niezgodne katalogi dołączania** (dotyczy tylko `/Wall` `/WX`)

   Poprzednie wersje kompilatora zaakceptowane, niezgodny katalog dołączania (`-I`) argumenty wiersza polecenia dla kompilatora między `-Yc` i `-Yu` kompilacje, korzystając z prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowana przez kompilator. Katalog dołączania kompilatora teraz CC4599, aby ułatwić zidentyfikowanie ostrzeżenia kompilatora, problemów niezgodność (`-I`) argumenty wiersza polecenia podczas korzystania z plików PCH.

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

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 Conformance Changes

### <a name="compiler"></a>Kompilator

- **Końcowego** — słowo kluczowe generuje nieokreślony symbol błędu, gdy kompilacja przebiegała wcześniej:

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

   We wcześniejszych wersjach, błąd nie był generowany ponieważ wywołanie było **wirtualnego** wywołania; Niemniej jednak program ulegał awarii w czasie wykonywania. Teraz zostaje zgłoszony błąd konsolidatora, ponieważ wiadomo, że klasa jest ostateczna. W tym przykładzie, aby naprawić błąd, należy połączyć przeciwko obj, który zawiera definicję `S2::f`.

- Gdy używasz zaprzyjaźnionych funkcji w przestrzeniach nazw, można ponownie zadeklarować zaprzyjaźnioną funkcję zanim odwołasz się do niego lub otrzymasz błąd, ponieważ kompilator jest teraz zgodny ze standardem ISO C++. Na przykład w tym przykładzie już się nie kompiluje:

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

   Aby poprawić ten kod, Zadeklaruj **friend** funkcji:

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

- C++ Standard nie zezwala na jawną specjalizacją w klasie. Mimo że Microsoft C++ kompilatora dopuszcza to w niektórych przypadkach, w przypadkach, takich jak poniższy, błąd jest generowany, ponieważ kompilator nie bierze pod uwagę drugiej funkcji jako specjalizacji pierwszej.

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

- Kompilator nie próbuje już odróżnić dwie funkcje w poniższym przykładzie i teraz produkuje błąd:

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

- Przed dokonaniem zmiany zgodne z ISO C ++ 11, poniższy kod będzie się kompilował i powodował `x` do rozpoznawania typu **int**:

    ```cpp
    auto x = {0};
    int y = x;
    ```

   Ten kod teraz rozwiązuje `x` dla typu `std::initializer_list<int>` i powoduje błąd w następnym wierszu, który próbuje przypisać `x` na typ **int**. (Nie ma domyślnej konwersji.) Aby poprawić ten kod, należy użyć **int** zastąpić **automatycznie**:

    ```cpp
    int x = {0};
    int y = x;
    ```

- Inicjowanie agregacji nie jest dozwolony, gdy typ wartości po prawej stronie jest niezgodny typ wartości po lewej stronie, który jest inicjowany, i zgłaszany jest błąd, ponieważ ISO C ++ 11 Standard wymaga jednolitej inicjalizacji działającej bez Konwersje zawężające. Wcześniej, jeśli powoduje zawężenie konwersji była dostępna, [ostrzeżenie kompilatora (poziom 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) ostrzeżenie będzie wystawiony zamiast błędu.

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

- Wyszukiwanie nazw zostało zmienione. Następujący kod jest rozwiązywany w inny sposób w kompilatorze języka C++ w Visual Studio 2012 i Visual Studio 2013:

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   W programie Visual Studio 2012 `E1` w wyrażeniu `E1::b` rozpoznany `::E1` w zakresie globalnym. W programie Visual Studio 2013 `E1` w wyrażeniu `E1::b` jest rozpoznawana jako `typedef E2` definicji w `main()` i ma typ `::E2`.

- {1&gt;Układ obiektu został zmieniony.&lt;1} W x64, układ obiektu klasy może się zmienić w porównaniu z poprzednimi wydaniami. Jeśli ma on **wirtualnego** funkcji, ale nie ma klasę bazową, która ma **wirtualnego** funkcji, model obiektu kompilatora wstawia wskaźnik do **wirtualnego** tabeli — funkcja Po układzie składowej danych. Oznacza to, że układ może nie być optymalny we wszystkich przypadkach. W poprzednich wersjach Optymalizacja x64 próbowała poprawić układ, ale ponieważ nie mogła działać poprawnie w sytuacjach, w złożonym kodzie, został usunięty w programie Visual Studio 2013. Na przykład, rozważmy ten kod:

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- W programie Visual Studio 2013, wynikiem `sizeof(S2)` na x64 wynosi 48, ale w poprzednich wersjach był oceniany do 32. Aby na 32 w kompilatorze Visual Studio 2013 C++ x64, Dodaj fikcyjną klasy bazową, która ma **wirtualnego** funkcji:

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

   Aby znaleźć miejsca w kodzie, które wcześniejsza wersja próbowałaby zoptymalizować, użyj kompilatora z tamtej wersji wraz z `/W3` — opcja kompilatora i Włącz ostrzeżenie 4370. Na przykład:

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

   Przed Visual Studio 2013, ten kod wyświetla następujący komunikat: "ostrzeżenie C4370: "S2": układ klasy zmienił się z poprzedniej wersji kompilatora ze względu na lepsze pakowanie ".

   X86 kompilatora ma ten sam problem nieoptymalne układ we wszystkich wersjach kompilatora. Na przykład, jeśli ten kod jest kompilowany dla architektury x86:

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   Wynik `sizeof(S)` to 24. Jednak go można zmniejszyć do 16 zastosować obejście, o których wspomniano x64:

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

C++ Kompilatora w programie Visual Studio 2013 wykrywa niezgodności w _ITERATOR_DEBUG_LEVEL, który został wprowadzony w programie Visual Studio 2010, a nie jest zgodny RuntimeLibrary. Tych niezgodności wystąpić podczas opcje kompilatora `/MT` (wersja statyczna), `/MTd` (statyczna do debugowania), `/MD` (Oficjalna wersja dynamiczna) i `/MDd` (wersja dynamiczna do debugowania) są mieszane.

- Twój kod potwierdza szablony aliasów symulowane poprzedniej wersji, należy ją zmienić. Na przykład, zamiast z `allocator_traits<A>::rebind_alloc<U>::other`, teraz należy podać `allocator_traits<A>::rebind_alloc<U>`. Mimo że `ratio_add<R1, R2>::type` nie jest już konieczny i teraz zalecamy powiedzieć `ratio_add<R1, R2>`, pierwsza będzie nadal kompilować ponieważ `ratio<N, D>` musi mieć element typedef "type" dla obniżonego współczynnika, który będzie tego samego typu, jeśli jest on już ograniczony.

- Należy użyć `#include <algorithm>` podczas wywoływania `std::min()` lub `std::max()`.

- Jeśli istniejący kod używa symulowanych poprzedniej wersji typów wyliczeniowych — tradycyjnych typów wyliczeniowych zapakowane w przestrzeni nazw bez zakresu — trzeba go zmienić. Na przykład, jeśli odwołanie do typu `std::future_status::future_status`, teraz należy podać `std::future_status`. Jednak większość kodu pozostanie nienaruszona — na przykład `std::future_status::ready` nadal będzie się kompilować.

- `explicit operator bool()` jest bardziej restrykcyjny niż unspecified-bool-type() operatora. `explicit operator bool()` zezwala na jawną konwersję na bool — na przykład, biorąc pod uwagę `shared_ptr<X> sp`, zarówno `static_cast<bool>(sp)` i `bool b(sp)` są prawidłowe — oraz weryfikowalne logicznych "konwersje kontekstowe" na bool — na przykład `if (sp)`, `!sp`, `sp &&` niezależnie od. Jednak `explicit operator bool()` zabrania konwersji niejawnych do bool, więc nie można zadeklarować `bool b = sp;` i biorąc pod uwagę zwracany typ bool, nie można zadeklarować `return sp`.

- Teraz, szablony zmiennych rzeczywistych, _VARIADIC_MAX i powiązane makra nie mają wpływu. Jeżeli nadal definiujesz _VARIADIC_MAX, jest on ignorowany. Jeśli przyjmiesz nasze rozwiązania makr przeznaczone do wspierania symulowanych szablonów wariadycznych w jakikolwiek inny sposób, musisz zmienić kod.

- Oprócz zwykłych słów kluczowych, nagłówki standardowej biblioteki języka C++ teraz zabraniają tworzenia zastąpienia makro kontekstowymi słowami kluczowymi **zastąpienia** i **końcowego**.

- `reference_wrapper`, `ref()`, i `cref()` teraz zabraniają powiązania do obiektów tymczasowych.

- \<losowy > teraz ściśle wymusza jego warunki wstępne czasu kompilacji.

- Różne cechy typu standardowej biblioteki języka C++ mają warunek wstępny "T musi być typem kompletnym". Mimo że kompilator wymusza teraz ten warunek wstępny bardziej restrykcyjnie, go nie może go wymusić we wszystkich sytuacjach. (Ponieważ naruszenia warunku wstępnego standardowej biblioteki języka C++ wyzwolić niezdefiniowane zachowanie, Standard nie gwarantuje egzekwowania.)

- Standardowa biblioteka C++ nie obsługuje `/clr:oldSyntax`.

- C ++ 11 specyfikacji common_type <> miała niepożądane i nieoczekiwane konsekwencje; w szczególności, to sprawia, że common_type\<int, int >:: typ zwracany int & &. W związku z tym, kompilator implementuje proponowane rozwiązanie dotyczące grupy roboczej Biblioteka, wydanie 2141, co sprawia, że common_type\<int, int = "" >:: typ zwracany int.

   Jako efekt uboczny tej zmiany, przestaje działać przypadek tożsamości (common_type\<T > nie zawsze skutkuje typem T). To zachowanie jest zgodne z proponowanym rozwiązaniem, ale unieważnia jakikolwiek kod, który opierał się na poprzednim zachowaniu.

   Jeśli wymagasz cechy typu tożsamości, nie używaj niestandardowego typu `std::identity` zdefiniowanego w \<type_traits >, ponieważ nie będzie działać dla \<void >. Zamiast tego wdróż własną cechę typu tożsamości odpowiednią do własnych potrzeb. Oto przykład:

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC i ATL

- **Programu Visual Studio 2013 tylko**: Biblioteka MFC MBCS nie jest zawarty w programie Visual Studio, ponieważ Unicode jest bardzo popularny i zastosowanie MBCS odrzucił znacznie. Ta zmiana podtrzymuje również ściślejszą relację między MFC a Windows SDK. ponieważ wiele nowych kontrolek i komunikatów wymaga Unicode. Jednak jeśli musisz nadal korzystać z biblioteki MFC MBCS, możesz ją pobrać z Centrum pobierania MSDN, w [wielobajtowych MFC Library for Visual Studio 2013](https://www.microsoft.com/download/details.aspx?id=40770). Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.  (Uwaga: Biblioteki DLL MBCS znajduje się za pomocą składników Instalatora języka C++ w programie Visual Studio 2015 lub nowszy).

- Ułatwienia dostępu dla wstążki MFC jest zmieniany.  Zamiast architektury jednego poziomu jest teraz architektura hierarchiczna. Można nadal używać starego zachowania wywołując `CRibbonBar::EnableSingleLevelAccessibilityMode()`.

- `CDatabase::GetConnect` Metoda jest usuwany. W celu poprawy bezpieczeństwa ciąg połączenia jest teraz przechowywany zaszyfrowany i odszyfrowywany tylko w razie potrzeby; nie może być zwracany jako zwykły tekst.  Ciąg znaków można uzyskać za pomocą `CDatabase::Dump` metody.

- Podpis `CWnd::OnPowerBroadcast` zostanie zmieniony. Sygnatura tego programu obsługi komunikatu została zmieniona, aby przyjąć LPARAM jako drugi parametr.

- Sygnatury zostały zmienione, aby uwzględnić programy obsługi komunikatów. Listy parametrów dla poniższych funkcji zostały zmienione, aby używać nowo dodanych programów obsługi komunikatów ON_WM_*:

   - `CWnd::OnDisplayChange` zmienione (UINT, int, int) zamiast (WPARAM, LPARAM) tak, aby nowe makro ON_WM_DISPLAYCHANGE mogą być używane w mapie komunikatów.

   - `CFrameWnd::OnDDEInitiate` zmieniony na (CWnd *, UINT, jednostka) zamiast (WPARAM, LPARAM) tak, aby nowe makro ON_WM_DDE_INITIATE mogą być używane w mapie komunikatów.

   - `CFrameWnd::OnDDEExecute` zmieniony na (* UCHWYT CWnd) zamiast (WPARAM, LPARAM) tak, aby nowe makro ON_WM_DDE_EXECUTE mogą być używane w mapie komunikatów.

   - `CFrameWnd::OnDDETerminate` zmieniony na (CWnd *) jako parametr zamiast (WPARAM, LPARAM) tak, aby nowe makro ON_WM_DDE_TERMINATE mogą być używane w mapie komunikatów.

   - `CMFCMaskedEdit::OnCut` tak, aby nowe makro ON_WM_CUT mogą być używane w mapie komunikatów, należy zmienić na bez parametrów zamiast (WPARAM, LPARAM).

   - `CMFCMaskedEdit::OnClear` tak, aby nowe makro ON_WM_CLEAR mogą być używane w mapie komunikatów, należy zmienić na bez parametrów zamiast (WPARAM, LPARAM).

   - `CMFCMaskedEdit::OnPaste` tak, aby nowe makro ON_WM_PASTE mogą być używane w mapie komunikatów, należy zmienić na bez parametrów zamiast (WPARAM, LPARAM).

- `#ifdef` dyrektywy w plikach nagłówkowych MFC są usuwane. Liczne `#ifdef` dyrektywy w plikach nagłówkowych MFC związane z nieobsługiwane wersje systemu Windows (WINVER &lt; 0x0501) są usuwane.

- Zostanie usunięty ATL DLL (atl120.dll). ATL jest obecnie dostarczany jako nagłówki i biblioteka statyczna (atls.lib).

- Atlsd.lib, atlsn.lib i atlsnd.lib są usuwane. Atls.lib nie ma już zależności zestawu znaków ani kodu, który jest specyficzny dla wersji do debugowania/oficjalnych. Ponieważ działa tak samo dla Unicode/ANSI i wersji do debugowania/oficjalnych, wymagana jest tylko jedna wersja biblioteki.

- Narzędzie śledzenia ATL/MFC jest usuwane wraz z biblioteką ATL DLL i mechanizm śledzenia jest uproszczony. `CTraceCategory` Konstruktor przyjmuje teraz jeden parametr (nazwę kategorii) a makra śledzenia wywoływać funkcje raportowania debugowania CRT.

## <a name="visual-studio-2012-breaking-changes"></a>Visual Studio 2012 Breaking Changes

### <a name="compiler"></a>Kompilator

- `/Yl` — Opcja kompilatora został zmieniony. Domyślnie kompilator używa tej opcji może prowadzić do błędów LNK2011 pod pewnymi warunkami. Aby uzyskać więcej informacji, zobacz [/Yl (wstrzyknąć Odnośnik PCH dla bibliotek debugowania)](../build/reference/yl-inject-pch-reference-for-debug-library.md).

- W kodzie, który jest kompilowany przy użyciu `/clr`, **wyliczenia** class, słowo kluczowe definiuje C ++ 11 wyliczenia, nie wspólnego języka wspólnego (CLR) wyliczenia. Aby zdefiniować wyliczenia CLR, musi być wyraźnie jej dostępność.

- Użyj słowa kluczowego szablonu, aby jawnie odróżnić nazwy zależne (zgodność w standardzie języka C++). W poniższym przykładzie wyróżnione template — słowo kluczowe jest wymagane, aby rozstrzygnąć niejednoznaczność. Aby uzyskać więcej informacji, zobacz [rozpoznawanie nazwy dla typów zależnych](../cpp/name-resolution-for-dependent-types.md).

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- Wyrażenie stałe typu zmiennoprzecinkowego nie jest już dozwolona jako argument szablonu, jak pokazano w poniższym przykładzie.

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- Kod, który jest kompilowany przy użyciu `/GS` opcji wiersza polecenia i że ma wyłączyć po drugim luk w zabezpieczeniach może prowadzić do przetwarzania zakończenia w czasie wykonywania, jak pokazano w poniższym przykładzie pseudokodzie.

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- Architektura domyślne dla kompilacji zostanie zmieniony na SSE2; x86 w związku z tym kompilator może emitować instrukcji SSE i użyje rejestrów XMM do wykonywania obliczeń zmiennopozycyjnych. Jeśli chcesz przywrócić poprzednie zachowanie, użyj `/arch:IA32` flagi kompilatora, aby określić architekturę jako IA32.

- Kompilator może wydać ostrzeżenia [ostrzeżenie kompilatora (poziom 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) i C4701, na którym wcześniej ją nie zmieniła się. Kompilator stosuje silniejsze kontrole do użytku niezainicjowanych zmiennych lokalnych typu wskaźnika.

- Kiedy flagi konsolidatora nowe `/HIGHENTROPYVA` jest określona, system Windows 8 zwykle powoduje alokacji pamięci zwrócić adres 64-bitowych. (Przed systemu Windows 8 takich przydziałów częściej zwrócone adresy, które były mniej niż 2 GB.) Ta zmiana może narazić usterki obcięcie wskaźnika w istniejącym kodzie. Domyślnie ten przełącznik jest włączony. Aby wyłączyć to zachowanie, należy określić `/HIGHENTROPYVA:NO`.

- Kompilator zarządzanych (Visual Basic / C#) obsługuje również `/HIGHENTROPYVA` dla zarządzanych kompilacji.  Jednak w tym przypadku `/HIGHENTROPYVAswitch` jest domyślnie wyłączona.

### <a name="ide"></a>IDE

- Mimo że zaleca się, że należy tworzyć aplikacje Windows Forms w C++sposób niezamierzony, konserwacja istniejących C++interfejsu wiersza polecenia w interfejsie użytkownika aplikacji jest obsługiwany. W przypadku tworzenia aplikacji Windows Forms lub innej aplikacji interfejsu użytkownika platformy .NET, należy użyć języka C# lub Visual Basic. Użyj C++sposób niezamierzony współdziałania w ramach wyłącznie do celów.

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Biblioteka równoległych wzorców i Biblioteka środowiska uruchomieniowego współbieżności

`SchedulerType` Wyliczenie `UmsThreadDefault` jest przestarzała. Specyfikacja `UmsThreadDefault` generuje ostrzeżenie przestarzałe, a następnie wewnętrznie mapuje do `ThreadScheduler`.

### <a name="standard-library"></a>Standardowa biblioteka

- Następujące istotnej zmiany między C ++ 11 standardów i języka C ++ 98/03, za pomocą jawnych argumentów szablonów do wywołania `make_pair()` — podobnie jak w `make_pair<int, int>(x, y)` — zwykle nie kompilacji w Visual C++ w programie Visual Studio 2012. Rozwiązaniem jest zawsze wywołuj `make_pair() `bez jawnych argumentów szablonów — podobnie jak w `make_pair(x, y)`. Zapewnianie zaprzeczenie argumentów jawnego szablonu celem tej funkcji. Jeśli potrzebujesz precyzyjną kontrolę nad tym wynikowy typ, użyj `pair` zamiast `make_pair` — podobnie jak w `pair<short, short>(int1, int2)`.

- Inny istotnej zmiany między C ++ 11 standardów i języka C ++ 98/03: Kiedy jest niejawnie konwertowany na B i B jest niejawnie konwertowany na C, A nie jest niejawnie konwertowany na C, C ++ 98/03 i programu Visual Studio 2010 dozwolone `pair<A, X>` (jawnie lub niejawnie) do przekonwertowania `pair<C, X>`. (Inny typ, X, nie jest tutaj zainteresowania i nie jest specyficzne dla pierwszego typu w parze.) Kompilator języka C++ w programie Visual Studio 2012 wykrywa, A nie jest niejawnie konwertowany na C i usuwa pary konwersja przeciążeniu rozdzielczości. Ta zmiana jest dodatni umożliwia obsługę wielu scenariuszy. Na przykład przeciążenie `func(const pair<int, int>&)` i `func(const pair<string, string>&)`i wywoływać metodę `func()` z `pair<const char *, const char *>` będzie kompilowany przy użyciu tej zmiany. Jednak ta zmiana podziały wierszy kodu, który opierał się na konwersji agresywne pary. Zazwyczaj można naprawić tego kodu, wykonując jedną z części pakietu konwersji jawnie — na przykład, przekazując `make_pair(static_cast<B>(a), x)` do funkcji, która oczekuje `pair<C, X>`.

- Program Visual Studio 2010 symulowane szablony wariadyczne — na przykład `make_shared<T>(arg1, arg2, argN)`— do określonego limitu 10 argumentów, przez wybijaniu przeciążenia i specjalizacje z preprocesora maszyny. W programie Visual Studio 2012 to ograniczenie jest ograniczone do pięciu argumentów, aby poprawić czasy kompilacji i zużycie pamięci kompilatora dla większości użytkowników. Jednak można ustawić poprzedniej limit przez jawne określenie _VARIADIC_MAX jako 10, całego projektu.

- C ++ 11 17.6.4.3.1 [macro.names]/2 zabrania makro zastępujące słów kluczowych podczas C++ nagłówki standardowej biblioteki są uwzględniane. Nagłówki teraz emitować błędy kompilatora, jeśli wykryją zastąpione makra słów kluczowych. (Definiowanie _ALLOW_KEYWORD_MACROS umożliwia taki kod skompilować, ale firma Microsoft zdecydowanie odradza to użycie). Jako wyjątek formie — makro `new` jest dozwolona domyślnie, ponieważ nagłówki kompleksowo bronić się przy użyciu `#pragma push_macro("new")` / `#undef new` / `#pragma pop_macro("new")`. Definiowanie _ENFORCE_BAN_OF_MACRO_NEW ma dokładnie co sama nazwa wskazuje.

- Aby zaimplementować różne optymalizacje i kontrole debugowania, implementacja standardowej biblioteki języka C++ celowo łamie zgodność binarną między wersjami programu Visual Studio (2005, 2008, 2010, 2012). W przypadku standardowej biblioteki C++ zabrania mieszania plików obiektów i bibliotek statycznych, które są kompilowane przy użyciu różnych wersji w jednym pliku binarnym (EXE lub DLL), a zabrania przekazywania obiektów standardowej biblioteki języka C++ między plikami binarnymi, które są kompilowane przez przy użyciu różnych wersji. Mieszanie plików obiektów i bibliotek statycznych (przy użyciu C++ biblioteki standardowej, które zostały skompilowane przy użyciu programu Visual Studio 2010 z tymi, które zostały skompilowane przy użyciu C++ kompilatora w programie Visual Studio 2012 powoduje błędy konsolidatora dotyczące niezgodności _MSC_VER, gdzie _MSC_VER to makro, które zawiera wersję główną kompilatora (1700 wizualizacji C++ w programie Visual Studio 2012). To sprawdzenie nie może wykryć mieszania bibliotek DLL i nie może wykryć mieszania, które obejmuje Visual Studio 2008 lub starszy.

- Oprócz wykrywania niezgodności w _ITERATOR_DEBUG_LEVEL, który został wdrożony w programie Visual Studio 2010 C++ kompilatora w programie Visual Studio 2012 wykrywa niezgodności biblioteki środowiska uruchomieniowego. Występują tych niezgodności po opcji kompilatora `/MT` (wersja statyczna), `/MTd` (statyczna do debugowania), `/MD` (Oficjalna wersja dynamiczna) i `/MDd` (wersja dynamiczna do debugowania) są mieszane.

- `operator<()`, `operator>()`, `operator<=()`, i `operator>=()` wcześniej były dostępne dla `std::unordered_map` i `stdext::hash_map` rodzin kontenerów, mimo że ich implementacji nie były przydatne. Te operatory niestandardowe zostały usunięte w programie Visual C++ w programie Visual Studio 2012. Ponadto implementacji `operator==()` i `operator!=()` dla `std::unordered_map` rodziny został rozszerzony na pokrycie `stdext::hash_map` rodziny. (Zaleca się, że należy unikać użycia `stdext::hash_map` rodziny w nowym kodzie.)

- C ++ 11 22.4.1.4 [locale.codecvt] Określa, że `codecvt::length()` i `codecvt::do_length()` powinno zająć można modyfikować `stateT&` parametrów, ale Visual Studio 2010 miał `const stateT&`. Kompilator języka C++ w programie Visual Studio 2012 przyjmuje `stateT&` nieużywanie przez standard. Różnica ta jest znacząca dla każdego, kto próbuje przesłonić funkcji wirtualnej `do_length()`.

### <a name="crt"></a>CRT

- Sterty C Runtime (CRT), który służy do nowych i malloc(), jest prywatna. CRT teraz używa sterty procesu. Oznacza to, że stos nie jest niszczony, kiedy biblioteka DLL jest zwalniana, więc biblioteki DLL połączone statycznie CRT musi zapewnić pamięci przydzielonej przez kod biblioteki DLL jest czyszczona przed jego został zwolniony.

- `iscsymf()` Funkcja potwierdza przy użyciu wartości ujemnych.

- `threadlocaleinfostruct` Struktury został zmieniony, aby uwzględnić zmiany w ustawieniach regionalnych funkcje.

- Funkcje CRT, które mają odpowiednie funkcje wewnętrzne, takie jak `memxxx()`, `strxxx()` są usuwane z intrin.h. W przypadku dołączenia intrin.h tylko dla tych funkcji możesz teraz mogą zawierać odpowiednie nagłówki CRT.

### <a name="mfc-and-atl"></a>MFC i ATL

- Usunięto obsługę łączenia (afxcomctl32.h); w związku z tym, wszystkie metody, które są zdefiniowane w \<afxcomctl32.h > zostały usunięte. Pliki nagłówkowe \<afxcomctl32.h > i \<afxcomctl32.inl > zostały usunięte.

- Zmieniono nazwę elementu `CDockablePane::RemoveFromDefaultPaneDividier` do `CDockablePane::RemoveFromDefaultPaneDivider`.

- Zmienione podpis `CFileDialog::SetDefExt` używać LPCTSTR; w związku z tym, wpływają na Unicode kompilacji.

- Usunięto przestarzały ATL kategorii śledzenia.

- Zmienione podpis `CBasePane::MoveWindow` podjęcie `const CRect`.

- Zmienione podpis `CMFCEditBrowseCtrl::EnableBrowseButton`.

- Usunięte `m_fntTabs` i `m_fntTabsBold` z `CMFCBaseTabCtrl`.

- Dodano parametr `CMFCRibbonStatusBarPane` konstruktorów. (Jest to domyślny parametr, a nie jest wymuszających).

- Dodano parametr `CMFCRibbonCommandsListBox` konstruktora. (Jest to domyślny parametr, a nie jest wymuszających).

- Usunięte `AFXTrackMouse` interfejsu API (i powiązanych czasomierza proc). Używa Win32 `TrackMouseEvent` API zamiast tego.

- Dodano parametr `CFolderPickerDialog` konstruktora. (Jest to domyślny parametr, a nie jest wymuszających).

- `CFileStatus` zmienić rozmiar struktury: `m_attribute` Elementu członkowskiego zmieniła się z BAJTU do typu DWORD (Aby dopasować wartość, która jest zwracana z `GetFileAttributes`).

- `CRichEditCtrl` i `CRichEditView` Użyj MSFTEDIT_CLASS (kontrolka RichEdit 4.1) zamiast RICHEDIT_CLASS (kontrolka RichEdit 3.0) w kompilacjach Unicode.

- Usunięte `AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` ponieważ zawsze ma wartość TRUE na Windows Vista, Windows 7 i Windows 8.

- Usunięte `AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` ponieważ zawsze ma wartość TRUE na Windows Vista, Windows 7 i Windows 8.

- Usunięte `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea`. Wywoływanie Windows API bezpośrednio w systemie Windows Vista, Windows 7 i Windows 8.

- Usunięte `AFX_GLOBAL_DATA::DwmDefWindowProc`. Wywoływanie Windows API bezpośrednio w systemie Windows Vista, Windows 7 i Windows 8.

- Zmieniono nazwę `AFX_GLOBAL_DATA::DwmIsCompositionEnabled` do `IsDwmCompositionEnabled` , aby wyeliminować kolizji nazw.

- Zmienić identyfikatory liczbę czasomierzy wewnętrznego MFC i przeniesiona definicje afxres.h (AFX_TIMER_ID_ *).

- Zmienione podpis `OnExitSizeMove` metodę, aby uzgodnić z makr ON_WM_EXITSIZEMOVE:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Zmieniono nazwę i podpis `OnDWMCompositionChanged` musieli się zgodzić za pomocą makra ON_WM_DWMCOMPOSITIONCHANGED:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- Zmienione podpis `OnMouseLeave` metodę, aby uzgodnić z makr ON_WM_MOUSELEAVE:

   - `CMFCCaptionBar`

   - `CMFCColorBar`

   - `CMFCHeaderCtrl`

   - `CMFCProperySheetListBox`

   - `CMFCRibbonBar`

   - `CMFCRibbonPanelMenuBar`

   - `CMFCRibbonRichEditCtrl`

   - `CMFCSpinButtonCtrl`

   - `CMFCToolBar` ReplaceThisText

   - `CMFCToolBarComboBoxEdit`

   - `CMFCToolBarEditCtrl`

   - `CMFCAutoHideBar`

- Zmienione podpis `OnPowerBroadcast` musieli się zgodzić za pomocą makra ON_WM_POWERBROADCAST:

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- Zmienione podpis `OnStyleChanged` musieli się zgodzić za pomocą makra ON_WM_STYLECHANGED:

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- Zmieniono nazwę metody wewnętrznej `FontFamalyProcFonts` do `FontFamilyProcFonts`.

- Usunąć wiele globalne statyczne `CString` obiektów, aby wyeliminować pamięci przecieki w niektórych sytuacjach (zastąpione #defines), oraz następujące klasy zmienne Członkowskie:

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

- Zmienione podpis `CKeyboardManager::ShowAllAccelerators` i usunąć parametr ogranicznik akceleratora.

- Dodano `CPropertyPage::GetParentSheet`, a następnie w `CPropertyPage` klasy, należy wywołać go zamiast `GetParent` okno arkusza poprawne nadrzędne, który może mieć nadrzędnego lub okna nadrzędnych do `CPropertyPage`. Może być konieczne zmian w kodzie, aby wywołać `GetParentSheet` zamiast `GetParent`.

- Stała niezrównoważone #pragma warning(push) ATLBASE. Godz., który spowodował ostrzeżeń, które mają zostać nieprawidłowo wyłączone. Po ATLBASE tych ostrzeżeń są teraz włączone poprawnie. Przeanalizowaniu H.

- Przeniesione metody dotyczące D2D z afx_global_data — do _AFX_D2D_STATE:

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - Zamiast wywoływania, na przykład `afxGlobalData.IsD2DInitialized`, wywołaj `AfxGetD2DState->IsD2DInitialized`.

- Usunięty ATL przestarzałe *. CPP pliki z folderu \atlmfc\include\.

- Przenieść `afxGlobalData` inicjalizacji na żądanie a nie w czasie inicjowania CRT, aby spełnić `DLLMain` wymagania.

- Dodano `RemoveButtonByIndex` metody `CMFCOutlookBarPane` klasy.

- Poprawione `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` do `IsFrequentlyUsedCmd`.

- Poprawione kilka wystąpień `RestoreOriginalstate` do `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)`.

- Usunąć nieużywane metody z `CDockablePane`: `SetCaptionStyle`, `IsDrawCaption`, `IsHideDisabledButtons`, `GetRecentSiblingPaneInfo`, i `CanAdjustLayout`.

- Usunięte `CDockablePane` zmiennych statycznych składowych `m_bCaptionText` i `m_bHideDisabledButtons`.

- Dodano zastąpienia `DeleteString` metody `CMFCFontComboBox`.

- Usunąć nieużywane metody z `CPane`: `GetMinLength` i `IsLastPaneOnLastRow`.

- Zmieniono nazwę `CPane::GetDockSiteRow(CDockingPanesRow *)` do `CPane::SetDockSiteRow`.

## <a name="visual-studio-2010-breaking-changes"></a>Visual Studio 2010 Breaking Changes

### <a name="compiler"></a>Kompilator

- **Automatycznie** — słowo kluczowe ma nowe znaczenie domyślne. Ponieważ użycia starego znaczenie jest rzadkie, większość aplikacji nie będzie wpływu ta zmiana.

- Nowy **static_assert** wprowadzone — słowo kluczowe, co spowoduje konflikt nazw, jeśli istnieje już identyfikator o tej nazwie w kodzie.

- Pomoc techniczna dla nowej notacji lambda nie obejmuje obsługę kodowania bez cudzysłowów identyfikator GUID w atrybucie uuid IDL.

- .NET Framework 4 wprowadzono pojęcie uszkodzony wyjątków, które są wyjątki, które opuszczają proces nieodwracalny uszkodzona. Domyślnie nie może przechwycić wyjątek uszkodzony, nawet w przypadku opcję kompilatora/eha, która przechwytuje wszystkie inne wyjątki.                 Aby jawnie przechwytywanie wyjątku typu uszkodzony, należy użyć __try -\__except instrukcji. Lub, zastosuj atrybut [HandledProcessCorruptedStateExceptions], aby włączyć funkcję przechwytywania wyjątków w stanie uszkodzenia.  Ta zmiana dotyczy przede wszystkim programistów systemu, którzy może okazać się przechwycić wyjątek stanie uszkodzenia. Osiem wyjątki są STATUS_ACCESS_VIOLATION STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, status_ — element UNWIND_CONSOLIDATE.                 Aby uzyskać więcej informacji na temat tych wyjątków, zobacz [GetExceptionCode](/windows/desktop/Debug/getexceptioncode) makra.

- Zweryfikowana `/GS` — opcja kompilatora chroni przed przepełnienia buforu bardziej wszechstronny niż w starszych wersjach. Ta wersja może wstawić dodatkowe kontrole zabezpieczeń na stosie, który może zmniejszyć wydajność. Użyj nowego `__declspec(safebuffers)` słowo kluczowe, aby poinstruować kompilator, aby nie wstawiać zabezpieczeń sprawdza, czy dla danej funkcji.

- Jeśli kompilujesz z opcją zarówno `/GL` (Optymalizacja Całoprogramowa) i `/clr` opcje kompilatora (kompilacja języka wspólnego środowiska uruchomieniowego), `/GL` opcja jest ignorowana. Ta zmiana została wprowadzona, ponieważ połączenie opcji kompilatora podany niewielkie korzyści. W wyniku tej zmiany lepsza wydajność kompilacji.

- Domyślnie pomoc techniczna dotycząca trójznaków jest wyłączone w programie Visual Studio 2010. Użyj `/Zc:trigraphs` opcję kompilatora, aby włączyć obsługę trójznaków. Trójznak składa się z dwóch następujących po sobie znaki zapytania ("??") następuje znak trzeci unikatowy. Kompilator zastępuje trójznak odpowiedni znak interpunkcyjny. Na przykład, kompilator zamienia `??=` trójznaków za pomocą znaku "#". Używać trójznaków w plikach źródłowych języka C, które używają zestawu znaków, który nie zawiera wygodnych reprezentacji graficznych dla niektórych znaków interpunkcyjnych.

- Konsolidator nie obsługuje już Optymalizacja dla Windows 98. `/OPT` (Optymalizacje) opcja generuje błąd w czasie kompilacji, jeśli określisz `/OPT:WIN98` lub `/OPT:NOWIN98`.

- Domyślne opcje kompilatora, które są określone przez RuntimeLibrary i DebugInformationFormat tworzenie systemu, które właściwości zostały zmienione. Domyślnie te właściwości są określone w projektach, które są tworzone przez Visual C++ kompilacji zwalnia 7.0 za pośrednictwem 10.0. Jeśli migrujesz projekt, który został utworzony przez Visual C++ 6.0, rozważ, czy określone wartości tych właściwości.

- W programie Visual Studio 2010 RuntimeLibrary = wielowątkowych (`/MD`) i DebugInformationFormat = ProgramDatabase (`/Zi`). W programie Visual C++ 9.0, RuntimeLibrary = wielowątkowych (`/MT`) i DebugInformationFormat = wyłączone.

### <a name="clr"></a>CLR

- Kompilatory Microsoft C# i Visual Basic można teraz utworzyć nie podstawowy zestaw międzyoperacyjny (nie PIA). Zestaw PIA nie można użyć typów modelu COM bez wdrożenia odpowiednie podstawowego zestawu międzyoperacyjnego (PIA). Podczas używania zestawów nie PIA generowane przez program Visual C# lub Visual Basic, przed odwołaniem zestawu nie PIA, który korzysta z biblioteki musi odwoływać się zestawów PIA na polecenie compile.

### <a name="visual-studio-c-projects-and-msbuild"></a>Program Visual Studio C++ projektów i MSBuild

- Program Visual Studio C++ projekty są teraz oparte na narzędziu MSBuild. W związku z tym pliki projektu użyj nowy format pliku XML i sufiks pliku .vcxproj. Program Visual Studio 2010 automatycznie konwertuje pliki projektu z wcześniejszych wersji programu Visual Studio na nowy format pliku. Istniejący projekt ma wpływ, jeśli zależy od poprzedniego .vcproj narzędzia, VCBUILD.exe lub sufiks pliku projektu, kompilacji.

- We wcześniejszych wersjach Visual C++ obsługiwane pod koniec oceny arkuszy właściwości. Na przykład arkusz właściwości nadrzędnej można importować arkusz własności podrzędny i nadrzędny można użyć zmiennej zdefiniowane w podrzędnym zdefiniować inne zmienne. Opóźnione oceny włączone nadrzędnej korzystały jeszcze zmiennej podrzędnych arkusza właściwości podrzędnych została zaimportowana. W programie Visual Studio 2010 nie można użyć zmiennej arkusza projektu, zanim zostanie on zdefiniowany, ponieważ MSBuild obsługuje tylko wczesne oceny.

### <a name="ide"></a>IDE

- Okno dialogowe zakończenia aplikacji nie jest już kończy aplikację. W poprzednich wersjach gdy `abort()` lub `terminate()` funkcja zamknięte kompilacji detalicznej aplikacji, biblioteki wykonawczej C wyświetlany komunikat zakończenia aplikacji w konsoli okno lub okno dialogowe. Wiadomość mówi, w części "Ta aplikacja zażądała środowiska uruchomieniowego do jej zakończenia w nietypowy sposób. Skontaktuj się z zespołem pomocy technicznej aplikacji Aby uzyskać więcej informacji." Komunikat zakończenia aplikacji została nadmiarowe, ponieważ Windows następnie wyświetlany bieżący programu obsługi zakończenia, który zwykle Windows raportowanie błędów (odzyskiwania po awarii. Okno dialogowe Watson) lub debugera programu Visual Studio. Począwszy od programu Visual Studio 2010 biblioteki wykonawczej języka C nie jest wyświetlany komunikat. Ponadto środowisko wykonawcze zapobiega aplikację zakończenie przed uruchomieniem debugera. Jest to istotną zmianę, tylko wtedy, gdy zależą od poprzedniego zachowania komunikat zakończenia aplikacji.

- Specjalnie dla programu Visual Studio 2010, funkcja IntelliSense nie działa dla C++kodu w sposób niezamierzony lub atrybuty, **Znajdź wszystkie odwołania** nie działa dla zmiennych lokalnych i modelu kodu nie pobierać nazwy typów z importowane zestawy lub rozwiązanie typów do ich w pełni kwalifikowanych nazw.

### <a name="libraries"></a>Biblioteki

- Safeint — klasa znajduje się w programie Visual C++ i nie jest już w ramach osobnego pobrania. Jest to istotną zmianę, tylko wtedy, gdy tworzyli klasę o nazwie "SafeInt".

- Modelu wdrażania przy użyciu biblioteki nie jest już używa manifesty znaleźć określoną wersję biblioteki dołączanej dynamicznie. Zamiast tego nazwa każdej biblioteki dołączanej dynamicznie zawiera numer wersji i użyć tej nazwy do lokalizowania biblioteki.

- W poprzednich wersjach programu Visual Studio można ponownie skompilować biblioteki czasu wykonywania. Program Visual Studio 2010 już nie obsługuje tworzenia kopii c uruchamiać pliki biblioteki czasu.

### <a name="standard-library"></a>Standardowa biblioteka

- \<Iterator > nagłówka nie jest automatycznie dołączany przez inne pliki nagłówkowe. Zamiast tego należy jawnie dołączyć nagłówek tego Jeśli potrzebujesz pomocy technicznej dla iteratorów autonomiczny zdefiniowany w nagłówku. Istniejący projekt ma wpływ, jeśli zależy od poprzedniego narzędzia do kompilowania, VCBUILD.exe lub sufiks pliku projektu,. vcproj.iterator.

- W \<algorytm > nagłówka, checked_ * i unchecked_\* funkcje są usuwane. I w \<iteratora >> nagłówka, `checked_iterator` klasy zostanie usunięty, a `unchecked_array_iterator` klasy został dodany.

- `CComPtr::CComPtr(int)` Konstruktor jest usuwany. Ten konstruktor może `CComPtr` obiekt był skonstruowany z makra o wartości NULL, ale nie jest konieczne i dozwolone pozbawiona sensu konstrukcje z liczbami całkowitymi od zera.

   A `CComPtr` nadal mogą zostać utworzone na podstawie wartość NULL, która jest zdefiniowana jako 0, ale zakończy się niepowodzeniem, jeśli zbudowany z liczbą całkowitą różną literału 0. Użyj **nullptr** zamiast tego.

- Następujące `ctype` usuniętych elementów członkowskich: `ctype::_Do_narrow_s`, `ctype::_Do_widen_s`, `ctype::_narrow_s`, `ctype::_widen_s`. Jeśli aplikacja używa jednej z tych funkcji elementu członkowskiego, należy zastąpić ją z odpowiednią wersją — zabezpieczanie: `ctype::do_narrow`, `ctype::do_widen`, `ctype::narrow`, `ctype::widen`.

### <a name="crt-mfc-and-atl-libraries"></a>CRT, MFC i ATL biblioteki

- Usunięto obsługę dla użytkowników do tworzenia biblioteki CRT, MFC i ATL. Na przykład nie odpowiedniego pliku NMAKE podano. Jednak użytkownicy nadal mieć dostęp do kodu źródłowego dla tych bibliotek. I dokumentu, który w tym artykule opisano opcje programu MSBuild, używane przez firmę Microsoft do tworzenia tych bibliotek, prawdopodobnie zostanie ona opublikowana na blogu zespołu Visual C++.

- Obsługa MFC dla IA64 zostało usunięte. Jednak nadal podano obsługę CRT i ATL na IA64.

- Liczby porządkowe są już używane ponownie w plikach definicji modułu (.def) MFC. Ta zmiana oznacza, że liczby porządkowe, nie będzie różna wersje pomocnicze, a zostanie on ulepszony zgodność binarną dodatków service pack i szybkiej poprawki inżynierii wersji.

- Nowa funkcja wirtualnych została dodana do `CDocTemplate` klasy. Jest to nowa funkcja wirtualnego [klasa CDocTemplate](../mfc/reference/cdoctemplate-class.md). Poprzednia wersja `OpenDocumentFile` ma dwa parametry. Nowa wersja ma trzy parametry. Do obsługi Menedżera ponownego uruchamiania, dowolnej klasy pochodnej `CDocTemplate` muszą wdrażać wersję, która ma trzy parametry. Nowy parametr jest `bAddToMRU`.

### <a name="macros-and-environment-variables"></a>Makra i zmiennych środowiskowych

- __MSVCRT_HEAP_SELECT zmiennych środowiskowych nie jest już obsługiwana. Ta zmienna środowiskowa jest usuwany, a istnieje nie można zastąpić.

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie

- Kilka dyrektyw zostały usunięte z kompilatora Microsoft Macro Assembler — odwołanie. Usunięto dyrektywy są `.186`, `.286`, `.286P`, `.287`, `.8086`, `.8087`, i `.NO87`.

## <a name="visual-studio-2008-breaking-changes"></a>Visual Studio 2008 Breaking Changes

### <a name="compiler"></a>Kompilator

- Windows 95, Windows 98, Windows ME i Windows NT platform nie są już obsługiwane. Te systemy operacyjne zostały usunięte z listy platformy docelowej.

- Kompilator nie obsługuje już wiele atrybutów, które zostały bezpośrednio skojarzone z serwerem biblioteki ATL. Następujące atrybuty nie są już obsługiwane:

   - perf_counter

   - perf_object

   - perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-studio-c-projects"></a>Visual Studio C++ projects

- Podczas uaktualniania projektów z poprzednich wersji programu Visual Studio, trzeba będzie zmodyfikować makra symboli WINVER i _WIN32_WINNT, aby były one większa lub równa 0x0500.

- Począwszy od programu Visual Studio 2008 Kreator nowego projektu nie ma opcji, aby utworzyć projekt C++ programu SQL Server. SQL Server — projekty utworzone za pomocą starszej wersji programu Visual Studio skompiluje i działać poprawnie.

- Plik nagłówka interfejsu Windows API Winable.h został usunięty. Zamiast tego zawierają Winuser.h.

- Biblioteka interfejsu Windows API Rpcndr.lib zostało usunięte. Zamiast łączyć się z rpcrt4.lib.

### <a name="crt"></a>CRT

- Usunięto obsługę Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4.0.

- Usunięto następujące zmienne globalne:

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- Następujące funkcje zostały usunięte. Użyj funkcji Windows API `GetVersion` lub `GetVersionEx` zamiast tego:

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- Składnia adnotacji SAL został zmieniony. Aby uzyskać więcej informacji, zobacz [adnotacji SAL](../c-runtime-library/sal-annotations.md).

- Filtr IEEE obsługuje teraz zestaw instrukcji SSE 4.1. Aby uzyskać więcej informacji, zobacz [_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt.

- Biblioteki wykonawczej C, które są dostarczane z programem Visual Studio nie są już zależne od msvcrt.dll biblioteki DLL systemu.

### <a name="standard-library"></a>Standardowa biblioteka

- Usunięto obsługę Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4.0.

- Podczas kompilowania w trybie debugowania za pomocą _HAS_ITERATOR_DEBUGGING zdefiniowane (zastąpiona [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010), aplikacji będzie teraz assert, gdy iterator próbuje zwiększyć lub zmniejszyć w przeszłości granice kontenera bazowego.

- C zmiennej elementu członkowskiego klasy stosu teraz zadeklarowano chronionych. Wcześniej ta zmienna członka zadeklarowano publicznych.

- Zachowanie `money_get::do_get` został zmieniony. Wcześniej, podczas analizowania kwotę pieniężną za pomocą więcej cyfr ułamek niż są wywoływane dla `frac_digits`, `do_get` używane do korzystania z nich wszystkich. Teraz `do_get` zatrzymuje się podczas analizowania po zużyciu co najwyżej `frac_digits` znaków.

### <a name="atl"></a>ATL

- ATL nie można utworzyć bez zależności CRT. We wcześniejszych wersjach programu Visual Studio, można użyć #define ATL_MIN_CRT się Projekt ATL minimalny zestaw zależne od CRT. W programie Visual Studio 2008 wszystkich projektów ATL zależą od co najmniej CRT niezależnie od tego, czy ATL_MIN_CRT jest zdefiniowana.

- Codebase serwera ATL zostało udostępnione jako projekt źródłowy udostępniony w witrynie CodePlex i nie jest instalowany jako część programu Visual Studio. Dane, kodowania i dekodowania klas z atlenc.h wraz z narzędziem funkcji i klas z atlutil.h i atlpath.h przebywać i są teraz częścią biblioteki ATL. Kilka plików skojarzonych z aplikacji serwera ATL. nie są już częścią Visual Studio.

- Niektóre funkcje nie są już znajdują się w bibliotece DLL. Nadal znajdują się w bibliotece importu. Nie ma to wpływu na kod, który używa funkcji statycznie. Wpłynie to tylko kodu, który używa tych funkcji dynamicznie.

- Makra PROP_ENTRY i PROP_ENTRY_EX zostały zaniechane i zastąpione makra PROP_ENTRY_TYPE i PROP_ENTRY_TYPE_EX ze względów bezpieczeństwa.

### <a name="atlmfc-shared-classes"></a>Klasy współdzielone ATL/MFC

- ATL nie można utworzyć bez zależności CRT. We wcześniejszych wersjach programu Visual Studio, można użyć `#define ATL_MIN_CRT` się Projekt ATL minimalny zestaw zależne od CRT. W programie Visual Studio 2008 wszystkich projektów ATL zależą od co najmniej CRT niezależnie od tego, czy ATL_MIN_CRT jest zdefiniowana.

- Codebase serwera ATL zostało udostępnione jako projekt źródłowy udostępniony w witrynie CodePlex i nie jest instalowany jako część programu Visual Studio. Dane, kodowania i dekodowania klas z atlenc.h wraz z narzędziem funkcji i klas z atlutil.h i atlpath.h przebywać i są teraz częścią biblioteki ATL. Kilka plików skojarzonych z aplikacji serwera ATL. nie są już częścią Visual Studio.

- Niektóre funkcje nie są już znajdują się w bibliotece DLL. Nadal znajdują się w bibliotece importu. Nie ma to wpływu na kod, który używa funkcji statycznie. Wpłynie to tylko kodu, który używa tych funkcji dynamicznie.

### <a name="mfc"></a>MFC

- `CTime` Klasa: `CTime` Klasy będzie teraz akceptować daty począwszy od 1/1/1900 r. zamiast 1/1/1970 r.

- Kolejność tabulacji kontrolek w oknach dialogowych MFC: Kolejność tabulacji poprawne wielu formantów w oknie dialogowym MFC jest rozproszonych była możliwa, jeśli formant MFC ActiveX jest wstawiana w kolejności tabulacji. Ta zmiana rozwiązuje ten problem.

   Na przykład utworzyć formant ActiveX i kilka formantów edycji aplikacji okna dialogowego MFC. Położenie formantu ActiveX w środku kolejność tabulacji kontrolek edycji. Uruchom aplikację, kliknij kontrolkę edycji, w których kolejność tabulacji jest po formantu ActiveX, a następnie kartę. Przed tą zmianą fokus zmieniał się do kontrolki edycji następującego formantu ActiveX, zamiast następny formant edycji, w kolejności tabulacji.

- `CFileDialog` Klasa: Szablony niestandardowe dla `CFileDialog` klasy nie można automatycznie przenieść do Windows Vista. One nadal można używać, ale nie mają dodatkowe funkcje lub wygląda systemu Windows Vista stylu w oknach dialogowych.

- `CWnd` Klasy i `CFrameWnd` klasy: `CWnd::GetMenuBarInfo` Metoda została usunięta.

   `CFrameWnd::GetMenuBarInfo` Metoda jest obecnie metody niewirtualnej. Aby uzyskać więcej informacji, zobacz **funkcja GetMenuBarInfo** w zestawie Windows SDK.

- Obsługa MFC ISAPI: MFC nie są już obsługuje tworzenie aplikacji z Internetu ISAPI Server Application Programming Interface (). Aby utworzyć aplikację interfejsu ISAPI, rozszerzenia ISAPI należy wywoływać bezpośrednio.

- Przestarzałe interfejsy API ANSI: Wersje ANSI kilka metod MFC są przestarzałe. Użyj wersji standardu Unicode tych metod w Twojej aplikacji tworzonych w przyszłości. Aby uzyskać więcej informacji, zobacz **tworzenie wymagania dla Windows Vista wspólnych formantów**.

## <a name="visual-studio-2005-breaking-changes"></a>Visual Studio 2005 Breaking Changes

### <a name="crt"></a>CRT

- Wiele funkcji zostało zdeprecjonowanych. Zobacz **przestarzałe funkcje CRT**.

- Wiele funkcji teraz sprawdzają poprawność swoich parametrów, w zatrzymania wykonywania, jeśli podane nieprawidłowe parametry. Kod, który przekazuje nieprawidłowe parametry i zależy od funkcji ignorowanie je lub po prostu zwróciło kod błędu może spowodować uszkodzenie tej weryfikacji. Zobacz **Parameter Validation**.

- Wartość deskryptora pliku -2 obecnie jest używana do wskazania, że `stdout` i `stderr` nie są dostępne dla danych wyjściowych, na przykład w aplikacji Windows, która ma żadnego okna konsoli. Poprzedniej wartości, używana była wartość -1. Aby uzyskać więcej informacji, zobacz [_fileno](../c-runtime-library/reference/fileno.md).

- Biblioteki CRT jednowątkowe (libc.lib i libcd.lib) zostały usunięte. Korzystanie z wielowątkowych bibliotek CRT. `/ML` Flagi kompilatora nie jest już obsługiwana. Blokowanie inne niż wersje niektóre funkcje zostały dodane w przypadkach, gdy jest potencjalnie znaczny różnic w wydajności między kod wielowątkowy i kod jednowątkowy.

- Przeciążenie pow, double pow (int, int), został usunięty lepiej są zgodne ze standardem.

- Specyfikator formatu %n nie jest już obsługiwana domyślnie w jednym z rodziny funkcji printf funkcji ponieważ ona jest z założenia niezabezpieczone. Jeśli okaże się %n, zachowanie domyślne jest wywołują procedurę obsługi nieprawidłowego parametru. Aby włączyć obsługę %n, należy użyć `_set_printf_count_output` (Zobacz też `_get_printf_count_output`).

- `sprintf` teraz drukuje minus zero podpisem.

- `swprintf` został zmieniony tak, aby były zgodne ze standardem; wymaga to teraz parametr rozmiaru. Formie `swprintf` bez parametr rozmiaru jest przestarzała.

- `_set_security_error_handler` została usunięta. Usuń wszelkie wywołania tej funkcji; domyślny program obsługi jest znacznie bezpieczniejsze sposób postępowania z błędami zabezpieczeń.

- `time_t` jest teraz wartość 64-bitowa (Jeśli nie zdefiniowano _use_32bit_time_t).

- `_spawn`, `_wspawn` Działa teraz pozostaw `errno` niezmienione w przypadku powodzenia, określony przez C Standard.

- Domyślnie RTC teraz używa znaków dwubajtowych.

- Funkcje pomocy technicznej słowo sterujące zmiennoprzecinkowe zostały zaniechane dla aplikacji skompilowanych za pomocą `/CLR` lub `/CLR:PURE`. Objęte funkcje są `_clear87`, `_clearfp`, `_control87`, `_controlfp`, `_fpreset`, `_status87`, `_statusfp`. Ostrzeżenie o zakończeniu obsługi można wyłączyć, definiując _CRT_MANAGED_FP_NO_DEPRECATE, ale korzystanie z tych funkcji w kodzie zarządzanym charakteryzuje się nieprzewidywalnością i nieobsługiwane.

- Niektóre funkcje zwracają teraz wskaźniki const. Zachowanie starej, niestały mogą zostać przywrócone, definiując _CONST_RETURN. Objęte funkcje

   - memchr, wmemchr

   - strchr, wcschr, _mbschr, _mbschr_l

   - strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l

   - strrchr, wcsrchr, _mbsrchr, _mbsrchr_l

   - strstr, wcsstr, _mbsstr, _mbsstr_l

- Podczas łączenia z Setargv.obj lub Wsetargv.obj, nie jest już możliwe do pomijania rozszerzenie symbolu wieloznacznego w wierszu polecenia, należy ująć w cudzysłów. Aby uzyskać więcej informacji, zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).

### <a name="standard-library-2005"></a>Biblioteki standardowej (2005)

- Klasy wyjątków (znajdujący się w \<wyjątku > Nagłówek) została przeniesiona do `std` przestrzeni nazw. W poprzednich wersjach ta klasa została w globalnej przestrzeni nazw. Aby rozwiązać wszelkie błędy, wskazujący, że nie można odnaleźć klasy wyjątku, Dodaj następujący kod przy użyciu instrukcji w kodzie: `using namespace std;`

- Podczas wywoływania `valarray::resize()`, zawartość `valarray` zostaną utracone i zostaną zastąpione wartościami domyślnymi. `resize()` Metoda jest przeznaczona do ponownego inicjowania `valarray` zamiast zwiększanie takich jak wektora.

- Debugowanie Iteratory: Aplikacje utworzone przy użyciu wersji debugowania biblioteki środowiska uruchomieniowego C i które Iteratory użycia niepoprawnie mogą zacząć Zobacz potwierdza w czasie wykonywania. Aby wyłączyć te potwierdza, należy zdefiniować _HAS_ITERATOR_DEBUGGING (zastąpione przez [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010) na wartość 0. Aby uzyskać więcej informacji, zobacz [Debug Iterator Support](../standard-library/debug-iterator-support.md)

## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003 Breaking Changes

### <a name="compiler"></a>Kompilator

- Nawias zamykający teraz wymagany dla zdefiniowanych dyrektywy preprocesora (C2004).

- Jawne specjalizacje nie są już znaleźć parametry szablonu z szablonu podstawowego ([błąd kompilatora C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md)).

- Chroniony element członkowski (n) może zostać oceniony jedynie za pośrednictwem funkcji składowej klasy (B), która dziedziczy z klasy (A), w której (n) jest członkiem ([błąd kompilatora C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md)).

- Kontrole Ulepszone ułatwienia dostępu w kompilatorze teraz wykrywanie niedostępnych klas podstawowych ([błąd kompilatora C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md)).

- Nie można przechwycić wyjątek, jeśli destruktor i/lub kopiowania Konstruktor jest niedostępny (C2316).

- Domyślne argumenty dotyczące wskaźników do funkcji, które nie są już dozwolone ([błąd kompilatora C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md)).

- Element członkowski danych statycznych nie można zainicjować za pomocą klasy pochodnej ([błąd kompilatora C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md)).

- Inicjowanie **typedef** nie jest dozwolona przez standard i generuje błąd kompilatora ([błąd kompilatora C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md)).

- **wartość logiczna** jest teraz odpowiedniego typu ([błąd kompilatora C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md)).

- UDC można teraz tworzyć przy użyciu przeciążonych operatorów niejednoznaczności ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).

- Więcej wyrażeń teraz są traktowane jako stałe nieprawidłowy wskaźnik o wartości null ([błąd kompilatora C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md)).

- <> szablonu jest teraz wymagany w miejscach, w którym kompilator wcześniej oznaczałoby go ([błąd kompilatora C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md)).

- Jawna specjalizacja funkcji członkowskiej poza klasą nie jest prawidłowa, jeśli funkcja już zostać jawnie specjalizowany za pośrednictwem specjalizacja szablonu klasy ([błąd kompilatora C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md)).

- Zmiennoprzecinkowe parametry szablonu bez typu punktu nie są już dozwolone ([błąd kompilatora C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md)).

- Szablony klas nie są dozwolone jako argumenty typu szablonu (C3206).

- Przyjazne nazwy funkcji nie są wprowadzane do zawierającą przestrzeń nazw ([błąd kompilatora C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md)).

- Kompilator nie będzie akceptował dodatkowe przecinkami w makrze (C4002).

- Obiekt typu POD skonstruowany przy użyciu inicjatora (formularza) będą inicjowane domyślnie (C4345).

- Nazwa typu jest teraz wymagany, jeśli zależna nazwa jest traktowane jako typ ([ostrzeżenie kompilatora (poziom 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).

- Funkcje, które zostały nieprawidłowo uznane za specjalizacje szablonu są przestaje być uważany za tak (C4347).

- Statyczne elementy członkowskie danych nie można zainicjować za pomocą klasy pochodnej (C4356).

- Specjalizacja szablonu klasy musi zdefiniować, zanim zostaną one użyte w zwracanym typem ([ostrzeżenie kompilatora (poziom 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).

- Kompilator zgłasza teraz nieosiągalnego kodu (C4702).

## <a name="see-also"></a>Zobacz także

[Co nowego w języku Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
