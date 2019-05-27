---
title: Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 27cfe90f33f71d82af90cf4fa62186c1c0a189ce
ms.sourcegitcommit: bde3279f70432f819018df74923a8bb895636f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2019
ms.locfileid: "66174847"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)

W ciągu lat Microsoft C++ kompilatora przeszła wiele zmian oraz zmian w C++ języka, C++ standardowej biblioteki C runtime (CRT) i inne biblioteki, takie jak MFC i ATL. W rezultacie podczas uaktualniania aplikacji ze starszej wersji programu Visual Studio, mogą wystąpić kompilatora i konsolidatora błędów i ostrzeżeń w kodzie, który wcześniej skompilowany nie pozostawia żadnych śladów. Starsze oryginalny kod podstawowy, tym większe ryzyko takie błędy. Ten przegląd zawiera podsumowanie najbardziej typowych klas problemów, prawdopodobnie wystąpi, i zawiera łącza do bardziej szczegółowych informacji.

> [!NOTE]
> W przeszłości zalecamy mają uaktualnień, które rozciągają się różne wersje programu Visual Studio powinien być wykonywane przyrostowe jednej wersji w danym momencie. Nie zalecamy tego podejścia. Znaleźliśmy się, że prawie zawsze jest prostsza do uaktualnienia do najnowszej wersji programu Visual Studio, niezależnie od tego, ile lat bazy kodu.

Pytania lub komentarze na temat procesu uaktualniania, które mogą być wysyłane do vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Zależności biblioteki i zestaw narzędzi

> [!NOTE]
> Ta sekcja ma zastosowanie do aplikacji i bibliotek utworzone za pomocą programu Visual Studio 2013 i starszych wersji. Zestawy narzędzi używanych w Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 r są zgodne z binarnym. Aby uzyskać więcej informacji, zobacz [ C++ zgodność binarną między Visual Studio 2015 i Visual Studio 2019](binary-compat-2015-2017.md).

Podczas uaktualniania aplikacji do nowej wersji programu Visual Studio, jest zalecane i w wielu przypadkach trzeba również uaktualnić wszystkie biblioteki i biblioteki dll, które łączy aplikację. Wymaga ona, czy masz dostęp do kodu źródłowego, albo że dostawcą biblioteki może zapewnić nowych plików binarnych skompilowanych z taką samą wersję główną kompilatora. Jeśli jeden z tych warunków jest spełniony, można pominąć w tej sekcji, która zajmuje się szczegółowe informacje o zgodność binarną. Jeśli żaden nie jest tak, może nie mieć możliwości przy użyciu bibliotek w uaktualnionej aplikacji. Informacje przedstawione w tej sekcji pomoże zrozumieć, czy należy kontynuować uaktualnianie.

### <a name="toolset"></a>Zestaw narzędzi

Formaty plików obj i lib są dobrze zdefiniowany i rzadko się zmieniają. Czasami dodawane są do tych formatów plików, ale te dodatki zwykle nie mają wpływu na możliwość korzystania z plików obiektów i bibliotek, tworzone przez starsze zestawy narzędzi nowsze zestawy narzędzi. Główne wyjątek w tym miejscu jest, jeśli kompilujesz przy użyciu [/GL (Optymalizacja Całoprogramowa)](../build/reference/gl-whole-program-optimization.md). Jeśli kompilujesz przy użyciu `/GL`, wynikowy plik obiektu może odnosić się tylko przy użyciu tego samego zestawu narzędzi, który został użyty do jego produkcji. Dlatego w przypadku utworzenia pliku obiektu z `/GL` i za pomocą kompilatora Visual Studio 2017 (w wersji 141), musisz połączyć za pomocą konsolidatora programu Visual Studio 2017 (w wersji 141). Jest on, ponieważ struktur danych wewnętrznych w plikach obiektu nie są stabilne różnych wersji głównych zestaw narzędzi i nowsze zestawy narzędzi nie rozumiesz starsze formaty danych.

C++nie ma interfejsem binarnym stabilnych aplikacji (ABI). Ale programu Visual Studio obsługuje stabilnego C++ ABI dla wszystkich wersji pomocniczej wersji. Program Visual Studio 2015 (wersja 140), program Visual Studio 2017 (w wersji 141) i Visual Studio 2019 (v142) różnią się tylko w ich wersji pomocniczej. Wszystkie one mają ten sam główny numer wersji, która jest 14. Aby uzyskać więcej informacji, zobacz [ C++ zgodność binarną między Visual Studio 2015 i Visual Studio 2019](binary-compat-2015-2017.md).

Jeśli masz plik obiektu, który zawiera zewnętrzne symbole z C++ powiązania, który obiekt pliku nie może poprawnie łącza z plikami obiekt utworzony przez inną wersję główną zestaw narzędzi. Istnieje wiele możliwych wyników: link może zakończyć się niepowodzeniem w całości (na przykład zmienić dekorowania nazw). Link może się powieść, a elementy mogą nie działać w czasie wykonywania (na przykład zmienić układ typu). Lub w wielu przypadkach rzeczy może się zdarzyć, pracę i nic nie zostanie pójdzie nie tak. Należy również zauważyć, podczas gdy C++ interfejsu ABI nie jest stabilna, C ABI i podzbiór C++ ABI wymagane dla modelu COM są stabilne.

Jeśli łączysz się do biblioteki importu żadnych nowszej wersji programu Visual Studio redystrybucyjnych bibliotek, które zachowania zgodności z interfejsem ABI może służyć w czasie wykonywania. Na przykład jeśli Twoja aplikacja jest kompilowana i połączone, przy użyciu zestawu narzędzi Visual Studio 2015 Update 3, umożliwia dowolnego programu Visual Studio 2017 lub Visual Studio 2019 redystrybucji, ponieważ biblioteki 2015, 2017 i 2019 zostały zachowane binarne zgodności z poprzednimi wersjami. Odwrotnej nie jest spełniony: Nie można użyć pakiet redystrybucyjny dla starszej wersji zestawu narzędzi programu niż używane do kompilowania swojego kodu, nawet jeśli mają niezgodne interfejsu ABI.

### <a name="libraries"></a>Biblioteki

Jeśli skompilujesz plik źródłowy przy użyciu określonej wersji programu Visual Studio C++ pliki nagłówkowe biblioteki (przez #including nagłówków), wynikowy plik obiektu musi być połączony z tej samej wersji bibliotek. Tak więc, na przykład, jeśli plik źródłowy jest kompilowany za pomocą programu Visual Studio 2015 Update 3 \<immintrin.h >, należy połączyć z biblioteką vcruntime Visual Studio 2015 Update 3. Podobnie jeśli plik źródłowy jest kompilowany za pomocą programu Visual Studio 2017 w wersji 15.5 \<iostream >, musisz połączyć za pomocą programu Visual Studio 2017 w wersji 15.5 standardowej bibliotece C++, msvcprt. Mieszanie i dopasowania nie jest obsługiwane.

Biblioteki standardowej języka C++, mieszanie i dopasowywania został jawnie zabroniony wykorzystaniem `#pragma detect_mismatch` w standardowych nagłówków od programu Visual Studio 2010. Jeśli spróbujesz połączyć pliki obiektów niezgodne lub jeśli zostanie podjęta próba połączenia z niewłaściwego biblioteki standardowej, łącze nie powiedzie się.

CRT mieszanie i dopasowywania nigdy nie było obsługiwane, ale często po prostu działało, co najmniej do programu Visual Studio 2015 i Universal CRT, ponieważ powierzchni interfejsu API nie zmieniły się znacznie wraz z upływem czasu. Universal CRT Przerwano wstecznej zgodności, aby w przyszłości firma Microsoft może zachować wstecznej zgodności. Innymi słowy nie mamy nie jest planowane wprowadzenie nowych, numerów wersji w przyszłości Universal CRT plików binarnych. Zamiast tego istniejącego Universal CRT zostało zaktualizowane w miejscu.

Ze względu na zgodność częściowe link przy użyciu obiektu plików (i biblioteki) skompilowany ze starszymi wersjami Microsoft C Runtime nagłówki, firma Microsoft oferuje biblioteki legacy_stdio_definitions.lib, za pomocą programu Visual Studio 2015 i nowszych. Ta biblioteka zawiera symbole zgodność dla większości eksportuje funkcje i dane, które zostały usunięte z Universal CRT. Zestaw symboli zgodności udostępnianych przez legacy_stdio_definitions.lib jest niewystarczająca do zapewnienia większość zależności, w tym wszystkie zależności bibliotek zawartych w zestawie Windows SDK. Istnieją jednak niektóre symbole, które zostały usunięte z Universal CRT, dla których nie jest możliwe zapewnienie zgodności symboli. Te symbole obejmują niektóre funkcje (na przykład \_ \_iob —\_func) i eksportuje dane (na przykład \_ \_imp\_\_\_iob —, \_ \_imp\_\_\_pctype —, \_ \_imp\_\_\_mb\_Waluta\_maksymalna).

Jeśli masz bibliotekę statyczną, który został zbudowany przy użyciu starszej wersji nagłówków środowiska uruchomieniowego C, zaleca się następujące działania, w następującej kolejności:

1. Ponownie skompiluj biblioteki statycznej przy użyciu nowej wersji programu Visual Studio i nagłówki Universal CRT do obsługi połączeń z Universal CRT. To podejście jest opcja pełni obsługiwaną (oraz związku z tym najlepszym).

1. Jeśli nie (lub nie chcesz) odbudować biblioteki statycznej, możesz spróbować konsolidowanie za pomocą starszej wersji\_stdio —\_definitions.lib. Jeśli spełnia czasie konsolidowania zależności biblioteki statycznej, należy dokładnie przetestować biblioteki statycznej, ponieważ jest używany w pliku binarnym, aby upewnić się, że nie ma negatywny wpływ przez żaden z [zmiany zachowania, które zostały wprowadzone do Universal CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Jeśli biblioteka statyczna zależności nie są spełnione przez starsze\_stdio —\_definitions.lib lub jeśli biblioteka nie działa z Universal CRT z powodu wyżej zmian zachowania, zalecamy enkapsulacji usługi biblioteka statyczna do biblioteki DLL, która łączy odpowiednią wersję środowiska uruchomieniowego C firmy Microsoft. Na przykład biblioteka statyczna został utworzony za pomocą programu Visual Studio 2013, należy utworzyć tę bibliotekę DLL przy użyciu programu Visual Studio 2013 i do bibliotek języka Visual Studio 2013 C++. Tworzenie biblioteki do biblioteki DLL, hermetyzację szczegółów implementacji, które jest zależność od określonej wersji środowiska uruchomieniowego C firmy Microsoft. Będziesz chciał należy zachować ostrożność, że interfejsu biblioteki DLL nie przecieku szczegółowe informacje, które środowiska uruchomieniowego C używa, na przykład, zwracając pliku * granicę biblioteki DLL lub zwracającej wskaźnik przydzielone funkcji malloc i Oczekiwany obiekt wywołujący, aby ją bezpłatnie.

Korzystanie z wielu im monitory CRT w pojedynczym procesie nie jest w i samego siebie problematyczne (w rzeczywistości większość procesów prowadzi to do umożliwienia wielu CRT bibliotek DLL ładowanych; na przykład Windows, składników systemu operacyjnego będzie zależeć od msvcrt.dll i środowiska CLR będzie zależeć od własnej prywatnej CRT). Problemy podczas jumble stan z innego im monitory CRT. Na przykład, nie powinny przydzielić pamięci przy użyciu msvcr110.dll!malloc i spróbować cofnąć alokacji pamięci za pomocą msvcr120.dll!free i nie należy próbować otworzyć plik za pomocą msvcr110! fopen — i podjęcie próby odczytu przy jego użyciu plików przy użyciu msvcr120! fread —. Tak długo, jak nie jumble stan z innego im monitory CRT, możesz bezpiecznie mieć wiele im monitory CRT, które są ładowane w pojedynczym procesie.

Aby uzyskać więcej informacji, zobacz [uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Błędy z powodu ustawień projektu

Aby rozpocząć proces uaktualniania, otwórz starsze projekt/rozwiązanie/obszar roboczy w najnowszej wersji programu Visual Studio. Visual Studio utworzy nowy projekt na podstawie starej ustawień projektu. Jeśli starszych projektu biblioteki lub zawierać ścieżek, które są zakodowane do lokalizacji niestandardowej, istnieje możliwość, czy pliki znajdujące się w tych ścieżek nie będzie widoczny dla kompilatora, jeśli projekt używa ustawień domyślnych. Aby uzyskać więcej informacji, zobacz [ustawienia konsolidatora Plik_wyjściowy](porting-guide-spy-increment.md#linker_output_settings).

Ogólnie rzecz biorąc teraz jest to doskonały moment na prawidłowo organizowania kodu projektu, aby uprościć zarządzanie projektu i pomogą Ci rozpocząć kodzie uaktualnionego kompilowanie tak szybko, jak to możliwe. Jeśli kod źródłowy jest już dobrze zorganizowanego i starszych projekt został skompilowany przy użyciu programu Visual Studio 2010 lub nowszej, można ręcznie edytować plik projektu do obsługi kompilacji na kompilatora stare i nowe. Poniższy przykład pokazuje, jak skompilować zarówno dla programu Visual Studio 2015 i Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: Nierozpoznany zewnętrzny

Dla nierozpoznanych symboli może być konieczne naprawić ustawień projektu.

- Jeśli plik źródłowy znajduje się w lokalizacji innej niż domyślna, czy należy dodać ścieżkę do projektu katalogi dyrektywy include?

- Jeśli zewnętrznej jest zdefiniowana w pliku .lib, mają określona ścieżka biblioteki we właściwościach projektu i jest poprawną wersję pliku .lib, znajduje się tam?

- Podjęto próbę łącze do pliku .lib, który został skompilowany przy użyciu różnych wersji programu Visual Studio? Jeśli tak, zobacz poprzednią sekcję zależności biblioteki i zestaw narzędzi.

- Są istniejące przeciążenia funkcji jest faktycznie zgodne typy argumentów w witrynie wywołania? Sprawdź, czy typy bazowe dla dowolnego definicje typów w sygnaturze funkcji i w kodzie, który wywołuje funkcję są oczekiwań, należy im.

Rozwiązywanie problemów nierozpoznanych symboli, możesz spróbować przy użyciu dumpbin.exe, aby zbadać symbole zdefiniowane w pliku binarnym. Wypróbuj następujący wiersz polecenia w celu wyświetlenia symboli zdefiniowanych w bibliotece:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchart-wchart-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)

(W Microsoft Visual C++ 6.0 i starszych wersjach **wchar_t** nie została zaimplementowana jako typ wbudowany, ale zadeklarowano w wchar.h jako element typedef dla typ unsigned short.) C++ Standardowa wymaga, aby **wchar_t** jest typem wbudowanym. Przy użyciu wersji typedef może spowodować problemy przenośności w programowaniu. Jeśli uaktualnienia ze starszych wersji programu Visual Studio i występuje błąd kompilatora C2664, ponieważ kod próbuje niejawnie skonwertować **wchar_t** do **typ unsigned short**, firma Microsoft zaleca, aby zmienić Kod, aby naprawić błąd, zamiast ustawiać `/Zc:wchar_t-`. Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Uaktualnianie przy użyciu opcji konsolidatora/nodefaultlib/Entry i/noentry

`/NODEFAULTLIB` — Opcja konsolidatora (lub właściwości konsolidatora Ignoruj wszystkie domyślne biblioteki) informuje konsolidator, które nie mają być automatycznie połączone biblioteki domyślne, takie jak CRT. Oznacza, że każda biblioteka jest wyświetlany jako dane wejściowe indywidualnie. Ta lista bibliotek znajduje się w **dodatkowe zależności** właściwość **konsolidatora** części **właściwości projektu** okna dialogowego.

Projekty, użyj tej opcji, które powodują problemu podczas uaktualniania, ponieważ zawartość niektórych domyślne biblioteki zostały zaprojektowane od nowa. Ponieważ każda biblioteka ma być wymienione na **dodatkowe zależności** właściwości lub w wierszu polecenia konsolidatora, musisz zaktualizować listę bibliotek, aby użyć bieżącej nazwy.

W poniższej tabeli przedstawiono biblioteki, w których zawartość zmienione, począwszy od programu Visual Studio 2015. Aby przeprowadzić uaktualnienie, należy dodać nowe nazwy biblioteki w drugiej kolumnie do bibliotek w pierwszej kolumnie. Niektóre z tych bibliotek są bibliotekami importowanymi, ale który nie ma znaczenia.

|||
|-|-|
|W przypadku używania:|Należy użyć następujących bibliotek:|
|libcmt.lib|biblioteki libcmt.lib, libucrt.lib, libvcruntime.lib|
|libcmtd.lib|biblioteki libcmtd.lib, libucrtd.lib, libvcruntimed.lib|
|msvcrt.lib|msvcrt.lib, ucrt.lib, vcruntime.lib|
|msvcrtd.lib|msvcrtd.lib, ucrtd.lib, vcruntimed.lib|

Ten sam problem ma również zastosowanie, gdy używasz `/ENTRY` opcji lub `/NOENTRY` opcja, która ma również wpływu na pomijanie biblioteki domyślne.

## <a name="errors-due-to-improved-language-conformance"></a>Błędy ze względu na zgodność języka ulepszone

Microsoft C++ kompilatora stale poprawiła się jego zgodnością C++ standardowa przez lata. Kod, który jest skompilowany w starszych wersjach może zakończyć się niepowodzeniem do kompilacji w nowszych wersjach programu Visual Studio, ponieważ kompilator poprawnie oznacza błąd, który wcześniej został zignorowany, lub jawnie dozwolone.

Na przykład `/Zc:forScope` switch została wprowadzona na wczesnym etapie historii MSVC. Umożliwia on niezgodnych zachowanie zmiennych pętli. Ten przełącznik jest już przestarzały i może zostać usunięta w przyszłych wersjach. Zdecydowanie zaleca się nie korzystać z tego przełącznika podczas uaktualniania kodu. Aby uzyskać więcej informacji, zobacz [/Zc:forScope-jest przestarzała](porting-guide-spy-increment.md#deprecated_forscope).

Jednym z przykładów typowych błąd kompilatora, które można napotkać podczas uaktualniania jest, gdy argument wartości innej niż stała jest przekazywany do parametru const. Starsze wersje kompilatora nie zawsze Oznacz ją jako błąd. Aby uzyskać więcej informacji, zobacz [konwersje bardziej rygorystyczne kompilatora](porting-guide-spy-increment.md#stricter_conversions).

Aby uzyskać więcej informacji na temat zgodności określonego ulepszeń, zobacz [Visual C++ — Historia latach 2003 – 2015 zmian](visual-cpp-change-history-2003-2015.md) i [ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Błędy dotyczące \<stdint.h > typów całkowitych

\<Stdint.h > nagłówka definiuje definicji typów i makra, w przeciwieństwie do wbudowanych typów całkowitych o gwarantowanej ma określony czas na wszystkich platformach. Oto kilka przykładów `uint32_t` i `int64_t`. \<Stdint.h > nagłówek został dodany do programu Visual Studio 2010. Kod, który został napisany przed 2010 mógł podać prywatny definicji dla tych typów i te definicje mogą nie zawsze jest zgodny z \<stdint.h > definicje.

Jeśli błąd jest C2371, a `stdint` uczestniczy typ, prawdopodobnie oznacza to, że typ jest zdefiniowany w nagłówku w kodzie lub plik biblioteki innej firmy. Podczas uaktualniania, należy wyeliminować wszelkie niestandardowe definicje \<stdint.h > typy, ale pierwszy porównania niestandardowe definicje do bieżącej definicji standard, aby upewnić się, nie są wprowadzenia nowych problemów.

Możesz nacisnąć przycisk **F12** (**przejdź do definicji**) aby zobaczyć, gdzie zdefiniowane jest danego typu.

[/Showincludes](../build/reference/showincludes-list-include-files.md) — opcja kompilatora może być przydatne w tym miejscu. W **stron właściwości** projektu, Otwórz okno dialogowe **C/C++** > **zaawansowane** strony, a następnie ustaw **Pokaż obejmuje** do **Tak**. Następnie ponownie skompilować projekt i przejrzyj listę rzeczy, `#include`s w oknie danych wyjściowych. Każdy nagłówek tworzone jest wcięcie w obszarze nagłówka zawierający go.

## <a name="errors-involving-crt-functions"></a>Błędy, obejmujące funkcje CRT

Wprowadzono wiele zmian do środowiska wykonawczego języka C przez lata. Dodano wiele bezpieczne wersje funkcji, a niektóre zostały usunięte. Ponadto zgodnie z opisem we wcześniejszej części tego artykułu, implementacja firmy Microsoft CRT został wycofany w programie Visual Studio 2015 na nowe pliki binarne i pliki .lib skojarzone.

Jeśli błąd dotyczy funkcji CRT, wyszukaj [Visual C++ latach 2003 – 2015 historię zmian](visual-cpp-change-history-2003-2015.md) lub [ C++ ulepszenia zgodności w programie Visual Studio](../overview/cpp-conformance-improvements.md) Jeśli te artykuły zawierają wszystkie dodatkowe informacje. Jeśli błąd jest LNK2019, nierozpoznany zewnętrzny, upewnij się, że funkcja nie została usunięta. W przeciwnym razie, gdy masz pewność, że funkcja jest nadal istnieje i kod wywołujący jest poprawny, sprawdź, czy projekt używa `/NODEFAULTLIB`. Jeśli tak, musisz zaktualizować listę bibliotek, więc, że projekt korzysta z nowej uniwersalnej bibliotek (UCRT). Aby uzyskać więcej informacji zobacz sekcję powyżej w bibliotece i zależności.

Jeśli ten błąd obejmuje `printf` lub `scanf`, upewnij się, że nie prywatnie definiujesz każdą z tych funkcji bez uwzględniania stdio.h. Jeśli tak, Usuń definicje prywatnej lub link do starszego\_stdio —\_definitions.lib. Możesz ustawić tę bibliotekę w **stron właściwości** , okno dialogowe **właściwości konfiguracji** > **konsolidatora** > **dane wejściowe** w **dodatkowe zależności** właściwości. Jeśli łączenia z Windows SDK 8.1 lub starszy, Dodaj starsza wersja\_stdio —\_definitions.lib.

Jeśli błąd dotyczy formatu argumentów ciągów, jest prawdopodobnie ponieważ kompilator jest bardziej rygorystyczne o wymuszanie standard. Aby uzyskać więcej informacji zobacz historię zmian. Należy zwracać szczególną uwagę na wszelkie błędy, w tym miejscu, ponieważ mogą one reprezentować potencjalnie zagrożenie bezpieczeństwa.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Błędy z powodu zmian w standardzie języka C++

Standard C++, sama powstał w sposób, który nie zawsze są zgodne z poprzednimi wersjami. Wprowadzenie w C ++ 11 semantyki przenoszenia, nowych słów kluczowych, a inne języka i funkcje standardowej biblioteki mogą potencjalnie powodować błędy kompilatora i nawet różne zachowania.

Na przykład stare program w języku C++ może obejmować nagłówek iostream.h. Ten nagłówek została zakończona na wczesnym etapie historię C++ i po pewnym czasie zostało całkowicie usunięte z programu Visual Studio. W takim przypadku należy użyć \<iostream > i ponownie zapisać swój kod. Aby uzyskać więcej informacji, zobacz [aktualizowanie stary kod iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: Zawężanie konwersji ostrzeżenie

C++ standard teraz Określa, że konwersje z typów bez znaku na podpisane wartości całkowitych są uznawane za konwersji zawężających. Kompilator nie wygenerował tego ostrzeżenia przed Visual Studio 2015. Sprawdź, czy każde wystąpienie, aby upewnić się, że zawężanie nie ma wpływu na poprawność kodu.

## <a name="warnings-to-use-secure-crt-functions"></a>Ostrzeżenia dotyczące używania bezpiecznego funkcji CRT

W ciągu lat bezpieczne wersje funkcji środowiska uruchomieniowego C zostały wprowadzone. Chociaż stare, które nie są bezpieczne wersje są nadal dostępne, zaleca się zmiany kodu, aby użyć bezpieczne wersje. Kompilator zgłosi ostrzeżenie użycia niezabezpieczone wersje. Można wyłączyć lub zignorować te ostrzeżenia. Aby wyłączyć ostrzeżenia dla wszystkich projektów w rozwiązaniu, otwórz **widoku** > **Menedżer właściwości**, wybierz wszystkie projekty, dla których chcesz wyłączyć to ostrzeżenie, a następnie kliknij prawym przyciskiem myszy na wybranym elementy, a następnie wybierz **właściwości**. W **stron właściwości** , okno dialogowe **właściwości konfiguracji** > **C/C++** > **zaawansowane**, Wybierz **Wyłącz określone ostrzeżenia**. Kliknij strzałkę listy rozwijanej, a następnie kliknij polecenie **Edytuj**. Wprowadź 4996 w polu tekstowym. (Nie dołączaj prefiksu "C"). Aby uzyskać więcej informacji, zobacz [przenoszenie do użycia zabezpieczenia CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Błędy z powodu zmian w interfejsach API Windows i przestarzałe zestawów SDK

W ciągu lat Windows interfejsów API i typy danych zostały dodane i czasami zmieniony lub usunięty. Ponadto innych zestawów SDK, które należy do podstawowego systemu operacyjnego mają pochodzić i stała. Starsze programy, w związku z tym może zawierać wywołania interfejsów API, który nie jest już istnieje. Może również zawierać wywołania interfejsów API w innych Microsoft SDKs, nie są już obsługiwane. Jeśli zostanie wyświetlony błąd obejmujące Windows API lub interfejsu API z poziomu starszych SDK firmy Microsoft, jest to możliwe, że interfejs API zostały usunięte lub zastąpione przez funkcje nowszymi, bardziej bezpiecznymi.

Aby dowiedzieć się więcej o bieżącym interfejsie API zestawu i minimalne obsługiwane systemy operacyjne dla konkretnego interfejsu API Windows, zobacz [Microsoft API i wykaz referencyjny](https://msdn.microsoft.com/library) i przejdź z interfejsem API.

### <a name="windows-version"></a>Wersja Windows

Podczas uaktualniania program, który używa interfejsu API Windows, bezpośrednio lub pośrednio, należy określić minimalną wersję Windows w celu obsługi. W większości przypadków Windows 7 jest dobrym wyborem. Aby uzyskać więcej informacji, zobacz [problemy pliku nagłówka](porting-guide-spy-increment.md#header_file_problems). `WINVER` — Makro definiuje najstarszą wersję systemu Windows, który program jest przeznaczony do uruchamiania na. Jeśli MFC program ustawia WINVER 0x0501 (Windows XP) otrzymasz ostrzeżenie ponieważ MFC nie obsługuje już XP, mimo że kompilator sam trybem XP.

Aby uzyskać więcej informacji, zobacz [aktualizowanie docelową wersję Windows](porting-guide-spy-increment.md#updating_winver) i [bardziej nieaktualne pliki nagłówkowe](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL / MFC

ATL i MFC są stosunkowo stabilne interfejsy API, ale zmiany wprowadzone od czasu do czasu. Aby uzyskać więcej informacji, zobacz [Visual C++ latach 2003 – 2015 historię zmian](visual-cpp-change-history-2003-2015.md), [What's New for Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md), i [ C++ ulepszenia zgodności w wizualizacji Studio](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 już zdefiniowana w biblioteki MSVCRTD.lib

Ten błąd może wystąpić w aplikacjach MFC. Wskazuje problem szeregowania między bibliotekę CRT i biblioteki MFC. MFC muszą być połączone najpierw, tak aby zawiera nowe i delete — operatory. Aby naprawić błąd, należy użyć `/NODEFAULTLIB` przełączyć się do ignorowania te domyślne biblioteki: MSVCRTD.lib and mfcs140d.lib. Następnie dodaj te sam libs jako dodatkowe zależności.

## <a name="32-vs-64-bit"></a>64-bitowym a 32

Jeśli oryginalny kod jest kompilowany dla systemów 32-bitowych, istnieje możliwość tworzenia 64-bitowej wersji zamiast lub oprócz nowej aplikacji 32-bitowych. Ogólnie rzecz biorąc należy pobrać pierwszy program kompilacji w trybie 32-bitowym a następnie spróbuj 64-bitowych. Kompilowanie dla 64-bitowych jest bardzo proste, ale w niektórych przypadkach może ujawnić błędy, które zostały ukryte przez 32-bitowych kompilacji.

Ponadto należy pamiętać o możliwych problemach kompilacji i środowiska uruchomieniowego, odnoszące się do rozmiaru wskaźnika, czas i wartości rozmiaru i specyfikatory formatu w funkcje printf i scanf. Aby uzyskać więcej informacji, zobacz [Konfigurowanie Visual C++ x64 64-bitowy, obiekty docelowe](../build/configuring-programs-for-64-bit-visual-cpp.md) i [problemy przy migracji wspólnej Visual C++-x 64](../build/common-visual-cpp-64-bit-migration-issues.md). Aby uzyskać wskazówki dotyczące migracji dodatkowych, zobacz [przewodnik programowania w Windows 64-bitowych](/windows/desktop/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode a MBCS/ASCII

Zanim został znormalizowany Unicode, wiele programów używana zestawu znaków wielobajtowych (MBCS) do reprezentowania znaków, które nie zostały uwzględnione w zestawie znaków ASCII. W starszych projektach MFC MBCS był domyślne ustawienie i po uaktualnieniu taki program, zostanie wyświetlony ostrzeżenia, aby zamiast tego użyć Unicode. Można wyłączyć lub zignorować to ostrzeżenie, jeśli zdecydujesz, że konwersja na Unicode nie jest warte rozwoju. Aby ją wyłączyć dla wszystkich projektów w rozwiązaniu, otwórz **widoku** > **Menedżer właściwości**, wybierz wszystkie projekty, dla których chcesz wyłączyć to ostrzeżenie, a następnie kliknij prawym przyciskiem myszy na wybranych elementach i Wybierz **właściwości**. W **stron właściwości** okno dialogowe, wybierz opcję **właściwości konfiguracji** > **C/C++** > **zaawansowane**. W **Wyłącz określone ostrzeżenia** właściwości, Otwórz strzałkę listy rozwijanej, a następnie wybierz **Edytuj**. Wprowadź 4996 w polu tekstowym. (Nie dołączaj prefiksu "C"). Wybierz **OK** można zapisać właściwości, następnie wybierz **OK** Aby zapisać zmiany.

Aby uzyskać więcej informacji, zobacz [przenoszenie z MBCS na Unicode](porting-guide-spy-increment.md#porting_to_unicode). Aby uzyskać ogólne informacje na temat MBCS w programie vs. Unicode, zobacz [tekst i ciągi w języku Visual C++](../text/text-and-strings-in-visual-cpp.md) i [internacjonalizacji](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Zobacz także

[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)