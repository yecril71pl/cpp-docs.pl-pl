---
title: Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)
ms.date: 05/03/2019
ms.assetid: 2c99a8cb-098f-4a9d-bf2c-b80fd06ace43
ms.openlocfilehash: 44fcb6776118e829fe7c96e54f3f51615604ac31
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368488"
---
# <a name="overview-of-potential-upgrade-issues-visual-c"></a>Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)

Z biegiem lat kompilator Microsoft C++ przeszedł wiele zmian, wraz ze zmianami w samym języku C++, bibliotece standardowej języka C++, środowisku uruchomieniowym języka C (CRT) i innych bibliotekach, takich jak MFC i ATL. W rezultacie podczas uaktualniania aplikacji z wcześniejszej wersji programu Visual Studio może wystąpić błędy kompilatora i konsolidatora i ostrzeżenia w kodzie, który wcześniej skompilowany czysto. Im starsza oryginalna podstawa kodu, tym większy potencjał dla takich błędów. W tym przeglądzie podsumowano najczęstsze klasy problemów, które mogą wystąpić, i zawiera łącza do bardziej szczegółowych informacji.

> [!NOTE]
> W przeszłości firma We zaleca się, że uaktualnienia, które obejmują kilka wersji programu Visual Studio powinny być wykonywane przyrostowo po jednej wersji naraz. Nie zalecamy już takiego podejścia. Odkryliśmy, że prawie zawsze jest łatwiej uaktualnić do najnowszej wersji programu Visual Studio, bez względu na to, ile lat ma baza kodu.

Pytania lub komentarze dotyczące procesu uaktualniania można wysyłać do pliku vcupgrade@microsoft.com.

## <a name="library-and-toolset-dependencies"></a>Zależności biblioteki i zestawu narzędzi

> [!NOTE]
> Ta sekcja dotyczy aplikacji i bibliotek utworzonych za pomocą programu Visual Studio 2013 i wcześniejszych. Zestawy narzędzi używane w programach Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 są zgodne z plikami binarnymi. Aby uzyskać więcej informacji, zobacz [Zgodność binarna c++ między programem Visual Studio 2015 a programem Visual Studio 2019](binary-compat-2015-2017.md).

Podczas uaktualniania aplikacji do nowej wersji programu Visual Studio, jest wskazane i w wielu przypadkach konieczne jest również uaktualnienie wszystkich bibliotek i bibliotek DLL, do których łączy się aplikacja. Wymaga to, że masz dostęp do kodu źródłowego lub że dostawca biblioteki może dostarczyć nowe pliki binarne skompilowane z tej samej wersji głównej kompilatora. Jeśli jeden z tych warunków jest spełniony, możesz pominąć tę sekcję, która dotyczy szczegółów zgodności binarnej. Jeśli tak nie jest, to może nie być w stanie korzystać z bibliotek w uaktualnionej aplikacji. Informacje zawarte w tej sekcji pomogą Ci zrozumieć, czy można kontynuować uaktualnienie.

### <a name="toolset"></a>Zestaw narzędzi

Formaty plików obj i .lib są dobrze zdefiniowane i rzadko się zmieniają. Czasami dodatki są dokonywane do tych formatów plików, ale te dodatki zazwyczaj nie wpływają na zdolność nowszych zestawów narzędzi do korzystania z plików obiektów i bibliotek produkowanych przez starsze zestawy narzędzi. Głównym wyjątkiem jest w tym przypadku, jeśli skompilować przy użyciu [/GL (Optymalizacja całego programu)](../build/reference/gl-whole-program-optimization.md). Jeśli skompilujesz przy użyciu, `/GL`wynikowy plik obiektu może być połączony tylko przy użyciu tego samego zestawu narzędzi, który został użyty do jego wytworzenia. Dlatego jeśli tworzysz plik `/GL` obiektu z kompilatorem programu Visual Studio 2017 (v141) i przy użyciu go, należy połączyć go za pomocą konsolidatora programu Visual Studio 2017 (wersja 141). To dlatego, że wewnętrzne struktury danych w plikach obiektów nie są stabilne w głównych wersjach zestawu narzędzi, a nowsze zestawy narzędzi nie rozumieją starszych formatów danych.

C++ nie ma stabilnego interfejsu binarnego aplikacji (ABI). Ale Visual Studio utrzymuje stabilny C++ ABI dla wszystkich wersji pomocniczych wydania. Visual Studio 2015 (w wersji 140), Visual Studio 2017 (v141) i Visual Studio 2019 (w wersji 142) różnią się tylko w wersji pomocniczej. Wszystkie mają ten sam główny numer wersji, który wynosi 14. Aby uzyskać więcej informacji, zobacz [Zgodność binarna c++ między programem Visual Studio 2015 a programem Visual Studio 2019](binary-compat-2015-2017.md).

Jeśli masz plik obiektu, który ma symbole zewnętrzne z powiązaniami C++, ten plik obiektu może nie łączyć się poprawnie z plikami obiektów wyprodukowanymi przez inną główną wersję zestawu narzędzi. Istnieje wiele możliwych wyników: link może całkowicie zakończyć się niepowodzeniem (na przykład, jeśli nazwa dekoracji została zmieniona). Łącze może zakończyć się pomyślnie, a rzeczy mogą nie działać w czasie wykonywania (na przykład, jeśli układ typu został zmieniony). Lub w wielu przypadkach, rzeczy mogą się zdarzyć do pracy i nic nie pójdzie źle. Należy również zauważyć, podczas gdy ABI C++ nie jest stabilny, C ABI i podzbiór C++ ABI wymagane dla COM są stabilne.

Jeśli łączysz się z biblioteką importu, w czasie wykonywania może być używana dowolna nowsza wersja bibliotek redystrybucyjnych programu Visual Studio, które zachowują zgodność z ABI. Na przykład jeśli aplikacja jest kompilowana i połączona przy użyciu zestawu narzędzi Aktualizacji 3 programu Visual Studio 2015, można użyć dowolnej zgodności z plikami binarnymi programu Visual Studio 2017 lub Visual Studio 2019, ponieważ biblioteki 2015, 2017 i 2019 zachowały zgodność z plikami binarnymi wstecznymi. Odwrotna sytuacja nie jest prawdziwa: nie można użyć redystrybucyjnego dla wcześniejszej wersji zestawu narzędzi niż do tworzenia kodu, nawet jeśli mają one zgodny ABI.

### <a name="libraries"></a>Biblioteki

Jeśli skompilujesz plik źródłowy przy użyciu określonej wersji plików nagłówkowych bibliotek programu Visual Studio C++ (przez #including nagłówków), wynikowy plik obiektu musi być połączony z tą samą wersją bibliotek. Tak na przykład, jeśli plik źródłowy jest skompilowany z Visual \<Studio 2015 Update 3 immintrin.h>, należy połączyć się z biblioteki vcruntime aktualizacji programu Visual Studio 2015. Podobnie jeśli plik źródłowy jest skompilowany z visual studio 2017 w wersji 15.5 \<> iostream, należy połączyć się z biblioteką visual studio 2017 w wersji 15.5 Standard C++, msvcprt. Mieszanie i dopasowywanie nie jest obsługiwane.

Dla biblioteki standardowej języka C++ mieszanie i dopasowywanie `#pragma detect_mismatch` zostało jawnie niedozwolone za pomocą standardowych nagłówków od programu Visual Studio 2010. Jeśli spróbujesz połączyć niezgodne pliki obiektów lub spróbujesz połączyć się z niewłaściwą biblioteką standardową, łącze zakończy się niepowodzeniem.

W przypadku CRT mieszanie i dopasowywanie nigdy nie było obsługiwane, ale często po prostu działało, przynajmniej do programu Visual Studio 2015 i uniwersalnego CRT, ponieważ powierzchnia interfejsu API nie zmieniła się znacznie w czasie. Universal CRT złamał wsteczną kompatybilność, dzięki czemu w przyszłości możemy utrzymać wsteczną kompatybilność. Innymi słowy, nie planujemy wprowadzenia nowych, wersjonowanych uniwersalnych plików binarnych CRT w przyszłości. Zamiast tego istniejący uniwersalny CRT jest teraz aktualizowany w miejscu.

Aby zapewnić zgodność łącza częściowego z plikami obiektów (i bibliotekami) skompilowanymi ze starszymi wersjami nagłówków środowiska wykonawczego Microsoft C, udostępniamy bibliotekę legacy_stdio_definitions.lib z programem Visual Studio 2015 i nowszymi. Ta biblioteka zawiera symbole zgodności dla większości funkcji i eksportu danych, które zostały usunięte z uniwersalnego CRT. Zestaw symboli zgodności dostarczonych przez legacy_stdio_definitions.lib jest wystarczający do zaspokojenia większości zależności, w tym wszystkich zależności w bibliotekach zawartych w zestawie Windows SDK. Istnieją jednak pewne symbole, które zostały usunięte z uniwersalnego CRT, dla których nie jest możliwe podanie symboli zgodności. Symbole te obejmują niektóre \_ \_funkcje\_(na przykład iob func) \_ \_\_\_\_i eksport \_ \_\_\_\_danych (na przykład imp iob, \_ \_imp pctype, imp\_\_\_mb\_cur\_max).

Jeśli masz bibliotekę statyczną, która została zbudowana ze starszą wersją nagłówków środowiska wykonawczego C, zalecamy następujące akcje w następującej kolejności:

1. Przebuduj bibliotekę statyczną przy użyciu nowej wersji programu Visual Studio i uniwersalnych nagłówków CRT do obsługi łączenia z uniwersalnym CRT. Takie podejście jest w pełni popieraną (a tym samym najlepszą) opcją.

1. Jeśli nie możesz (lub nie chcesz) odbudować biblioteki statycznej, możesz\_spróbować\_połączyć się ze starszymi stdio definitions.lib. Jeśli spełnia zależności czasu łącza biblioteki statycznej, będziemy chcieli dokładnie przetestować biblioteki statycznej, jak to jest używane w pliku binarnym, aby upewnić się, że nie jest niekorzystnie wpływ żadnej z [zmian behawioralnych, które zostały wprowadzone do Uniwersalnego CRT](visual-cpp-change-history-2003-2015.md#BK_CRT).

1. Jeśli zależności biblioteki statycznej nie są\_spełnione\_przez starsze stdio definitions.lib lub jeśli biblioteka nie działa z uniwersalnym CRT z powodu wyżej wymienionych zmian behawioralnych, zaleca się hermetyzowanie biblioteki statycznej w bibliotece DLL, która łączy się z poprawną wersją środowiska wykonawczego Microsoft C. Na przykład jeśli biblioteka statyczna została zbudowana przy użyciu programu Visual Studio 2013, należy utworzyć tę bibliotekę DLL przy użyciu programu Visual Studio 2013 i bibliotek c++ programu Visual Studio 2013. Tworząc bibliotekę w bibliotece DLL, można hermetyzować szczegóły implementacji, który jest jego zależność od określonej wersji środowiska wykonawczego języka Microsoft C. Należy zachować ostrożność, że interfejs DLL nie przecieka szczegóły, który C Runtime używa, na przykład przez zwrócenie pliku* przez granicę biblioteki DLL lub zwracając wskaźnik malloc przydzielone i oczekując wywołującego, aby go zwolnić.

Korzystanie z wielu CRT w jednym procesie nie jest samo w sobie problematyczne (w rzeczywistości większość procesów skończy się ładowanie wielu bibliotek DLL CRT; na przykład składniki systemu operacyjnego Windows będą zależeć od msvcrt.dll i CLR będzie zależeć od własnego prywatnego CRT). Problemy pojawiają się, gdy pomieszasz stan z różnych CRT. Na przykład nie należy przydzielić pamięci przy użyciu pliku msvcr110.dll!malloc i próbować przydzielić tę pamięć za pomocą pliku msvcr120.dll!free i nie należy próbować otworzyć pliku przy użyciu msvcr110!fopen i próbować odczytać z tego pliku za pomocą pliku msvcr120!fread. Tak długo, jak nie pomieszać stan z różnych CRT, można bezpiecznie mieć wiele CRTs załadowany w jednym procesie.

Aby uzyskać więcej informacji, zobacz [Uaktualnianie kodu do uniwersalnego CRT](upgrade-your-code-to-the-universal-crt.md).

## <a name="errors-due-to-project-settings"></a>Błędy spowodowane ustawieniami projektu

Aby rozpocząć proces uaktualniania, otwórz starszy projekt/rozwiązanie/obszar roboczy w najnowszej wersji programu Visual Studio. Visual Studio utworzy nowy projekt na podstawie starych ustawień projektu. Jeśli starszy projekt ma bibliotekę lub zawiera ścieżki, które są zakodowane na czas do niestandardowych lokalizacji, jest możliwe, że pliki w tych ścieżkach nie będą widoczne dla kompilatora, gdy projekt używa ustawień domyślnych. Aby uzyskać więcej informacji, zobacz [Ustawienie pliku wyjściowego konsoli .](porting-guide-spy-increment.md#linker_output_settings)

Ogólnie rzecz biorąc teraz jest to świetny czas, aby zorganizować kod projektu poprawnie w celu uproszczenia konserwacji projektu i pomóc uzyskać uaktualniony kod kompilacji tak szybko, jak to możliwe. Jeśli kod źródłowy jest już dobrze zorganizowany, a starszy projekt jest kompilowany za pomocą programu Visual Studio 2010 lub nowszego, można ręcznie edytować nowy plik projektu do obsługi kompilacji zarówno na starym, jak i nowym kompilatorze. W poniższym przykładzie pokazano, jak skompilować zarówno visual studio 2015 i Visual Studio 2017:

```xml
<PlatformToolset Condition="'$(VisualStudioVersion)'=='14.0'">v140</PlatformToolset>
<PlatformToolset Condition="'$(VisualStudioVersion)'=='15.0'">v141</PlatformToolset>
```

### <a name="lnk2019-unresolved-external"></a>LNK2019: Nierozwiązane zewnętrzne

W przypadku nierozwiązanych symboli może być konieczne naprawienie ustawień projektu.

- Jeśli plik źródłowy znajduje się w lokalizacji nieobekoniowej, czy ścieżka do katalogów dołączanych do projektu?

- Jeśli zewnętrzny jest zdefiniowany w pliku lib, czy określono ścieżkę lib we właściwościach projektu i czy znajduje się tam poprawna wersja pliku lib?

- Czy próbujesz połączyć się z plikiem lib, który został skompilowany z inną wersją programu Visual Studio? Jeśli tak, zobacz poprzednią sekcję dotyczącą zależności biblioteki i zestawu narzędzi.

- Czy typy argumentów w lokacji wywołania faktycznie odpowiadają istniejącemu przeciążeniu funkcji? Sprawdź typy podstawowe dla wszystkich typedefs w podpisie funkcji i w kodzie, który wywołuje funkcję są to, czego oczekujesz.

Aby rozwiązać problemy z nierozwiązanymi błędami symboli, można spróbować użyć pliku dumpbin.exe w celu zbadania symboli zdefiniowanych w pliku binarnym. Aby wyświetlić symbole zdefiniowane w bibliotece, spróbuj użyć następującego wiersza polecenia:

```cmd
dumpbin.exe /LINKERMEMBER somelibrary.lib
```

### <a name="zcwchar_t-wchar_t-is-native-type"></a>/Zc:wchar_t (wchar_t jest typem natywnym)

(W programie Microsoft Visual C++ 6.0 i wcześniejszych **wchar_t** nie został zaimplementowany jako typ wbudowany, ale został zadeklarowany w wchar.h jako typedef dla niepodpisanego skrótu.) Standard C++ wymaga, **aby wchar_t** jest typem wbudowanym. Korzystanie z wersji typedef może powodować problemy z przenoszeniem. W przypadku uaktualnienia z wcześniejszych wersji programu Visual Studio i napotkania błędu kompilatora C2664, ponieważ kod próbuje niejawnie przekonwertować `/Zc:wchar_t-` **wchar_t** na **niepodpisane krótkie**, zaleca się zmianę kodu, aby naprawić błąd, zamiast ustawienia . Aby uzyskać więcej informacji, zobacz [/Zc:wchar_t (wchar_t jest typem macierzystym).](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

### <a name="upgrading-with-the-linker-options-nodefaultlib-entry-and-noentry"></a>Uaktualnianie za pomocą opcji konsolidatora /NODEFAULTLIB, /ENTRY i /NOENTRY

Opcja `/NODEFAULTLIB` konsolidatora (lub właściwości ignoruj wszystkie biblioteki domyślne) informuje konsolidatora, aby nie łączył się automatycznie w bibliotekach domyślnych, takich jak CRT. Oznacza to, że każda biblioteka musi być wymieniona jako dane wejściowe indywidualnie. Ta lista bibliotek znajduje się we właściwości **Dodatkowe zależności** w sekcji **Konsolidator** w oknie dialogowym **Właściwości projektu.**

Projekty korzystające z tej opcji stanowią problem podczas uaktualniania, ponieważ zawartość niektórych bibliotek domyślnych została refaktoryzowana. Ponieważ każda biblioteka musi być wymieniona we właściwości **Dodatkowe zależności** lub w wierszu polecenia konsolidatora, należy zaktualizować listę bibliotek, aby używać wszystkich bieżących nazw.

W poniższej tabeli przedstawiono biblioteki, których zawartość uległa zmianie, począwszy od programu Visual Studio 2015. Aby uaktualnić, należy dodać nowe nazwy bibliotek w drugiej kolumnie do bibliotek w pierwszej kolumnie. Niektóre z tych bibliotek są biblioteki importu, ale to nie powinno mieć znaczenia.

|||
|-|-|
|Jeśli używasz:|Należy użyć następujących bibliotek:|
|Libcmt.lib|libcmt.lib, libucrt.lib, libvcruntime.lib|
|Libcmtd.lib|libcmtd.lib, libucrtd.lib, libvcruntimed.lib|
|Msvcrt.lib|msvcrt.lib, ucrt.lib, vcruntime.lib|
|msvcrtd.lib|msvcrtd.lib, ucrtd.lib, vcruntimed.lib|

Ten sam problem ma zastosowanie `/ENTRY` również w `/NOENTRY` przypadku użycia opcji lub opcji, które również mają wpływ na ominięcie bibliotek domyślnych.

## <a name="errors-due-to-improved-language-conformance"></a>Błędy spowodowane lepszą zgodnością z językami

Kompilator Microsoft C++ stale poprawiał swoją zgodność ze standardem C++ na przestrzeni lat. Kod, który skompilowany we wcześniejszych wersjach może nie skompilować w nowszych wersjach programu Visual Studio, ponieważ kompilator poprawnie flagi błąd, który wcześniej ignorowane lub jawnie dozwolone.

Na przykład `/Zc:forScope` przełącznik został wprowadzony na początku historii MSVC. Umożliwia zachowanie niezgodne dla zmiennych pętli. Ten przełącznik jest teraz przestarzały i może zostać usunięty w przyszłych wersjach. Zdecydowanie zaleca się, aby nie używać tego przełącznika podczas uaktualniania kodu. Aby uzyskać więcej informacji, zobacz [/Zc:forScope- jest przestarzałe](porting-guide-spy-increment.md#deprecated_forscope).

Jednym z przykładów błędu wspólnego kompilatora, który może pojawić się podczas uaktualniania, jest przekazywanie argumentu non-const do parametru const. Starsze wersje kompilatora nie zawsze oflagować go jako błąd. Aby uzyskać więcej informacji, zobacz [bardziej rygorystyczne konwersje kompilatora](porting-guide-spy-increment.md#stricter_conversions).

Aby uzyskać więcej informacji na temat określonych ulepszeń zgodności, zobacz [Visual C++ change history 2003 - 2015](visual-cpp-change-history-2003-2015.md) i [C++ ulepszenia zgodności w programie Visual Studio](../overview/cpp-conformance-improvements.md).

## <a name="errors-involving-stdinth-integral-types"></a>Błędy związane \<z stdint.h> typów integralnych

Nagłówek \<> stdint.h definiuje typedefs i makra, które w przeciwieństwie do wbudowanych typów całkowitych, są gwarantowane mieć określoną długość na wszystkich platformach. Niektóre przykłady `uint32_t` `int64_t`są i . Nagłówek \<> stdint.h został dodany w programie Visual Studio 2010. Kod, który został napisany przed 2010 r. mógł dostarczyć prywatnych definicji dla \<tych typów i te definicje nie zawsze mogą być zgodne z definicjami> stdint.h.

Jeśli błąd jest C2371 `stdint` i typ jest zaangażowany, prawdopodobnie oznacza to, że typ jest zdefiniowany w nagłówku albo w kodzie lub pliku lib innej firmy. Podczas uaktualniania należy wyeliminować wszelkie \<niestandardowe definicje typów> stdint.h, ale najpierw porównać definicje niestandardowe z bieżącymi definicjami standardowymi, aby upewnić się, że nie wprowadzasz nowych problemów.

Możesz nacisnąć **klawisz F12** (**Przejdź do definicji), aby**zobaczyć, gdzie zdefiniowano dany typ.

[/showIncludes](../build/reference/showincludes-list-include-files.md) opcja kompilatora może być przydatna tutaj. W oknie dialogowym **Strony właściwości** projektu otwórz stronę**Zaawansowane** **c/c++** > i ustaw **pokaż zawiera** na **Tak**. Następnie odbuduj projekt `#include`i zobacz listę s w oknie danych wyjściowych. Każdy nagłówek jest wcięcie pod nagłówkiem, który go zawiera.

## <a name="errors-involving-crt-functions"></a>Błędy związane z funkcjami CRT

Wiele zmian zostało wprowadzonych do środowiska wykonawczego C na przestrzeni lat. Dodano wiele bezpiecznych wersji funkcji, a niektóre zostały usunięte. Ponadto, jak opisano wcześniej w tym artykule, implementacja crt firmy Microsoft została refaktoryzowana w programie Visual Studio 2015 do nowych plików binarnych i skojarzonych plików lib.

Jeśli błąd dotyczy funkcji CRT, wyszukaj [w programie Visual C++ change history 2003 - 2015](visual-cpp-change-history-2003-2015.md) lub [C++ conformance ulepszenia w programie Visual Studio,](../overview/cpp-conformance-improvements.md) aby sprawdzić, czy te artykuły zawierają dodatkowe informacje. Jeśli błąd to LNK2019, nierozwiązany zewnętrzny, upewnij się, że funkcja nie została usunięta. W przeciwnym razie, jeśli masz pewność, że funkcja nadal istnieje, a kod wywołujący jest poprawny, sprawdź, czy projekt używa `/NODEFAULTLIB`. Jeśli tak, należy zaktualizować listę bibliotek, tak aby projekt używał nowych bibliotek uniwersalnych (UCRT). Aby uzyskać więcej informacji, zobacz sekcję powyżej biblioteki i zależności.

Jeśli błąd dotyczy `printf` `scanf`lub , upewnij się, że nie są prywatnie definiowania żadnej funkcji bez uwzględnienia stdio.h. Jeśli tak, usuń definicje prywatne lub\_łącze do starszych stdio\_definitions.lib. Tę bibliotekę można ustawić w oknie dialogowym **Strony właściwości** w obszarze Wejście**konsolidatora** > **Input** **Configuration Properties** > właściwości konfiguracji we właściwości **Dodatkowe zależności.** Jeśli łączysz się z zestawem Windows SDK 8.1 lub starszym, dodaj starsze\_stdio\_definitions.lib.

Jeśli błąd obejmuje argumenty ciągu formatu, to prawdopodobnie dlatego, że kompilator jest bardziej rygorystyczne dotyczące wymuszania standardu. Aby uzyskać więcej informacji, zobacz historię zmian. Należy zwrócić szczególną uwagę na wszelkie błędy w tym miejscu, ponieważ mogą one potencjalnie stanowić zagrożenie bezpieczeństwa.

## <a name="errors-due-to-changes-in-the-c-standard"></a>Błędy spowodowane zmianami w standardzie C++

Sam standard C++ ewoluował w sposób, który nie zawsze jest kompatybilny z wstecznym. Wprowadzenie w języku C++ 11 semantyki przenoszenia, nowe słowa kluczowe i inne funkcje biblioteki języka i standardowej biblioteki może potencjalnie spowodować błędy kompilatora, a nawet różne zachowanie środowiska uruchomieniowego.

Na przykład stary program C++ może zawierać nagłówek iostream.h. Ten nagłówek został przestarzały na początku historii języka C++ i ostatecznie został całkowicie usunięty z programu Visual Studio. W takim przypadku należy użyć \<iostream> i przepisać kod. Aby uzyskać więcej informacji, zobacz [Aktualizowanie starego kodu iostreams](porting-guide-spy-increment.md#updating_iostreams_code).

### <a name="c4838-narrowing-conversion-warning"></a>C4838: ostrzeżenie o zawężeniu konwersji

Standard C++ określa teraz, że konwersje z niepodpisanych na podpisane wartości zintegrowane są traktowane jako konwersje zawężające. Kompilator nie podniósł tego ostrzeżenia przed programem Visual Studio 2015. Sprawdź każde wystąpienie, aby upewnić się, że zwężenie nie wpływa na poprawność kodu.

## <a name="warnings-to-use-secure-crt-functions"></a>Ostrzeżenia dotyczące korzystania z bezpiecznych funkcji CRT

Z biegiem lat wprowadzono bezpieczne wersje funkcji środowiska wykonawczego języka C. Mimo że stare, niezabezpieczonych wersji są nadal dostępne, zaleca się, aby zmienić kod, aby korzystać z bezpiecznych wersji. Kompilator wyda ostrzeżenie dotyczące użycia wersji niezabezpieczonych. Można wyłączyć lub zignorować te ostrzeżenia. Aby wyłączyć ostrzeżenie dla wszystkich projektów w rozwiązaniu, otwórz **View** > **Property Manager**, wybierz wszystkie projekty, dla których chcesz wyłączyć ostrzeżenie, a następnie kliknij prawym przyciskiem myszy wybrane elementy i wybierz polecenie **Właściwości**. W oknie dialogowym **Strony właściwości** w obszarze **Właściwości** > konfiguracji**C/C++** > **Advanced**wybierz pozycję Wyłącz **określone ostrzeżenia**. Kliknij strzałkę listy rozwijanej, a następnie kliknij pozycję **Edytuj**. Wprowadź 4996 w polu tekstowym. (Nie dołączaj prefiksu "C"). Aby uzyskać więcej informacji, zobacz [Przenoszenie w celu użycia bezpiecznego CRT](porting-guide-spy-increment.md#porting_to_secure_crt).

## <a name="errors-due-to-changes-in-windows-apis-or-obsolete-sdks"></a>Błędy spowodowane zmianami w interfejsach API systemu Windows lub przestarzałymi zestawy SDK

Z biegiem lat interfejsy API systemu Windows i typy danych zostały dodane, a czasami zmienione lub usunięte. Ponadto inne SDK, które nie należały do podstawowego systemu operacyjnego, odeszły. Starsze programy mogą zatem zawierać wywołania interfejsów API, które już nie istnieją. Mogą również zawierać wywołania interfejsów API w innych pakietach MICROSOFT, które nie są już obsługiwane. Jeśli zostanie wyświetlony błąd związany z interfejsem API systemu Windows lub interfejsem API ze starszego pliku Microsoft SDK, możliwe, że interfejs API został usunięty i/lub zastąpiony przez nowszą, bezpieczniejszą funkcję.

Aby uzyskać więcej informacji na temat bieżącego zestawu interfejsu API i minimalnych obsługiwanych systemów operacyjnych dla określonego interfejsu API systemu Windows, zobacz [Interfejs API firmy Microsoft i katalog odwołań](https://msdn.microsoft.com/library) oraz przejdź do danego interfejsu API.

### <a name="windows-version"></a>Wersja systemu Windows

Podczas uaktualniania programu, który używa interfejsu API systemu Windows bezpośrednio lub pośrednio, należy zdecydować minimalną wersję systemu Windows do obsługi. W większości przypadków, Windows 7 jest dobrym wyborem. Aby uzyskać więcej informacji, zobacz [Problemy z plikami nagłówka](porting-guide-spy-increment.md#header_file_problems). Makro `WINVER` definiuje najstarszą wersję systemu Windows, na którą program jest przeznaczony do działania. Jeśli program MFC ustawia winver do 0x0501 (Windows XP) otrzymasz ostrzeżenie, ponieważ MFC nie obsługuje już XP, mimo że sam kompilator ma tryb XP.

Aby uzyskać więcej informacji, zobacz [Aktualizowanie docelowej wersji systemu Windows](porting-guide-spy-increment.md#updating_winver) i [bardziej nieaktualnych plików nagłówkowych](porting-guide-spy-increment.md#outdated_header_files).

## <a name="atl--mfc"></a>ATL / MFC

ATL i MFC są stosunkowo stabilne interfejsy API, ale zmiany są wprowadzane sporadycznie. Aby uzyskać więcej informacji, zobacz [Visual C++ change history 2003 - 2015](visual-cpp-change-history-2003-2015.md), [Co nowego w programie Visual C++ w programie Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)i ulepszenia zgodności języka [C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md).

### <a name="lnk-2005-_dllmain12-already-defined-in-msvcrtdlib"></a>LNK 2005 _DllMain@12 już zdefiniowane w MSVCRTD.lib

Ten błąd może wystąpić w aplikacjach MFC. Wskazuje problem z kolejnością między biblioteką CRT a biblioteką MFC. MFC musi być połączony najpierw tak, aby zapewniał nowe i usuwać operatory. Aby naprawić ten błąd, użyj przełącznika, `/NODEFAULTLIB` aby zignorować te biblioteki domyślne: MSVCRTD.lib i mfcs140d.lib. Następnie dodaj te same libs jako dodatkowe zależności.

## <a name="32-vs-64-bit"></a>32 vs 64 bit

Jeśli oryginalny kod jest kompilowany dla systemów 32-bitowych, masz możliwość utworzenia wersji 64-bitowej zamiast lub oprócz nowej aplikacji 32-bitowej. Ogólnie rzecz biorąc, należy najpierw uzyskać kompilację programu w trybie 32-bitowym, a następnie spróbować 64-bitowych. Kompilowanie dla 64-bitowych jest proste, ale w niektórych przypadkach może ujawnić błędy, które zostały ukryte przez kompilacje 32-bitowe.

Ponadto należy pamiętać o możliwych problemów w czasie kompilacji i czasie wykonywania związanych z rozmiarem wskaźnika, wartościami czasu i rozmiaru oraz specyfikatorami formatu w funkcjach printf i scanf. Aby uzyskać więcej informacji, zobacz [Konfigurowanie języka Visual C++ dla 64-bitowych obiektów docelowych x64](../build/configuring-programs-for-64-bit-visual-cpp.md) i [typowych 64-bitowych problemów z migracją w języku Visual C++](../build/common-visual-cpp-64-bit-migration-issues.md). Aby uzyskać dodatkowe wskazówki dotyczące migracji, zobacz [Przewodnik po programowaniu 64-bitowego systemu Windows](/windows/win32/WinProg64/programming-guide-for-64-bit-windows).

## <a name="unicode-vs-mbcsascii"></a>Unicode vs MBCS/ASCII

Zanim unicode został ustandaryzowany, wiele programów używane Multibyte Character Set (MBCS) do reprezentowania znaków, które nie zostały uwzględnione w zestawie znaków ASCII. W starszych projektach MFC MBCS było ustawieniem domyślnym, a po uaktualnieniu takiego programu zostaną wyświetlone ostrzeżenia, które zalecają użycie Unicode. Możesz wyłączyć lub zignorować ostrzeżenie, jeśli zdecydujesz, że konwersja na Unicode nie jest warta kosztu rozwoju. Aby wyłączyć go dla wszystkich projektów w rozwiązaniu, otwórz **View** > **Property Manager**, wybierz wszystkie projekty, dla których chcesz wyłączyć ostrzeżenie, a następnie kliknij prawym przyciskiem myszy wybrane elementy i wybierz polecenie **Właściwości**. W oknie dialogowym **Strony właściwości** wybierz pozycję **Właściwości** > konfiguracji**C/C++** > **Zaawansowane**. We właściwości **Wyłącz określone ostrzeżenia** otwórz strzałkę listy rozwijanej, a następnie wybierz pozycję **Edytuj**. Wprowadź 4996 w polu tekstowym. (Nie dołączaj prefiksu "C"). Wybierz **przycisk OK,** aby zapisać właściwość, a następnie wybierz przycisk **OK,** aby zapisać zmiany.

Aby uzyskać więcej informacji, zobacz [Przenoszenie z MBCS do Unicode](porting-guide-spy-increment.md#porting_to_unicode). Aby uzyskać ogólne informacje o mbcs vs Unicode, zobacz [Tekst i ciągi ciągów w visual C++](../text/text-and-strings-in-visual-cpp.md) i [internacjonalizacji](../c-runtime-library/internationalization.md) .

## <a name="see-also"></a>Zobacz też

[Uaktualnianie projektów z wcześniejszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)
