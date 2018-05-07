---
title: Błąd narzędzi konsolidatora LNK1104 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1104
dev_langs:
- C++
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d2b832d4bceab88fbf3fbe8325a414669d11073c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk1104"></a>Błąd narzędzi konsolidatora LNK1104

> Nie można otworzyć pliku "*filename*"

Konsolidator nie można otworzyć określonego pliku. Najbardziej typowe przyczyny tego problemu są, że plik jest w użyciu lub zablokowany przez inny proces, nie istnieje, nie można znaleźć w jednym z katalogów wyszukiwania konsolidator lub nie masz wystarczających uprawnień dostępu do tego pliku. Rzadziej mógł zostać uruchomiony mało miejsca na dysku, plik może być za duża lub ścieżka do pliku może być zbyt długa.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ten błąd może wystąpić, jeśli konsolidator próbuje otworzyć pliku do odczytu lub zapisu. Aby zawęzić możliwe przyczyny, należy najpierw sprawdź, jaki rodzaj plików jest i użyj następujących sekcji, aby zidentyfikować i rozwiązać konkretnego problemu.

### <a name="cannot-open-your-app-or-its-pdb-file"></a>Nie można otworzyć aplikację lub plik PDB

Jeśli nazwa pliku jest plikiem wykonywalnym kompilacji projektu lub pliku .pdb skojarzone Najczęstszą przyczyną jest, że aplikacja jest już uruchomiony podczas próby go odbudować lub jest on załadowany w debugerze. Aby rozwiązać ten problem, należy zatrzymać program i zwolnić ją z debugera przed zbudowaniem go ponownie. Jeśli aplikacja jest otwarty w innym programie, takich jak edytor zasobów, zamknij go. W ekstremalnych przypadkach może być konieczne użycie Menedżera zadań na zakończenie procesu, lub Zatrzymaj i uruchom ponownie program Visual Studio.

Programy antywirusowe często tymczasowo blokowanie dostępu do nowo utworzonych plików, szczególnie .exe i .dll plików wykonywalnych. Aby rozwiązać ten problem, spróbuj wykluczanie katalogów kompilacji projektu skanera antywirusowego.

### <a name="cannot-open-a-microsoft-library-file"></a>Nie można otworzyć pliku Microsoft Library.

Jeśli plik, którego nie można otworzyć plików biblioteki standardowe dostarczane przez firmę Microsoft, np. kernel32.lib, może być błąd konfiguracji projektu lub wystąpił błąd instalacji. Sprawdź, czy zestaw Windows SDK został zainstalowany, a jeśli projekt wymaga innych bibliotek firmy Microsoft, takich jak MFC, upewnij się, że składniki MFC również zostały zainstalowane przez Instalatora programu Visual Studio. Możesz uruchomić Instalatora ponownie, aby dodać składniki opcjonalne w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [zmodyfikować Visual Studio](/visualstudio/install/modify-visual-studio). Karta pojedynczych składników w instalatorze można wybrać określone biblioteki i zestawy SDK.

Jeśli tworzysz projekt, który został utworzony przy użyciu starszej wersji programu Visual Studio, zestaw narzędzi platformy i biblioteki dla tej wersji może nie być zainstalowana. Jeśli komunikat o błędzie dla nazwy określonej wersji biblioteki, takich jak msvcr100.lib, jest to prawdopodobnie przyczyną. Aby rozwiązać ten problem, dostępne są dwie opcje: można uaktualnić projektu do bieżącego zestawu narzędzi platformy w zainstalowaniu lub można zainstalować starszej zestaw narzędzi i tworzenie projektu bez zmian. Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów z wcześniejszych wersji programu Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) i [Użyj natywnego wielowersyjności kodu w programie Visual Studio do kompilacji projektów starego](../../porting/use-native-multi-targeting.md).

Jeśli zostanie wyświetlony ten błąd podczas tworzenia nowego platformy docelowej lub w konfiguracji z bibliotekami narzędzi konfiguracji lub platformę tego projektu może nie być zainstalowana. Sprawdź, czy **zestaw narzędzi platformy** i **zestawu SDK systemu Windows w wersji** określony w [stronę Ogólne właściwości](../../ide/general-property-page-project.md) projektu są zainstalowane, a następnie sprawdź, czy wymagane biblioteki są dostępne w **katalogi bibliotek** określony w [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md) ustawień konfiguracji. Istnieją oddzielne ustawienia dla debugowania i konfiguracje sieci sprzedaży, a także konfiguracji 32-bitowe i 64-bitowe, więc jeśli jednego kompilacji działa, ale inny powoduje błąd, upewnij się, ustawienia są poprawne i wymagane narzędzia i biblioteki są zainstalowane dla każdego konfigurację kompilacji.

Jeśli używasz programu Visual Studio IDE do kompilacji projektu, który został skopiowany z innego komputera, lokalizacje instalacji biblioteki mogą się różnić. Sprawdź **katalogi bibliotek** właściwość [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md) dla projektu i zaktualizuj ją w razie potrzeby. Aby wyświetlić i edytować bieżącej ścieżki biblioteki w IDE, wybierz kontrolka listy rozwijanej dla **katalogi bibliotek** właściwości i wybierz polecenie **Edytuj**. **Obliczyć wartość** sekcji **katalogi bibliotek** okno dialogowe wyświetla listę bieżącej ścieżki wyszukiwane pliki biblioteki.

Ten błąd może również wystąpić, jeśli ścieżka do zestawu Windows SDK jest nieaktualna. Jeśli zainstalowano wersję zestawu Windows SDK, która jest nowsza od używanej wersji programu Visual Studio, upewnij się, że ścieżki określona w [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md) są aktualizowane zgodnie z nowego zestawu SDK. Korzystając z wiersza polecenia dewelopera, upewnij się, że plik wsadowy inicjuje zmienne środowiskowe Zaktualizowano nowe ścieżki zestawu SDK. Za pomocą Instalatora programu Visual Studio SDK zaktualizowanej można uniknąć tego problemu.

### <a name="cannot-open-a-third-party-library-file"></a>Nie można otworzyć pliku biblioteki innych firm

Istnieje kilka typowych przyczyn tego problemu:

- Ścieżka do pliku biblioteki może być nieprawidłowa lub nie określono go do konsolidatora.

- Zainstalowano 32-bitowej wersji biblioteki, ale tworzona dla 64-bitowej lub na odwrót.

- Biblioteka może być zależny od innych bibliotek, które nie są zainstalowane.

Aby rozwiązać problem ze ścieżką, sprawdź, czy lib — zmienna środowiskowa jest ustawiona i zawiera wszystkie katalogi bibliotek, używanego dla każdej konfiguracji kompilacji. W środowisku IDE programu lib — zmienna jest ustawiona **katalogi bibliotek** właściwość [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md). Upewnij się, że wszystkie katalogi, które zawiera bibliotek, które są potrzebne są wymienione w tym miejscu, dla każdej konfiguracji kompilacji.

Jeśli należy podać katalog biblioteki który zastępuje katalog biblioteki standardowej, możesz użyć [/libpath](../../build/reference/libpath-additional-libpath.md) opcji w wierszu polecenia lub w środowisku IDE, można użyć **dodatkowe katalogi bibliotek** właściwości w **właściwości konfiguracji > konsolidatora > Ogólne** stronę właściwości projektu.

Upewnij się, że zainstalowano każdej wersji biblioteki potrzebnych do tworzenia konfiguracje. Należy rozważyć użycie [vcpkg](../../vcpkg.md) pakietu Narzędzia zarządzania do automatyzowania instalacji i konfiguracji dla wielu wspólne biblioteki. Gdy to możliwe, najlepiej kompilacji kopii bibliotek innych firm, co się, że wszystkie zależności lokalne wymaga bibliotek, które zostały one utworzone dla tej samej konfiguracji jako projektu.

### <a name="cannot-open-a-file-built-by-your-project"></a>Nie można otworzyć plik utworzony przez projektu

Może występować ten błąd, jeśli plik *filename* jest konstruowany przez rozwiązania, ale jeszcze nie istnieje, gdy konsolidator spróbuje uzyskać do niego dostęp. Może się to zdarzyć, gdy jeden projekt jest zależny od innego projektu, ale projekty nie są tworzone we właściwej kolejności. Aby rozwiązać ten problem, upewnij się, odwołania projektu są ustawione w projekcie, który używa pliku, więc brakujący plik jest skompilowane zanim jest wymagana. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań do projektów Visual C++](../../ide/adding-references-in-visual-cpp-projects.md) i [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Nie można otworzyć pliku "C:\\Program.obj"

Jeśli zostanie wyświetlony ten błąd lub błąd podobny uwzględniającą .obj nieoczekiwany plik w folderze głównym dysku, problem jest prawie na pewno ścieżce biblioteki, która nie jest ujęty w podwójny cudzysłów.

Aby rozwiązać ten problem do kompilacji z wiersza polecenia, sprawdź [/libpath](../../build/reference/libpath-additional-libpath.md) opcji parametrów, ścieżek określonych w zmiennej środowiskowej LIB i ścieżek określonych w wierszu polecenia i upewnij się, że Użyj podwójnych cudzysłowów wokół żadnych ścieżek zawierające spacje.

Aby rozwiązać ten problem w IDE, sprawdź **katalogi bibliotek** właściwość [właściwości konfiguracji > katalogi VC ++](../../ide/vcpp-directories-property-page.md) strony właściwości **dodatkowe katalogi bibliotek** właściwości w **właściwości konfiguracji > konsolidatora > Ogólne** strony właściwości oraz **dodatkowe zależności** właściwości w **konfiguracji Właściwości > konsolidatora > wprowadzania** stronę właściwości projektu. Upewnij się, że wszystkie ścieżki katalogu zawierające bibliotek, które są potrzebne są ujęte w cudzysłów podwójny, w razie potrzeby.

### <a name="other-common-issues"></a>Inne typowe problemy

Ten błąd może wystąpić, gdy nazwa pliku biblioteki lub ścieżka do konsolidatora w wierszu polecenia lub w [#pragma komentarz (lib, "library_name")](../../preprocessor/comment-c-cpp.md) dyrektywa jest niepoprawny lub ścieżka zawiera nieprawidłowe określenie dysku. Sprawdź pisownię i rozszerzenie pliku i sprawdź, czy plik istnieje w określonej lokalizacji.

Inny program może mieć plik jest otwarty i konsolidator nie może zapisywać do niego. Programy antywirusowe często tymczasowo zablokować dostęp do nowo utworzonych plików. Aby rozwiązać ten problem, spróbuj wykluczanie katalogów kompilacji projektu skanera antywirusowego.

Jeśli używasz opcji równoległych kompilacji jest możliwe, że program Visual Studio został zablokowany w pliku w innym wątku. Aby rozwiązać ten problem, sprawdź nie utworzenie tego samego obiektu kodu lub biblioteki w wielu projektach, i użyj zależności kompilacji lub odwołania projektu do odebrania skompilowanych plików binarnych w projekcie.

Po określeniu poszczególnych bibliotekach w **dodatkowe zależności** właściwości bezpośrednio, przy użyciu funkcji miejsca do oddzielnych nazw bibliotek, nie przecinkami lub średnikami. Jeśli używasz **Edytuj** element menu, aby otworzyć **dodatkowe zależności** okno dialogowe, użyj newlines Rozdziel nazwy, nie przecinkami, średnikami lub spacjami. Również użyć newlines po określeniu ścieżki biblioteki w **katalogi bibliotek** i **dodatkowe katalogi bibliotek** okien dialogowych.

Może występować ten błąd po ścieżce dla *filename* rozwijany do więcej niż 260 znaków. Zmiana nazw lub rozmieszczanie struktury katalogów, w razie potrzeby w celu skrócenia ścieżki do wymaganych plików.

Ten błąd może wystąpić, ponieważ plik jest zbyt duży. Biblioteki lub obiekt pliki więcej niż gigabajt rozmiar może powodować problemy dla konsolidator 32-bitowy. Możliwe rozwiązanie tego problemu polega na użyciu zestawu narzędzi 64-bitowych. Aby uzyskać więcej informacji na temat w tym celu w wierszu polecenia, zobacz [porady: Włączanie 64-bitowych Visual C++ narzędzi w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Aby uzyskać informacje, jak to zrobić w środowisku IDE, zobacz [przy użyciu programu MSBuild z 64-bitowych narzędzi i kompilatora](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) i ten wpis przepełnienie stosu: [jak Visual Studio Użyj łańcuchem narzędzi natywnego amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Ten błąd może wystąpić, jeśli masz pliku niewystarczające uprawnienia dostępu do *filename*. Może się to zdarzyć, jeśli można użyć kontem zwykłego użytkownika, a następnie spróbuj uzyskać dostęp do plików biblioteki w katalogach chronionego systemu lub plików skopiowanych z innych użytkowników, którzy mają uprawnienia oryginalnego ustawić. Aby rozwiązać ten problem, należy przenieść plik do katalogu projektu zapisywalny. Jeśli plik znajduje się w katalogu zapisywalny, ale ma uprawnienia niedostępne, można użyć wiersza polecenia z uprawnieniami administratora i uruchom polecenie takeown.exe, aby przejąć na własność pliku.

Ten błąd może wystąpić, gdy nie ma wystarczającej ilości wolnego miejsca. Konsolidator używa pliki tymczasowe w kilku przypadkach. Nawet jeśli masz wystarczającą ilość miejsca na dysku, bardzo dużych łącza można warstwę lub fragmentu dostępne miejsce na dysku. Należy rozważyć użycie [od (optymalizacje)](../../build/reference/opt-optimizations.md) opcja; czynności przechodnie odczyty eliminacji COMDAT wszystkie pliki obiektów wiele razy.

Jeśli *filename* nosi nazwę LNK*nnn*, czyli generowanych przez konsolidator pliku tymczasowego pliku, katalogu określonym w zmiennej środowiskowej TMP może nie istnieć lub może być więcej niż jeden katalog określona dla zmiennej środowiskowej TMP. Dla zmiennej środowiskowej TMP powinna zostać określona ścieżka tylko jeden katalog.
