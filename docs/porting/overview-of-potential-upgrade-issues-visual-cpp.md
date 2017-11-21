---
title: "Omówienie potencjalne problemy z uaktualnieniem (Visual C++) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 977c13eabe0f25081b1bfe6b25e615002f0e6987
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Omówienie potencjalne problemy z uaktualnieniem (Visual C++)
Całościowo kompilatora Visual C++ wprowadzono wiele zmian oraz zmian w samego języka C++, standardowa biblioteka C++, C runtime (CRT) i innych bibliotek, takie jak MFC i ATL. W związku z tym podczas uaktualniania aplikacji z wcześniejszej wersji programu Visual C++ może wystąpić kompilatorze i konsolidatorze błędów i ostrzeżeń w kodzie, który wcześniej skompilowany prawidłowo. Starsze oryginalny kod podstawowy, oznacza większe możliwości takie błędy. W tym omówieniu przedstawiono klasy najbardziej typowe problemy, które prawdopodobnie mogą wystąpić, oraz udostępniono linki do bardziej szczegółowych informacji.  
  
 Uwaga: W przeszłości firma Microsoft rekomendowanie uaktualnień, które obejmują kilka wersji programu Visual Studio powinna być wykonywana stopniowo jednej wersji w czasie. Nie zalecamy tej metody. Znaleźliśmy się, że prawie zawsze jest prostsza do uaktualnienia do najnowszej wersji programu Visual Studio niezależnie od tego, jak stare bazowej kodu.  
  
 Pytania lub komentarze dotyczące procesu uaktualnienia mogą być wysyłane do vcupgrade firmy Microsoft.  
  
## <a name="library-and-toolset-dependencies"></a>Zależności biblioteki i zestawu narzędzi  
 Podczas uaktualniania aplikacji do nowej wersji kompilatora Visual C++, zdecydowanie zaleca się i w wielu przypadkach trzeba również uaktualnić wszystkie biblioteki i bibliotek DLL, które łączy aplikacji. Wymaga to, czy masz dostęp do kodu źródłowego, lub że biblioteki dostawcy może zapewniać nowych plików binarnych skompilowane z taką samą wersję główną kompilatora Visual C++. Jeśli spełniony jest jeden z tych warunków, można pominąć w tej sekcji, która zajmuje się szczegóły zgodności plików binarnych. Jeśli żadna z są case, może nie być możliwe przy użyciu bibliotek w uaktualnionym aplikacji. Informacje przedstawione w tej sekcji pomoże zrozumieć, czy można kontynuować proces uaktualniania.  
  
### <a name="toolset"></a>Zestaw narzędzi  
 Formaty plików obj i lib są dobrze zdefiniowany i rzadko zmiany. Czasami dodawane są w tych formatach plików, ale te dodatki zazwyczaj nie ma wpływu na możliwość korzystania z plików obiektu i bibliotek utworzone przez starszą procesami nowszej procesami. W tym miejscu jedynym wyjątkiem big jest Jeśli kompilacja przy użyciu /GL (Generowanie kodu w czasie konsolidacji / optymalizacja całego programu). Jeśli kompilacja przy użyciu /GL, wynikowy plik obiektu może odnosić się tylko przy użyciu tego samego zestawu narzędzi, którego użyto do jego utworzenia. Tak Jeśli można utworzyć pliku obiektu z opcją /GL i przy użyciu kompilatora Visual Studio 2017 (v141), należy połączyć za pomocą konsolidatora Visual Studio 2017 (v141). Jest to spowodowane struktur danych wewnętrznych obiektów /GL nie są stabilne przez główne wersje zestawu narzędzi i nowszej procesami nie rozumie starsze formaty danych.  
  
 C++ nie ma aplikacji stabilna interfejsu binarne (ABI). Visual C++ obsługuje stabilna ABI dla wszystkich wersji pomocniczych wersji. Na przykład Visual Studio 2017 i wszystkie jego aktualizacje są zgodne binarnego. Ale ABI nie jest zawsze zgodny w wersjach głównych programu Visual C++ (z wyjątkiem 2015 i 2017, które _są_ zgodne dane binarne). Oznacza to, że możemy wprowadzić przełomowe zmiany układu typu C++, nazwij dekorację, obsługa wyjątków i innych części interfejsie ABI języka C++. W związku z tym jeśli plik obiektu, który zawiera symboli zewnętrznych z powiązaniem C++, ten plik obiektu może łączą poprawnie z plikami obiekt utworzony z różnych wersji głównej zestaw narzędzi Visual C++. Należy pamiętać, że w tym miejscu "może nie działać" ma wiele możliwych wartości: link może się nie powieść całkowicie (np. zmiana nazwij dekorację), może się powieść, łącze i czynności może nie działać w czasie wykonywania (np. zmiana typu układu), lub rzeczy może mieć miejsce, do pracy w wielu przypadkach i nic nie zostanie umieszczona wro NG. Należy pamiętać, że podczas interfejsie ABI języka C++ nie jest stabilna C ABI i podzbiór interfejsie ABI języka C++ wymagane dla modelu COM są stałe.  
  
### <a name="libraries"></a>Biblioteki  

 Jeśli kompilacja pliku źródłowego za pomocą konkretnej wersji nagłówki bibliotek języka Visual C++ (przez #including nagłówki), plik wynikowy obiekt musi być połączony z tej samej wersji bibliotek języka Visual C++. Tak, na przykład, jeśli plik źródłowy jest skompilowana przy użyciu programu Visual Studio 2017 \<immintrin.h >, należy połączyć z biblioteki vcruntime programu Visual Studio 2017 r. Podobnie jeśli plik źródłowy jest skompilowana przy użyciu programu Visual Studio 2017 \<iostream >, należy połączyć z biblioteki programu Visual Studio 2017 Standard C++, msvcprt. Mieszanie i dopasowywania nie jest obsługiwane.  
  
 Standardowe biblioteki C++, mieszania i dopasowywania został jawnie zabroniony wykorzystaniem `#pragma detect_mismatch` w standardowych nagłówków od programu Visual Studio 2010. Jeśli użytkownik próbuje połączyć pliki niezgodny obiekt lub próba łączyć się z niewłaściwego biblioteki standardowej łącze zakończy się niepowodzeniem.  
  
 CRT mieszania i dopasowywania nigdy nie było obsługiwane, ale często działał, co najmniej do programu Visual Studio 2015 i uniwersalne środowisko CRT, ponieważ nie zmieniły się znacznie w czasie powierzchni interfejsu API. Uniwersalne środowisko CRT spowodowało przerwanie zapewnienia zgodności, aby w przyszłości firma Microsoft może zapewnić wstecz zgodność. Innymi słowy nie mamy żadnych planów wprowadzenie nowych wersji w przyszłości Universal CRT plików binarnych.. Zamiast tego istniejących uniwersalne środowisko CRT jest teraz zaktualizować w miejscu.  
  
 Ze względu na zgodność częściowe łącza z obiektu plików (i biblioteki) skompilowany ze starszymi wersjami programu Microsoft C Runtime nagłówków, firma Microsoft udostępnia bibliotekę legacy_stdio_definitions.lib, z programu Visual Studio 2015 i nowszych. Ta biblioteka zawiera symbole zgodności dla większości eksportuje funkcji i danych, które zostały usunięte z Universal CRT. Zestaw symboli zgodności dostarczonych przez legacy_stdio_definitions.lib jest niewystarczająca do zapewnienia większości zależności, w tym wszystkie zależności w biblioteki dołączony do zestawu SDK systemu Windows. Istnieją jednak niektóre symbole, które zostały usunięte z Universal CRT, dla których nie jest możliwe zapewnienie zgodności symbole, takie jak to. Niektóre funkcje obejmują te symbole (np. \_ \_iob —\_func) i eksportuje dane (np. \_ \_— Importowanie pakietu administracyjnego\_\_\_iob —, \_ \_— Importowanie pakietu administracyjnego\_\_\_pctype —, \_ \_— Importowanie pakietu administracyjnego\_\_\_mb\_Waluta\_maksymalnej).  
  
 Jeśli masz bibliotekę statyczną, który został utworzony przy użyciu starszej wersji środowiska uruchomieniowego C nagłówków, zaleca się następujące działania (w podanej kolejności):  
  
1.  Odbuduj biblioteki statycznej przy użyciu programu Visual C++ 2017 i nagłówki Universal CRT do obsługi połączeń z Universal CRT. Jest to opcja pełnej (i w związku z tym najlepszym).  
  
2.  Jeśli nie (lub nie chcesz) odbudować biblioteki statycznej, możesz spróbować łączenie z legacy_stdio_definitions.lib. Spełnia łącza — czas zależności biblioteki statyczne, należy dokładnie przetestować z biblioteką statyczną, ponieważ jest używany w danych binarnych, aby upewnić się, że nie ma go negatywnego wpływu na żadnego z [wprowadzone do zmiany zachowania Uniwersalne środowisko CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).  
  
3.  Jeśli biblioteka statyczna zależności nie są spełnione przez legacy_stdio_definitions.lib lub jeśli biblioteka nie działa z Universal CRT z powodu wyżej wymienione zmiany funkcjonalne, zalecamy hermetyzując biblioteki statycznej do biblioteki DLL które Link w odpowiedniej wersji programu Microsoft C Runtime. Na przykład jeśli biblioteka statyczna został utworzony za pomocą programu Visual C++ 2013, czy chcesz zbudować tę bibliotekę DLL przy użyciu programu Visual C++ 2013 i w bibliotekach Visual C++ 2013. Tworzenie biblioteki do biblioteki DLL, możesz hermetyzować szczegółów implementacji, który jest jego zależność od określonej wersji środowiska uruchomieniowego Microsoft C. (Należy zauważyć, że można należy zachować ostrożność, że interfejsu biblioteki DLL nie nastąpił przeciek szczegółowe informacje, które C środowiska uruchomieniowego używa, np. przez zwrócenie plik * w poprzek granic DLL lub zwracającej wskaźnik przydzielone — funkcja malloc i Oczekiwany obiekt wywołujący, aby zwolnić go).  
  
 Korzystanie z wielu im monitory CRT w ramach jednego procesu jest nie znajduje się w i samego siebie problematyczne (w rzeczywistości większość procesów zakończą się ładowanie wielu CRT bibliotek DLL; na przykład systemu Windows, składników systemu operacyjnego będzie zależeć od msvcrt.dll i środowisko CLR będzie zależeć od własnej prywatnej CRT). Problemów podczas jumble stan z innego im monitory CRT. Na przykład nie należy przydzielić pamięci przy użyciu msvcr110.dll!malloc i próba cofnięcie przydziału pamięci, przy użyciu msvcr120.dll!free, i nie powinny podejmować próbę otwarcia pliku przy użyciu msvcr110! fopen — i próba odczytania od tego pliku przy użyciu msvcr120! fread —. Tak długo, jak nie jumble stan z innego im monitory CRT, można bezpiecznie ma wiele im monitory CRT, które są ładowane w ramach jednego procesu.  
  
 Aby uzyskać więcej informacji, zobacz [uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md).  
  
## <a name="errors-due-to-project-settings"></a>Błędy z powodu ustawienia projektu  
 Aby rozpocząć proces uaktualniania, po prostu otworzyć starsze projektu/rozwiązania/obszar roboczy w najnowszej wersji programu Visual Studio. Visual Studio utworzy nowy projekt na podstawie ustawień starego projektu. Jeśli starsze projektu biblioteki lub zawierać ścieżek, które są zakodowane na stałe w lokalizacjach niestandardowych, jest to możliwe, że pliki w tych ścieżkach będzie widoczny w kompilatorze projekt używa ustawień domyślnych. Aby uzyskać więcej informacji, zobacz [ustawienia konsolidatora OutputFile](porting-guide-spy-increment.md#linker_output_settings).  
  
 Ogólnie rzecz biorąc obecnie jest to doskonały moment na poprawnie uporządkowanie kodu projektu Aby uprościć zarządzanie projektu i ułatwiają rozpoczęcie uaktualnionego kodu kompilowanie możliwie jak najszybciej. Jeśli kod źródłowy jest już dobrą organizację, a starsze projektu jest skompilowana z programu Visual Studio 2010 lub nowszej, można ręcznie edytować plik projektu do obsługi kompilacji w starym i nowym kompilatora. Poniższy przykład przedstawia sposób kompilacji dla programu Visual Studio 2015 i Visual Studio 2017:  
  
```  
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>  
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>   
```  
  
### <a name="lnk2019-unresolved-external"></a>LNK2019: Nierozpoznany zewnętrzny  
 Dla nierozpoznane symbole konieczne może być napraw ustawień projektu.  
  
-   Dołącz katalogi, jeśli plik źródłowy znajduje się w lokalizacji innej niż domyślna, czy należy dodać ścieżkę do projektu?  
  
-   Jeśli zewnętrznej jest zdefiniowany w pliku .lib, mieć określona ścieżka lib we właściwościach projektu i jest prawidłową wersją pliku lib rzeczywiście znajduje się tam?  
  
-   Podjęto próbę łącza do pliku .lib, który został skompilowany z różnych wersji programu Visual Studio? Jeśli tak, zobacz poprzednią sekcję zależności biblioteki i zestawu narzędzi.  
  
-   Typy argumentów w wywołaniu lokacji faktycznie zgadzają się z istniejącą przeciążenia funkcji? Sprawdź, czy są typy bazowe dla dowolnego definicje typów w funkcji podpisu i kod, który wywołuje funkcję oczekiwań je.  
  
 Rozwiązywanie problemów nierozwiązanych symbolu, można spróbować użyć dumpbin.exe do sprawdzenia symbole zdefiniowane w pliku binarnym. Spróbuj wykonać następujące polecenie, aby wyświetlić symbole zdefiniowane w bibliotece:  
  
```  
dumpbin.exe /LINKERMEMBER somelibrary.lib  
```  
  
### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)  
 (W programie Visual C++ 6.0 i starszych wchar_t nie została zaimplementowana jako typ wbudowany, ale został zadeklarowany w wchar.h jako typedef skrócie bez znaku). C++ standard wymaga tego wchar_t jest typem wbudowanym. Przy użyciu wersji — typedef może spowodować problemy z przenośnością. Jeśli uaktualnienie z wcześniejszych wersji programu Visual C++ i wystąpi błąd kompilatora C2664, ponieważ kod próbuje niejawnie konwertowane wchar_t krótkiej bez znaku, zaleca się zmieniania kod, aby naprawić błąd, a ustawienie /Zc:wchar_t-. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).  
  
### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Uaktualnianie przy użyciu opcji konsolidatora/nodefaultlib/Entry i/noentry  
 Opcja konsolidatora/nodefaultlib (lub właściwość konsolidatora Ignoruj wszystkie domyślne biblioteki) informuje konsolidator, które nie mają być automatycznie połączone biblioteki domyślne, takie jak CRT. Oznacza to, że każdej biblioteki ma był wyświetlany jako dane wejściowe pojedynczo. Ta lista bibliotek znajduje się we właściwości dodatkowe zależności, w sekcji konsolidatora właściwości projektu.  
  
 Projekty, które używają tej opcji stanowi problem podczas uaktualniania, ponieważ zmieniono nazwy niektórych bibliotek domyślnych. Ponieważ każdej biblioteki musi znajdować się we właściwości dodatkowe zależności lub w wierszu polecenia konsolidatora, należy zaktualizować listę bibliotek, aby użyć bieżącej nazwy.  
  
 W poniższej tabeli przedstawiono bibliotek, których nazwy zmienione w programie Visual Studio 2015. Do uaktualnienia, należy zastąpić nazwy w pierwszej kolumnie nazwy w drugiej kolumnie.  Niektóre z tych bibliotek są biblioteki importu, ale który nie ma znaczenia.  
  
|||  
|-|-|  
|W przypadku używania:|Należy zastąpić go ciągiem:|  
|libcmt.lib|libucrt.lib, libvcruntime.lib|  
|biblioteki libcmtd.lib|libucrtd.lib, libvcruntimed.lib|  
|Msvcrt.lib|ucrt.lib, vcruntime.lib|  
|msvcrtd.lib|ucrtd.lib, vcruntimed.lib|  
  
 Ten sam problem dotyczy również za pomocą opcji/Entry lub opcja/noentry mających wpływ pomijanie biblioteki domyślne.  
  
## <a name="errors-due-to-improved-language-conformance"></a>Błędy ze względu na zgodność języka ulepszone  
 Kompilator Visual C++ stale ulepszono jego zgodność C++ standard całościowo. Kod, który skompilowany w starszych wersjach programu Visual C++ może zakończyć się niepowodzeniem do kompilowania w programie Visual Studio 2017, ponieważ kompilator prawidłowo flagi błąd, który wcześniej został zignorowany, lub jawnie dozwolone.  
  
 Na przykład przełącznika/Zc: forscope została wprowadzona w historii Visual C++. Umożliwia ona niezgodnych zachowanie zmiennych pętli. Ten przełącznik jest teraz przestarzałe i może zostać usunięta w przyszłych wersjach. Zdecydowanie zaleca się aby nie używać tego przełącznika podczas uaktualniania kodu. Aby uzyskać więcej informacji, zobacz [/Zc:forScope-jest przestarzały](porting-guide-spy-increment.md#deprecated_forscope).  
  
 Jednym z przykładów typowych napotkać podczas uaktualniania jest argument z systemem innym niż stała jest przekazany do parametru const błąd kompilatora. Starsze wersje programu Visual C++ nie zawsze oznaczał to jako błąd. Aby uzyskać więcej informacji, zobacz [konwersje ściślejsze kompilatora](porting-guide-spy-increment.md#stricter_conversions).  
  
 Uzyskać więcej informacji o zgodności określonego ulepszenia, zobacz [Historia 2003 2015 zmian Visual C++](visual-cpp-change-history-2003-2015.md) i [ulepszenia zgodność języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md).  
  
## <a name="errors-involving-stdinth-integral-types"></a>Błędy dotyczące \<stdint.h > Typy całkowite  
 \<Stdint.h > nagłówka definiuje definicje typów i makra, które, w przeciwieństwie do wbudowanych typów całkowitych, mogą mieć określonej długości na wszystkich platformach. Oto kilka przykładów uint32_t i int64_t. Visual C++ dodane \<stdint.h > w programie Visual Studio 2010. Kodu napisanego przed 2010 udostępnionych prywatnej definicje dla tych typów i definicje może nie być zgodne z \<stdint.h > definicje.  
  
 Jeśli błąd jest C2371 i jest elementem typu stdint, prawdopodobnie oznacza to, że typ jest zdefiniowany w nagłówku, kodu lub pliku lib innych firm.  Podczas uaktualniania, należy usunąć wszelkie niestandardowe definicje \<stdint.h > typów, ale pierwszy porównania niestandardowe definicje do bieżącej definicji standardowe zapewnienie nie udostępniono nowe problemy.  
  
 Można nacisnąć klawisz F12 **przejdź do definicji** aby zobaczyć, których zdefiniowano danego typu.  
  
 [/Showincludes](../build/reference/showincludes-list-include-files.md) — opcja kompilatora mogą być przydatne w tym miejscu. W oknie dialogowym stron właściwości projektu, otwórz **C/C++**, **zaawansowane** strony i ustaw **Pokaż obejmuje** do **tak**. Następnie ponownie skompiluj projekt i wyświetlić listę #includes w oknie danych wyjściowych.  Każdy nagłówek tworzone jest wcięcie pod nagłówkiem, która go zawiera.  
  
## <a name="errors-involving-crt-functions"></a>Błędy funkcje CRT  
 Wprowadzono wiele zmian do środowiska wykonawczego C latach. Wiele wersji bezpieczne funkcje zostały dodane, a niektóre zostały usunięte. Ponadto zgodnie z opisem we wcześniejszej części tego artykułu, implementacji CRT firmy Microsoft został zrefaktoryzowany w programie Visual Studio 2015 do nowych danych binarnych i skojarzone .lib — pliki.  
  
 Jeśli błąd obejmuje funkcji CRT, wyszukaj [Historia 2003 2015 zmian Visual C++](visual-cpp-change-history-2003-2015.md) lub [ulepszenia zgodność języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md) Jeśli te tematy zawierają informacje dodatkowe. Jeśli błąd jest LNK2019, nierozpoznany zewnętrzny, upewnij się, że funkcja nie została usunięta. W przeciwnym razie, gdy funkcja nadal istnieje, czy kod wywołujący jest poprawny, sprawdź, czy projekt używa/nodefaultlib. Jeśli tak, należy zaktualizować na liście bibliotek, tak, że projekt korzysta z nowych uniwersalnych bibliotek (Biblioteka UCRT). W bibliotece i zależności, aby uzyskać więcej informacji, zobacz sekcję powyżej.  
  
 Błąd obejmuje printf lub scanf, upewnij się, czy nie prywatnie definiujesz albo funkcja bez uwzględniania stdio.h. Jeśli tak, Usuń definicje prywatnych lub łącze do legacy_stdio_definitions.lib (projektu &#124; Właściwości &#124; Konsolidatora &#124; Dane wejściowe konsolidatora). Jeśli łączysz się z systemem Windows 8.1 SDK lub starszym, Dodaj legacy_stdio_definitions.lib.  
  
 Jeśli błąd obejmuje argumenty ciągu formatu, prawdopodobnie kompilator jest bardziej restrykcyjne o wymuszania standardowego. Zobacz historię zmian, aby uzyskać więcej informacji. Zapłać szczególną uwagę na błędy w tym miejscu, ponieważ potencjalnie reprezentują zagrożenie bezpieczeństwa.  
  
## <a name="errors-due-to-changes-in-the-c-standard"></a>Błędy z powodu zmian w standardowym języku C++  
 Standard C++, sama powstał w sposób, w którym nie zawsze są zgodne z poprzednimi wersjami. Wprowadzenie C ++ 11 semantyki przenoszenia, nowych słów kluczowych i inne języka oraz funkcje standardowej biblioteki mogą potencjalnie spowodować błędy kompilatora i nawet zachowania w czasie wykonywania różnych.  
  
 Na przykład starego programu C++ może obejmować iostream.h nagłówka. Ten nagłówek została uznana za przestarzałą historię C++ na początku i ostatecznie została całkowicie usunięta z języka Visual C++. W takim przypadku należy użyć \<iostream > i ponownie swój kod. Aby uzyskać więcej informacji, zobacz [aktualizowanie poprzedni kod iostream](porting-guide-spy-increment.md#updating_iostreams_code).  
  
### <a name="c4838-narrowing-conversion-warning"></a>C4838: ostrzeżenie konwersja zawężająca  
 C++ standard teraz Określa, że konwersje z niepodpisanych podpisem wartości całkowite są traktowane jako zawężanie konwersji. Kompilator Visual C++ nie wygenerował ostrzeżenie przed Visual Studio 2015. Należy sprawdzić każde wystąpienie, aby upewnić się, czy zawężającej, będzie mieć wpływu na poprawność kodu.  
  
## <a name="warnings-to-use-secure-crt-functions"></a>Ostrzeżenia, aby używać bezpiecznego funkcje CRT  
 Całościowo bezpieczne wersje funkcji środowiska wykonawczego języka C zostały wprowadzone. Mimo że nadal dostępne są wersje stare, niezabezpieczone, zaleca się zmienić swój kod, aby używać bezpiecznego wersji. Kompilator zgłosi ostrzeżenie dotyczące użycia niezabezpieczonego wersji. Można wyłączyć lub zignorować ostrzeżenia. Aby wyłączyć ostrzeżenia dla wszystkich projektów w rozwiązaniu, otwórz **widoku &#124; Menedżer właściwości**, wybierz wszystkie projekty, do których chcesz wyłączyć ostrzeżenia, a następnie kliknij prawym przyciskiem myszy wybrane elementy i wybierz polecenie **właściwości &#124; C/C++ &#124; Zaawansowane &#124; Wyłącz określone ostrzeżenia**. Kliknij strzałkę listy rozwijanej, a następnie kliknij przycisk Edytuj. Wprowadź 4996 w polu tekstowym. (Nie obejmuje prefiksu "C"). Aby uzyskać więcej informacji, zobacz [przenoszenie do użycia bezpiecznego CRT](porting-guide-spy-increment.md#porting_to_secure_crt).  
  
## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Błędy z powodu zmian w interfejsów API systemu Windows lub przestarzałe zestawów SDK  
 Całościowo interfejsów API systemu Windows i typy danych zostały dodane, a czasami zmienić lub usunąć. Ponadto innych zestawów SDK, które nie należą do podstawowego systemu operacyjnego mają pochodzić i usunięty. Starsze programy, w związku z tym może zawierać wywołania interfejsów API, który już istnieje. Może również zawierać wywołania interfejsów API w innych SDKs firmy Microsoft, które nie są już obsługiwane.  Jeśli zostanie wyświetlony błąd, interfejs API systemu Windows lub interfejsu API z starsze SDK firmy Microsoft, jest to możliwe, że interfejsu API został usunięty lub zastąpiony przez funkcję nowsze, bardziej bezpieczne.  
  
 Aby uzyskać więcej informacji na temat bieżącego interfejsu API ustawić i minimalnych obsługiwanych systemów operacyjnych dla określonego interfejsu API systemu Windows, zobacz [indeksu interfejsu API systemu Windows](https://msdn.microsoft.com/en-us/library/ff818516\(v=vs.85\).aspx) i przejdź do danego interfejsu API.  
  
### <a name="windows-version"></a>Wersja systemu Windows  
 Podczas uaktualniania program, który używa interfejsu API systemu Windows, bezpośrednio lub pośrednio, należy określić minimalną wersję systemu Windows do obsługi. W większości przypadków systemu Windows 7 jest dobrym rozwiązaniem. Aby uzyskać więcej informacji, zobacz [problemów pliku nagłówka](porting-guide-spy-increment.md#header_file_problems). Makro WINVER definiuje najstarszą wersję systemu Windows, program przeznaczony do uruchamiania na. Jeśli MFC program ustawia WINVER 0x0501 (z systemem Windows XP) możesz zostanie wyświetlone ostrzeżenie, ponieważ MFC nie obsługuje już XP, nawet jeśli sam kompilator ma XP mode.  
  
 Aby uzyskać więcej informacji, zobacz [aktualizowanie docelową wersję systemu Windows](porting-guide-spy-increment.md#updating_winver) i [więcej nieaktualne pliki nagłówkowe](porting-guide-spy-increment.md#outdated_header_files).  
  
## <a name="atl--mfc"></a>ATL / MFC  
 ATL i MFC są stosunkowo stabilna interfejsów API, ale zmiany zostały wprowadzone od czasu do czasu. Zobacz [Historia 2003 2015 zmian Visual C++](visual-cpp-change-history-2003-2015.md) Aby uzyskać więcej informacji i [nowości w języku Visual C++ w programie Visual Studio 2017](../what-s-new-for-visual-cpp-in-visual-studio.md) i [ulepszenia zgodność języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md).  
  
### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 już zdefiniowana w MSVCRTD.lib  
 Ten błąd może wystąpić w aplikacjach MFC. Wskazuje problem porządkowania między biblioteki CRT biblioteki MFC. MFC musi być połączona najpierw, dzięki czemu zapewnia new i delete — operatory. Aby naprawić błąd, należy użyć przełącznika/nodefaultlib ignoruje te domyślne biblioteki: MSVCRTD.lib i mfcs140d.lib. Następnie należy dodać te tej samej biblioteki jako dodatkowe zależności.  
  
## <a name="32-vs-64-bit"></a>64-bitowej wersji programu vs 32  
 Jeśli oryginalny kod jest skompilowany dla systemów 32-bitowych, istnieje możliwość tworzenia 64-bitowej wersji zamiast lub oprócz nowej aplikacji 32-bitowych. Ogólnie rzecz biorąc należy uzyskać pierwszy program kompilowania kodu w trybie 32-bitowym, a następnie spróbuj 64-bitowych. Kompilowanie dla 64-bitowych jest proste, ale w niektórych przypadkach może ujawnić usterki, które zostały ukryte w wersjach 32-bitowych.  
  
 Ponadto należy pamiętać o możliwych problemach kompilacji i środowiska uruchomieniowego dotyczące rozmiaru wskaźnika, czas i wartości rozmiaru i specyfikatory formatu w funkcje printf i scanf. Aby uzyskać więcej informacji, zobacz [skonfigurować Visual C++ dla 64-bitowy, x64 cele](../build/configuring-programs-for-64-bit-visual-cpp.md) i [problemy przy migracji wspólnej Visual C++-x 64](../build/common-visual-cpp-64-bit-migration-issues.md). Aby uzyskać wskazówki dotyczące migracji dodatkowych, zobacz [przewodnik programowania w języku dla 64-bitowym systemie Windows](https://msdn.microsoft.com/library/windows/desktop/bb427430\(v=vs.85\).aspx).  
  
## <a name="unicode-vs-mbcsascii"></a>Unicode a MBCS/ASCII  
 Przed Unicode został znormalizowany, ustaw znaków wielobajtowych (MBCS) jest wiele programów używana do reprezentowania znaki, które nie zostały dołączone do zestawu znaków ASCII. W starszych projektach MFC MBCS był ustawienie domyślne, a po uaktualnieniu takiego programu będą wyświetlane ostrzeżenia, które zalecamy, aby zamiast niej używać Unicode. Można wyłączyć lub zignorować to ostrzeżenie, jeśli zdecydujesz, że konwersji na format Unicode nie jest warto programowanie kosztów. Aby ją wyłączyć dla wszystkich projektów w rozwiązaniu, otwórz **widoku &#124; Menedżer właściwości**, wybierz wszystkie projekty, do których chcesz wyłączyć ostrzeżenia, a następnie kliknij prawym przyciskiem myszy wybrane elementy i wybierz polecenie **właściwości &#124; C/C++ &#124; Zaawansowane &#124; Wyłącz określone ostrzeżenia**. Kliknij strzałkę listy rozwijanej, a następnie kliknij przycisk Edytuj. Wprowadź 4996 w polu tekstowym. (Nie obejmuje prefiksu "C").  
  
 Aby uzyskać więcej informacji, zobacz [eksportowaniu z MBCS na Unicode](porting-guide-spy-increment.md#porting_to_unicode). Aby uzyskać ogólne informacje o wersji programu vs MBCS. Unicode, zobacz [tekst i ciągi w programie Visual C++](../text/text-and-strings-in-visual-cpp.md) i [internacjonalizacji](../c-runtime-library/internationalization.md) .  
  
## <a name="see-also"></a>Zobacz też  
 [Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md) [ulepszenia zgodność języka C++ w programie Visual Studio 2017 r.](../cpp-conformance-improvements-2017.md)
