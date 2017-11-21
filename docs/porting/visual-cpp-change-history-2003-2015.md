---
title: Historia 2003 2015 zmian Visual C++ | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
caps.latest.revision: "124"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 89b02c277faa3da102909ce88f33aea0c653ea50
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="visual-c-change-history-2003---2015"></a>Historia 2003 2015 zmian Visual C++
W tym artykule opisano zmiany podziału z programu Visual Studio 2015, wracając do programu Visual Studio 2003 oraz w tym artykule warunki "nowe zachowanie" lub "teraz" odnoszą się do programu Visual Studio 2015 i później. Warunki "stare zachowanie" i "przed" odnoszą się do programu Visual Studio 2013 i wcześniejszych wersjach. 
 
 Informacje dotyczące programu Visual Studio 2017, zobacz [nowości w języku Visual C++ w programie Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodność w programie Visual C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md). 
 > [!NOTE]
 > Nie ma żadnych danych binarnych fundamentalne zmiany między Visual Studio 2015 i Visual Studio 2017 r.

Po uaktualnieniu do nowej wersji kompilatora Visual C++ można napotkać błędy kompilacji i/lub błędy czasu wykonywania w kodzie, który wcześniej kompilował się i uruchamiał poprawnie. Zmiany w nowej wersji, które powodują takich problemów są określane jako *fundamentalne zmiany*, i zazwyczaj są wymagane przez modyfikacje w standard języka C++, sygnatury funkcji lub układ obiektów w pamięci.  
  
 Aby uniknąć błędów czasu wykonywania, które są trudne do wykrycia i zdiagnozowania, zalecamy, aby nigdy nie łączyć statycznie do plików binarnych, które zostały skompilowane przy użyciu innych wersji kompilatora. Ponadto, gdy uaktualniasz projekt EXE lub DLL, upewnij się, że uaktualniasz również biblioteki, z którymi się on łączy. Jeśli używasz CRT (C Runtime) i typy standardowe biblioteki C++ (standardowa biblioteka C++), nie przekazywania między plików binarnych (łącznie z biblioteki dll), które zostały skompilowane przy użyciu różnych wersji kompilatora. Aby uzyskać więcej informacji, zobacz [potencjalne błędy przekazywanie CRT obiektów między granic DLL](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md).  
  
 Zalecamy też, aby nigdy nie pisać kodu, który zależy od określonego układu dla obiektu niebędącego interfejsem COM lub obiektem POD. Jeśli jednak piszesz taki kod, upewnij się, że działa po uaktualnieniu. Aby uzyskać więcej informacji, zobacz [przenośność na granicach ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md).  
  
 Ponadto w bieżących ulepszenia kompilatora zgodność jak kompilator rozumie istniejącego kodu źródłowego czasami można zmienić. W takim przypadku nowe lub inne błędy mogą wystąpić podczas kompilacji lub nawet behawioralnej różnice w kodzie, który uprzednio utworzony i z działała poprawnie. Mimo że nie są one fundamentalne zmiany takich jak te omówionych w tym dokumencie, mogą być wymagane zmiany kodu źródłowego, aby rozwiązać te problemy.  
  
  
1.  [Fundamentalne zmiany biblioteka języka C Runtime (CRT)](#BK_CRT)  
  
2.  [Standard C++ i standardowa biblioteka C++ fundamentalne zmiany](#BK_STL)  
  
3.  [MFC i ATL fundamentalne zmiany](#BK_MFC)  
  
4.  [Współbieżność środowiska wykonawczego podziału zmiany](#BK_ConcRT)  
  
## <a name="VC_2015"></a>Visual C++ 2015 zgodność zmiany  
  
###  <a name="BK_CRT"></a>Biblioteka środowiska wykonawczego języka C (CRT)  
  
#### <a name="general-changes"></a>Ogólne zmiany  
  
-   **Pliki binarne refaktoryzowane** Biblioteka CRT ma został zrefaktoryzowany do dwóch różnych plików binarnych, uniwersalne środowisko CRT (ucrtbase), który zawiera większość standardowych funkcji, a biblioteka środowiska uruchomieniowego VC (vcruntime), który zawiera powiązane kompilatora Funkcje, takie jak obsługa wyjątków i funkcje wewnętrzne. Jeśli korzystasz z domyślnych ustawień projektu, następnie ta zmiana nie ma wpływu możesz ponieważ konsolidator będzie automatycznie używać nowej biblioteki domyślne. Jeśli ustawisz projekt **konsolidatora** właściwości **Ignoruj wszystkie domyślne biblioteki** do **tak** lub w przypadku używania opcji konsolidatora/nodefaultlib w wierszu polecenia, a następnie należy lista bibliotek (w **dodatkowe zależności** właściwości) do uwzględnienia bibliotek nowy, refaktoryzowane. Zastąp równoważnych bibliotek refactored starego biblioteki CRT (libcmt.lib, libcmtd.lib, msvcrt.lib, msvcrtd.lib). Dla każdego z dwóch bibliotek refactored są statyczna (lib) i wersji dynamicznie (dll) i wersji (nie sufiksem) i wersji debugowania (wraz z sufiksem "d"). Dynamiczne wersje mają biblioteki importu, który należy połączyć z. Dwie biblioteki refactored są uniwersalne środowisko CRT, w szczególności ucrtbase.dll lub lib, plik ucrtbased.dll lub .lib, a biblioteka środowiska uruchomieniowego VC, libvcruntime.lib, vcruntime*wersji*dll, libvcruntimed.lib i vcruntimed*wersji*dll. *Wersji* w Visual Studio 2015 i Visual Studio 2017 jest 140. Zobacz [funkcje bibliotek CRT](../c-runtime-library/crt-library-features.md).  
  
#### <a name="localeh"></a>\<Locale.h >  
  
-   **localeconv —** [localeconv —](../c-runtime-library/reference/localeconv.md) funkcja zadeklarowana w locale.h teraz działa prawidłowo po [ustawienia regionalne dla każdego wątku](../parallel/multithreading-and-locales.md) jest włączona. W poprzednich wersjach biblioteki ta funkcja zwróci dane lconv — globalnych ustawień regionalnych nie ustawienia regionalne wątku.  
  
     Użycie na ustawienia regionalne wątku, należy sprawdzić użytkowania localeconv — aby zobaczyć, jeśli kod przyjęto założenie, że dane lconv — zwracane jest globalnych ustawień regionalnych dla i odpowiednio zmodyfikuj.  
  
#### <a name="mathh"></a>\<Math.h >  
  
-   **C++ przeciążeń funkcje biblioteki matematyczne** w poprzednich wersjach \<math.h > określone niektóre, ale nie wszystkie przeciążenia C++ dla funkcje matematyczne biblioteki. \<cmath > zdefiniowane pozostałych przeciążeń, dlatego w celu uzyskania wszystkich przeciążeń, co potrzebne do dołączenia \<cmath > nagłówka. To doprowadziło do problemów z Rozpoznanie przeciążenia funkcji w kodzie, zawierającego tylko \<math.h >. Teraz, zostały usunięte wszystkie przeciążenia C++ z \<math.h > i są teraz dostępne tylko w \<cmath >.  
  
     Aby naprawić błędy, obejmują <cmath> uzyskać deklaracje funkcji, które zostały usunięte z \<math.h >. W poniższej tabeli wymieniono funkcje, które zostały przeniesione.  
  
     Funkcje, które zostały przeniesione:  
  
    1.  Podwójna abs(float) abs(double) i zmiennoprzecinkowych  
  
    2.  Podwójna pow (dwa razy, int), float pow (float, float), float pow (float, int), liczba typu double pow (podwójnej długości, podwójnej długości), liczba typu double pow (int podwójnej długości)  
  
    3.  float i podwójnej długości wersje zmiennoprzecinkową punkt acos funkcje, acosh, asin, asinh, atan, atanh, atan2, cbrt —, ceil copysign —, cos, cosh erf, erfc, exp, exp2 —, expm1 —, fabs —, fdim —, floor, fma, fmax, fmin, fmod —, frexp —, hypot —, ilogb —, ldexp —, lgamma —, llrint, llround —, dziennika , log10, log1p —, log2, lrint, lround —, modf —, nearbyint —, nextafter —, nexttoward, pozostałą, remquo —, drukowanie, round, scalbln, scalbn —, sin, sinh, sqrt, tan, tanh, tgamma —, trunc  
  
     Jeśli masz kod, czy abs korzysta z liczbą zmiennoprzecinkową punkt typu, który zawiera tylko nagłówek math.h, zmiennoprzecinkowy wersji będzie nie będzie już dostępna, więc argument punktu połączenia, nawet w przypadku liczbą zmiennoprzecinkową, teraz jest rozpoznawana jako abs(int). Daje to kod błędu:  
  
    ```Output  
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data  
    ```  
  
     Poprawka dla to ostrzeżenie jest Zastąp wywołanie abs z liczbą zmiennoprzecinkową punktu wersji abs, takich jak fabs — argumentu podwójne lub fabsf — argumentu typu float, lub Dołącz nagłówek cmath i nadal używać abs.  
  
-   **Przestawne zgodność punktu** wprowadzono wiele zmian do biblioteki matematyczne, aby zwiększyć zgodność ze specyfikacją IEEE-754 i C11 załączniku F względem specjalnych przypadków wejść, takie jak wartości NaN i infinities. Na przykład quiet NaN danych wejściowych, które często są traktowane jako błędy w poprzednich wersjach biblioteki, nie są traktowane jako błędy. Zobacz [IEEE 754 standardowe](http://grouper.ieee.org/groups/754) i załącznika F [C11 Standard](http://www.iso-9899.info/wiki/The_Standard).  
  
     Te zmiany nie będzie powodować błędy kompilacji, ale może spowodować programów zachowywać się inaczej, właściwie zgodnie ze standardowego.  
  
-   **Flt_rounds —** w programie Visual Studio 2013, flt_rounds — makro rozszerzyć, aby wyrażenie stałe jest niepoprawne, ponieważ można skonfigurować w czasie wykonywania, na przykład przez wywołanie fesetround trybu zaokrąglania. Flt_rounds — makro jest teraz dynamiczne i poprawnie odzwierciedla bieżący tryb zaokrąglania.  
  
#### <a name="new-and-newh"></a>\<Nowy > i \<new.h >  
  
-   **nowe i usunąć** w poprzednich wersjach biblioteki nowy operator zdefiniowane w implementacji i usuwania funkcji zostały wyeksportowane z biblioteki środowiska uruchomieniowego DLL (na przykład msvcr120.dll). Te funkcje operatorów są teraz zawsze połączone statycznie do Twojej plików binarnych, nawet w przypadku używania biblioteki środowiska uruchomieniowego bibliotek DLL.  
  
     Nie jest to istotne zmiany kodu natywnego lub mieszane (/ clr), jednak kod skompilowany jako [/CLR: pure](../build/reference/clr-common-language-runtime-compilation.md), może to spowodować niepowodzenie skompilować kod. Jeśli Skompiluj kod jako/CLR: pure, należy dodać #include \<nowych > lub #include \<new.h > Aby uniknąć błędów kompilacji z powodu tej zmiany. Należy pamiętać, że/CLR: pure jest przestarzała w programie Visual Studio 2015 i może zostać usunięta w przyszłych wersjach.  
  
#### <a name="processh"></a>\<process.h >  
  
-   **_beginthread — i _beginthreadex —** [_beginthread —](../c-runtime-library/reference/beginthread-beginthreadex.md) i [_beginthreadex —](../c-runtime-library/reference/beginthread-beginthreadex.md) funkcji teraz przechowuje odwołania do modułu, w którym określono procedury wątku na czas trwania Wątek. Pomaga to zapewnić, że moduły nie są zwalniane, dopóki wątku ma działać do zakończenia.  
  
#### <a name="stdargh"></a>\<stdarg.h >  
  
-   **Dokumentacja i va_start — typy** podczas kompilowania kodu C++ [va_start —](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) teraz weryfikuje w czasie kompilacji, która argumentu przekazanego do niego nie jest typu referencyjnego. Argumenty typu odwołania są zabronione przez C++ Standard.  
  
#### <a name="stdioh-and-conioh"></a>\<stdio.h > i \<conio.h >  
  
-   **Teraz zdefiniowano printf i scanf rodziny funkcji wbudowanej.** Definicje wszystkie funkcje printf i scanf zostały przeniesione wbudowany w \<stdio.h >, \<conio.h > i inne CRT nagłówków. Jest to istotne zmiany, który prowadzi do konsolidatora błąd (LNK2019, nierozpoznany zewnętrzny symbol) dla wszystkich programów, które lokalnie zadeklarowane tych funkcji bez uwzględniania odpowiednie nagłówki CRT. Jeśli to możliwe, należy zaktualizować kodu do uwzględnienia nagłówki CRT (to znaczy dodawać #include \<stdio.h >) i funkcji śródwierszowych, ale jeśli nie chcesz zmodyfikować swój kod, aby uwzględnić te pliki nagłówkowe, alternatywne rozwiązanie jest dodanie dodatkowych Biblioteka do Twojej legacy_stdio_definitions.lib wejściowych, konsolidatora.  
  
     Aby dodać dane wejściowe konsolidatora w IDE tej biblioteki, otwórz menu kontekstowe dla węzła projektu, wybierz pozycję **właściwości**, a następnie w **właściwości projektu** oknie dialogowym wybierz **konsolidatora**i edytować **dane wejściowe konsolidatora** do dodania do listy rozdzielanych colon rozdzielana legacy_stdio_definitions.lib.  
  
     Jeśli projekt łączy się z bibliotek statycznych, które zostały skompilowane z języka Visual C++ w wersji wcześniejszej niż 2015, konsolidator może raportować nierozpoznany zewnętrzny symbol. Te błędy mogą odwoływać się do wewnętrznej stdio — definicje _iob —, _iob_func lub powiązane Importy dla niektórych funkcji stdio — w formie\_*. Firma Microsoft zaleca skompiluj wszystkie biblioteki statyczne z najnowszą wersją kompilatora Visual C++ i bibliotek podczas uaktualniania projektu. Jeśli biblioteka jest biblioteki innych firm dla źródła, które nie jest dostępna, należy żądanie zaktualizowano binarnego z innej firmy lub hermetyzują użycie tej biblioteki w oddzielnych bibliotekach DLL Kompiluj ze starszą wersją kompilatora Visual C++ i biblioteki.  
  
    > [!WARNING]
    >  Jeśli łączysz się z systemem Windows 8.1 SDK lub wcześniej, mogą wystąpić błędy nierozpoznany zewnętrzny symbol. W takim przypadku należy poprawić błąd, dodając legacy_stdio_definitions.lib do konsolidatora wprowadzania opisanych powyżej.  
  
     Rozwiązywanie problemów nierozwiązanych symbolu, można spróbować użyć [dumpbin.exe](../build/reference/dumpbin-reference.md) do sprawdzenia symbole zdefiniowane w pliku binarnym. Spróbuj następujący wiersz polecenia w celu wyświetlenia symboli zdefiniowanych w bibliotece.  
  
    ```cpp  
    dumpbin.exe /LINKERMEMBER somelibrary.lib  
    ```  
  
-   **pobiera i _getws —** [pobiera](../c-runtime-library/gets-getws.md) i [_getws —](../c-runtime-library/gets-getws.md) funkcje zostały usunięte. Funkcja pobiera została usunięta z biblioteki standardowe C w C11, ponieważ nie można używać w bezpieczny sposób. _Getws — funkcja została rozszerzenia firmy Microsoft, który był równoważny pobiera, ale dla szerokiego ciągów. Jako alternatywy dla tych funkcji, należy rozważyć użycie [fgets —](../c-runtime-library/reference/fgets-fgetws.md), [fgetws —](../c-runtime-library/reference/fgets-fgetws.md), [gets_s —](../c-runtime-library/reference/gets-s-getws-s.md), i [_getws_s —](../c-runtime-library/reference/gets-s-getws-s.md).  
  
-   **_cgets — i _cgetws —** [_cgets —](../c-runtime-library/cgets-cgetws.md) i [_cgetws —](../c-runtime-library/cgets-cgetws.md) funkcje zostały usunięte. Jako alternatywy dla tych funkcji, należy rozważyć użycie [_cgets_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md) i [_cgetws_s —](../c-runtime-library/reference/cgets-s-cgetws-s.md).  
  
-   **Infinity i formatowanie NaN** w poprzednich wersjach infinities i wartości NaN będzie formatowana przy użyciu zestaw Visual C++ specyficzne dla wartownik ciągów.  
  
    -   Infinity: 1. #INF  
  
    -   NaN cichy: 1. #QNAN  
  
    -   NaN sygnalizowania: 1. #SNAN  
  
    -   NaN nieograniczonego: 1. #IND  
  
     Żadnego z tych adresów może poprzedzona znakiem i mogła zostać sformatowana nieco inaczej w zależności od szerokość pola i dokładność (czasami nietypowe efekty, np. printf ("%.2f\n", NIESKOŃCZONOŚCI) czy drukowanie 1. #J ponieważ #INF czy "zaokrąglony" dokładności 2 cyfr). C99 wprowadzono nowe wymagania na jak infinities i wartości NaN powinny być sformatowane. Obecnie implementacja Visual C++ spełnia te wymagania. Nowe parametry są następujące:  
  
    -   Infinity: inf  
  
    -   Quiet NaN: nan  
  
    -   Sygnalizowanie NaN: nan(snan)  
  
    -   Nieokreślony NaN:nan(ind)  
  
     Żadnego z tych adresów może być poprzedzona znakiem. Jeśli specyfikator formatu kapitału jest używana (%F zamiast %f), a następnie ciągi są napisane wielkimi literami (INF zamiast inf), jest wymagana.  
  
     [Scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) funkcje zostały zmodyfikowane i przeanalizować tych nowych ciągów, dlatego te ciągi będzie przesyłania danych za pośrednictwem printf i scanf.  
  
-   **Zmiennoprzecinkowa formatowania ani do analizowania** wprowadzono nowy format ruchomy punkt i analizowania algorytmów zwiększające poprawności. Ta zmiana wpływa na [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) i [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) rodziny funkcji, a także funkcji, takich jak [strtod —](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
     Stary algorytmów formatowania wygenerowanie ograniczoną liczbę cyfr, a następnie zero spowoduje wypełnienie pozostałych miejsc dziesiętnych. To jest wystarczająco dobre, że do generowania ciągów, które będzie wykonywać Rundy w następujących wstecz do oryginalnego wartość zmiennoprzecinkową o, ale nie jest doskonałym dokładną wartość (lub jego najbliższej reprezentacja decimal). Nowe algorytmy formatowania Generowanie jak dużo cyfr, które są wymagane do reprezentowania wartości (lub do wypełnienia określona precyzja). Na przykład poprawy; Podczas drukowania dużych potęgą liczby dwa, należy wziąć pod uwagę wyniki:  
  
    ```cpp  
    printf("%.0f\n", pow(2.0, 80))  
  
    ```  
  
    ```Output  
        Old:  1208925819614629200000000    New:  1208925819614629174706176  
    ```  
  
     Stare algorytmy analizy czy należy wziąć pod uwagę tylko maksymalnie 17 cyfr znaczących w ciągu wejściowym i czy odrzucić pozostałe cyfry. To jest wystarczający, aby wygenerować ścisłe zbliżenia wartość reprezentowany przez ciąg, a wynik jest zwykle bliski poprawnie zaokrąglony wynik. Nowej implementacji uwzględnia wszystkie cyfry obecne i tworzy poprawnie zaokrąglony wynik dla wszystkich danych wejściowych (maksymalnie 768 cyfr długości). Ponadto te funkcje teraz zgodne trybu zaokrąglania (sterowane za pośrednictwem fesetround).  To jest potencjalnie fundamentalne zmienić zachowanie, ponieważ te funkcje mogą output różne wyniki. Nowe wyniki są zawsze poprawne niż starych wyników.  
  
-   **Szesnastkowy i przestawne nieskończoności/NaN punktu analizy** zmiennoprzecinkowej podczas analizowania algorytmów teraz będzie analizować ciągów szesnastkowych ruchomy punkt (na przykład wygenerowanych przez %a oraz specyfikatory formatu printf %A) i wszystkie nieskończoności i NaN ciągów, które są generowane przez funkcje printf zgodnie z powyższym opisem.  
  
-   **%A i %a zero dopełnienie** specyfikatory formatu %a i %A sformatować zmiennoprzecinkową numer punktu jako szesnastkowe mantysa i wykładnik binarnego. W poprzednich wersjach funkcje printf czy ciągi niepoprawnie konsoli zero. Na przykład printf ("%07.0a\n", 1.0) przetwarzającej 00x1p + 0, którego należy wydrukować, 0x01p + 0. Problem został rozwiązany.  
  
-   **Dokładność %A i %a** domyślna dokładność specyfikatory formatu %A i %a to 6 w poprzednich wersjach biblioteki. Domyślna dokładność jest teraz 13 dla zgodności z C Standard.  
  
     Jest to zmiana zachowania środowiska uruchomieniowego w danych wyjściowych z dowolnej funkcji, który używa ciągu formatu %A lub %. Zachowania stare dane wyjściowe na podstawie specyfikator %A może być "1.1A2B3Cp + 111". Teraz taką samą wartość w danych wyjściowych jest "1.1A2B3C4D5E6F7p + 111". Aby pobrać stare zachowanie, można określić dokładność, na przykład %.6A. Zobacz [Specyfikacja dokładności](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision).  
  
-   **Specyfikator %F** specyfikator formatu/konwersji %F obecnie jest obsługiwany. Jest funkcjonalnym odpowiednikiem %f specyfikatora formatu, z wyjątkiem tego, że infinities i wartości NaN są sformatowane przy użyciu wielkimi literami.  
  
     W poprzednich wersjach implementacji używany do analizowania F i N jako modyfikatory długości. To zachowanie wydanych wstecz do wieku przestrzeni adresowych segmentu: te Modyfikatory długość zostały służy do wskazania do tej pory i niemal wskaźników, odpowiednio, jak % Fp lub %Ns. Ten problem został usunięty. W przypadku %F teraz jest traktowane jako specyfikator formatu %F; w przypadku %N teraz jest traktowane jako nieprawidłowy parametr.  
  
-   **Wykładnik formatowania** %e i %E format specyfikatorów formatu zmiennoprzecinkową numer punktu jako dziesiętne mantysa i wykładnik. %G i specyfikatory formatu %G również formatu liczb w tym formularzu w niektórych przypadkach. W poprzednich wersjach CRT będzie zawsze Generuj ciągi zawierające wykładniki cyfry. Na przykład printf ("%e\n", 1.0) przetwarzającej 1.000000e + 000. To jest niepoprawne: C wymaga, aby w przypadku reprezentacja przy użyciu tylko jedną lub dwie cyfry wykładnik, następnie dwie cyfry były do drukowania.  
  
     W programie Visual Studio 2005 dodano przełącznika globalnego zgodność: [_set_output_format —](../c-runtime-library/set-output-format.md). Program można wywołać tej funkcji z _two_digit_exponent — argument, aby umożliwić drukowanie wykładnika zgodnych. Domyślne zachowanie został zmieniony do zgodnych standardów wykładnika drukowania trybu.  
  
-   **Format ciągu weryfikacji** w poprzednich wersjach, funkcje printf i scanf dyskretnie będzie akceptować wielu ciągów nieprawidłowy format, niekiedy z efektami nietypowe. Na przykład % hlhlhld będzie traktowane jako %d. Wszystkie ciągi nieprawidłowy format teraz są traktowane jako nieprawidłowe parametry.  
  
-   **fopen — tryb ciąg weryfikacji**  
  
     W poprzednich wersjach rodziny fopen — funkcji dyskretnie akceptowane niektórych ciągów nieprawidłowy tryb (np. r + b). Nieprawidłowy tryb ciągi teraz wykrytych i traktowane jako nieprawidłowe parametry.  
  
-   **Tryb _O_U8TEXT**  
  
     [_Setmode —](../c-runtime-library/reference/setmode.md) funkcja teraz prawidłowo raportów trybu z strumieni otworzyć in_O_U8TEXT tryb. W poprzednich wersjach biblioteki go rozpoczną przesyłanie raportów o tych strumieni jako otwierany w _O_WTEXT.  
  
     Jest to istotne zmiany, jeśli kod interpretuje tryb _O_WTEXT dla strumieni, gdzie jest kodowanie UTF-8. Jeśli aplikacja nie obsługuje UTF_8, należy rozważyć dodanie obsługi coraz częściej kodowania.  
  
-   **snprintf — i vsnprintf —** [snprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) i [vsnprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) funkcje są teraz zaimplementowane. Starszego kodu często podać definicji makra wersje tych funkcji, ponieważ nie zostały one wykonywane przez bibliotekę CRT, ale nie są już potrzebne w nowszej wersji. Jeśli [snprintf —](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) lub [vsnprintf —](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) jest zdefiniowany jako makra przed dołączeniem \<stdio.h >, teraz kompilacja zakończy się niepowodzeniem z powodu błędu, który wskazuje, gdzie został zdefiniowany makra.  
  
     Zwykle rozwiązano ten problem należy usunąć wszystkie deklaracje snprintf — lub vsnprintf — w kodzie użytkownika.  
  
-   **tmpnam — generuje można używać nazwy plików** w poprzednich wersjach, funkcje tmpnam — i tmpnam_s — generowane nazwy plików w folderze głównym dysku (na przykład \sd3c.). Te funkcje teraz Generowanie pliku można używać nazwy ścieżki w katalogu tymczasowym.  
  
-   **Hermetyzację plików** w poprzednich wersjach, typu pliku została całkowicie zdefiniowana w \<stdio.h >, aby było możliwe kod użytkownika uzyskać dostęp do pliku i zmodyfikować jego wewnętrzne. Biblioteki stdio — został zmieniony tak, aby ukryć szczegóły implementacji. W ramach tego pliku, zgodnie z definicją w \<stdio.h > jest teraz typ nieprzezroczyste i jej elementów członkowskich są niedostępne z poza CRT sam.  
  
-   **_outp — i _inp —** funkcje [_outp —](../c-runtime-library/outp-outpw-outpd.md), [_outpw —](../c-runtime-library/outp-outpw-outpd.md), [_outpd —](../c-runtime-library/outp-outpw-outpd.md), [_inp —](../c-runtime-library/inp-inpw-inpd.md), [_inpw —](../c-runtime-library/inp-inpw-inpd.md), i [_inpd —](../c-runtime-library/inp-inpw-inpd.md) zostały usunięte.  
  
#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h >, \<malloc.h >, a \<sys/stat.h >  
  
-   **strtof — i wcstof —** funkcji strtof — i wcstof — nie można ustawić na erange — numer błędu, gdy wartości nie można przedstawić jako wartości zmiennoprzecinkowej. Problem został rozwiązany. (Należy zauważyć, że ten błąd został specyficzne dla tych dwóch funkcji; strtod —, wcstod —, strtold i funkcje wcstold nie miała wpływu). To środowisko uruchomieniowe fundamentalne zmiany.  
  
-   **Funkcje alokacji wyrównane** w poprzednich wersjach, funkcje wyrównany alokacji (_aligned_malloc —, _aligned_offset_malloc — itp.) dyskretnie będzie akceptować żądania bloku z wyrównaniem 0. Żądana wyrównanie musi być potęgą liczby dwa, które zero nie jest. Problem został rozwiązany i żądanym wyrównaniem 0 teraz jest traktowane jako nieprawidłowy parametr. To środowisko uruchomieniowe fundamentalne zmiany.  
  
-   **Funkcje stercie** _heapadd — _heapset — i _heapused funkcje zostały usunięte. Te funkcje zostały prawidłowo, ponieważ CRT zostało zaktualizowane do używania sterty systemu Windows.  
  
-   **smallheap** opcja łącze smalheap została usunięta. Zobacz [opcje łącza](../c-runtime-library/link-options.md).  
  
#### <a name="stringh"></a>\<String.h >  
  
-   **wcstok —** podpis wcstok — funkcja został zmieniony do dopasowania, co jest wymagane przez C Standard. W poprzednich wersjach biblioteki podpis tej funkcji to:  
  
    ```cpp  
    wchar_t* wcstok(wchar_t*, wchar_t const*)  
    ```  
  
     Do śledzenia stanu połączenia, co jest wykonywane na potrzeby strtok — on używany wewnętrznie w kontekście dla każdego wątku. Funkcja ma teraz podpis wchar_t * wcstok — (wchar_t\*, wchar_t const\*, wchar_t\*\*) i wymaga obiekt wywołujący, aby przekazać kontekst jako trzeci argument funkcji.  
  
     Nowa funkcja _wcstok został dodany podpisem stare do jej obsługi ułatwiają przenoszenie. Podczas kompilowania kodu C++, dostępna jest również przeciążenia wbudowanego wcstok —, który ma podpis stary. To przeciążenie jest zadeklarowany jako przestarzały. W kodzie C możesz define_CRT_NON_CONFORMING_WCSTOK spowodować _wcstok do użycia zamiast wcstok —.  
  
#### <a name="timeh"></a>\<Time.h >  
  
-   **zegar** w poprzednich wersjach [zegara](../c-runtime-library/reference/clock.md) funkcja został wdrożony przy użyciu interfejsu API systemu Windows [GetSystemTimeAsFileTime](http://msdn.microsoft.com/library/windows/desktop/ms724397.aspx). Z tą implementacją funkcji zegara było wrażliwe na czas systemowy i nie był w związku z tym niekoniecznie monotoniczna. Funkcja zegara ma zostały reimplemented w postaci liczby [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) i jest teraz monotoniczna.  
  
-   **fstat — i _utime —** w poprzednich wersjach [_stat](../c-runtime-library/reference/stat-functions.md), [fstat —](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md), i [_utime —](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) funkcje obsługi czasu letniego niepoprawnie. Przed Visual Studio 2013 wszystkie te funkcje nieprawidłowe ustawienie godziny (czas standardowy), tak jakby były w czas letni.  
  
     W programie Visual Studio 2013 problem został rozwiązany w rodzinie _stat funkcji, ale podobne problemy w rodzin fstat — i _utime — funkcje nie zostały usunięte. Przeprowadzony problemy z powodu niespójności między funkcji. Teraz zostały ustalone rodzin fstat — i _utime — funkcji, aby teraz wszystkie te funkcje obsługi czasu letniego poprawnej i spójnej.  
  
-   **asctime —** w poprzednich wersjach [asctime —](../c-runtime-library/reference/asctime-wasctime.md) funkcja czy konsoli jednocyfrowej dni z zerem, na przykład: PT cze 06 08:00:00 2014 r. Specyfikacja wymaga, że takie dni można dopełniane przy spację, np. PT cze 6 08:00:00 2014 r. Problem został rozwiązany.  
  
-   **strftime — i wcsftime —** funkcji strftime — i wcsftime — obsługują teraz %C, %D, %e, %F, %g, %G, %h, %n, %r, %R, %t, %T, %u i %V specyfikatorów formatu. Ponadto Modyfikatory E oraz O są przeanalizować, ale ignorowane.  
  
     Specyfikator formatu %c jest określana jako tworzenie folderu "odpowiednie Data i godzina reprezentacji" dla bieżących ustawień regionalnych. W ustawieniach regionalnych C taka reprezentacja musi być taka sama jak %a %b %e %T %Y. Jest to tego samego formularza, ponieważ jest generowany przez asctime —. W poprzednich wersjach %c specyfikator formatu jest nieprawidłowo sformatowana użyciu reprezentację MM/DD/RR GG. Problem został rozwiązany.  
  
-   **timespec i TIME_UTC** \<time.h > nagłówka teraz definiuje typ timespec i funkcja timespec_get C11 Standard. Ponadto w makrze TIME_UTC do użycia z funkcją timespec_get teraz jest zdefiniowany. Jest to istotne zmiany kod, który ma dla każdego z tych definicji powodujące konflikt.  
  
-   **CLOCKS_PER_SEC** CLOCKS_PER_SEC makro rozszerza się teraz na liczbę całkowitą clock_t — typ, co jest wymagane przez języka C.  
  
####  <a name="BK_STL"></a>Standardowa biblioteka C++  
 Aby włączyć nowe optymalizacje i kontrole debugowania, implementacja standardowej biblioteki C++ w Visual Studio celowo łamie zgodność binarną między wersjami. W związku z tym gdy używana jest standardowa biblioteka C++, pliki obiektowe i biblioteki statyczne, które są kompilowane przy użyciu różnych wersji, nie mogą być mieszane w jednym pliku binarnym (EXE lub DLL), a obiekty standardowej biblioteki C++ nie mogą być przekazywane między plikami binarnymi, które są kompilowane przy użyciu różnych wersji. Takie mieszanie powoduje błędy konsolidatora dotyczące niezgodności _MSC_VER. (Elemencie _MSC_VER jest makrem, zawierający głównej wersji kompilatora — na przykład 1800 dla programu Visual Studio 2013.) Tego wyboru nie może wykryć mieszanie biblioteki DLL i nie może wykryć mieszanie, która obejmuje Visual C++ 2008 lub starszej.  
  
-   **Pliki nagłówkowe standardowej biblioteki C++** niektóre zmiany zostały wprowadzone w strukturze include w nagłówkach standardowa biblioteka C++. Nagłówki standardowa biblioteka C++ mogą zawierać siebie nawzajem w sposób nieokreślony. Ogólnie rzecz biorąc należy zapisać swój kod, aby dokładnie zawiera wszystkie nagłówki, które wymaga zgodnie z C++ standard i nie zależą od tego, która standardowa biblioteka C++ nagłówki obejmują które nagłówki standardowa biblioteka C++. Dzięki temu kod przenośny między wersjami i platform. Co najmniej dwie zmiany nagłówka w programie Visual Studio 2015 mają wpływ na kod użytkownika. Najpierw \<ciąg > nie zawiera już \<iteratora >. Drugi, \<krotki > teraz deklaruje std::array bez wraz ze wszystkimi \<tablicy >, które mogą być dzielone kodu za pomocą następujących kombinacji konstrukcji kodu: kod zawiera zmienną o nazwie "array", a masz dyrektywy using "przy użyciu przestrzeń nazw std; ", i Dołącz nagłówek standardowa biblioteka C++ (takich jak \<funkcjonalności >) zawierającej \<spójnej kolekcji >, które teraz deklaruje std::array.  
  
-   **steady_clock** \<chrono > wykonanie [steady_clock](../standard-library/steady-clock-struct.md) został zmieniony w celu spełnienia wymagań C++ Standard opanowanie i monotonicity. steady_clock teraz jest oparta na [QueryPerformanceCounter](https://msdn.microsoft.com/library/windows/desktop/ms644904.aspx) i high_resolution_clock jest teraz typedef dla steady_clock. W związku z tym w programie Visual C++ steady_clock::time_point jest teraz typedef dla chrono::time_point < steady_clock >; Jednak to nie jest zawsze w przypadku innych implementacji.  
  
-   **allocators — i const** wymaga porównania równości i nierówności alokatora akceptować argumenty const po obu stronach.  Jeśli Twoje allocators — zdefiniuj tych operatorów w następujący sposób:  
  
    ```cpp  
    bool operator==(const MyAlloc& other)  
    ```  
  
     Należy zaktualizować je, aby zadeklarować je jako elementy członkowskie const.  
  
    ```cpp  
    bool operator==(const MyAlloc& other) const  
    ```  
  
-   **elementy Const** standard C++ zawsze jest zabroniona kontenery elementów const (takich jak wektorowa\<const T > lub ustaw\<const T >). Visual C++ 2013 i starsze wersje zaakceptowane takie kontenerów. W bieżącej wersji takie nie można skompilować.  
  
-   **STD::Allocator:: deallocate** w programie Visual C++ 2013 i wcześniejszych std::allocator::deallocate(p, n) ignorowane argument przekazany do n.  Zawsze C++ standard wymaga tego n być równa wartości przekazanej jako pierwszy argument dla wywołania funkcji alokacji, który jest zwracany p. Jednak w bieżącej wersji wartość n jest sprawdzana. Kod, który przekazuje n argumentów, które różnią się od jakiego standard wymaga może ulec awarii w czasie wykonywania.  
  
-   **hash_map — i hash_set** hash_map pliki niestandardowy nagłówek i hash_set nie są używane w programie Visual Studio 2015 i zostanie usunięta w przyszłej wersji. Zamiast tego użyj unordered_map i unordered_set.  
  
-   **komparatorów i operator()** asocjacyjnej kontenery ( \<mapy > rodziny) wymaga ich komparatorów mają const można wywołać funkcji wywołania operatorów. Następujący kod w deklaracji klasy komparatora teraz nie powiedzie się do kompilacji:  
  
    ```cpp  
    bool operator()(const X& a, const X& b)  
    ```  
  
     Aby rozwiązać ten problem, zmień deklarację funkcji do:  
  
    ```cpp  
    bool operator()(const X& a, const X& b) const  
    ```  
  
-   **Wpisz cech** stare nazwy cech typu w kompilatorze ze starszej wersji standard projekt C++ zostały usunięte. Te zostały zmienione w języku C ++ 11 i C ++ 11 wartości w programie Visual Studio 2015 zostały zaktualizowane. W poniższej tabeli przedstawiono starej i nowej nazwy.  
  
    |Stara nazwa|Nowa nazwa|  
    |--------------|--------------|  
    |add_reference|add_lvalue_reference|  
    |has_default_constructor|is_default_constructible|  
    |has_copy_constructor|is_copy_constructible|  
    |has_move_constructor|is_move_constructible|  
    |has_nothrow_constructor —|is_nothrow_default_constructible —|  
    |has_nothrow_default_constructor|is_nothrow_default_constructible —|  
    |has_nothrow_copy —|is_nothrow_copy_constructible —|  
    |has_nothrow_copy_constructor|is_nothrow_copy_constructible —|  
    |has_nothrow_move_constructor|is_nothrow_move_constructible —|  
    |has_nothrow_assign —|is_nothrow_copy_assignable —|  
    |has_nothrow_copy_assign|is_nothrow_copy_assignable —|  
    |has_nothrow_move_assign|is_nothrow_move_assignable|  
    |has_trivial_constructor|is_trivially_default_constructible —|  
    |has_trivial_default_constructor —|is_trivially_default_constructible —|  
    |has_trivial_copy —|is_trivially_copy_constructible —|  
    |has_trivial_move_constructor|is_trivially_move_constructible|  
    |has_trivial_assign —|is_trivially_copy_assignable|  
    |has_trivial_move_assign|is_trivially_move_assignable|  
    |has_trivial_destructor|is_trivially_destructible|  
  
-   **zasady Launch::any i launch::sync** niestandardowe zasady launch::any i launch::sync zostały usunięte. Dla launch::any, użyj uruchamiania: asynchroniczne &#124; uruchamianie: opóźnieniem. W przypadku launch::sync Użyj launch::deferred. Zobacz [launch — wyliczenie](../standard-library/future-enums.md#launch).  
  
####  <a name="BK_MFC"></a>MFC i ATL  
  
-   **Microsoft Foundation Classes (MFC)** znajduje się już w "Typowych" Instalacja programu Visual Studio z powodu jego duży rozmiar. Aby zainstalować MFC, wybierz opcję instalacji niestandardowej w Instalatorze programu Visual Studio 2015. Jeśli masz już zainstalowany program Visual Studio 2015, należy zainstalować MFC, uruchom ponownie Instalator programu Visual Studio, wybierając opcję instalacji niestandardowej i wybierając pozycję Microsoft Foundation Classes. Można ponownie uruchomić Instalatora programu Visual Studio z apletu Programy i funkcje, lub z nośnika instalacyjnego.  
  
     Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.  
  
####  <a name="BK_ConcRT"></a>Współbieżność środowiska wykonawczego  
  
-   **YIELD — makro z Windows.h powoduje konflikt z concurrency::Context::Yield** współbieżność środowiska wykonawczego wcześniej umożliwia #undef Usuń makro Yield zapobiegania konfliktom występującym między makro wydajności zdefiniowanych w Windows.h h i concurrency::Context: : Uzyskanie funkcji. #Undef ten został usunięty, a następnie wywołać nowy niekolidujących równoważne interfejs API [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) został dodany. Aby uniknąć konfliktów z wydajnością, można zaktualizować swój kod, aby zamiast tego wywołaj funkcję YieldExecution lub przestrzenny nazwą funkcji Yield nawiasów w lokacjach wywołanie, jak w poniższym przykładzie:  
  
    ```cpp  
    (concurrency::Context::Yield)();  
    ```  
  
## <a name="compiler-conformance-improvements-in-visual-c-2015"></a>Ulepszenia kompilatora zgodność w programie Visual C++ 2015  
 Podczas uaktualniania kodu z poprzednich wersji, również mogą wystąpić błędy kompilatora, które są ze względu na zgodność usprawnienia wprowadzone w programie Visual C++ 2015. Te ulepszenia nie dzielone zgodności plików binarnych z wcześniejszych wersji programu Visual C++, ale gdy brak zostały wyemitowane przed może powodować błędy kompilatora. Aby uzyskać więcej informacji, zobacz [Visual C++ co przez nowy 2003 za pośrednictwem 2015](../porting/visual-cpp-what-s-new-2003-through-2015.md).  
  
 W programie Visual C++ 2015 trwającej ulepszenia kompilatora zgodność czasami można zmienić sposób kompilator rozumie istniejącego kodu źródłowego. W takim przypadku nowe lub inne błędy mogą wystąpić podczas kompilacji lub nawet behawioralnej różnice w kodzie, który uprzednio utworzony i z działała poprawnie.  
  
 Na szczęście tych różnic mają niewielkiego lub żadnego wpływu na większości kodu źródłowego i kiedy kodu źródłowego lub inne zmiany są potrzebne w celu rozwiązania tych różnic, poprawki są zwykle małe i proste. Dodaliśmy wiele przykładów kodu źródłowego wcześniej dopuszczalne, który może zaistnieć konieczność zmiany *(przed)* i poprawki, aby je poprawić *(po)*.  
  
 Mimo że te różnice mogą wpływać na kodu źródłowego lub pozostałych artefaktów kompilacji, nie wpływają na binarne zgodność aktualizacji do wersji Visual C++. Inne poważne rodzaju zmiany, *fundamentalne zmiany* może mieć wpływ na zgodność binarną, ale tego rodzaju podziały zgodność binarną występować tylko między główne wersje programu Visual C++. Na przykład między Visual C++ 2013 i Visual C++ 2015. Informacje dotyczące zmian podziału między Visual C++ 2013 i Visual C++ 2015 znajdują się w temacie [Visual C++ 2015 zgodność zmiany](#VC_2015).  
  
-   [Ulepszenia zgodność w programie Visual C++ 2015](#VS_RTM)  
  
-   [Ulepszenia zgodność aktualizacji 1](#VS_Update1)  
  
-   [Ulepszenia zgodność aktualizacji 2](#VS_Update2)  
  
-   [Ulepszenia zgodność aktualizacji 3](#VS_Update3)  
  
###  <a name="VS_RTM"></a>Ulepszenia zgodność w programie Visual C++ 2015  
  
-   Opcja /Zc:forScope-  
  
     Opcja kompilatora **/Zc:forScope-** jest przestarzała i zostanie usunięta w przyszłej wersji.  
  
    ```cpp  
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release  
    ```  
  
     Zazwyczaj użyto opcji w celu umożliwienia niestandardowy kod, który używa zmiennych w pętli od momentu, gdy zgodnie ze standardowego, ich powinien przeszły poza zakresem. Konieczne było tylko gdy kompilacja z opcją /Za od bez /Za, za pomocą zmiennej pętli po zakończeniu pętli zawsze jest dozwolone. Jeśli nie interesują o standardach zgodności (na przykład, jeśli kod nie jest przeznaczone do przenośnych do inne kompilatory), użytkownik może wyłączyć opcję /Za (lub ustaw właściwość Wyłącz rozszerzenia języka nie). Jeśli interesują dotyczące pisania kodu przenośnego, zgodnych ze standardami, dzięki czemu jest zgodny ze standardem przenosząc deklaracji tych zmiennych do punktu poza pętli powinien ponownego zapisywania kodu.  
  
    ```cpp  
    // C2065 expected  
    int main() {  
        // Uncomment the following line to resolve.  
        // int i;  
        for (int i = 0; i < 1; i++);  
        i = 20;   // i has already gone out of scope under /Za  
    }  
  
    ```  
  
-   **/ZG — opcja kompilatora**  
  
     Opcja kompilatora /Zg (Generuj prototypy funkcji) nie jest już dostępny. Ta opcja kompilatora wcześniej została uznana za przestarzałą.  
  
-   Nie można uruchomić testów jednostkowych z C + +/ CLI w wierszu polecenia z mstest.exe. Zamiast tego należy użyć vstest.console.exe. Zobacz [opcje wiersza polecenia VSTest.Console.exe](/devops-test-docs/test/vstest-console-exe-command-line-options).  
  
-   **Mutable — słowo kluczowe**  
  
     `mutable` Specyfikator klasy magazynu nie jest dozwolony w miejscach, w którym, wcześniej skompilowane go bez błędów. Teraz, kompilator zapewnia błąd C2071 (niedozwolona Klasa magazynu). Zgodnie z standard specyfikator modyfikowalny mogą być stosowane tylko do nazwy klasy elementy członkowskie danych, nie można zastosować do zadeklarować jako const lub statycznej nazwy i nie można zastosować do odwołań do elementów członkowskich.  
  
     Rozważmy na przykład następujący kod:  
  
    ```cpp  
    struct S   
    {  
        mutable int &r;  
    };  
  
    ```  
  
     Poprzednie wersje kompilatora Visual C++ zaakceptowane to, ale teraz kompilator zapewnia następujący błąd:  
  
    ```Output  
    error C2071: 'S::r': illegal storage class  
    ```  
  
     Aby naprawić błąd, po prostu Usuń nadmiarowe mutable — słowo kluczowe.  
  
-   **char_16_t i char32_t**  
  
     Nie można korzystać `char16_t` lub `char32_t` jako aliasów w instrukcji typedef, ponieważ te typy, teraz są traktowane jako wbudowanych. W przypadku użytkowników i autorów biblioteki do definiowania char16_t i char32_t jako aliasów uint16_t i uint32_t, odpowiednio było.  
  
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
  
     Zaktualizuj kod, Usuń deklaracje typedef i Zmień nazwę innych identyfikatorów, które powodują kolizję z tych nazw.  
  
-   **Parametry szablonu bez typu**  
  
     Niektóre kodu, który wymaga parametrów szablonu bez typu są teraz prawidłowo sprawdzane pod kątem zgodności typu podając jawne argumenty szablonu. Na przykład następujący kod skompilowany bez błędów w poprzednich wersjach programu Visual C++.  
  
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
  
     Kompilator bieżącego poprawnie zwraca błąd, ponieważ argument szablonu nie jest zgodny z typem parametru szablonu (parametr jest wskaźnik do stały element członkowski, ale funkcja f jest wartością stałą):  
  
    ```Output  
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'  
    ```  
  
     Aby rozwiązać ten błąd w kodzie, należy upewnić się, że typ argumentu szablonu jest zgodny z typem zadeklarowanym parametru szablonu.  
  
-   **__declspec(align)**  
  
     Kompilator nie będzie akceptował `__declspec(align)` na funkcje. To zawsze została zignorowana, ale teraz generuje błąd kompilatora.  
  
    ```cpp  
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations  
    ```  
  
     Aby rozwiązać ten problem, Usuń `__declspec(align)` z deklaracją funkcji. Ponieważ nie miał żadnego skutku, usuwając go nie zmian.  
  
-   **Obsługa wyjątków**  
  
     Istnieje kilka zmian do obsługi wyjątków. Po pierwsze obiekty wyjątków muszą być copyable lub przenośne. Poniższy kod skompilowany w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nie Kompiluj w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
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
  
     Problem jest Konstruktor kopiujący jest prywatny, więc nie można skopiować obiektu, ponieważ odbywa się w trakcie normalnego przebiegu Obsługa wyjątku. Dotyczy to Konstruktor kopiujący jest zadeklarowany jako `explicit`.  
  
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
  
     Aby zaktualizować kodu, upewnij się, że Konstruktor kopiujący dla obiekt wyjątku jest publiczna i nie oznaczone `explicit`.  
  
     Przechwytywanie wyjątku przez wartość wymaga również być copyable obiekt wyjątku. Poniższy kod skompilowany w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale nie Kompiluj w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
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
  
     Można rozwiązać ten problem, zmieniając typ parametru `catch` do odwołania.  
  
    ```cpp  
    catch (D& d)  
    {  
    }  
  
    ```  
  
-   **Literały ciągu następuje makra**  
  
     Kompilator obsługuje teraz literały zdefiniowanych przez użytkownika. W rezultacie następuje makra bez żadnych spacji pośredniczące literałów ciągów są interpretowane jako literały zdefiniowane przez użytkownika, które spowodują błędy lub nieoczekiwane wyniki. Na przykład w poprzednim kompilatory następujący kod powiodło:  
  
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
  
     Kompilator interpretowana to jako ciąg literału "hello" następuje makra jest rozwinięta "Brak", a następnie literałów ciągów dwóch zostały połączone w jeden. W [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], kompilator interpretuje jako literału zdefiniowanego przez użytkownika, ale ponieważ nie ma żadnych pasujących zdefiniowane przez użytkownika literału _x zdefiniowane, zawiera błąd.  
  
    ```Output  
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found  
    note: Did you forget a space between the string literal and the prefix of the following string literal?  
    ```  
  
     Aby rozwiązać ten problem, Dodaj odstęp między literałem ciągu i makra.  
  
-   **Literały ciągu sąsiadujących ze sobą**  
  
     Podobnie do poprzedniego, z powodu zmiany podczas analizy ciągu, literałów ciągów sąsiadujących ze sobą (albo literałów ciągów znaków szerokości lub wąskie) bez żadnych spacji zostały interpretowane jako pojedynczy ciąg połączonych w poprzednich wersjach Visaul C++. W [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], teraz należy dodać odstępu między dwa ciągi. Na przykład można zmienić następujący kod:  
  
    ```cpp  
    char * str = "abc""def";  
    ```  
  
     Po prostu Dodaj odstęp między dwa ciągi.  
  
    ```cpp  
    char * str = "abc" "def";  
    ```  
  
-   **Umieszczania nowych i delete**  
  
     Dokonano zmian dla operatora delete w celu dostosowania do zgodność z języka C ++ 14 standardowa. Szczegółowe informacje o zmianie standardów można znaleźć w folderze [cofania alokacji o rozmiarze w języku C++](http://isocpp.org/files/papers/n3778.html). Zmiany dodać formę operatora delete globalny, który przyjmuje parametr rozmiaru. Istotne zmiany jest, że jeśli zostały wcześniej za pomocą operatora delete o tej samej sygnaturze (odpowiadającą operatora new umieszczania), zostanie wyświetlony błąd kompilatora (C2956, co następuje w momencie, gdzie nowe umieszczania są używane, ponieważ to jest operator delete pozycji w kodzie, w którym kompilator podejmie próbę identyfikacji odpowiadającym odpowiednią).  
  
     Funkcja `void operator delete(void *, size_t)` został umieszczania operatora delete, odpowiadające nowej funkcji umieszczania "void \* nowy operator (size_t, size_t)" w języku C ++ 11. Z języka C ++ 14 dezalokacji rozmiarze, ta funkcja delete jest teraz *funkcja dezalokacji zwykle* (operator delete globalne). Standard wymaga użycia nowego położenia wyszukuje odpowiedniej funkcji usuwania, znajduje się funkcja dezalokacji zwykle program źle sformułowane.  
  
     Na przykład załóżmy, że kod definiuje zarówno nowego położenia i usuwania umieszczania:  
  
    ```cpp  
    void * operator new(std::size_t, std::size_t);  
    void operator delete(void*, std::size_t) noexcept;  
  
    ```  
  
     Wystąpił problem z powodu dopasowania w podpisach funkcja między umieszczania operatora delete, które zdefiniowany przez użytkownika, a nowy operator delete o rozmiarze globalnych. Należy rozważyć, czy można użyć innego typu niż size_t do dowolnego umieszczania nowych i delete — operatory.  Należy pamiętać, że typ size_t typedef zależne od kompilatora; jest typedef dla unsigned int w programie Visual C++. Dobrym rozwiązaniem jest używany typ wyliczeniowy takich jak ta:  
  
    ```cpp  
    enum class my_type : size_t {};  
  
    ```  
  
     Zmień definicja umieszczania nowe, a następnie, Usuń, aby użyć tego typu jako drugi argument zamiast size_t. Należy również zaktualizować wywołania do umieszczenia nowego przekazać nowy typ (na przykład za pomocą `static_cast<my_type>` do przekonwertowania z wartością całkowitą) i nowych aktualizacji definicji i Usuń można rzutować typu Liczba całkowita. Nie trzeba używać wyliczenia dla tej; Typ klasy z elementem członkowskim size_t również będzie działać.  
  
     Alternatywnego rozwiązania jest, że można całkowicie wyeliminować umieszczania nowej. Jeśli kod używa umieszczania nowej implementacji puli pamięci, gdy argument umieszczania rozmiar jest obiekt przydzielony lub usunięty, to funkcja cofania alokacji o rozmiarze może być swoim własnym kodem puli pamięci niestandardowych zastąpienie i można pozbyć się z umieszczanie funkcje i użyć własnych operatora delete dwuargumentowej zamiast funkcji umieszczania.  
  
     Jeśli nie chcesz natychmiast zaktualizować kodu, możesz przywrócić poprzednie działanie przy użyciu opcji kompilatora /Zc:sizedDealloc-. Jeśli używasz tej opcji, funkcje delete dwuargumentowej nie istnieje i nie powoduje konfliktu z operatorem delete umieszczania.  
  
-   **Elementy członkowskie danych Unii**  
  
     Elementy członkowskie danych Unii nie mogą mieć typów referencyjnych. Poniższy kod skompilowany pomyślnie w [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], ale powoduje błąd w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
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
  
     Poprzedni kod tworzy następujące błędy:  
  
    ```Output  
  
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type  
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type  
  
    ```  
  
     Aby rozwiązać ten problem, zmień typy odwołań do wskaźnika lub wartość. Zmiana typu do wskaźnika wymaga wprowadzenia zmian w kodzie, który używa pola union. Zmiana kodu do wartości zmieniłby danych przechowywanych w Unii, który ma wpływ na inne pola, ponieważ pola w Unii mieć tej samej pamięci. W zależności od rozmiaru wartość może on również zmienić rozmiar Unii.  
  
-   Związki anonimowe są teraz więcej zgodność ze standardem. Poprzednie wersje kompilatora generowane jawny Konstruktor i destruktor dla elementu związki anonimowe. Są one usuwane z [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)].  
  
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
  
     Poprzedni kod generuje następujący błąd w [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)]:  
  
    ```cpp  
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function  
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here  
  
    ```  
  
     Aby rozwiązać ten problem, należy podać własne definicje Konstruktor i/lub destruktor.  
  
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
  
-   **Unie z struktury anonimowe**  
  
     Aby można było zgodne ze standardem, zachowania w czasie wykonywania została zmieniona dla elementów członkowskich struktury anonimowe w Unii. Konstruktor elementy członkowskie struktury anonimowe w Unii jest nie już wywoływany niejawnie po utworzeniu takiej Unii. Ponadto destruktor dla elementu elementy członkowskie struktury anonimowe w Unii jest nie już wywoływany niejawnie przypadku Unii wykracza poza zakres. Rozważmy następujący kod, w którym Unii U zawiera strukturę anonimowe, zawierający element, który jest strukturą nazwanego S, która ma destruktor.  
  
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
  
     W [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)], Konstruktor S jest wywoływana po utworzeniu Unii, a destruktor dla elementu S jest wywoływane, gdy jest wyczyszczone stosu dla funkcji f. Jednak [!INCLUDE[cpp_dev14_long](../porting/includes/cpp_dev14_long_md.md)], Konstruktor i destruktor nie są wywoływane. Kompilator wyświetla ostrzeżenie o tej zmianie zachowanie.  
  
    ```Output  
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called  
    ```  
  
     Aby przywrócić oryginalne zachowanie, nadaj struktury anonimowe nazwę. Zachowanie środowiska uruchomieniowego struktur nieanonimowych jest taki sam, niezależnie od wersji kompilatora.  
  
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
  
     Alternatywnie spróbuj przenieść kod Konstruktor i destruktor do nowych funkcji, a następnie dodaj wywołań funkcji z Konstruktor i destruktor dla Unii.  
  
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
  
-   **Szablon rozwiązania**  
  
     Zmiany zostały wprowadzone do rozpoznawania nazw dla szablonów. W języku C++, rozważając kandydatów do rozpoznawania nazw można go sprawę, że jedną lub więcej nazw pod uwagę jako potencjalny dopasowań powoduje utworzenie wystąpienia szablonu jest nieprawidłowa. Te nieprawidłowe wystąpień nie powodują zwykle błędy kompilatora, zasady, znany jako techniki SFINAE (podstawienie niepowodzenia nie błąd jest).  
  
     Teraz Jeśli techniki SFINAE wymaga kompilatora, można utworzyć wystąpienia specjalizacji szablonu klasy, wszystkie błędy w trakcie tego procesu są błędy kompilatora. W poprzednich wersjach kompilator będzie ignorować takie błędy. Rozważmy na przykład następujący kod:  
  
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
  
     Jeśli kompilacja z kompilatorem bieżący, otrzymasz następujący błąd:  
  
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
  
     Wynika to z faktu w punkcie pierwsze wywołanie is_base_of — klasa będzie "jeszcze nie został zdefiniowany.  
  
     W takim przypadku będzie nie należy używać tych cech typu w kompilatorze, dopóki ta klasa została zdefiniowana. Jeśli przeniesiesz definicje B i D na początku pliku kodu błędu, zostaje rozwiązany. Jeśli definicje znajdują się w pliki nagłówkowe, sprawdź, aby pliki nagłówkowe upewnić się, że wszystkie definicje klas są kompilowane przed problematyczne szablony są używane instrukcje include.  
  
-   **Kopiowanie konstruktorów**  
  
     W obu [!INCLUDE[vs_dev12](../atl-mfc-shared/includes/vs_dev12_md.md)] i programu Visual Studio 2015, kompilator generuje Konstruktor kopiujący dla klasy, jeśli tej klasy ma Konstruktor przenoszący zdefiniowane przez użytkownika, ale nie Konstruktor kopiujący zdefiniowane przez użytkownika. W Dev14 ten Konstruktor kopiujący niejawnie wygenerowany jest również oznaczone jako "= delete".  

<!--From here to VS_Update1 added 04/21/2017-->

-   **main jest zadeklarowany jako zewnętrzny "C" wymaga teraz zwracanego typu.**  

Poniższy kod tworzy teraz C4430. 
```cpp
extern "C" __cdecl main(){} // C4430
```
Aby naprawić błąd, Dodaj typ zwracany:
```cpp
extern "C" int __cdecl main(){} // OK
```

 -   **Właściwość TypeName nie jest dozwolona w inicjator elementu członkowskiego**  

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
Aby naprawić błąd, należy usunąć `typename` z inicjatora:
```cpp
S1() : T::type() // OK
...
```

-   **Klasa magazynu na jawne specjalizacje jest ignorowana.** 

W poniższym kodzie Specyfikator klasy magazynu statycznego jest ignorowany 
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

-   **Stała używane w static_assert wewnątrz szablonu klasy zawsze kończy się niepowodzeniem.**  

Poniższy kod powoduje static_assert zawsze niepowodzenie:
```cpp
template <size_t some_value>
struct S1
{
    static_assert(false, "default not valid"); // always invoked

};

//other partial specializations here
```

Aby obejść ten problem, zawijanie wartość w struktury:
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

-   **Reguły wymuszane dla deklaracji do przodu. (Dotyczy tylko C.)**  

Poniższy kod tworzy teraz C2065:
```cpp
struct token_s;
typedef int BOOL;
typedef int INT;



typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
```

Aby rozwiązać problem, Dodaj odpowiednie deklaracje do przodu:

```cpp
struct token_s;
typedef int BOOL;
typedef int INT;

// forward declarations:
typedef struct token_s TOKEN; 
typedef TOKEN *PTOKEN;

typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
```

-   **Bardziej spójny wymuszania typów wskaźnika funkcji**  

Poniższy kod tworzy teraz C2197:

```cpp
typedef int(*F1)(int);
typedef int(*F2)(int, int);

void func(F1 f, int v1, int v2)
{
    f(v1, v2); // C2197
}
```

-   **Niejednoznaczne wywołania funkcji przeciążenia**  

Poniższy kod tworzy teraz C266: "N::bind": niejednoznaczne wywołanie przeciążonej funkcji
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

Aby naprawić błąd, można pełnej kwalifikacji wywołania do powiązania: N::bind(...). Jednak jeśli ta zmiana jest manifestu do niezadeklarowanego identyfikatora (C2065), następnie może być ustalenie to z deklaracją "przy użyciu".

Ten wzorzec jest często wykonywane z comptr — a innymi typami danych w Microsoft::wrl — przestrzeń nazw.

-   **Napraw nieprawidłowy adres**  

Poniższy kod tworzy teraz C2440: "=": nie można przekonwertować z "typ *" do "type". Aby naprawić błąd, Zmień & (typ) na (typ) i (& f()) do (f()).
 
```cpp
\\ C
typedef void (*type)(void);
 
void f(int i, type p);
void g(int);
void h(void)
{
    f(0, &(type)g);
}
 
\\ C++
typedef void(*type)(void);
 
type f();
 
void g(type);
 
void h()
{
    g(&f());
}

```

-   **Literał ciągu jest tablicą stałej**  

Poniższy kod tworzy teraz C2664: "void f (void *)": nie można przekonwertować argumentu 1 z "const char (*) [2]" do "void *"
```cpp
void f(void *);
 
void h(void)
{
    f(&__FUNCTION__); 
    void *p = &"";
}
```

Aby naprawić błąd, Zmień typ parametru funkcji "const void *", w przeciwnym razie należy zmienić treść h w następujący sposób:

```cpp
void h(void)
{
    char name[] = __FUNCTION__;
    f( name); 
    void *p = &"";
}

```

-   **C ++ 11 UDL ciągów znaków**  

Poniższy kod tworzy teraz błąd C3688: nieprawidłowy sufiks literału "L"; operator literału lub szablonu operatora literału "operator" "L" nie znaleziono


```cpp
#define MACRO

#define STRCAT(x, y) x\#\#y

int main(){

    auto *val1 = L"string"MACRO;
    auto *val2 = L"hello "L"world";

    std::cout << STRCAT(L"hi ", L"there");
}
```
Aby naprawić błąd, Zmień kod to:

```cpp
#define MACRO

// Remove ##. Strings are automatically
// concatenated so they are not needed
#define STRCAT(x, y) x y

int main(){
    //Add space after closing quote
    auto *val1 = L"string" MACRO;
    auto *val2 = L"hello " L"world";

    std::cout << STRCAT(L"hi ", L"there");
}

```
W powyższym przykładzie `MACRO` jest już być analizowana jako dwa tokeny (ciąg następuje makr).  Teraz jest analizowany jako pojedynczy UDL tokenu.  To samo dotyczy L "" L"", który został wcześniej analizowana jako L"" i L "", a teraz jest analizowana jako L "" L i "".

Reguły łączenia ciągu również zostały przeniesione do zgodności ze standardem, co oznacza, że jest odpowiednikiem L "ab" L "a" "b". Poprzednie wersje programu Visual Studio nie zaakceptowała konkatenacji ciągów szerokość znaków.


-   **Znak usunąć pusty c ++ 11**  

Poniższy kod tworzy teraz C2137 błąd: stała znakowa pusty

```cpp
bool check(wchar_t c){
    return c == L''; //implicit null character
}
```

Aby naprawić błąd, Zmień kod to:

```cpp
bool check(wchar_t c){
    return c == L'\0';
}
```

-   **Nie można przechwycić wyjątków MFC według wartości, ponieważ nie są one copyable**  

Następujący kod w aplikacji MFC teraz powoduje błąd C2316: miał ": nie można przechwycić elementu, ponieważ destruktor i/lub Konstruktor kopiujący są niedostępne lub zostały usunięte

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
Aby naprawić kod, można zmienić blok catch do "catch (const D &)", ale lepszym rozwiązaniem jest zwykle używanie makr MFC TRY/CATCH.

-   **alignof jest teraz słowo kluczowe**  

Poniższy kod tworzy teraz błąd C2332: "class": Brak nazwy tagu. Aby naprawić kod musisz zmienić nazwę klasy lub, jeśli klasa jest wykonywane tego samego pracy jako alignof, po prostu zastąpić klasy słowo kluczowe new.
```cpp
class alignof{}
```

-   **constexpr jest teraz słowo kluczowe**  

Poniższy kod tworzy teraz błąd C2059: błąd składniowy: ")". Aby naprawić kod, należy zmienić nazwę funkcji ani nazwy zmiennych, które są określane jako "constexpr". 
```cpp
int constexpr() {return 1;}
```

-   **Typy ruchome nie może być wartością stałą**  

Gdy funkcja zwraca typ, który ma zostać przeniesiona, jej typu zwracanego nie powinna być stała.

-   **Usunięto kopiowanie konstruktorów**  

Poniższy kod tworzy teraz w C2280:: S(S &&) ": próba odwania usunięta funkcja do:

```cpp
struct S{
    S(int, int);
    S(const S&) = delete;
    S(S&&) = delete;
};

S s2 = S(2, 3); //C2280
```
Aby naprawić błąd, należy użyć bezpośredniego inicjowania dla S2:
```cpp
struct S{
    S(int, int);
    S(const S&) = delete;
    S(S&&) = delete;
};

S s2 = {2,3}; //OK
```

-   **Konwersja wskaźnika funkcji generowany tylko, gdy nie przechwytywania lambda**  

Poniższy kod tworzy C2664 w programie Visual Studio 2015. 

```cpp
void func(int(*)(int)) {}

int main() {

    func([=](int val) { return val; });
}
```
Aby naprawić błąd, należy usunąć `=` na liście przechwytywania.

-   **Niejednoznaczne wywołania obejmujące operatory konwersji**  

Poniższy kod tworzy teraz błąd C2440: "rzutowanie typu": nie można przekonwertować z "S2" na "S1":

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
Aby naprawić błąd, jawnie wywołać operatora konwersji:

```cpp
void f(S2 s2)
{
    //Explicitly call the conversion operator
    s2.operator S1();
    // Or
    S1((int)s2);
}

```

Poniższy kod tworzy teraz błąd C2593: "operator =" jest niejednoznaczny:

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
Aby naprawić błąd, jawnie wywołać operatora konwersji:
```cpp
void f(S1 *p, S2 s)
{
       *p = s.operator S1&();
}
```

-   **Usuń nieprawidłowy kopiowania inicjowania na inicjowanie elementu członkowskiego danych niestatycznych (NSDMI)**  

Poniższy kod tworzy teraz błąd C2664: "S1::S1(S1 &&)": nie można przekonwertować argumentu 1 z "bool" na "const S1 &":
```cpp
struct S1 {
    explicit S1(bool);
};

struct S2 {
    S1 s2 = true; // error
};
```
Aby naprawić błąd, należy użyć bezpośredniego inicjowania:
```cpp
struct S2 {
S1 s1{true}; // OK
};
```

-   **Uzyskiwanie dostępu do konstruktorów wewnątrz decltype — instrukcje**  

Poniższy kod tworzy teraz C2248: "S::S": nie można zadeklarować dostępu prywatnego elementu członkowskiego, w klasy ":
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
Aby naprawić błąd, należy dodać deklaracji elementu zaprzyjaźnionego dla S2 w S:
```cpp
class S {
    S();
    friend class S2; // Make S2 a friend
public:
    int i;
};
```

-   **Domyślne ctor lambda niejawnie zostanie usunięta.**  

Poniższy kod tworzy teraz błąd C3497: nie można skonstruować wystąpienia lambdy:
```cpp
void func(){
    auto lambda = [](){};    
 
    decltype(lambda) other;
}
```
Aby naprawić błąd, należy usunąć potrzebę do wywołania konstruktora domyślnego. Jeśli wyrażenie lambda nie przechwytywania niczego następnie go mogą być rzutowane na wskaźnik funkcji.

-   **Wyrażenia lambda za pomocą operatora przypisania usunięte**  

Poniższy kod tworzy teraz błąd C2280:

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
Aby naprawić błąd, Zamień lambda klasy obiekt lub usuń konieczność użycia operatora przypisania.

-   **Próba przeniesienia z konstruktorami kopiowania usuniętego obiektu**  

Poniższy kod tworzy teraz błąd C2280: "ruchoma:: moveable(const moveable &)": próba odwołania usunięta funkcja
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
Aby naprawić błąd, należy użyć std::move:
```cpp
S(moveable && m) :
    m_m(std::move(m))
```
-   **Klasy lokalnej nie może odwoływać się inne klasy lokalnej zdefiniowaną w dalszej części tej samej funkcji**  

Poniższy kod tworzy teraz błąd C2079: w "używa niezdefiniowana main::S2" struct"
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
Aby naprawić błąd, Przenieś w górę definicji S2:
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

-   **Nie można wywołać chronionych ctor podstawowej w treści pochodne ctor.**  

Poniższy kod tworzy teraz błąd C2248: "S1::S1": nie można uzyskać dostępu do chronionego członka zadeklarowana w klasie "S1"
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
Aby naprawić błąd, w S2 Usuń wywołanie S1() z konstruktora i w razie potrzeby umieść ją w innej funkcji.

-   **{} Zapobiega konwersji na wskaźnik**  

Poniższy kod tworzy teraz C2439 "S::p": nie można zainicjować elementu członkowskiego   
```cpp
struct S {
    S() : p({ 0 }) {}
    void *p;
};
```
Aby naprawić błąd, Usuń nawiasy z wokół 0 w przeciwnym razie użyj `nullptr` zamiast tego, jak pokazano w poniższym przykładzie:
```cpp
struct S {
    S() : p(nullptr) {}
    void *p;
};
```

-   **Nieprawidłowe makra definicji i użycia za pomocą nawiasów**  

Poniższy przykład tworzy teraz błąd C2008: ';': nieoczekiwany w definicji makra
```cpp
#define A; //cause of error

struct S {
    A(); // error
};
```
Aby rozwiązać problem, zmień pierwszego wiersza do`#define A();`

Poniższy kod tworzy błąd C2059: błąd składniowy: ")"
```cpp

//notice the space after 'A'
#define A () ;

struct S {
    A();
};
```
Aby naprawić kod Usuń odstęp między A i ().

Poniższy kod tworzy błąd C2091: funkcja zwraca funkcję:

```cpp

#define DECLARE void f()

struct S {
    DECLARE();
};
```
Aby naprawić błąd, należy usunąć nawiasy po DECLARE w S: `DECLARE;`.

Poniższy kod tworzy błąd C2062: typ "int" Nieoczekiwany

```cpp
#define A (int)

struct S {
    A a;
};
```
Aby rozwiązać ten problem, należy zdefiniować A następująco:
```cpp
#define A int
```

-   **Bardzo parens w deklaracjach**  

Poniższy kod tworzy błąd C2062: typ "int" Nieoczekiwany
```cpp

struct S {
    int i;
    (int)j;
};
```
Aby naprawić błąd, należy usunąć parens z `j`. Jeśli parens są wymagane dla uzyskania przejrzystości, a następnie użyj typem typedef.

-   **Konstruktory generowane przez kompilator i __declspec(novtable)**  

W programie Visual Studio 2015 jest zwiększone prawdopodobieństwo, że wbudowany generowane przez kompilator konstruktorów klas abstrakcyjnych z wirtualnymi klasami podstawowymi może narazić niepoprawne użycie __declspec(novtable) w połączeniu z __declspec(dllimport).

-   **Auto wymaga jednego wyrażenia w Inicjalizacja listy bezpośrednio** poniższy kod tworzy teraz błąd C3518: "testPositions": w kontekście Inicjalizacja listy bezpośrednio typu "Auto" można określić tylko na podstawie pojedynczego wyrażenia inicjatora

```cpp
auto testPositions{
    std::tuple<int, int>{13, 33},
    std::tuple<int, int>{-23, -48},
    std::tuple<int, int>{38, -12},
    std::tuple<int, int>{-21, 17}
};
```
Aby naprawić błąd, jedną z możliwości jest zainicjowanie testPositions w następujący sposób:

```cpp
std::tuple<int, int> testPositions[]{
    std::tuple<int, int>{13, 33},
    std::tuple<int, int>{-23, -48},
    std::tuple<int, int>{38, -12},
    std::tuple<int, int>{-21, 17}
};
```

-   **Sprawdzanie typów a wskaźniki do typów is_convertible —**  

Poniższy kod powoduje teraz asercja statyczna się niepowodzeniem. 

```cpp
struct B1 {
private:
    B1(const B1 &);
};
struct B2 : public B1 {};
struct D : public B2 {};

static_assert(std::is_convertible<D, B2>::value, "fail");
```
Aby naprawić błąd, należy zmienić static_assert, tak aby porównuje wskaźniki do D i B2:

```cpp
static_assert(std::is_convertible<D*, B2*>::value, "fail");
```

-   **deklaracje declspec(novtable) muszą być zgodne**  

deklaracje declspec musi być spójna we wszystkich bibliotek. Poniższy kod spowodują teraz wygenerowanie naruszenia reguły jednej definicji (ODR):

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


  
###  <a name="VS_Update1"></a>Ulepszenia zgodność aktualizacji 1  
  
-   **Prywatne wirtualne klasy podstawowe i pośredniego dziedziczenia**  
  
     Poprzednie wersje kompilatora dozwolone klasy pochodnej w celu wywołania funkcji Członkowskich jego *pośrednio pochodzi* `private virtual` klasy podstawowej. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator nie akceptuje kod napisany w ten sposób i w związku z tym problemów błąd kompilatora C2280.  
  
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
  
     - lub -  
  
    ```cpp  
    class base;  // as above  
  
    class middle : private virtual base {};  
    class top : public virtual middle, private virtual bottom {};  
  
    void destroy(top *p)  
    {  
        delete p;  
    }  
  
    ```  
  
-   **Przeciążony operator new ani operator delete**  
  
     Poprzednie wersje kompilatora dozwolone niebędący elementem członkowskim `operator new` i niebędący elementem członkowskim `operator delete` być zadeklarowany jako statyczny i można zadeklarować w przestrzeni nazw innej niż globalna przestrzeń nazw.  To zachowanie starego utworzone ryzyko, że program nie może wywołać `new` lub `delete` implementacji operator, który przeznaczony programistę, co powoduje zachowanie dyskretnej zły środowiska wykonawczego. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C2323 zamiast tego.  
  
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
  
     Ponadto mimo że kompilator nie zapewnia określonych diagnostyczne, nowy operator wbudowanego jest uważany za źle sformułowane.  
  
-   **Wywołanie "operator *typu*()" (konwersja zdefiniowana przez użytkownika) dla typów innych niż klasa**  
  
     Poprzednie wersje kompilatora dozwolone "operator *typu*() ' ma być wywoływana dla typów innych niż klasa podczas w trybie dyskretnym zostanie on zignorowany. To zachowanie starego utworzony ryzyko generowania kodu zły dyskretnej spowodować nieprzewidywalne zachowanie. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C2228 zamiast tego.  
  
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
  
-   **Nadmiarowe typename w specyfikatorze specyfikatorze typu**  
  
     Poprzednie wersje kompilatora dozwolone `typename` w specyfikatorze typu rozwinięciem; kod napisany w ten sposób jest semantycznie nieprawidłowy. Kompilator nie akceptuje kod napisany w ten sposób i generuje błąd kompilatora C3406 zamiast tego.  
  
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
  
-   **Wnioskowanie typów tablic z listy inicjatora**  
  
     Poprzednie wersje kompilatora nie obsługuje wnioskowanie typów tablic z listy inicjatorów. Kompilator obsługuje teraz ten formularz wnioskowanie typu i, w związku z tym wywołań szablonów funkcji przy użyciu listy inicjatorów teraz może być niejednoznaczna lub innego przeciążenia może wybrany niż w poprzednich wersjach kompilatora. Aby rozwiązać te problemy, program teraz należy jawnie określić zamierzony przez programistę przeciążenia.  
  
     Gdy to nowe zachowanie powoduje Rozpoznanie przeciążenia wziąć pod uwagę dodatkowe kandydujących, który jest równie candidate historycznych, wywołanie staje się niejednoznaczne i kompilator generuje błąd kompilatora C2668 w związku z tym.  
  
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
  
     Gdy Rozpoznanie przeciążenia wziąć pod uwagę dodatkowe kandydujących, będący lepszym dopasowaniem niż candidate historycznych, wywołanie jest rozpoznawany jako jednoznacznie candidate nowe, powoduje to nowe zachowanie powoduje zmianę zachowania programu prawdopodobnie różni się od programista przeznaczone.  
  
     Przykład 2: zmiana Rozpoznanie przeciążenia (przed)  
  
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
  
     Przykład 2: zmiana Rozpoznanie przeciążenia (po)  
  
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
  
-   **Przywracanie ostrzeżenia instrukcji switch**  
  
     Poprzedni wersji kompilatora usunięte uprzednio istniejące ostrzeżenia dotyczące `switch` instrukcje; te ostrzeżenia zostały przywrócone. Kompilator generuje teraz przywróconej ostrzeżenia, a powiązane z szczególnych przypadkach (w tym przypadku domyślnego) są teraz wyświetlane ostrzeżenia na wiersz zawierający w przypadku ataku, a nie w ostatnim wierszu instrukcji switch. W związku z tym teraz wydawania tych ostrzeżeń w wierszach innego niż w przeszłości, ostrzeżenia poprzednio pominąć przy użyciu `#pragma warning(disable:####)` nie może zostać pominięta, zgodnie z założeniami. Aby pominąć te ostrzeżenia, zgodnie z założeniami, może być konieczne przenieść `#pragma warning(disable:####)` dyrektywy do wiersza powyżej pierwszym przypadku potencjalnie naruszeń. Poniżej przedstawiono przywróconej ostrzeżenia.  
  
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
  
     Przykłady przywróconej ostrzeżenia znajdują się w dokumentacji.  
  
-   **#include: użycie specyfikatora katalogu nadrzędnego '..' w pathname** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora nie wykrył użycie specyfikatora katalogu nadrzędnego '..' w nazwie ścieżki `#include` dyrektywy. Kod napisany w ten sposób ma zwykle obejmują nagłówki, które istnieją poza projektem za pomocą nieprawidłowo ścieżek względnych projektu. To zachowanie starego utworzony ryzyko, że program można kompilować przez dołączenie pliku źródłowego innego niż programisty przeznaczone lub że nie jest przenoszony do innego środowiska kompilacji tych ścieżek względnych. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C4464, jeśli włączone.  
  
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
  
     Ponadto, mimo że kompilator nie daje określonych diagnostyki, również zaleca się specyfikator katalogu nadrzędnego ".." Uwaga należy określić katalogi dołączenia projektu.  
  
-   **#pragma optimize() rozciąga się poza koniec pliku nagłówka** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora nie wykrył zmiany ustawień flagi optymalizacji, które escape uwzględnionych w jednostce tłumaczenia pliku nagłówka. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C4426 w lokalizacji naruszeń `#include`, jeśli jest włączona. To ostrzeżenie zostanie wyświetlone tylko, jeśli konflikt zmian z flagi optymalizacji przez kompilator argumenty wiersza polecenia.  
  
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
  
-   **Niezgodne #pragma warning(push)** i **#pragma warning(pop)** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora nie wykrył `#pragma warning(push)` stan zmieni się łączyć się z `#pragma warning(pop)` stanu zmian w pliku innego źródła, które rzadko są przeznaczone. To zachowanie starego utworzone zagrożenie program będzie można skompilować z innym zestawem ostrzeżenia włączone niż programisty przeznaczone, prawdopodobnie co powoduje zachowanie dyskretnej zły środowiska wykonawczego. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C5031 w lokalizacji dopasowywania `#pragma warning(pop)`, jeśli jest włączona. To ostrzeżenie obejmuje uwagi odwołujące się do lokalizacji odpowiedniego #pragma warning(push).  
  
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
  
     Chociaż jest to rzadko, kod napisany w ten sposób jest czasami zamierzone. Kod napisany w ten sposób jest czułe na zmiany `#include` kolejność; Jeśli to możliwe, firma Microsoft zaleca, aby pliki kodu źródłowego Zarządzanie stan ostrzegawczy w sposób niezależny.  
  
-   **Niedopasowane #pragma warning(push)** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora nie wykrył niedopasowane `#pragma warning(push)` zmiany na końcu jednostce tłumaczenia stanów. Kompilator teraz wykrywa i powiadamia programistę kod napisany w ten sposób i wystawia opcjonalne kompilatora ostrzeżenie C5032 w lokalizacji niedopasowane #pragma warning(push), jeśli włączone. To ostrzeżenie zostanie wyświetlone tylko, jeśli nie ma żadnych błędów kompilacji w jednostce tłumaczenia.  
  
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
  
-   **Może zostać wygenerowany dodatkowych ostrzeżeń wyniku śledzenia stanu ostrzeżenia #pragma ulepszone**  
  
     Poprzednie wersje kompilatora śledzone ostrzeżenia #pragma zmian stanu niewystarczająco również do wystawienia przeznaczone wszystkie ostrzeżenia. To zachowanie utworzony ryzyka to pewność, że ostrzeżenia będzie efektywnie pomijane w sytuacjach innych niż programisty przeznaczone. Kompilator teraz śledzi stan ostrzeżenia #pragma bardziej niezawodnie — szczególnie odnoszących się do zmian stanu ostrzeżenia #pragma wewnątrz szablonów — i opcjonalnie wystawia nowe ostrzeżenia C5031 i C5032, które mają pomóc programisty zlokalizować niezamierzone zastosowań `#pragma warning(push)` i `#pragma warning(pop)`.  
  
     Wyniku ulepszone #pragma zmian stanu śledzenia, ostrzeżenia wcześniej niepoprawnie pominięte lub ostrzeżenia dotyczące problemów, które wcześniej misdiagnosed mogą teraz być ostrzeżenie.  
  
-   **Ulepszenia identyfikacji nieosiągalny kod**  
  
     Standardowa biblioteka C++ zmiany i ulepszona możliwość wywołania funkcji wbudowanej w porównaniu z poprzednimi wersjami kompilatora mogą zezwalać kompilator, aby udowodnić, że niektóre kodu jest nieosiągalny. To nowe zachowanie może spowodować nowych i innych często wydane wystąpień ostrzeżenie C4720.  
  
    ```Output  
    warning C4720: unreachable code  
    ```  
  
     W wielu przypadkach to ostrzeżenie może być wystawiane tylko podczas kompilowania z włączonymi optymalizacjami, od optymalizacji mogą wbudowanego więcej wywołania funkcji, wyeliminować nadmiarowy kod lub w przeciwnym razie była możliwość określenia, że niektóre kod jest nieosiągalny. Zaobserwowano, że nowe wystąpienia ostrzeżenia C4720 często wystąpiły w blokach try/catch, szczególnie w związku z korzystaniem z [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True).  
  
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
  
###  <a name="VS_Update2"></a>Ulepszenia zgodność aktualizacji 2  
  
-   **Dodatkowych ostrzeżeń i błędów może zostać utworzony w wyniku częściowej obsługi techniki SFINAE wyrażeń**  
  
     Poprzednie wersje kompilatora nie jest przetwarzany niektóre rodzaje wyrażeń wewnątrz `decltype` specyfikatory ze względu na brak obsługi techniki SFINAE wyrażeń. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator teraz analizuje tych wyrażeń i ma częściowej obsługi techniki SFINAE wyrażeń, z powodu trwającej zgodność ulepszenia. W związku z tym kompilator generuje teraz ostrzeżenia i błędy znalezione w wyrażeniach, że poprzednie wersje kompilatora nie jest przetwarzany.  
  
     Gdy to nowe zachowanie analizuje `decltype` wyrażenie zawiera typ, którego nie ma jeszcze zadeklarowana, kompilator generuje błąd kompilatora C2039 w związku z tym.  
  
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
  
     Gdy to nowe zachowanie analizuje `decltype` wyrażenie, które nie ma potrzeby stosowania `typename` — słowo kluczowe, aby określić, że typem, kompilator jest zależna nazwa generuje ostrzeżenie C4346 wraz z błąd kompilatora C2923 kompilatora.  
  
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
  
-   `volatile`**zmienne Członkowskie zapobiec niejawnie zdefiniowanych konstruktorów i operatory przypisania**  
  
     Poprzednie wersje kompilatora dozwolone klasy, która ma `volatile` skopiowania/przeniesienia konstruktorów zmienne Członkowskie mają domyślne i domyślne operatory przypisania kopiowania/przenoszenia generowane automatycznie. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. Kompilator uwzględnia teraz klasę, która ma zmiennych Członkowskich volatile nieuproszczony konstrukcji i operatory przypisania co zapobiega domyślnej implementacji tych operatorów są generowane automatycznie.  Jeśli taka klasa jest elementem członkowskim Unii (lub anonimowego związku wewnątrz klasy), konstruktorach kopiowania/przenoszenia i operatory przypisania skopiowania/przeniesienia Unii (lub klasy zawierającej Unii unonymous) będzie można niejawnie zdefiniowany jako usunięty. Podjęto próbę utworzenia lub skopiuj Unii (lub klasa zawierająca anonimowa Unia) bez jawnie definiując je w związku z tym jest błąd i błąd kompilatora problemów kompilatora C2280.  
  
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
  
-   **Statyczne funkcje Członkowskie nie obsługują kwalifikatorów cv.**  
  
     Poprzednie wersje programu Visual C++ 2015 dozwolone statycznych funkcji Członkowskich mają kwalifikatorów cv. To zachowanie jest spowodowane Regresja w programie Visual C++ 2015 i Visual C++ 2015 Update 1; Visual C++ 2013 i poprzednie wersje programu Visual C++ odrzucić kod napisany w ten sposób. Zachowanie środowiska Visual C++ 2015 i Visual C++ 2015 Update 1 jest nieprawidłowa i nie odpowiada C++ standard.  Visual Studio 2015 Update 2 odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2511 zamiast tego.  
  
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
  
-   **Deklaracja przekazująca dalej wyliczenie nie jest dozwolona w kodzie WinRT** (dotyczy tylko /ZW)  
  
     Kodu skompilowanego dla środowiska uruchomieniowego systemu Windows (WinRT) nie zezwala na `enum` typów do przodu, podobnie do podczas kompilowania kodu zarządzanego języka C++ dla programu .net Framework za pomocą kompilatora/CLR przełącznika. Jest to zachowanie gwarantuje, że rozmiar wyliczenie zawsze jest znany i może zostać poprawnie przedstawione w systemie typu WinRT. Kompilator odrzuca kod napisany w ten sposób i generuje błąd kompilatora C2599 wraz z błąd kompilatora C3197.  
  
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
  
-   **Przeciążony operator niebędący elementem członkowskim nowe ani operator delete nie można zadeklarować wbudowanego** (poziom 1 (/ W1) na domyślnie)  
  
     Poprzednie wersje kompilatora nie ostrzeżenie podczas niebędący elementem członkowskim operator new ani operator delete funkcje są deklarowane jako śródwierszowe. Kod napisany w ten sposób jest niepoprawnie sformułowanych (Diagnostyka nie jest wymagane) i może spowodować pamięci problemy wynikające z niezgodne new i delete — operatory (zwłaszcza gdy jest używany z cofania alokacji o rozmiarze), które mogą być trudne do diagnozowania.   Kompilator generuje teraz kompilatora ostrzeżenie C4595 zidentyfikować kod napisany w ten sposób.  
  
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
  
     Ustalenie kodu, który jest zapisany w ten sposób mogą wymagać czy definicje operatora można przenieść pliku nagłówka i do odpowiadający mu plik źródłowy.  
  
###  <a name="VS_Update3"></a>Ulepszenia zgodność aktualizacji 3  
  
-   **STD::is_convertable teraz wykrywane jest przypisanie własne** (standardowa biblioteka)  
  
     Poprzednie wersje `std::is_convertable` typu cechy nie poprawnie wykrył przypisanie własne typu klasy, po usunięciu jej Konstruktor kopiujący lub prywatnej. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie `false` po zastosowaniu do typu klasy z konstruktorami kopiowania usunięte lub prywatnej.  
  
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
  
     W poprzednich wersjach programu Visual C++, statyczne potwierdzenia w dolnej części w tym przykładzie przekazać, ponieważ `std::is_convertable<>::value` została niepoprawnie ustawiona `true`. Teraz `std::is_convertable<>::value` jest ustawiana poprawnie `false`, powoduje statycznych potwierdzenia się niepowodzeniem.  
  
-   **Domyślnie lub usunięty trivial kopiowania i przenoszenia specyfikatory dostępu względem konstruktorów**  
  
     Poprzednie wersje kompilatora nie Sprawdź specyfikator dostępu do kopii trivial domyślne lub został usunięty i Przenieś konstruktorów przed umożliwieniem jej do wywołania. To zachowanie starego było nieprawidłowe i nie jest zgodny ze standardem C++. W niektórych przypadkach to stare zachowanie utworzony ryzyko generowania kodu zły dyskretnej spowodować nieprzewidywalne zachowanie. Kompilator teraz sprawdza specyfikator dostępu do kopii trivial domyślne lub został usunięty i Przenieś konstruktorów w celu ustalenia, czy można wywołać, a jeśli nie, kompilator problemów w związku z tym ostrzeżenie C2248.  
  
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
  
-   **Amortyzacja oparte na atrybutach obsługi kodu ATL** (poziom 1 (/ W1) na domyślnie)  
  
     Poprzednie wersje kompilatora obsługiwane przypisane kodu biblioteki ATL. Jako następnej fazy usunięta obsługa ATL z atrybutami kod, który [rozpoczął się w programie Visual C++ 2008](https://msdn.microsoft.com/library/bb384632\(v=vs.90\).aspx), oparte na atrybutach kodu biblioteki ATL jest przestarzałe. Kompilator generuje teraz C4467 do identyfikowania tego rodzaju przestarzały kod ostrzeżenia kompilatora.  
  
    ```Output  
    warning C4467: Usage of ATL attributes is deprecated  
    ```  
  
     Jeśli chcesz nadal używać oparte na atrybutach kodu biblioteki ATL z kompilatora została usunięta obsługa można wyłączyć to ostrzeżenie, przekazując `/Wv:18` lub `/wd:4467` argumenty wiersza polecenia do kompilatora lub dodając `#pragma warning(disable:4467)` w kodzie źródłowym.  
  
     Przykład 1 (przed)  
  
    ```cpp  
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]  
    class A {};  
  
    ```  
  
     Przykład 1 (po)  
  
    ```cpp  
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};  
  
    ```  
  
     Czasami może być konieczne lub chcesz utworzyć IDL plik, aby uniknąć użycia przestarzałe atrybutów ATL, tak jak poniżej przykładowy kod  
  
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
  
     Najpierw należy utworzyć plik *.idl; vc140.idl wygenerowany plik może zostać użyty do uzyskania \*zawierający interfejsów i adnotacje pliku .idl.  
  
     Następnie dodaj krok MIDL do kompilacji, aby upewnić się, że definicje interfejsu C++ są generowane.  
  
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
  
     Następnie należy użyć ATL bezpośrednio w pliku implementacji, tak jak przykładowy kod poniżej.  
  
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
  
-   **Prekompilowanych plików nagłówka (PCH) i jest niezgodny # dyrektywy include** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora zaakceptowane niezgodne `#include` dyrektywy w plikach źródłowych między `-Yc` i `-Yu` kompilacje używając prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowane przez kompilator.   Kompilator teraz niezgodne kompilatora problemów ostrzeżenie CC4598 zidentyfikować `#include` dyrektywy podczas korzystania z plików PCH.  
  
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
  
-   **Prekompilowanych plików nagłówka (PCH) i jest niezgodny Dołącz katalogi** (dotyczy tylko/Wall /WX)  
  
     Poprzednie wersje kompilatora zaakceptowane niezgodne katalog dołączania (`-I`) argumenty wiersza polecenia dla kompilatora między `-Yc` i `-Yu` kompilacje używając prekompilowanych plików nagłówka (PCH). Kod napisany w ten sposób nie jest akceptowane przez kompilator.   Katalog dołączania kompilatora teraz kompilatora problemów ostrzeżenie CC4599 zidentyfikować niezgodne (`-I`) argumenty wiersza polecenia, korzystając z plików PCH.  
  
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
  
## <a name="visual-c-2013-conformance-changes"></a>Visual C++ 2013 zgodność zmiany  
  
### <a name="compiler"></a>Kompilatora  
  
-   Ostateczne — słowo kluczowe teraz generuje błąd nierozwiązane symbol którym go będzie mieć skompilowane wcześniej:  
  
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
  
     We wcześniejszych wersjach, błąd nie był generowany ponieważ wywołanie było wywołaniem wirtualnym; niemniej jednak program ulegał awarii w czasie wykonywania. Teraz zostaje zgłoszony błąd konsolidatora, ponieważ wiadomo, że klasa jest ostateczna. W tym przykładzie Aby naprawić błąd, należy połączyć przed obj, który zawiera definicję S2::f.  
  
-   Podczas korzystania z funkcji friend w przestrzeni nazw, należy ponownie zadeklarować funkcji zaprzyjaźnionej przed odwołuje się lub ponieważ kompilator teraz zgodne z normą ISO C++ spowoduje błąd. Na przykład, ten kod się już nie kompiluje:  
  
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
  
     Aby poprawić ten kod, zadeklaruj funkcję zaprzyjaźnioną:  
  
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
  
-   C++ Standard nie zezwala na jawna Specjalizacja w klasie. Chociaż Visual C++ dopuszcza to w niektórych przypadkach, to w przypadku takim, jak poniższy, błąd jest teraz generowany, ponieważ kompilator nie bierze pod uwagę drugiej funkcji jako specjalizacji pierwszej funkcji.  
  
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
  
-   Visual C++ nie próbuje odróżniania dwóch funkcji w poniższym przykładzie, a teraz emituje błąd:  
  
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
  
-   Przed dokonaniem kompilator zgodne z normą ISO C ++ 11, skompilowany i spowodował następujący kod x rozpoznane jako typ int:  
  
    ```cpp  
    auto x = {0};  
    int y = x;  
  
    ```  
  
     Ten kod teraz rozpoznaje x z typem obiektu std::initializer_list\<int > i powoduje błąd w następnym wierszu, który próbuje przypisać x na typ int. (Nie ma domyślnej konwersji.) Aby rozwiązać ten kod, należy użyć int zastąpić automatycznie:  
  
    ```cpp  
    int x = {0};  
    int y = x;  
  
    ```  
  
-   Inicjalizacja agregująca nie jest dozwolone, gdy typ po prawej stronie wartości niezgodny z typem wartości po lewej stronie, która jest inicjowany, a ponieważ ISO C ++ 11 Standard wymaga jednolite inicjowanie pracę bez, zgłaszany jest błąd Zawężanie konwersji. Wcześniej, jeśli zawężanie konwersji była dostępna, [C4242 ostrzeżenie kompilatora (poziom 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) ostrzeżenie będą wyświetlone zamiast błędu.  
  
    ```cpp  
    int i = 0;  
    char c = {i}; // error  
  
    ```  
  
     Aby poprawić ten kod, dodaj jawną konwersję zawężającą:  
  
    ```cpp  
    int i = 0;  
    char c = {static_cast<char>(i)};  
  
    ```  
  
-   Następujące inicjowania nie jest dozwolony:  
  
    ```cpp  
    void *p = {{0}};  
  
    ```  
  
     Aby poprawić ten kod, użyj którejś z tych postaci:  
  
    ```cpp  
    void *p = 0;  
    // or  
    void *p = {0};  
  
    ```  
  
-   Nazwa wyszukiwania została zmieniona. Następujący kod został rozwiązany inaczej w programie Visual C++ w programie Visual Studio 2012 i Visual C++ w programie Visual Studio 2013:  
  
    ```cpp  
    enum class E1 { a };  
    enum class E2 { b };  
  
    int main()  
    {  
        typedef E2 E1;  
        E1::b;  
    }  
  
    ```  
  
     W programie Visual C++ w programie Visual Studio 2012 rozpoznać E1 w wyrażeniu E1::b:: E1 w zakresie globalnym. W programie Visual C++ w programie Visual Studio 2013 E1 w wyrażeniu E1::b jest rozpoznawany jako element typedef E2 definicji w main() i ma typ:: E2.  
  
-   Układ obiektu został zmieniony. W x64, układ obiektu klasy może się zmienić w porównaniu z poprzednimi wydaniami. Jeśli ma on funkcję wirtualną, ale nie ma klasy podstawowej, która ma funkcję wirtualną, model obiektu kompilatora wstawia wskaźnik do tablicy funkcji wirtualnych po układzie elementu członkowskiego danych. Oznacza to, że układ może nie być optymalny we wszystkich przypadkach. W poprzednich wersjach Optymalizacja x64 może spróbować poprawić układu dla Ciebie, ale ponieważ nie działa prawidłowo w sytuacjach złożonego kodu, został usunięty w programie Visual C++ w programie Visual Studio 2013. Na przykład, rozważmy ten kod:  
  
    ```cpp  
    __declspec(align(16)) struct S1 {  
    };  
  
    struct S2 {  
        virtual ~S2();  
        void *p;  
        S1 s;  
    };  
  
    ```  
  
-   W programie Visual C++ w programie Visual Studio 2013 wynik sizeof(S2) na x64 jest 48, ale w poprzednich wersjach, ocenia 32 znaków. Aby to ocenić 32 w programie Visual C++ w programie Visual Studio 2013 dla x64, Dodaj klasę podstawową fikcyjny ma funkcję wirtualną:  
  
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
  
     Znajdowanie miejsc w kodzie wcześniejsza wersja będzie próbować optymalizacji, użyj kompilatora z tą wersją wraz z /W3 — opcja kompilatora i włączyć 4370 ostrzeżenie. Na przykład:  
  
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
  
     Na Kompilatory języka Visual C++ przed Visual C++ w programie Visual Studio 2013, ten kod wyświetla ten komunikat: ostrzeżenie C4370: "S2": układ klasy zmienił się od poprzedniej wersji kompilatora, ze względu na lepsze pakowanie  
  
     Kompilator x86 ma ten sam problem z nieoptymalnym układem we wszystkich wersjach Visual C++. Na przykład, jeśli ten kod jest kompilowany dla architektury x86:  
  
    ```cpp  
    struct S {  
        virtual ~S();  
        int i;  
        double d;  
    };  
  
    ```  
  
     Wynik sizeof (S) jest 24. Można go jednak zmniejszyć do 16, jeśli użyje się wymienionego wcześniej obejścia dla x64:  
  
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
 Visual C++ w Visual Studio 2013 wykrywa niezgodności w _ITERATOR_DEBUG_LEVEL, który został wprowadzony w Visual C++ 2010, i niezgodności RuntimeLibrary. One wystąpić, gdy kompilatora opcje/MT (statyczne release), /MTd (debugowanie statycznych), / / MD (wersja dynamicznych) i/mdd (debugowanie dynamiczne).  
  
-   Kod potwierdza szablonów aliasów symulowane poprzedniej wersji, należy ją zmienić. Na przykład zamiast allocator_traits —\<A >:: rebind_alloc\<U >:: innych, teraz trzeba powiedzieć allocator_traits —\<A >:: rebind_alloc\<U >. Mimo że ratio_add\<R1, R2 >:: typu nie jest już konieczne, i teraz zalecamy, aby powiedzieć ratio_add\<R1, R2 >, pierwsza będą nadal skompilować, ponieważ współczynnik\<N, D > musi być typem typedef "type" dla obniżonej stosunek, którego ma być tego samego typu, jeśli już zostanie zmniejszona.  
  
-   Należy użyć #include \<algorytm > podczas wywoływania std::min() lub std::max().  
  
-   Jeśli używany przez istniejący kod poprzedniej wersji elementu symulowane zakres wyliczenia — tradycyjnych niewystępującego w zakresie wyliczenia opakowane w przestrzeniach nazw — trzeba je zmienić. Na przykład jeśli określony typ std::future_status::future_status, teraz należy powiedzieć std::future_status. Jednak większość kodu nie mają wpływu — na przykład std::future_status::ready nadal kompiluje.  
  
-   jawny operator bool() jest bardziej restrykcyjne od unspecified-bool-type() operatora. zezwala na bool() jawny operator jawnej konwersji na typ logiczny — na przykład podane shared_ptr\<X > sp, zarówno static_cast\<bool > (sp) i bool b(sp) są prawidłowe — i wartość logiczną skonfigurowaną "konwersje kontekstowych" na typ logiczny — na przykład Jeśli (sp),! sp, sp & & niezależnie od. Jednak bool() jawny operator zabrania niejawne konwersje na bool, więc nie można podać bool b = sp; a podana zwracanego typu bool, nie można powiedzieć sp zwracany.  
  
-   Teraz, gdy zostaną zaimplementowane szablony wariadyczne prawdziwe, _VARIADIC_MAX i powiązanych makr nie obowiązują. Jeżeli nadal definiujesz _VARIADIC_MAX, jest to po prostu ignorowane. Jeśli przyjmiesz nasze rozwiązania makr przeznaczone do wspierania symulowanych szablonów wariadycznych w jakikolwiek inny sposób, musisz zmienić kod.  
  
-   Oprócz zwykłych słów kluczowych nagłówki standardowa biblioteka C++ zabraniać makro izing kontekstowe słowa kluczowe "override" i "końcowe".  
  
-   reference_wrapper/REF()/cref() teraz zabraniać powiązanie do obiektów tymczasowych.  
  
-   \<losowe > teraz ściśle wymusza warunki wstępne jego kompilacji.  
  
-   Różnych cech typu standardowa biblioteka C++ mieć warunek wstępny "T być pełny typ to". Mimo że kompilator wymusza to teraz bardziej restrykcyjnie, nie może go wymusić we wszystkich sytuacjach. (Ponieważ naruszeń warunek wstępny standardowa biblioteka C++ wyzwolić niezdefiniowane zachowanie, Standard nie gwarantuje wymuszania.)  
  
-   Standardowa biblioteka C++ nie obsługuje: oldsyntax.  
  
-   W języku C ++ 11 specyfikacji <> common_type — ma nieoczekiwany i niepożądane skutki; w szczególności ułatwia common_type —\<int, int >:: typ zwracany int & &. W związku z tym Visual C++ implementuje proponowane rozwiązanie problemu grupę roboczą bibliotece 2141, dzięki czemu common_type —\<int, int = "" >:: typ zwracany int.  
  
     Jako efekt uboczny tej zmiany, nie będzie działać w przypadku tożsamości (common_type —\<T > nie zawsze powoduje typu T). Jest to zgodne z Proponowanym rozwiązaniem, ale unieważnia jakikolwiek kod, który opierał się na poprzednim zachowaniu.  
  
     Jeśli potrzebujesz cechy typu tożsamości, nie używaj std::identity niestandardowej, która jest zdefiniowana w < type_traits >, ponieważ nie będzie działać dla \<void >. Zamiast tego wdróż własną cechę typu tożsamości odpowiednią do własnych potrzeb. Oto przykład:  
  
    ```cpp  
    template < typename T> struct Identity {  
        typedef T type;  
    };  
  
    ```  
  
### <a name="mfc-and-atl"></a>MFC i ATL  
  
-  **Visual Studio 2013 r. z tylko**: Biblioteka MFC MBCS jest niedostępna w programie Visual Studio, ponieważ Unicode jest więc popularnych i znacznie zmniejsza użycie MBCS. Ta zmiana podtrzymuje również ściślejszą relację między MFC a Windows SDK. ponieważ wiele nowych kontrolek i komunikatów wymaga Unicode. Jednak jeśli nadal należy używać biblioteki MFC MBCS, można go pobrać z Centrum pobierania MSDN [wielobajtowe Biblioteka MFC dla programu Visual Studio 2013](https://www.microsoft.com/en-us/download/details.aspx?id=40770). Pakiet redystrybucyjny Visual C++ wciąż zawiera tę bibliotekę.  (Uwaga: MBCS DLL jest uwzględniona w składników instalacji programu Visual C++ w programie Visual Studio 2015 i nowszych).
  
-   Ułatwienia dostępu dla wstążki MFC zostanie zmieniona.  Zamiast architektury jeden poziom jest teraz architekturę hierarchiczną. Można nadal używać starego zachowania przez wywołanie CRibbonBar::EnableSingleLevelAccessibilityMode().  
  
-   Metoda CDatabase::GetConnect zostaną usunięte. Aby zwiększyć bezpieczeństwo, parametry połączenia są obecnie przechowywane zaszyfrowane i zostaną odszyfrowane tylko w razie potrzeby; Nie można zwrócić jako zwykły tekst.  Ciąg można uzyskać za pomocą metody CDatabase::Dump.  
  
-   Podpis CWnd::OnPowerBroadcast zostanie zmieniona. Sygnatura tego programu obsługi komunikatu została zmieniona, aby przyjąć LPARAM jako drugi parametr.  
  
-   Podpisy są zmieniane w celu uwzględnienia obsługi komunikatów. Listy parametrów dla poniższych funkcji zostały zmienione, aby używać nowo dodanych programów obsługi komunikatów ON_WM_*:  
  
    -   CWnd::OnDisplayChange zmienione (UINT, int, int) zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_DISPLAYCHANGE mogą być używane w mapie komunikatów.  
  
    -   CFrameWnd::OnDDEInitiate zmienione (CWnd *, UINT, jednostka) zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_DDE_INITIATE mogą być używane w mapie komunikatów.  
  
    -   CFrameWnd::OnDDEExecute zmienione aby (* dojście CWnd) zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_DDE_EXECUTE mogą być używane w mapie komunikatów.  
  
    -   CFrameWnd::OnDDETerminate zmienione aby (CWnd *) jako parametr zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_DDE_TERMINATE mogą być używane w mapie komunikatów.  
  
    -   CMFCMaskedEdit::OnCut zmieniony na Brak parametrów zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_CUT mogą być używane w mapie komunikatów.  
  
    -   CMFCMaskedEdit::OnClear zmieniony na Brak parametrów zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_CLEAR mogą być używane w mapie komunikatów.  
  
    -   CMFCMaskedEdit::OnPaste zmieniony na Brak parametrów zamiast (WPARAM LPARAM) tak, aby nowe makro ON_WM_PASTE mogą być używane w mapie komunikatów.  
  
-   \#ifdefs w plikach nagłówek MFC zostaną usunięte. Wiele #ifdefs w nagłówku MFC plików związanych z nieobsługiwanej wersji systemu Windows (WINVER &lt; 0x0501) zostaną usunięte.  
  
-   ATL DLL (atl120.dll) zostaną usunięte. ATL jest obecnie dostarczany jako nagłówki i biblioteka statyczna (atls.lib).  
  
-   Atlsd.lib, atlsn.lib i atlsnd.lib zostały usunięte. Atls.lib nie ma już zależności zestawu znaków ani kodu, który jest specyficzny dla wersji do debugowania/oficjalnych. Ponieważ działa tak samo dla Unicode/ANSI i wersji do debugowania/oficjalnych, wymagana jest tylko jedna wersja biblioteki.  
  
-   Narzędzie śledzenia ATL/MFC zostanie usunięta wraz z ATL DLL i upraszcza mechanizm śledzenia. Konstruktor CTraceCategory teraz przyjmuje jeden parametr (nazwa kategorii), a makra śledzenia wywołań debugowania CRT funkcje raportowania.  
  
## <a name="visual-c-2012-breaking-changes"></a>Visual C++ 2012 najważniejszych zmian  
  
### <a name="compiler"></a>Kompilatora  
  
-   /Yl — opcja kompilatora została zmieniona. Domyślnie kompilator używa tej opcji, co może prowadzić do błędów LNK2011 w niektórych warunkach. Aby uzyskać więcej informacji, zobacz [/Yl (Wstaw Odnośnik PCH dla bibliotek debugowania)](../build/reference/yl-inject-pch-reference-for-debug-library.md).  
  
-   Kod, który ma być kompilowana przy użyciu/CLR enum class, słowo kluczowe definiuje C ++ 11 wyliczenia, nie wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) wyliczenia. Aby zdefiniować wyliczenia CLR, musi być jawnym o jego dostępność.  
  
-   Użyj słowa kluczowego szablonu, aby odróżnić jawnie zależna nazwa (zgodność języka C++ — standardowe). W poniższym przykładzie wyróżnione template — słowo kluczowe jest wymagane w celu rozwiązania niejednoznaczności. Aby uzyskać więcej informacji, zobacz [rozpoznawanie nazwy dla typów zależnych](../cpp/name-resolution-for-dependent-types.md).  
  
    ```cpp  
    template < typename X = "", typename = "" AY = "">  
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };  
  
    ```  
  
-   Stałego wyrażenia typu zmiennoprzecinkowego nie jest dozwolona jako argument szablonu, jak pokazano w poniższym przykładzie.  
  
    ```cpp  
    template<float n=3.14>  
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'  
  
    ```  
  
-   Kod, który ma być kompilowana przy użyciu opcji wiersza polecenia/GS i ma luki w zabezpieczeniach poza o jedno może prowadzić do przetworzenia zakończenia w czasie wykonywania, jak pokazano w poniższym przykładzie pseudocode.  
  
    ```cpp  
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate  
    ```  
  
-   Architektura domyślne x86 kompilacji jest zmieniana na SSE2; Dlatego kompilator może emitować instrukcje SSE i użyje rejestrów XMM do obliczeń zmiennoprzecinkowych. Jeśli chcesz powrócić do poprzedniej zachowanie, Użyj flagi kompilatora /arch:IA32 umożliwia określenie architekturę jako IA32.  
  
-   Kompilator może wydać ostrzeżenia [C4703 ostrzeżenie kompilatora (poziom 4)](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) i C4701, na którym wcześniej go nie. Kompilator stosuje silniejsze kontrole niezainicjowanych zmiennych lokalnych typu wskaźnika do użytku.  
  
-   Gdy nowy konsolidatora flagi/highentropyva jest określony, Windows 8 zwykle powoduje, że przydziału pamięci zwrócić 64-bitowy adres.                 (Przed systemem Windows 8 takich przydziałów częściej zwrócił adresów, które były mniej niż 2 GB.)  Ta operacja może narazić usterki obcięcie wskaźnika w istniejącym kodzie. Domyślnie ten przełącznik jest na.  Aby wyłączyć to zachowanie, należy określić /HIGHENTROPYVA:NO.  
  
-   Kompilator zarządzanych (Visual Basic / C#) obsługuje również/highentropyva dla zarządzanych kompilacji.  Jednak w takim przypadku /HIGHENTROPYVAswitch jest wyłączone domyślnie.  
  
### <a name="ide"></a>IDE  
  
-   Mimo że firma Microsoft zaleca, aby nie twórz aplikacji formularzy systemu Windows w języku C + +/ CLI i konserwacja istniejących C + +/ CLI interfejsu użytkownika aplikacji jest obsługiwana. Jeśli masz do tworzenia aplikacji formularzy systemu Windows lub innej aplikacji .NET interfejsu użytkownika, należy użyć C# lub Visual Basic. Użyj C + +/ CLI współdziałania tylko do celów.  
  
### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>Biblioteka równoległych wzorców i biblioteki wykonawczej współbieżności  
 Schedulertype — wyliczenie z UmsThreadDefault jest przestarzały. Specyfikacja UmsThreadDefault generuje ostrzeżenie przestarzałe i wewnętrznie mapy do ThreadScheduler.  
  
### <a name="standard-library"></a>Standardowa biblioteka  
  
-   Następujące istotne zmiany między C ++ 98/03 i C ++ 11 standardy, przy użyciu argumentów jawnego szablonu do wywołania (make_pair —) — jako inmake_pair\<int, int >(x, y) — zwykle nie kompiluje się w programie Visual C++ w programie Visual Studio 2012. Rozwiązanie to zawsze wywołania (make_pair —) bez argumentów jawnego szablonu — tak jak make_pair — (x, y). Udostępnianie stanowi zaprzeczenie argumentów jawnego szablonu w celu funkcji. Jeśli potrzebna jest ścisła kontrola nad wynikowy typ, użyj pary zamiast make_pair — — tak jak pary\<krótkie, krótki >(int1, int2).  
  
-   Inna zmiana podziału między C ++ 98/03 i C ++ 11 standardy: po umożliwiają niejawnej konwersji na A B i B jest niejawnie przekonwertować C, ale A nie umożliwiają niejawnej konwersji na C i C ++ 98/03 Visual C++ 2010 dozwolone pary\<, X > należy przekonwertować () jawnie lub niejawnie) parę\<C, X >. (Type, X, nie jest tutaj odsetek i nie jest specyficzne dla pierwszego typu pary.) Ponieważ C ++ 11 i języka Visual C++ w programie Visual Studio 2012 wykrył, że A jest nie umożliwiają niejawnej konwersji na C, będą oni mogli usunąć konwersja pary z wiązaniem. Jest to pozytywnych zmian w różnych scenariuszach. Na przykład przeładowanie func (const pary\<int, int > &) i func (const pary\<ciąg, ciąg > &) i wywoływanie func() z pary\<const char *, const char \*> zostanie skompilowany z tą zmianą. Jednak ta zmiana dzieli kod, który będzie zależał od konwersje agresywne pary. Zazwyczaj można naprawić taki kod, wykonując jedną z części konwersji jawnie — na przykład przez przekazanie make_pair — (operatora static_cast\<B > (a), x) do funkcji, która oczekuje pary\<C, X >.  
  
-   Visual C++ 2010 symulowane szablony wariadyczne — na przykład make_shared —\<T > (arg1, arg2, argN) — do limitu 10 argumenty, znakowania przeciążenia i specjalizacje preprocesora maszyny. W programie Visual C++ w programie Visual Studio 2012 ten limit, zostanie zmniejszona do 5 argumentów, aby zwiększyć czas kompilacji i zmniejszenie zużycia pamięci kompilatora dla większości użytkowników. Jednak można ustawić poprzedniej limit przez jawne zdefiniowanie _VARIADIC_MAX jako 10, na poziomie projektu.  
  
-   C ++ 11 17.6.4.3.1 [macro.names]/2 zabrania słowa kluczowe izing makra, gdy nagłówki standardowa biblioteka C++ są uwzględnione. Nagłówki teraz Emituj błędy kompilatora, jeśli wykryją ized makro słów kluczowych. (Definiowanie _ALLOW_KEYWORD_MACROS zezwala na taki kod skompilować, ale firma Microsoft zdecydowanie zniechęcić wykorzystanie). Jako wyjątek nowe makro ized domyślnie jest dozwolona, ponieważ nagłówki szerokim zakresie bronić się przy użyciu #pragma push_macro("new") / #undef nowe / #pragma pop_macro("new"). Definiowanie _ENFORCE_BAN_OF_MACRO_NEW ma dokładnie co sugeruje jego nazwa.  
  
-   Aby zaimplementować różnych optymalizacji i debugowania kontroli, implementacja standardowa biblioteka C++ celowo dzieli zgodności plików binarnych między wersjami programu Visual Studio (2005, 2008, 2010, 2012). Gdy jest używana standardowa biblioteka C++, to zabrania mieszania plików obiektu i bibliotek statycznych, które są kompilowane przy użyciu różnych wersji w jedną wartość binarną (plik EXE lub DLL), a zabrania przekazywanie obiektów standardowa biblioteka C++ między plików binarnych, które są kompilowane przez przy użyciu różnych wersji. Mieszanie obiektów pliki oraz bibliotek statycznych (przy użyciu standardowa biblioteka C++, które zostały skompilowane przy użyciu programu Visual C++ 2010 z tymi, które zostały skompilowane przy użyciu programu Visual C++ w programie Visual Studio 2012 emituje błędy konsolidatora o elemencie _MSC_VER niezgodność, gdy w elemencie _MSC_VER jest makra zawiera wersję główną kompilatora (1700 w języku Visual C++ w programie Visual Studio 2012). Tego wyboru nie może wykryć mieszanie biblioteki DLL i nie może wykryć mieszanie, która obejmuje Visual C++ 2008 lub starszej.  
  
-   Oprócz wykrycia niezgodności _ITERATOR_DEBUG_LEVEL, który został wdrożony w programie Visual C++ 2010, Visual C++ w programie Visual Studio 2012 wykrywa niezgodności biblioteki środowiska uruchomieniowego. Te wystąpić, gdy kompilator opcje/MT (statyczne release), /MTd (debugowanie statycznych), / / MD (wersja dynamicznych) i/mdd (debugowanie dynamiczne).  
  
-   operator\<(), operator > (), operator\<= (), a operator > () = wcześniej były dostępne dla rodziny andstdext::hash_map std::unordered_map kontenerów, chociaż nie zostały faktycznie przydatne ich implementacji. Te niestandardowe operatory zostały usunięte w programie Visual C++ w programie Visual Studio 2012. Ponadto, aby pokrywał się z rodziny stdext::hash_map został rozszerzony implementacja operator==() i operator!=() thestd::unordered_map rodziny. (Zaleca się należy unikać użycia thestdext::hash_map family nowy kod.)  
  
-   C ++ 11 22.4.1.4 [locale.codecvt] Określa, czy codecvt::length() i codecvt::do_length() powinno zająć można modyfikować stateT & parametrami, ale Visual C++ 2010 trwało const stateT &. Visual C++ w Visual Studio 2012 ma stateT & jako obowiązkowego przez standard. Ta różnica jest ważna dla każdego, kto próbuje przesłonić funkcji wirtualnej do_length().  
  
### <a name="crt"></a>CRT  
  
-   Sterty C Runtime (CRT), która jest stosowana do nowych i malloc(), nie jest już prywatnych. CRT używa teraz stercie procesu. Oznacza to, że stos nie jest niszczony, gdy biblioteka DLL jest zwolniony, więc biblioteki DLL połączone statycznie CRT musi zapewnić pamięci przydzielonej przez kod biblioteki DLL jest wyczyszczone przed jego został zwolniony.  
  
-   Funkcja iscsymf() potwierdza z wartości ujemnych.  
  
-   Struktury threadlocaleinfostruct został zmieniony w celu uwzględnienia zmiany ustawień regionalnych funkcji.  
  
-   Funkcje CRT mają odpowiednie funkcje wewnętrzne, takie jak memxxx(), strxxx() są usuwane z intrin.h. Uwzględnione intrin.h tylko dla tych funkcji, należy zawierają teraz odpowiednie nagłówki CRT.  
  
### <a name="mfc-and-atl"></a>MFC i ATL  
  
-   Usunięta obsługa Fusion (afxcomctl32.h); w związku z tym wszystkie metody, które są zdefiniowane w afxcomctl32.h zostały usunięte. Afxcomctl32.h pliki nagłówka i afxcomctl32.inl zostały usunięte.  
  
-   Zmienić nazwę CDockablePane::RemoveFromDefaultPaneDividier na CDockablePane::RemoveFromDefaultPaneDivider.  
  
-   Zmieniony podpis CFileDialog::SetDefExt do użycia LPCTSTR; w związku z tym dotyczy kompilacji Unicode.  
  
-   Usunięto nieaktualny ATL kategorii śledzenia.  
  
-   Zmieniony podpis CBasePane::MoveWindow podjęcie const CRect.  
  
-   Zmieniony podpis CMFCEditBrowseCtrl::EnableBrowseButton.  
  
-   Usunięto m_fntTabs i m_fntTabsBold z CMFCBaseTabCtrl.  
  
-   Dodaje parametr CMFCRibbonStatusBarPane konstruktorów. (Jest to parametr domyślny, a nie jest źródła podziału).  
  
-   Dodaje parametr do konstruktora cmfcribboncommandslistbox —. (Jest to parametr domyślny, a nie jest źródła podziału).  
  
-   Usunięte z interfejsu API AFXTrackMouse (i związane z procesem czasomierza). W zamian użyj interfejsu API Win32 zdarzenia TrackMouseEvent.  
  
-   Dodaje parametr do konstruktora CFolderPickerDialog. (Jest to parametr domyślny, a nie jest źródła podziału).  
  
-   Zmieniono rozmiar struktury CFileStatus: element członkowski m_attribute zmieniła się z BAJTÓW do DWORD (do dopasowania wartości, który zwrócił fromGetFileAttributes).  
  
-   CRichEditCtrl i CRichEditView Użyj MSFTEDIT_CLASS (formantu RichEdit 4.1) zamiast RICHEDIT_CLASS (formantu RichEdit 3.0) w kompilacjach kodu Unicode.  
  
-   Usunąć AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground, ponieważ jest ona zawsze wartości TRUE w systemie Windows Vista, Windows 7 i Windows 8.  
  
-   Usunąć AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable, ponieważ jest ona zawsze wartości TRUE w systemie Windows Vista, Windows 7 i Windows 8.  
  
-   Usunięto AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea. Wywołanie Windows API bezpośrednio w systemie Windows Vista, Windows 7 i Windows 8.  
  
-   Usunięto AFX_GLOBAL_DATA::DwmDefWindowProc. Wywołanie Windows API bezpośrednio w systemie Windows Vista, Windows 7 i Windows 8.  
  
-   Zmieniona AFX_GLOBAL_DATA::DwmIsCompositionEnabled na IsDwmCompositionEnabled, aby wyeliminować kolizję nazw.  
  
-   Zmienione identyfikatory liczby wewnętrznych czasomierze MFC i przeniesiona definicje afxres.h (AFX_TIMER_ID_ *).  
  
-   Zmieniony podpis metody OnExitSizeMove Akceptuję makro ON_WM_EXITSIZEMOVE:  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
    -   CPaneFrameWnd  
  
-   Zmienić nazwę i podpis OnDWMCompositionChanged aby uzgodnić z makra ON_WM_DWMCOMPOSITIONCHANGED:  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
    -   CPaneFrameWnd  
  
-   Zmieniony podpis metody OnMouseLeave Akceptuję makro ON_WM_MOUSELEAVE:  
  
    -   CMFCCaptionBar  
  
    -   CMFCColorBar  
  
    -   CMFCHeaderCtrl  
  
    -   Cmfcproperysheetlistbox —  
  
    -   CMFCRibbonBar  
  
    -   CMFCRibbonPanelMenuBar  
  
    -   CMFCRibbonRichEditCtrl  
  
    -   CMFCSpinButtonCtrl  
  
    -   CMFCToolBar ReplaceThisText  
  
    -   CMFCToolBarComboBoxEdit  
  
    -   CMFCToolBarEditCtrl  
  
    -   CMFCAutoHideBar  
  
-   Zmieniony podpis OnPowerBroadcast aby uzgodnić z makra ON_WM_POWERBROADCAST:  
  
    -   CFrameWndEx  
  
    -   CMDIFrameWndEx  
  
-   Zmieniony podpis OnStyleChanged aby uzgodnić z makra ON_WM_STYLECHANGED:  
  
    -   CMFCListCtrl  
  
    -   CMFCStatusBar —  
  
-   Zmieniona metody wewnętrznej FontFamalyProcFonts na FontFamilyProcFonts.  
  
-   Usunięte wiele globalne statycznych cstring — obiekty wyeliminować przecieki pamięci w niektórych sytuacjach (zastąpione #defines), a następujące klasy zmienne Członkowskie:  
  
    -   CKeyBoardManager::m_strDelimiter  
  
    -   CMFCPropertyGridProperty::m_strFormatChar  
  
    -   CMFCPropertyGridProperty::m_strFormatShort  
  
    -   CMFCPropertyGridProperty::m_strFormatLong  
  
    -   CMFCPropertyGridProperty::m_strFormatUShort  
  
    -   CMFCPropertyGridProperty::m_strFormatULong  
  
    -   CMFCPropertyGridProperty::m_strFormatFloat  
  
    -   CMFCPropertyGridProperty::m_strFormatDouble  
  
    -   CMFCToolBarImages::m_strPngResType  
  
    -   CMFCPropertyGridProperty::m_strFormat  
  
-   Zmieniony podpis CKeyboardManager::ShowAllAccelerators i usunąć parametr ogranicznik akceleratora.  
  
-   Dodano CPropertyPage::GetParentSheet oraz w cpropertypage — klasa, należy wywołać ją zamiast GetParent oknie arkusza poprawne nadrzędnego, które mogą być nadrzędne lub okna nadrzędnego cpropertypage —. Trzeba zmienić swój kod, aby w zamian wywołaj GetParentSheet ofGetParent.  
  
-   Stała niezrównoważonej #pragma warning(push) ATLBASE. H, który spowodował ostrzeżenia, które mają zostać nieprawidłowo wyłączone. Po ATLBASE tych ostrzeżeń są teraz włączone poprawnie. H został przeanalizowany.  
  
-   Przeniesione metody związanych z D2D z afx_global_data — do _AFX_D2D_STATE:  
  
    -   GetDirectD2dFactory  
  
    -   GetWriteFactory  
  
    -   GetWICFactory  
  
    -   InitD2D  
  
    -   ReleaseD2DRefs  
  
    -   IsD2DInitialized  
  
    -   D2D1MakeRotateMatrix  
  
    -   Zamiast kontaktować, na przykład afxGlobalData.IsD2DInitialized, wywołanie AfxGetD2DState -> IsD2DInitialized.  
  
-   Usunięto nieaktualny ATL *. CPP pliki z folderu \atlmfc\include\.  
  
-   Przenieść inicjowania afxGlobalData do na żądanie zamiast w czasie inicjowania CRT, aby spełniać wymagania dotyczące funkcji DLLMain.  
  
-   Metoda RemoveButtonByIndex dodawana do klasy CMFCOutlookBarPane.  
  
-   Rozwiązany CMFCCmdUsageCount::IsFreqeuntlyUsedCmd do IsFrequentlyUsedCmd.  
  
-   Poprawiono wiele wystąpień RestoreOriginalstate do RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane).  
  
-   Usunąć nieużywane metody z CDockablePane: SetCaptionStyle, IsDrawCaption, IsHideDisabledButtons, GetRecentSiblingPaneInfo, andCanAdjustLayout.  
  
-   Usunięte CDockablePane statyczny element członkowski zmienne m_bCaptionText i m_bHideDisabledButtons.  
  
-   Zastąpienie metody DeleteString należy dodać do CMFCFontComboBox.  
  
-   Usunąć nieużywane metody z CPane: GetMinLength i IsLastPaneOnLastRow.  
  
-   Zmieniono nazwę CPane::GetDockSiteRow(CDockingPanesRow *) do CPane::SetDockSiteRow.  
  
## <a name="visual-c-2010-breaking-changes"></a>Visual C++ 2010 najważniejszych zmian  
  
### <a name="compiler"></a>Kompilatora  
  
-   Auto — słowo kluczowe ma nowe znaczenie domyślne. Użyj starego znaczenie jest rzadko, większość aplikacji nie wpłynie tej zmiany.  
  
-   Wprowadzono słowo kluczowe new static_assert, która spowoduje konflikt nazw, jeśli istnieje już identyfikator o takiej nazwie w kodzie.  
  
-   Obsługa nowej notacji lambda nie obejmuje obsługę kodowania bez cudzysłowów GUID w atrybucie IDL uuid.  
  
-   .NET Framework 4 wprowadza pojęcia uszkodzony wyjątków, które są wyjątki, które opuszczają proces nieodwracalny uszkodzona. Domyślnie nie może przechwycić wyjątek nieprawidłowego stanu, nawet w przypadku opcję kompilatora/eha, która przechwytuje wszystkie pozostałe wyjątki.                 Aby jawnie catch wyjątku uszkodzony, należy użyć __try -\__except instrukcje. Lub, zastosuj atrybut [HandledProcessCorruptedStateExceptions], aby włączyć funkcję przechwytują wyjątki uszkodzony.  Ta zmiana wpływa głównie programistów systemu, którzy może być konieczne catch wyjątku uszkodzony. Osiem wyjątki są STATUS_ACCESS_VIOLATION, STATUS_STACK_OVERFLOW, EXCEPTION_ILLEGAL_INSTRUCTION, EXCEPTION_IN_PAGE_ERROR, EXCEPTION_INVALID_DISPOSITION, EXCEPTION_NONCONTINUABLE_EXCEPTION, EXCEPTION_PRIV_INSTRUCTION, status_ — UNWIND_CONSOLIDATE.                 Aby uzyskać więcej informacji o tych wyjątków, zobacz [getexceptioncode —](https://msdn.microsoft.com/en-us/library/windows/desktop/ms679356.aspx) makra.  
  
-   Poprawione opcję kompilatora/GS chroni przed przepełnienia buforu więcej szerokim zakresie niż w starszych wersjach. Ta wersja może wstawić dodatkowe testy zabezpieczeń ze stosu, który może zmniejszyć wydajność. Użyj słowa kluczowego __declspec(safebuffers) nowe nakazać kompilator, aby nie wstawić kontroli zabezpieczeń dla danej funkcji.  
  
-   Należy skompilować z opcją /GL (optymalizacja całego programu) i opcje kompilatora/CLR (kompilacja języka wspólnego środowiska uruchomieniowego), /GLoption jest ignorowana. Ta zmiana została wprowadzona, ponieważ kombinacja opcji kompilatora podany małego korzyści. W wyniku tej zmiany zwiększona wydajność kompilacji.  
  
-   Domyślnie Obsługa elementów trigraph jest wyłączona w programie Visual C++ 2010. Aby włączyć obsługę trigramów, należy użyć opcji kompilatora/Zc: trigraphs. — Trigram składa się z dwóch następujących po sobie znaki zapytania ("?") następuje znak trzeci unikatowy. Kompilator zastępuje — trigram odpowiedni znak interpunkcyjny. Na przykład kompilator zastępuje "? = "— trigram znakiem '#'. Użyj trigramów w plikach źródłowych C, korzystających z zestawu znaków, która nie zawiera graficzne przedstawienie wygodny dla niektórych znaków interpunkcyjnych.  
  
-   Konsolidator nie obsługuje już Optymalizacja dla Windows 98. Opcja od (optymalizacje) generuje błąd w czasie kompilacji, jeśli określisz / OPT: WIN98 lub/OPT: nowin98.  
  
-   Domyślne opcje kompilatora, które są określone przez RuntimeLibrary i DebugInformationFormat kompilacji systemu, które właściwości zostały zmienione. Domyślnie te właściwości są określone w projektach, które zostały utworzone przy użyciu programu Visual C++ kompilacji zwalnia 7.0 za pośrednictwem 10.0. W przypadku migrowania projektu, który został utworzony przez program Visual C++ 6.0, rozważyć określenie wartości tych właściwości.  
  
-   W programie Visual C++ 2010, RuntimeLibrary = wielowątkowych (/ MD) i DebugInformationFormat = ProgramDatabase (/Zi). W programie Visual C++ 9.0, RuntimeLibrary = wielowątkowych (/ MT) i DebugInformationFormat = wyłączone.  
  
### <a name="clr"></a>CLR  
  
-   Kompilatory języka Microsoft C# i Visual Basic można teraz utworzyć nie podstawowy zestaw międzyoperacyjny (no-PIA). Zestaw nie PIA można używać typów COM bez wdrożenia odpowiednie podstawowy zestaw międzyoperacyjny (PIA). Podczas używania zestawów nie PIA utworzonego przez Visual C# lub Visual Basic, musi odwoływać się do zestawu PIA polecenie kompilacji, przed odwołaniem zestawu nie PIA, który korzysta z biblioteki.  
  
### <a name="visual-c-projects-and-msbuild"></a>Projekty Visual C++ i MSBuild  
  
-   Projekty Visual C++, teraz są oparte na narzędzia MSBuild. W związku z tym pliki projektu używać sufiksu pliku .vcxproj oraz na nowy format pliku XML. Visual C++ 2010 automatycznie konwertuje pliki projektu z wcześniejszych wersji programu Visual Studio do nowego formatu pliku. Problem ma wpływ istniejącego projektu, jeśli zależy od poprzedniego .vcproj narzędzia, VCBUILD.exe lub sufiks pliku projektu, kompilacji.  
  
-   We wcześniejszych wersjach programu Visual C++ obsługiwane późne oceny arkuszy właściwości. Na przykład arkusz właściwości nadrzędnej można zaimportować arkusz właściwości podrzędnej, a nadrzędnego można użyć zmiennej zdefiniowanej w podrzędnym, aby zdefiniować inne zmienne. Późne oceny włączony element nadrzędny korzystały nawet zmiennej podrzędnego arkusza właściwości podrzędnej został zaimportowany. W programie Visual C++ 2010 nie można użyć zmiennej arkusza projektu, zanim zostanie on zdefiniowany program MSBuild obsługuje tylko wczesne oceny.  
  
### <a name="ide"></a>IDE  
  
-   Okno dialogowe Kończenie działania aplikacji już nie kończy się aplikacja. W poprzednich wersjach funkcji abort() lub terminate() zamknięcie kompilacji handlowej aplikacji, biblioteki wykonawczej języka C wyświetlany komunikat Kończenie działania aplikacji w konsoli okno lub okno dialogowe. Komunikat powiedział, w części "Ta aplikacja zażądała środowiska uruchomieniowego zakończenia działania w nietypowego. Skontaktuj się z zespołem pomocy technicznej aplikacji Aby uzyskać więcej informacji."                 Komunikat zakończenia aplikacji został nadmiarowego, ponieważ Windows następnie wyświetlane bieżącej obsługi zakończenia, który został zazwyczaj raportowanie błędów systemu Windows (odzyskiwania po awarii. Okno dialogowe Watson) lub debuger programu Visual Studio. Począwszy od programu Visual Studio 2010, biblioteki wykonawczej języka C nie jest wyświetlany komunikat. Ponadto środowisko uruchomieniowe uniemożliwia aplikacji kończyć przed rozpoczęciem debugera. Jest to istotne zmiany tylko wtedy, gdy zależy zachowanie poprzedniego komunikatu Kończenie działania aplikacji.  
  
-   Specjalnie dla programu Visual Studio 2010, IntelliSense nie działa dla języka C + +/ kodu interfejsu wiersza polecenia lub atrybutów, Znajdź wszystkie odwołania nie działa w przypadku zmiennych lokalnych i modelu kodu nie pobrać nazwy typów importowane zestawy lub rozpoznać typy ich qualifi pełni ED nazwy.  
  
### <a name="libraries"></a>Biblioteki  
  
-   Safeint — klasa znajduje się w programie Visual C++ i nie jest już pobierana osobno. Jest to istotne zmiany tylko wtedy, gdy utworzono klasę o nazwie "Safeint —".  
  
-   Model wdrażania przy użyciu bibliotek nie są już używane w manifestach można znaleźć określonej wersji biblioteki dołączanej dynamicznie. Zamiast tego nazwa każdej biblioteki dll zawiera jej numer wersji i użyć tej nazwy do lokalizowania biblioteki.  
  
-   W poprzednich wersjach programu Visual Studio można odtworzyć biblioteki czasu wykonywania. Visual C++ 2010 nie obsługuje tworzenia kopii c pliki bibliotek czasu uruchomienia.  
  
### <a name="standard-library"></a>Standardowa biblioteka  
  
-   \<Iteratora > nagłówka nie jest już uwzględniona automatycznie przez inne pliki nagłówków. Zamiast tego nagłówka jawnie zawierały, jeśli wymagana jest obsługa Iteratory autonomiczny zdefiniowane w istniejący projekt jest zmienione, jeśli zależy on od poprzedniego narzędzia kompilacji, VCBUILD.exe lub sufiks pliku projektu,. vcproj.interator > on ader.  
  
-   W \<algorytm > nagłówka, checked_ * i unchecked_\* funkcje zostały usunięte. I w \<iteratora >> nagłówka, checked_iteratorclass zostanie usunięty, a unchecked_array_iterator — klasa została dodana.  
  
-   Konstruktor CComPtr::CComPtr(int) zostaną usunięte. Ten konstruktor dozwolonych obiekt CComPtr, aby zostać utworzone na podstawie makro wartość NULL, ale nie jest konieczne i dozwolone nonsensical konstrukcji od zera liczb całkowitych.  
  
     CComPtr nadal mogą zostać utworzone na podstawie wartości NULL, która jest zdefiniowana jako 0, ale zakończy się niepowodzeniem, jeśli utworzone na podstawie innych niż 0 literału typu integer. Zamiast tego użyj nullptr.  
  
-   Usunięto następujące funkcje Członkowskie ctype: ctype::_Do_narrow_s, ctype::_Do_widen_s, ctype::_narrow_s, ctype::_widen_s. Jeśli aplikacja korzysta z jednego z tych funkcji elementów członkowskich, należy zastąpić go z odpowiednią wersję niezabezpieczonego: ctype::do_narrow, ctype::do_widen, ctype::narrow, ctype::widen.  
  
### <a name="crt-mfc-and-atl-libraries"></a>CRT, MFC i ATL biblioteki  
  
-   Aby umożliwić użytkownikom tworzenie bibliotek CRT, MFC i ATL została usunięta obsługa. Na przykład plik odpowiednie nmake nie jest obsługiwane.                 Jednak użytkownicy nadal mieć dostęp do kodu źródłowego dla tych bibliotek. I dokument, który opisuje opcje MSBuild, używane przez firmę Microsoft do tworzenia biblioteki prawdopodobnie zostaną opublikowane w blogu zespołu Visual C++.  
  
-   Obsługa MFC dla IA64 została usunięta. Jednak nadal podano obsługę CRT i ATL na IA64.  
  
-   Porządkowe nie są już ponownie w plikach definicji modułu (.def) MFC. Ta zmiana oznacza porządkowe nie będzie różna wersje pomocnicze i zgodności plików binarnych dla dodatków service pack i szybkiej poprawki inżynierii wersjach zostanie poprawiona.  
  
-   Cdoctemplate — klasa dodano nowych funkcji wirtualnej. Jest to nowa funkcja wirtualnego [cdoctemplate — klasa](../mfc/reference/cdoctemplate-class.md). Poprzednia wersja OpenDocumentFile mają dwa parametry. Nowa wersja ma trzy parametry. Do obsługi Menedżera ponownego uruchomienia, każda klasa pochodzi od cdoctemplate — musi implementować wersji, która ma trzy parametry. Nowy parametr jest bAddToMRU.  
  
### <a name="macros-and-environment-variables"></a>Makra i zmienne środowiskowe  
  
-   __MSVCRT_HEAP_SELECT zmiennej środowiskowej nie jest już obsługiwana. Tej zmiennej środowiskowej zostanie usunięta i nie ma żadnych zastąpienia.  
  
### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler — odwołanie  
  
-   Kilka dyrektyw zostały usunięte z kompilatora Microsoft Macro Assembler — odwołanie. Usunięto dyrektywy są.186,.286, .286P.287,.8086,.8087, i. NO87.  
  
## <a name="visual-c-2008-breaking-changes"></a>Visual C++ 2008 najważniejszych zmian  
  
### <a name="compiler"></a>Kompilatora  
  
-   System operacyjny Windows 95, Windows 98, Windows ME i platformy systemu Windows NT nie są już obsługiwane. Te systemy operacyjne zostały usunięte z listy platformy docelowej.  
  
-   Kompilator nie obsługuje wiele atrybutów, które zostały bezpośrednio skojarzone z biblioteki ATL Server. Następujące atrybuty nie są już obsługiwane:  
  
    -   perf_counter  
  
    -   perf_object  
  
    -   Monitora wydajności  
  
    -   request_handler  
  
    -   soap_handler  
  
    -   soap_header  
  
    -   soap_method  
  
    -   tag_name  
  
### <a name="visual-c-projects"></a>Projekty Visual C++  
  
-   Podczas uaktualniania projektów z poprzednich wersji programu Visual Studio, może być konieczne modyfikowanie symboli WINVER i _WIN32_WINNT makra, aby były większe niż lub równa 0x0500.  
  
-   Począwszy od programu Visual Studio 2008, Kreator nowego projektu nie ma opcji tworzenia projektu C++ programu SQL Server. Projektów programu SQL Server utworzonych za pomocą wcześniejszej wersji programu Visual Studio będą nadal skompilować i działa poprawnie.  
  
-   Plik nagłówka Winable.h interfejsu API systemu Windows została usunięta. Zamiast tego zawierają Winuser.h.  
  
-   Biblioteka interfejsu API systemu Windows Rpcndr.lib została usunięta. Połącz z rpcrt4.lib zamiast tego.  
  
### <a name="crt"></a>CRT  
  
-   Została usunięta obsługa systemu Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4.0.  
  
-   Usunięto następujące zmienne globalne:  
  
    -   _osplatform  
  
    -   _osver  
  
    -   _winmajor  
  
    -   _winminor  
  
    -   _winver  
  
-   Następujące funkcje zostały usunięte. Zamiast tego użyć funkcji Windows API GetVersion lub GetVersionEx:  
  
    -   _get_osplatform  
  
    -   _get_osver  
  
    -   _get_winmajor  
  
    -   _get_winminor  
  
    -   _get_winver  
  
-   Składnia dla adnotacji SAL została zmieniona. Aby uzyskać więcej informacji, zobacz [adnotacji SAL](../c-runtime-library/sal-annotations.md).  
  
-   Filtr IEEE teraz obsługuje zestaw instrukcji SSE 4.1. Aby uzyskać więcej informacji, zobacz [_fpieee_flt —](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt —.  
  
-   Biblioteki wykonawcze języka C, które są dostarczane z programem Visual Studio nie są już zależne od msvcrt.dll biblioteki DLL systemu.  
  
### <a name="standard-library"></a>Standardowa biblioteka  
  
-   Została usunięta obsługa systemu Windows 95, Windows 98, Windows Millennium Edition i Windows NT 4.0.  
  
-   W przypadku kompilowania kodu w trybie debugowania z _HAS_ITERATOR_DEBUGGING zdefiniowane (zastąpiona [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010), aplikacji będzie teraz assert, gdy iteratora próbuje następuje zwiększenie lub zmniejszenie po granice podstawowej kontenera.  
  
-   C zmiennej elementu członkowskiego klasy stosu teraz jest zadeklarowany jako chroniony. Wcześniej ta zmienna elementu członkowskiego zadeklarowano publicznego.  
  
-   Zachowanie money_get::do_get zostało zmienione. Wcześniej podczas analizowania pieniężnego ilości do ułamek dłuższy niż są nazywane dla przez frac_digits, do_get pozwala korzystać z je wszystkie. Teraz do_get zatrzymuje analizowania po użyciu najwyżej frac_digits znaków.  
  
### <a name="atl"></a>ATL  
  
-   ATL nie może być wbudowane bez zależności w CRT. We wcześniejszych wersjach programu Visual Studio, można użyć #define atl_min_crt — aby Projekt ATL minimalny zestaw zależny od CRT. W programie Visual C++ 2008 wszystkie projekty ATL zależą od co najmniej CRT niezależnie od tego, czy atl_min_crt — jest zdefiniowane.  
  
-   Codebase serwera ATL zostało zwolnione jako projektu udostępnionego źródła w witrynie CodePlex i nie jest instalowany jako część programu Visual Studio. Dane kodowania i dekodowania klasy z funkcji atlenc.h i narzędzie i klasy z atlutil.h i atlpath.h były trzymane i są częścią biblioteki ATL. Kilka pliki skojarzone z serwerem ATL nie są już częścią programu Visual Studio.  
  
-   Niektóre funkcje znajdują się już w bibliotece DLL. Nadal znajdują się w bibliotece importu. Nie wpłynie to na kod, który używa funkcji statycznie. Ma wpływ na tylko kod, który używa tych funkcji dynamicznie.  
  
-   Makra PROP_ENTRY i PROP_ENTRY_EX zostały przestarzałe i zastępowane andPROP_ENTRY_TYPE_EX PROP_ENTRY_TYPE makra ze względów bezpieczeństwa.  
  
### <a name="atlmfc-shared-classes"></a>ATL/MFC udostępnionych klas  
  
-   ATL nie może być wbudowane bez zależności w CRT. We wcześniejszych wersjach programu Visual Studio, można użyć #define atl_min_crt — aby Projekt ATL minimalny zestaw zależny od CRT. W programie Visual C++ 2008 wszystkie projekty ATL zależą od co najmniej CRT niezależnie od tego, czy atl_min_crt — jest zdefiniowane.  
  
-   Codebase serwera ATL zostało zwolnione jako projektu udostępnionego źródła w witrynie CodePlex i nie jest instalowany jako część programu Visual Studio. Dane kodowania i dekodowania klasy z funkcji atlenc.h i narzędzie i klasy z atlutil.h i atlpath.h były trzymane i są częścią biblioteki ATL. Kilka pliki skojarzone z serwerem ATL nie są już częścią programu Visual Studio.  
  
-   Niektóre funkcje znajdują się już w bibliotece DLL. Nadal znajdują się w bibliotece importu. Nie wpłynie to na kod, który używa funkcji statycznie. Ma wpływ na tylko kod, który używa tych funkcji dynamicznie.  
  
### <a name="mfc"></a>MFC  
  
-   Ctime — klasa: Klasa ctime — teraz akceptuje daty, począwszy od 1/1/1900 r. N.E. zamiast 1/1/1970 r.              
-   Karta zlecenia formantów w oknach dialogowych MFC: kolejności poprawne wielu formantów w oknie dialogowym MFC jest rozproszonych była możliwa, jeśli formant MFC ActiveX jest wstawione w kolejności tabulacji. Ta zmiana rozwiązuje ten problem.  
  
     Na przykład można utworzyć aplikacji okna dialogowego MFC z formantu ActiveX i kilka formantów edycyjnych. Pozycja formantu ActiveX w środku kolejności kart formantów edycyjnych. Uruchom aplikację, kliknij przycisk edycji, których kolejność tabulacji po formantu ActiveX, a następnie kartę. Przed zmianą fokus poszło do kontrolki edycji następującego formantu ActiveX, zamiast następnej kontrolki edycji w kolejności tabulacji.  
  
-   Klasa CFileDialog: Szablony niestandardowe dla klasy CFileDialog nie może być automatycznie przenoszone do systemu Windows Vista. Są one nadal używać, ale nie ma dodatkowych funkcji lub wygląda dialogowych styl systemu Windows Vista.  
  
-   Klasa CWnd i cframewnd — klasa: metoda CWnd::GetMenuBarInfo został usunięty.  
  
     Metoda CFrameWnd::GetMenuBarInfo jest teraz metody niewirtualnej. Aby uzyskać więcej informacji zobacz GetMenuBarInfo Functionin zestaw Windows SDK.  
  
-   Obsługa MFC ISAPI: MFC nie obsługuje tworzenie aplikacji z Internetu ISAPI Server Application Programming Interface (). Jeśli chcesz utworzyć aplikację ISAPI, rozszerzenia ISAPI należy wywołać bezpośrednio.  
  
-   Przestarzałe interfejsy API ANSI: Wersje ANSI kilka metod MFC są przestarzałe. Użyj wersji Unicode tych metod w przyszłych aplikacji. Aby uzyskać więcej informacji zobacz Tworzenie wymagania dla Vista formanty standardowe systemu Windows.  
  
## <a name="visual-c-2005-breaking-changes"></a>Visual C++ 2005 najważniejszych zmian  
  
### <a name="crt"></a>CRT  
  
-   Wiele funkcji są przestarzałe. Zobacz funkcje CRT przestarzałe.  
  
-   Wiele funkcji teraz sprawdzić poprawność ich parametry zatrzymania wykonywania, jeśli wystąpi dane nieprawidłowe parametry. Może to spowodować uszkodzenie kodu, który przekazuje nieprawidłowe parametry i zależy od funkcji ich zignorowanie lub po prostu zwróciło kod błędu. Zobacz Sprawdzanie poprawności parametru.  
  
-   Wartość deskryptora pliku -2 jest teraz służy do wskazania, że stdout i stderr nie są dostępne dla danych wyjściowych, na przykład w aplikacji systemu Windows, która ma żadnego okna konsoli. Poprzedniej wartości, używana jest wartość -1. Aby uzyskać więcej informacji, zobacz [_fileno —](../c-runtime-library/reference/fileno.md).  
  
-   Jednowątkowe CRT bibliotek, libc.lib i libcd.lib, zostały usunięte. Użyj wielowątkowych bibliotek CRT. Flagi kompilatora/ml nie jest już obsługiwana. Blokowanie inne niż wersje niektóre funkcje zostały dodane w przypadkach, gdy jest potencjalnie znaczny różnica w wydajności wielowątkowe kod i kod jednowątkowy.  
  
-   Przeciążenie pow, double pow (int, int), został usunięty lepiej zgodności ze standardem.  
  
-   Specyfikator formatu %n nie jest obsługiwana przez domyślne w żadnym z rodziny printf funkcji, ponieważ jest z założenia niezabezpieczone. Domyślne zachowanie po napotkaniu %n jest program obsługi nieprawidłowych parametrów wywołania. Aby włączyć obsługę %n, użyj _set_printf_count_output — (również see_get_printf_count_output).  
  
-   sprintf — teraz drukuje znakiem minus podpisem zero.  
  
-   swprintf — został zmieniony na zgodne ze standardem; wymaga to teraz parametr rozmiaru. Formę swprintf — bez rozmiar parametru jest przestarzała.  
  
-   _set_security_error_handler została usunięta. Usuń wszystkie wywołania tej funkcji; domyślny program obsługi jest znacznie bezpieczniejsze sposób postępowania z błędami zabezpieczeń.  
  
-   time_t — jest teraz wartość 64-bitowa (o ile nie zdefiniowano _USE_32BIT_TIME_T).  
  
-   _Spawn, _wspawn — funkcje teraz pozostaw errno bez zmian w przypadku powodzenia, określony przez C Standard.  
  
-   RTC domyślnie używa teraz znaki dwubajtowe.  
  
-   Funkcje obsługi słowo formantu zmiennoprzecinkowe są przestarzałe dla aplikacji skompilowanych z/CLR lub/CLR: PURE. Dotyczy funkcji są _clear87 —, _clearfp —, _control87 —, _controlfp —, _fpreset —, _status87 —, _statusfp —. Ostrzeżenie można wyłączyć, definiując _CRT_MANAGED_FP_NO_DEPRECATE, ale korzystanie z tych funkcji w kodzie zarządzanym jest nieprzewidywalne i nieobsługiwane.  
  
-   Niektóre funkcje zwracają teraz const wskaźników. Definiując _CONST_RETURN można cofać zachowanie stare, wartością stałą. Dotyczy funkcji  
  
    1.  memchr, wmemchr  
  
    2.  strchr, wcschr, _mbschr, _mbschr_l  
  
    3.  strpbrk, wcspbrk, _mbspbrk, _mbspbrk_l  
  
    4.  strrchr, wcsrchr, _mbsrchr, _mbsrchr_l  
  
    5.  strstr, wcsstr, _mbsstr, _mbsstr_l  
  
-   Podczas łączenia z Setargv.obj lub Wsetargv.obj, go nie jest już możliwe do pomijania rozszerzenie symbolu wieloznacznego w wierszu polecenia należy ująć w podwójny cudzysłów. Aby uzyskać więcej informacji, zobacz [rozszerzanie argumentów z symbolami wieloznacznymi](../c-language/expanding-wildcard-arguments.md).  
  
### <a name="standard-library-2005"></a>Biblioteki standardowej (2005)  
  
-   Klasy wyjątków (znajdujące się w \<wyjątku > Nagłówek) została przeniesiona do przestrzeni nazw std. W poprzednich wersjach ta klasa została w globalnej przestrzeni nazw. Aby rozwiązać wszelkie błędy wskazujące, że nie można znaleźć klasy wyjątków, Dodaj następujący kod przy użyciu instrukcji w kodzie: za pomocą przestrzeni nazw std;  
  
-   Podczas wywoływania metody valarray::resize(), zawartość valarray — zostaną utracone i zostaną zastąpione wartościami domyślnymi. Metoda resize() jest przeznaczona do ponownego inicjowania valarray — zamiast zwiększanie jak wektora.  
  
-   Iteratory debugowania: Aplikacje utworzone za pomocą debugowania wersji biblioteki środowiska uruchomieniowego C i które Iteratory użycia niepoprawnie może zacząć Zobacz potwierdzeń w czasie wykonywania. Aby wyłączyć te potwierdzeń, należy zdefiniować _HAS_ITERATOR_DEBUGGING (zastąpiona [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) po Visual Studio 2010) na 0. Aby uzyskać więcej informacji, zobacz [Obsługa iteratora debugowania](../standard-library/debug-iterator-support.md)  
  
## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003 najważniejszych zmian  
  
### <a name="compiler"></a>Kompilatora  
  
-   Zamykanie nawiasów teraz wymagane dla określonych dyrektywy preprocesora (C2004).  
  
-   Jawne specjalizacje nie jest już Znajdź parametry szablonu z szablonu podstawowego ([C2146 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2146.md)).  
  
-   Chroniony element członkowski (n) można uzyskać tylko za pośrednictwem funkcji członkowskiej klasy, która dziedziczy po klasie (A), w której (n) jest elementem członkowskim (B) ([C2247 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2247.md)).  
  
-   Sprawdzanie dostępności ulepszone w kompilatorze teraz wykrywać niedostępny klas podstawowych ([C2248 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2248.md)).  
  
-   Nie można przechwycić wyjątek, jeśli destruktor i/lub kopiowania Konstruktor jest niedostępny (C2316).  
  
-   Domyślne argumenty dotyczące wskaźników do funkcji już dozwolone ([C2383 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2383.md)).  
  
-   Nie można zainicjować statycznego elementu członkowskiego danych za pośrednictwem pochodnej klasy ([C2477 błąd kompilatora](../error-messages/compiler-errors-1/compiler-error-c2477.md)).  
  
-   Inicjowanie jako element typedef nie jest dozwolona przez standardowe i generuje błąd kompilatora ([C2513 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c2513.md)).  
  
-   bool jest teraz odpowiedniego typu ([C2632 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c2632.md)).  
  
-   UDC można teraz utworzyć niejednoznaczności z przeciążone operatory ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md)).  
  
-   Wyrażenia więcej teraz są traktowane jako prawidłowego wskaźnika null — stałe ([C2668 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c2668.md)).  
  
-   Szablon <> teraz jest wymagany w miejscach, w którym kompilator wcześniej oznaczałoby go ([C2768 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c2768.md)).  
  
-   Specjalizacja expilicit ourside funkcja elementu członkowskiego klasy jest nieprawidłowa, jeśli funkcja już został jawnie specjalizowany za pośrednictwem specjalizacji szablonu klasy ([C2910 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c2910.md)).  
  
-   Przestawne parametrów szablonu bez typu punktów nie są już dozwolone ([C2993 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c2993.md)).  
  
-   Szablony klas nie są dozwolone jako argumentów typu szablonu (C3206).  
  
-   Przyjazne nazwy funkcji nie są wprowadzane do zawierającą przestrzeń nazw ([C3767 błąd kompilatora](../error-messages/compiler-errors-2/compiler-error-c3767.md)).  
  
-   Kompilator nie będzie akceptował dodatkowe przecinkami w makrze (C4002).  
  
-   Obiekt typu POD skonstruowany przy użyciu inicjatora formy () będzie inicjowany domyślnie (C4345).  
  
-   Nazwa typu jest teraz wymagany, jeśli zależna nazwa jest traktowane jako typ ([C4346 ostrzeżenie kompilatora (poziom 1)](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md)).  
  
-   Funkcje, które zostały nieprawidłowo uznany za specjalizacji szablonu nie są traktowane jako tak (C4347).  
  
-   Statyczne elementy członkowskie danych nie można zainicjować za pomocą klasy pochodnej (C4356).  
  
-   Specjalizacja szablonu klasy musi być zdefiniowane przed została użyta w zwracany typ ([C4686 ostrzeżenie kompilatora (poziom 3)](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md)).  
  
-   Kompilator zgłasza teraz nieosiągalny kod (C4702).  
  
## <a name="see-also"></a>Zobacz też  
[Nowości w języku Visual C++ w programie Visual Studio](../what-s-new-for-visual-cpp-in-visual-studio.md)
