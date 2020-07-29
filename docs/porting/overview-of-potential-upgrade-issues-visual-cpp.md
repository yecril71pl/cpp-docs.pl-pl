---
title: Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: fcfa8e8ea334cf7c2486513ae162b04014e7f24b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231640"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)

W ciągu lat kompilator języka Microsoft C++ przeszedł wiele zmian, wraz ze zmianami w języku C++, standardowa biblioteka C++, środowisko uruchomieniowe języka C (CRT) i inne biblioteki, takie jak MFC i ATL. W związku z tym podczas uaktualniania aplikacji ze starszej wersji programu Visual Studio mogą wystąpić błędy kompilatora i konsolidatora oraz ostrzeżenia w kodzie, który został wcześniej skompilowany jako czysty. Starsza wersja pierwotna kodu, tym większy potencjał dla takich błędów. Ten przegląd zawiera podsumowanie najbardziej typowych klas problemów, które mogą wystąpić, i zawiera linki do bardziej szczegółowych informacji.

> [!NOTE]
> W przeszłości zaleca się przeprowadzanie uaktualnień obejmujących kilka wersji programu Visual Studio jednocześnie. Nie zalecamy już tego podejścia. Znaleźliśmy, że prawie zawsze łatwiej jest uaktualnić system do najnowszej wersji programu Visual Studio niezależnie od tego, jak stara się baza kodu.

Pytania lub komentarze dotyczące procesu uaktualniania mogą być wysyłane do programu vcupgrade@microsoft.com .

## <a name="library-and-toolset-dependencies"></a>Zależności biblioteki i zestawu narzędzi

> [!NOTE]
> Ta sekcja dotyczy aplikacji i bibliotek utworzonych przy użyciu Visual Studio 2013 i starszych. Zestawy narzędzi używane w programie Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 są zgodne ze standardami binarnymi. Aby uzyskać więcej informacji, zobacz [zgodność binarna języka C++ między programami Visual Studio 2015 i Visual studio 2019](binary-compat-2015-2017.md).

Podczas uaktualniania aplikacji do nowej wersji programu Visual Studio jest to zalecane, a w wielu przypadkach konieczne jest uaktualnienie wszystkich bibliotek i bibliotek DLL, z którymi łączy się aplikacja. Wymaga on dostępu do kodu źródłowego lub że dostawca biblioteki może udostępniać nowe pliki binarne skompilowane z tą samą wersją główną kompilatora. Jeśli jeden z tych warunków ma wartość true, można pominąć tę sekcję, która zajmuje się szczegółami zgodności binarnej. Jeśli nie jest to przypadek, być może nie będzie można używać bibliotek w uaktualnionej aplikacji. Informacje przedstawione w tej sekcji ułatwią zrozumienie, czy można kontynuować uaktualnianie.

### <a name="toolset"></a>Zestaw narzędzi

Formaty plików. obj i. lib są dobrze zdefiniowane i rzadko zmieniane. Czasami Dodatki są wprowadzane do tych formatów plików, ale te dodatki zwykle nie wpływają na zdolność nowszych zestawów narzędzi do korzystania z plików obiektów i bibliotek utworzonych przez starsze zestawy narzędzi. Najważniejszym wyjątkiem jest Kompilowanie za pomocą [/GL (Optymalizacja całego programu)](../build/reference/gl-whole-program-optimization.md). W przypadku kompilowania przy użyciu `/GL` plik obiektu może być połączony tylko przy użyciu tego samego zestawu narzędzi, który został użyty do jego utworzenia. Dlatego, jeśli tworzysz plik obiektu za pomocą `/GL` i korzystasz z kompilatora programu Visual studio 2017 (najnowsze 141), musisz połączyć go za pomocą konsolidatora programu Visual studio 2017 (najnowsze 141). Wynika to z faktu, że wewnętrzne struktury danych w plikach obiektów nie są stabilne w głównych wersjach zestawu narzędzi, a nowsze zestawy narzędzi nie rozumieją starszych formatów danych.

C++ nie ma stabilnego interfejsu binarnego aplikacji (ABI). Ale program Visual Studio utrzymuje stabilną ABI języka C++ dla wszystkich mniejszych wersji wersji. Program Visual Studio 2015 (wersji 140), Visual Studio 2017 (najnowsze 141) i Visual Studio 2019 (v142) różni się tylko w wersji pomocniczej. Wszystkie mają ten sam główny numer wersji, który jest 14. Aby uzyskać więcej informacji, zobacz [zgodność binarna języka C++ między programami Visual Studio 2015 i Visual studio 2019](binary-compat-2015-2017.md).

Jeśli masz plik obiektu z zewnętrznymi symbolami z powiązaniem C++, ten plik obiektu może nie łączyć się prawidłowo z plikami obiektów produkowanymi przez inną wersję główną zestawu narzędzi. Istnieje wiele możliwych wyników: Link może się całkowicie kończyć niepowodzeniem (na przykład w przypadku zmiany dekoracji nazw). Link może zakończyć się pomyślnie, a elementy mogą nie pracować w czasie wykonywania (na przykład jeśli zmieniono układ typu). Lub w wielu przypadkach może się zdarzyć, że nic się nie stało. Należy również pamiętać, że chociaż C++ ABI nie jest stabilna, ABI C i podzbiór C++ ABI wymagany dla modelu COM są stabilne.

W przypadku łączenia się z biblioteką importu wszystkie późniejsze wersje bibliotek redystrybucyjnych programu Visual Studio, które zachowują zgodność ABI, mogą być używane w środowisku uruchomieniowym. Na przykład jeśli aplikacja została skompilowana i połączona przy użyciu zestawu narzędzi programu Visual Studio 2015 Update 3, możesz użyć dowolnego pakietu redystrybucyjnego programu Visual Studio 2017 lub Visual Studio 2019, ponieważ biblioteki 2015, 2017 i 2019 mają zachowaną zgodność binarną z poprzednimi wersjami. Odwrócenie nie jest prawdziwe: nie można użyć pakietu redystrybucyjnego dla starszej wersji zestawu narzędzi niż użyty do skompilowania kodu, nawet jeśli mają zgodne ABI.

### <a name="libraries"></a>Biblioteki

W przypadku skompilowania pliku źródłowego przy użyciu określonej wersji plików nagłówkowych bibliotek Visual Studio C++ (przez #including nagłówki) plik obiektu musi być połączony z tą samą wersją bibliotek. Jeśli na przykład plik źródłowy jest kompilowany za pomocą programu Visual Studio 2015 Update 3 \<immintrin.h> , należy połączyć się z biblioteką vcruntime programu Visual studio 2015 Update 3. Podobnie, jeśli plik źródłowy jest kompilowany za pomocą programu Visual Studio 2017 w wersji 15,5 \<iostream> , należy połączyć się z biblioteką Visual studio 2017 w wersji 15,5 Standard C++, msvcprt. Mieszanie i dopasowywanie nie jest obsługiwane.

Dla standardowej biblioteki języka C++, mieszanie i dopasowywanie zostało jawnie niedozwolone przez użycie `#pragma detect_mismatch` w standardowym nagłówku od programu Visual Studio 2010. Jeśli spróbujesz połączyć niezgodne pliki obiektów lub jeśli spróbujesz połączyć się z nieprawidłową biblioteką standardową, link zakończy się niepowodzeniem.

W przypadku CRT, mieszanie i dopasowywanie nigdy nie jest obsługiwane, ale często właśnie działały, co najmniej do programu Visual Studio 2015 i uniwersalnej CRT, ponieważ powierzchnia interfejsu API nie zmieniła się znacznie z upływem czasu. Uniwersalna platforma CRT przerwała zgodność wstecz, aby w przyszłości można było zachować zgodność z poprzednimi wersjami. Innymi słowy, nie mamy żadnych planów, aby w przyszłości wprowadzić nowe, w wersji uniwersalne pliki binarne CRT. Zamiast tego istniejący Uniwersalny CRT jest teraz aktualizowany w miejscu.

Aby zapewnić zgodność linków częściowych z plikami obiektów (i bibliotekami) skompilowanymi ze starszymi wersjami nagłówków środowiska uruchomieniowego Microsoft C, udostępniamy bibliotekę legacy_stdio_definitions. lib z programem Visual Studio 2015 lub nowszym. Ta biblioteka zawiera symbole zgodności dla większości funkcji i eksportów danych, które zostały usunięte ze uniwersalnej CRT. Zestaw symboli zgodności zapewnianych przez legacy_stdio_definitions. lib wystarcza do spełnienia większości zależności, w tym wszystkich zależności w bibliotekach zawartych w Windows SDK. Istnieje jednak kilka symboli, które zostały usunięte ze uniwersalnej CRT, dla którego nie można dostarczyć symboli zgodności. Te symbole obejmują niektóre funkcje (na przykład \_ \_ IOB \_ Func) i eksporty danych (na przykład \_ \_ IMP \_ \_ \_ IOB, \_ \_ IMP \_ \_ \_ pctype, \_ \_ IMP \_ \_ \_ MB \_ CUR \_ max).

Jeśli masz bibliotekę statyczną, która została skompilowana przy użyciu starszej wersji nagłówków środowiska uruchomieniowego języka C, zalecamy wykonanie następujących czynności w następującej kolejności:

1. Skompiluj ponownie bibliotekę statyczną za pomocą nowej wersji programu Visual Studio i uniwersalnych nagłówków CRT, aby obsługiwać łączenie z uniwersalną CRT. To podejście jest w pełni obsługiwane (i w ten sposób najlepiej).

1. Jeśli nie możesz ponownie skompilować biblioteki statycznej, możesz spróbować połączyć się ze starszymi \_ \_ definicjami stdio. lib. Jeśli jest to zgodne z zależnościami czasu konsolidacji biblioteki statycznej, należy dokładnie przetestować bibliotekę statyczną, która jest używana w pliku binarnym, aby upewnić się, że nie ma to niekorzystny wpływ na wszystkie [zmiany behawioralne dokonane w uniwersalnej CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Jeśli zależności biblioteki statycznej nie są spełnione przez starsze \_ definicje stdio \_ . lib lub biblioteka nie działa w przypadku uniwersalnej CRT ze względu na powyższe zmiany behawioralne, zalecamy hermetyzację biblioteki statycznej do biblioteki DLL połączonej z poprawną wersją środowiska uruchomieniowego Microsoft C. Na przykład, jeśli biblioteka statyczna została skompilowana przy użyciu Visual Studio 2013, warto również skompilować tę bibliotekę DLL przy użyciu bibliotek Visual Studio 2013 i Visual Studio 2013 C++. Przez skompilowanie biblioteki do biblioteki DLL, można hermetyzować szczegóły implementacji, która jest zależna od określonej wersji środowiska uruchomieniowego języka Microsoft C. Należy zachować ostrożność, aby interfejs biblioteki DLL nie wyciekł szczegółowych informacji o tym, które środowisko uruchomieniowe języka C używa, na przykład przez zwrócenie pliku * przez granicę biblioteki DLL lub przez zwrócenie wskaźnika przydzielonego przez program malloc i oczekiwanie na jego zwolnienie.

Korzystanie z wielu CRTs w pojedynczym procesie nie jest w i nie występuje, ponieważ większość procesów spowoduje zakończenie ładowania wielu bibliotek DLL CRT; na przykład składniki systemu operacyjnego Windows będą zależeć od msvcrt.dll, a środowisko CLR będzie zależeć od własnej prywatnej technologii CRT). Problemy powstają podczas Jumble stanu z różnych CRTs. Na przykład nie należy przydzielać pamięci za pomocą msvcr110.dll! malloc i próbować cofnąć alokacji tej pamięci za pomocą narzędzia msvcr120.dll! Free i nie należy próbować otworzyć pliku przy użyciu msvcr110! fopen i spróbować odczytać go z pliku przy użyciu msvcr120! fread. Dopóki nie Jumble stanu z różnych CRTs, można bezpiecznie załadować wiele CRTs w jednym procesie.

Aby uzyskać więcej informacji, zobacz [uaktualnianie kodu do uniwersalnej CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Błędy ze względu na ustawienia projektu

Aby rozpocząć proces uaktualniania, Otwórz starszy projekt/rozwiązanie/obszar roboczy w najnowszej wersji programu Visual Studio. Program Visual Studio utworzy nowy projekt na podstawie starych ustawień projektu. Jeśli starszy projekt ma bibliotekę lub zawiera ścieżki, które są trwale kodowane do lokalizacji niestandardowych, istnieje możliwość, że pliki w tych ścieżkach nie będą widoczne dla kompilatora, gdy projekt używa ustawień domyślnych. Aby uzyskać więcej informacji, zobacz [ustawienie konsolidatora plik_wyjściowy](porting-guide-spy-increment.md#linker_output_settings).

Ogólnie rzecz biorąc, jest to świetny czas na prawidłowe zorganizowanie kodu projektu w celu uproszczenia konserwacji projektu i ułatwienia kompilowania uaktualnionego kodu tak szybko, jak to możliwe. Jeśli kod źródłowy jest już dobrze zorganizowany, a starszy projekt jest kompilowany przy użyciu programu Visual Studio 2010 lub nowszego, można ręcznie edytować nowy plik projektu, aby obsługiwał kompilację zarówno starego, jak i nowego kompilatora. Poniższy przykład pokazuje, jak kompilować dla programu Visual Studio 2015 i Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: nierozpoznany zewnętrzny

W przypadku nierozpoznanych symboli może być konieczne naprawienie ustawień projektu.

- Jeśli plik źródłowy znajduje się w lokalizacji innej niż domyślna, czy dodano ścieżkę do katalogów dołączania projektu?

- Jeśli zewnętrzny jest zdefiniowany w pliku lib, należy określić ścieżkę lib we właściwościach projektu i czy w tym miejscu znajduje się poprawna wersja pliku. lib?

- Czy próbujesz połączyć się z plikiem lib, który został skompilowany przy użyciu innej wersji programu Visual Studio? Jeśli tak, zobacz poprzednią sekcję w temacie zależności biblioteki i zestawu narzędzi.

- Czy typy argumentów w miejscu wywołania rzeczywiście pasują do istniejącego przeciążenia funkcji? Sprawdź typy bazowe dla dowolnych elementów typedef w sygnaturze funkcji i w kodzie, który wywołuje funkcję, są oczekiwane.

Aby rozwiązać problemy z nierozwiązanymi błędami symboli, można spróbować użyć dumpbin.exe, aby sprawdzić symbole zdefiniowane w danych binarnych. Spróbuj użyć następującego wiersza polecenia, aby wyświetlić symbole zdefiniowane w bibliotece:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)

(W Microsoft Visual C++ 6,0 i wcześniejszych **`wchar_t`** nie został zaimplementowany jako typ wbudowany, ale został zadeklarowany w WCHAR. h jako element typedef dla niepodpisanego Short). Standard C++ wymaga **`wchar_t`** typu wbudowanego. Użycie wersji typedef może spowodować problemy z przenośnością. W przypadku uaktualniania z wcześniejszych wersji programu Visual Studio i napotkania błędu kompilatora C2664, ponieważ kod próbuje niejawnie skonwertować **`wchar_t`** do **`unsigned short`** , zalecamy zmianę kodu w celu naprawienia błędu, a nie ustawienie `/Zc:wchar_t-` . Aby uzyskać więcej informacji, zobacz [/Zc: wchar_t (Wchar_t jest typem natywnym)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md).

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Uaktualnianie przy użyciu opcji konsolidatora/NODEFAULTLIB,/ENTRY i/NOENTRY

`/NODEFAULTLIB`Opcja konsolidatora (lub właściwość "Ignoruj wszystkie domyślne biblioteki") informuje konsolidator, aby nie automatycznie łączyć się z domyślnymi bibliotekami, takimi jak CRT. Oznacza to, że każda biblioteka musi być wyświetlana jako dane wejściowe pojedynczo. Ta lista bibliotek jest określona we właściwości **dodatkowe zależności** w sekcji **konsolidator** okna dialogowego **właściwości projektu** .

Projekty używające tej opcji powodują problem podczas uaktualniania, ponieważ zawartość niektórych bibliotek domyślnych została przetworzonych. Ponieważ każda biblioteka musi znajdować się na liście właściwości **dodatkowe zależności** lub w wierszu polecenia konsolidatora, należy zaktualizować listę bibliotek, aby używała wszystkich bieżących nazw.

W poniższej tabeli przedstawiono biblioteki, których zawartość została zmieniona, począwszy od programu Visual Studio 2015. Aby uaktualnić, należy dodać nowe nazwy bibliotek w drugiej kolumnie do bibliotek w pierwszej kolumnie. Niektóre z tych bibliotek są importowane, ale nie powinny mieć znaczenia.

|||
|-|-|
|Jeśli używasz:|Musisz użyć następujących bibliotek:|
|libcmt. lib|libcmt. lib, libucrt. lib, libvcruntime. lib|
|libcmtd. lib|libcmtd. lib, libucrtd. lib, libvcruntimed. lib|
|msvcrt. lib|msvcrt. lib, UCRT. lib, vcruntime. lib|
|msvcrtd. lib|msvcrtd. lib, ucrtd. lib, vcruntimed. lib|

Ten sam problem stosuje się również w przypadku używania `/ENTRY` opcji lub `/NOENTRY` opcji, która również ma wpływ na pominięcie domyślnych bibliotek.

## <a name="errors-due-to-improved-language-conformance"></a>Błędy ze względu na ulepszoną zgodność języka

Kompilator języka Microsoft C++ ciągle poprawił swoją zgodność ze standardem C++ w ciągu lat. Kod, który został skompilowany we wcześniejszych wersjach, może się nie powieść w nowszych wersjach programu Visual Studio, ponieważ kompilator prawidłowo oflagowuje błąd, który był wcześniej ignorowany lub jawnie dozwolony.

Na przykład `/Zc:forScope` przełącznik został wprowadzony wcześniej w historii MSVC. Pozwala to na zachowanie niezgodności dla zmiennych pętli. Ten przełącznik jest obecnie przestarzały i może zostać usunięty w przyszłych wersjach. Zdecydowanie zaleca się, aby nie używać tego przełącznika podczas uaktualniania kodu. Aby uzyskać więcej informacji, zobacz [/Zc: forScope-jest przestarzałe](porting-guide-spy-increment.md#deprecated_forscope).

Przykład typowego błędu kompilatora, który może zostać wyświetlony podczas uaktualniania, gdy argument niestały jest przenoszona do parametru const. Starsze wersje kompilatora nie zawsze były oflagowane jako błąd. Aby uzyskać więcej informacji, zobacz [bardziej rygorystyczne konwersje kompilatora](porting-guide-spy-increment.md#stricter_conversions).

Aby uzyskać więcej informacji na temat ulepszeń związanych z zgodnością, zobacz [Visual C++ historię zmian 2003-2015](visual-cpp-change-history-2003-2015.md) i [ulepszenia zgodności C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Błędy związane z \<stdint.h> typami całkowitymi

\<stdint.h>Nagłówek definiuje elementy typedef i makra, które w przeciwieństwie do wbudowanych typów całkowitych mają mieć określoną długość na wszystkich platformach. Przykłady to `uint32_t` i `int64_t` . \<stdint.h>Nagłówek został dodany w programie Visual Studio 2010. Kod, który został zapisany przed 2010, mógł dostarczyć prywatnych definicji dla tych typów, a definicje te mogą nie zawsze być zgodne z \<stdint.h> definicjami.

Jeśli błąd to C2371, a `stdint` Typ jest uwzględniany, prawdopodobnie oznacza to, że typ jest zdefiniowany w nagłówku albo w kodzie, albo w pliku lib innej firmy. Podczas uaktualniania należy wyeliminować wszelkie niestandardowe definicje \<stdint.h> typów, ale najpierw porównać definicje niestandardowe z bieżącymi definicjami standardowymi, aby upewnić się, że nie występują nowe problemy.

Możesz nacisnąć klawisz **F12** (**Przejdź do definicji**), aby zobaczyć, gdzie jest zdefiniowany dany typ.

Opcja kompilatora [/showIncludes](../build/reference/showincludes-list-include-files.md) może być przydatna w tym miejscu. W oknie dialogowym **strony właściwości** dla projektu Otwórz stronę Zaawansowane **C/C++**  >  **Advanced** i wybierz opcję **Pokaż** dołączenie na **tak**. Następnie ponownie skompiluj projekt i Zobacz listę `#include` s w oknie danych wyjściowych. Każdy nagłówek jest wcięty w nagłówku, który go zawiera.

## <a name="errors-involving-crt-functions"></a>Błędy dotyczące funkcji CRT

Wprowadzono wiele zmian w środowisku uruchomieniowym języka C przez lata. Dodano wiele bezpiecznych wersji funkcji, a niektóre zostały usunięte. Ponadto, zgodnie z opisem we wcześniejszej części tego artykułu, implementacja CRT firmy Microsoft została wdrożona w programie Visual Studio 2015 do nowych plików binarnych i skojarzonych z nimi plików lib.

Jeśli błąd obejmuje funkcję CRT, Wyszukaj [Visual C++ historię zmian 2003-2015](visual-cpp-change-history-2003-2015.md) lub [C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md) , aby sprawdzić, czy te artykuły zawierają dodatkowe informacje. Jeśli błąd to LNK2019, nierozwiązana zewnętrzna, upewnij się, że funkcja nie została usunięta. W przeciwnym razie, jeśli masz pewność, że funkcja nadal istnieje, a kod wywołujący jest poprawny, sprawdź, czy Twój projekt używa `/NODEFAULTLIB` . W takim przypadku należy zaktualizować listę bibliotek, aby projekt korzystał z nowych bibliotek uniwersalnych (UCRT). Aby uzyskać więcej informacji, zobacz sekcję powyżej biblioteki i zależności.

Jeśli błąd dotyczy `printf` lub `scanf` , należy się upewnić, że nie masz prywatnej definicji żadnej funkcji bez uwzględnienia stdio. h. Jeśli tak, Usuń definicje prywatne lub Połącz ze starszymi \_ stdio \_ definicjami. lib. Tę bibliotekę można ustawić w oknie dialogowym **strony właściwości** w obszarze **Właściwości konfiguracji**  >  **Linker**  >  **dane wejściowe**konsolidatora we właściwości **dodatkowe zależności** . Jeśli łączysz się z Windows SDK 8,1 lub wcześniejszym, Dodaj starsze \_ definicje stdio \_ . lib.

Jeśli błąd obejmuje argumenty ciągu formatu, prawdopodobnie kompilator jest bardziej rygorystyczny, aby wymuszać Standard. Aby uzyskać więcej informacji, zobacz historię zmian. Zwróć uwagę na wszystkie błędy w tym miejscu, ponieważ mogą one stanowić zagrożenie dla bezpieczeństwa.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Błędy ze względu na zmiany w standardzie C++

Sam standardowy język C++ został rozwijający się w sposób, który nie zawsze jest zgodny z poprzednimi wersjami. Wprowadzenie w języku C++ 11 semantyki przenoszenia, nowe słowa kluczowe i inne funkcje języka i biblioteki standardowej mogą potencjalnie spowodować błędy kompilatora, a nawet inne zachowanie w czasie wykonywania.

Na przykład stary program C++ może zawierać nagłówek iostream. h. Ten nagłówek był wcześniej przestarzały w historii języka C++ i ostatecznie całkowicie usunięty z programu Visual Studio. W takim przypadku należy użyć \<iostream> i napisać ponownie swój kod. Aby uzyskać więcej informacji, zobacz [Aktualizowanie starego kodu iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: Zawężanie ostrzeżenia konwersji

Standard C++ określa teraz, że konwersje z niepodpisanej do podpisanych wartości całkowitych są uznawane za konwersje zawężające. Kompilator nie zgłosił tego ostrzeżenia przed wystąpieniem programu Visual Studio 2015. Sprawdź każde wystąpienie, aby się upewnić, że Zawężanie nie ma wpływu na poprawność kodu.

## <a name="warnings-to-use-secure-crt-functions"></a>Ostrzeżenia dotyczące używania funkcji Secure CRT

W ciągu lat wprowadzono bezpieczne wersje funkcji środowiska uruchomieniowego języka C. Mimo że stare, niezabezpieczone wersje są nadal dostępne, zaleca się zmianę kodu w celu używania bezpiecznych wersji. Kompilator wyda ostrzeżenie dotyczące użycia niezabezpieczonych wersji. Można wybrać opcję wyłączenia lub zignorowania tych ostrzeżeń. Aby wyłączyć Ostrzeżenie dla wszystkich projektów w rozwiązaniu, Otwórz **Widok**  >  **Menedżer właściwości**, zaznacz wszystkie projekty, dla których chcesz wyłączyć ostrzeżenie, a następnie kliknij prawym przyciskiem myszy wybrane elementy i wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** w obszarze **Właściwości konfiguracji**  >  **C/C++**  >  **Zaawansowane**wybierz opcję **Wyłącz określone ostrzeżenia**. Kliknij strzałkę listy rozwijanej, a następnie kliknij pozycję **Edytuj**. Wprowadź 4996 w polu tekstowym. (Nie dołączaj prefiksu "C"). Aby uzyskać więcej informacji, zobacz [przenoszenie do używania bezpiecznego CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Błędy spowodowane zmianami w interfejsie API systemu Windows lub przestarzałymi zestawami SDK

W ciągu lat interfejsy API systemu Windows i typy danych zostały dodane i czasami ulegają zmianie lub usunięciu. Ponadto inne zestawy SDK, które nie należą do podstawowego systemu operacyjnego, zostały utracone. W związku z tym starsze programy mogą zawierać wywołania interfejsów API, które już nie istnieją. Mogą również zawierać wywołania interfejsów API w innych zestawach Microsoft SDK, które nie są już obsługiwane. Jeśli widzisz błąd dotyczący interfejsu API systemu Windows lub interfejsu API ze starszego zestawu Microsoft SDK, istnieje możliwość, że interfejs API został usunięty i/lub zastąpiony przez nowszą, bardziej bezpieczną funkcję.

Aby uzyskać więcej informacji o bieżącym zestawie interfejsów API i minimalnych obsługiwanych systemach operacyjnych dla określonego interfejsu API systemu Windows, zobacz [indeks interfejsu API dla aplikacji klasycznych systemu Windows](/windows/win32/apiindex/api-index-portal) i przejdź do podanego interfejsu API.

### <a name="windows-version"></a>Wersja systemu Windows

Podczas uaktualniania programu korzystającego z interfejsu API systemu Windows bezpośrednio lub pośrednio należy określić minimalną wersję systemu Windows, która ma być obsługiwana. W większości przypadków jest to dobry wybór dla systemu Windows 7. Aby uzyskać więcej informacji, zobacz temat [problemy z plikiem nagłówka](porting-guide-spy-increment.md#header_file_problems). `WINVER`Makro definiuje najstarszą wersję systemu Windows, która jest przeznaczona do uruchamiania programu. Jeśli program MFC ustawia wartość WINVER na 0x0501 (Windows XP), zostanie wyświetlone ostrzeżenie, ponieważ MFC nie obsługuje już systemu XP, mimo że kompilator ma tryb XP.

Aby uzyskać więcej informacji, zobacz [Aktualizowanie docelowej wersji systemu Windows](porting-guide-spy-increment.md#updating_winver) i [innych nieaktualnych plików nagłówkowych](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL/MFC

Biblioteki ATL i MFC są stosunkowo stabilnymi interfejsami API, ale czasami zmiany są wprowadzane. Aby uzyskać więcej informacji, zobacz [Visual C++ historię zmian 2003-2015](visual-cpp-change-history-2003-2015.md), [Nowości dotyczące Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)i [ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 już zdefiniowany w msvcrtd. lib

Ten błąd może wystąpić w aplikacjach MFC. Wskazuje na problem z porządkowaniem między biblioteką CRT a biblioteką MFC. Najpierw należy połączyć MFC, aby zapewnić operatorom New i DELETE. Aby naprawić ten błąd, użyj `/NODEFAULTLIB` przełącznika, aby zignorować następujące biblioteki domyślne: msvcrtd. lib i mfcs140d. lib. Następnie Dodaj te same libs, co w przypadku dodatkowych zależności.

## <a name="32-vs-64-bit"></a>32 a 64 — bit

Jeśli oryginalny kod jest kompilowany dla systemów 32-bitowych, będziesz mieć możliwość utworzenia wersji 64-bitowej zamiast lub oprócz nowej aplikacji 32-bitowej. Ogólnie rzecz biorąc należy otrzymać najpierw kompilację programu w trybie 32-bitowym, a następnie spróbować 64-bitowy. Kompilacja dla 64-bitowej jest prosta, ale w niektórych przypadkach może ujawnić błędy, które zostały ukryte przez kompilacje 32-bitowe.

Należy również pamiętać o możliwych problemach dotyczących czasu kompilacji i środowiska uruchomieniowego odnoszących się do rozmiaru wskaźnika, wartości czasu i rozmiaru oraz specyfikatorów formatu w funkcjach printf i scanf. Aby uzyskać więcej informacji, zobacz [konfigurowanie Visual C++ dla 64-bitowych, elementów docelowych x64](../build/configuring-programs-for-64-bit-visual-cpp.md) i [typowych problemów z migracją Visual C++ 64](../build/common-visual-cpp-64-bit-migration-issues.md)). Aby uzyskać dodatkowe porady dotyczące migracji, zobacz [Przewodnik programowania dla systemu Windows 64-bitowego](/windows/win32/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode vs MBCS/ASCII

Przed znormalizowaniem Unicode wiele programów używało zestawu znaków wielobajtowych (MBCS) do reprezentowania znaków, które nie zostały uwzględnione w zestawie znaków ASCII. W starszych projektach MFC MBCS było ustawieniem domyślnym i po uaktualnieniu takiego programu zobaczysz ostrzeżenia, które doradzają zamiast użycia Unicode. Możesz zdecydować się na wyłączenie lub Zignorowanie ostrzeżenia, jeśli zdecydujesz, że konwersja na Unicode nie jest powarta kosztem rozwoju. Aby wyłączyć go dla wszystkich projektów w rozwiązaniu, Otwórz **Widok**  >  **Menedżer właściwości**, zaznacz wszystkie projekty, dla których chcesz wyłączyć ostrzeżenie, a następnie kliknij prawym przyciskiem myszy wybrane elementy i wybierz polecenie **Właściwości**. W oknie dialogowym **strony właściwości** wybierz pozycję **Właściwości konfiguracji**  >  **C/C++**  >  **Zaawansowane**. W właściwości **Wyłącz określone ostrzeżenia** Otwórz strzałkę listy rozwijanej, a następnie wybierz polecenie **Edytuj**. Wprowadź 4996 w polu tekstowym. (Nie dołączaj prefiksu "C"). Wybierz **przycisk OK** , aby zapisać właściwość, a następnie wybierz przycisk **OK** , aby zapisać zmiany.

Aby uzyskać więcej informacji, zobacz [przenoszenie z MBCS do Unicode](porting-guide-spy-increment.md#porting_to_unicode). Aby uzyskać ogólne informacje na temat MBCS i Unicode, zobacz [tekst i ciągi w Visual C++](../text/text-and-strings-in-visual-cpp.md) i [międzynarodowe](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Zobacz także

[Uaktualnianie projektów z wcześniejszych wersji Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)
