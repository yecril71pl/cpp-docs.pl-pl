---
title: Błąd narzędzi konsolidatora LNK1104
ms.date: 05/17/2017
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: eadeeb7ac19e3975a37a1364502b33400018cb05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255516"
---
# <a name="linker-tools-error-lnk1104"></a>Błąd narzędzi konsolidatora LNK1104

> Nie można otworzyć pliku "*filename*"

Konsolidator nie można otworzyć określonego pliku. Najbardziej typowe przyczyny tego problemu to, czy plik jest używany lub zablokowany przez inny proces, nie istnieje, nie można znaleźć w jednym z katalogów wyszukiwania konsolidator lub nie masz wystarczających uprawnień dostępu do tego pliku. Rzadziej użytkownik może zabrakło wolnego miejsca na dysku, plik jest za duży lub ścieżkę do pliku może być zbyt długa.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i potencjalne rozwiązania

Ten błąd może wystąpić, gdy konsolidator podejmuje próbę otwarcia pliku do odczytu lub zapisu. Aby zawęzić możliwe przyczyny, należy najpierw sprawdź, jakiego typu pliku jest i użyj poniższych sekcji do ułatwiającego identyfikowanie i Rozwiązywanie konkretnego problemu.

### <a name="cannot-open-your-app-or-its-pdb-file"></a>Nie można otworzyć aplikację lub plik .pdb

Jeśli nazwa pliku wykonywalnego projekt jest kompilowany lub skojarzony plik .pdb, Najczęstszą przyczyną jest, że aplikacja jest już uruchomiony podczas próby odbudować lub jest on ładowany w debugerze. Aby rozwiązać ten problem, należy zatrzymać program i zwolnienia z debugera przed kompilacją go ponownie. Jeśli aplikacja jest otwarty w innym programie, takich jak edytor zasobów, zamknij go. W skrajnych przypadkach może być konieczne zakończenie procesu, lub Zatrzymaj i uruchom ponownie program Visual Studio za pomocą Menedżera zadań.

Programy antywirusowe często tymczasowe blokowanie dostępu do nowo tworzonych plików, szczególnie .exe i .dll plików wykonywalnych. Aby rozwiązać ten problem, spróbuj wykluczenie katalogów kompilacji projektu za pomocą skanera oprogramowania antywirusowego.

### <a name="cannot-open-a-microsoft-library-file"></a>Nie można otworzyć pliku Microsoft Library

Jeśli plik, którego nie można otworzyć plików biblioteki standardowej, dostarczone przez firmę Microsoft, np. kernel32.lib, może być błąd konfiguracji projektu lub komunikat o błędzie instalacji. Sprawdź, czy został zainstalowany zestaw Windows SDK i jeśli Twój projekt wymaga innych bibliotek Microsoft, takie jak MFC, upewnij się, że składniki MFC były także zainstalowane przez Instalatora programu Visual Studio. Możesz uruchomić Instalatora ponownie w celu dodania opcjonalnych składników w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [modyfikowanie programu Visual Studio](/visualstudio/install/modify-visual-studio). Użyj na karcie poszczególne składniki w Instalatorze wybrać określonych bibliotek i zestawów SDK.

Jeśli tworzysz projekt, który został utworzony przy użyciu starszej wersji programu Visual Studio, zestaw narzędzi platformy i biblioteki dla tej wersji może nie być zainstalowana. Jeśli komunikat o błędzie dla nazwy określonej wersji biblioteki, takie jak msvcr100.lib, prawdopodobnie jest przyczyną. Aby rozwiązać ten problem, masz dwie opcje: możesz uaktualnić projekt, aby użyć bieżącego zestawu narzędzi platformy, zainstalowano lub można zainstalować starszej zestaw narzędzi i skompilowania projektu bez zmian. Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów ze starszych wersji programu Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) i [Użyj natywnej wielowersyjności kodu w programie Visual Studio do kompilacji starych projektów](../../porting/use-native-multi-targeting.md).

Jeśli zostanie wyświetlony ten błąd podczas tworzenia nowej docelowej platformy lub konfiguracji biblioteki dla tej konfiguracji lub platformy zestaw narzędzi projektu może nie być zainstalowana. Upewnij się, że **zestawu narzędzi platformy** i **wersja zestawu SDK Windows** określonych w [strona właściwości ogólnych](../../build/reference/general-property-page-project.md) dla projektu są zainstalowane i upewnij się, że wymagane biblioteki są dostępne w **katalogi bibliotek** określonych w [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) ustawień konfiguracji. Istnieją oddzielne ustawienia do debugowania i konfiguracje sieci sprzedaży, a także konfiguracji 32-bitowych i 64-bitowych, więc jeśli jednej kompilacji działa, ale inny powoduje błąd, upewnij się, ustawienia są poprawne, a wymagane narzędzia i biblioteki są instalowane dla każdego Konfiguracja, które tworzysz.

Jeśli używasz środowiska IDE programu Visual Studio do utworzenia projektu, który został skopiowany z innego komputera, lokalizacje instalacji dla bibliotek mogą różnić się. Sprawdź **katalogi bibliotek** właściwość [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) dla projektu i zaktualizować go, jeśli to konieczne. Aby wyświetlić i edytować bieżącej ścieżki biblioteki ustawić w IDE, wybierz formant listy rozwijanej dla **katalogi bibliotek** właściwości i wybierz polecenie **Edytuj**. **Obliczone wartości** części **katalogi bibliotek** okno dialogowe wyświetla listę bieżących ścieżek wyszukiwane pliki biblioteki.

Ten błąd może również wystąpić, gdy ścieżka do zestawu Windows SDK jest nieaktualna. Jeśli zainstalowano wersję zestawu Windows SDK, która jest nowsza niż ta wersja programu Visual Studio, upewnij się, że ścieżki określona w [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md) zostaną zaktualizowane w celu nowy zestaw SDK. Korzystając z wiersza polecenia dla deweloperów, upewnij się, że plik wsadowy, który inicjuje zmienne środowiskowe został zaktualizowany w nowej ścieżki zestawu SDK. Za pomocą Instalatora programu Visual Studio i zainstalować zaktualizowane zestawy SDK można uniknąć tego problemu.

### <a name="cannot-open-a-third-party-library-file"></a>Nie można otworzyć pliku biblioteki innej firmy

Istnieje kilka typowych przyczyn tego problemu:

- Ścieżka do pliku biblioteki może być nieprawidłowa lub nie określono go do konsolidatora.

- Zainstalowany 32-bitowej wersji biblioteki, ale tworzona dla 64-bitowej lub na odwrót.

- Biblioteka może być zależny od innych bibliotek, które nie są zainstalowane.

Aby rozwiązać problem ze ścieżką, sprawdź, czy zmienna środowiskowa LIB jest ustawiona i zawiera wszystkie katalogi bibliotek, których używasz, dla każdej konfiguracji, które tworzysz. W środowisku IDE, zmienna LIB jest ustawiana przez **katalogi bibliotek** właściwość [VC ++ Directories Property Page](../../build/reference/vcpp-directories-property-page.md). Upewnij się, że wszystkie katalogi, które zawierają biblioteki, potrzebne są wymienione w tym miejscu dla każdej konfiguracji, które tworzysz.

Jeśli należy podać katalog biblioteki, zastępuje katalog biblioteki standardowej, możesz użyć [/libpath —](../../build/reference/libpath-additional-libpath.md) opcji w wierszu polecenia lub w środowisku IDE, możesz użyć **dodatkowe katalogi bibliotek** Właściwość **właściwości konfiguracji > Konsolidator > Ogólne** strony właściwości dla projektu.

Upewnij się, że zainstalowano wszystkie wersje biblioteki, czego potrzebujesz do konfiguracji, które tworzysz. Należy rozważyć użycie [vcpkg](../../vcpkg.md) pakietu Narzędzia zarządzania w celu zautomatyzowania instalacji i konfiguracji na potrzeby wielu wspólnych bibliotek. Gdy to możliwe, najlepiej jest tworzyć własne kopie bibliotek innych firm, tak, aby upewnij się, że wszystkie lokalne zależności, które wymagają biblioteki, a następnie zostały one utworzone dla tej samej konfiguracji jako projekt.

### <a name="cannot-open-a-file-built-by-your-project"></a>Nie można otworzyć pliku, utworzone w projekcie

Jeśli ten błąd może zostać wyświetlony plik *filename* został skompilowany według rozwiązania, ale jeszcze nie istnieje podczas konsolidator próbuje uzyskać do niego dostęp. Może to nastąpić, gdy jeden projekt jest zależny od innego projektu, ale projekty są kompilowane w odpowiedniej kolejności. Aby rozwiązać ten problem, upewnij się, odwołania projektu są ustawione w projekcie, który używa pliku, więc brakujący plik jest skompilowane, zanim jest to wymagane. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań w projektach języka Visual C++](../../build/adding-references-in-visual-cpp-projects.md) i [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Nie można otworzyć pliku "C:\\Program.obj"

Jeśli widzisz ten błąd lub błąd podobny, obejmujące .obj nieoczekiwany plik w folderze głównym dysku, problem polega na prawie na pewno ścieżka biblioteki, która nie jest ujęty w cudzysłów.

Aby rozwiązać ten problem w przypadku kompilacji z wiersza polecenia, sprawdź [/libpath —](../../build/reference/libpath-additional-libpath.md) opcji parametrów, określone w zmiennej środowiskowej LIB ścieżki i ścieżek określonych w wierszu polecenia i upewnij się, że Użyj podwójnych cudzysłowów wokół wszystkie ścieżki która zawiera spacje.

Aby rozwiązać ten problem w środowisku IDE, zapoznaj się z **katalogi bibliotek** właściwość [właściwości konfiguracji > katalogi VC ++](../../build/reference/vcpp-directories-property-page.md) strona właściwości **dodatkowe katalogi bibliotek** właściwości w **właściwości konfiguracji > Konsolidator > Ogólne** stronę właściwości i **dodatkowe zależności** właściwość **konfiguracji Właściwości > Konsolidator > wejście** strony właściwości dla projektu. Upewnij się, że wszystkie ścieżki katalogu, które zawierają biblioteki, potrzebne są opakowane w podwójne cudzysłowy, jeśli to konieczne.

### <a name="other-common-issues"></a>Inne typowe problemy

Ten błąd może wystąpić, gdy biblioteka, nazwa_pliku lub ścieżka do konsolidatora, w wierszu polecenia lub w [#pragma comment (lib, "library_name")](../../preprocessor/comment-c-cpp.md) dyrektywa jest niepoprawny lub ścieżka ma nieprawidłowe określenie dysku. Sprawdź pisownię i rozszerzenie pliku, a następnie sprawdź, czy plik istnieje w określonej lokalizacji.

Inny program może mieć plik jest otwarty i konsolidator nie może zapisać do niego. Programy antywirusowe często tymczasowo zablokować dostęp do nowo tworzonych plików. Aby rozwiązać ten problem, spróbuj wykluczenie katalogów kompilacji projektu za pomocą skanera oprogramowania antywirusowego.

Jeśli używasz opcji kompilacji równoległych, jest to możliwe, że program Visual Studio został zablokowany w pliku w innym wątku. Aby rozwiązać ten problem, sprawdź, nie tworzysz ten sam obiekt kodu lub biblioteki w wielu projektach i użyj zależności kompilacji lub odwołania do projektu aby wczytać skompilowane pliki binarne w projekcie.

Po określeniu poszczególnych bibliotekach w **dodatkowe zależności** właściwości bezpośrednio, przy użyciu spacji do oddzielania nazw bibliotek, nie przecinkami lub średnikami. Jeśli używasz **Edytuj** element menu, aby otworzyć **dodatkowe zależności** okno dialogowe, użyj tabulacji, aby rozdzielić nazwy, nie przecinkami, średnikami lub spacjami. Również użyć oddzielane po określeniu ścieżki biblioteki w **katalogi bibliotek** i **dodatkowe katalogi bibliotek** okien dialogowych.

Może zostać wyświetlony ten błąd podczas ścieżkę dla *filename* rozwija się do więcej niż 260 znaków. Zmień nazwy lub zmień ich rozmieszczenie struktury katalogów, w razie potrzeby skrócenie czasu ścieżki do wymaganych plików.

Ten błąd może wystąpić, ponieważ plik jest zbyt duży. Biblioteki lub obiekt pliki więcej niż gigabajta rozmiarze mogą powodować problemy dla konsolidator 32-bitowy. Możliwych poprawkę rozwiązującą ten problem polega na użyciu 64-bitowego zestawu narzędzi. Aby uzyskać więcej informacji na temat w tym celu w wierszu polecenia, zobacz [jak: Włączanie 64-bitowego zestawu narzędzi Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Aby uzyskać informacje, jak to zrobić w środowisku IDE, zobacz [przy użyciu programu MSBuild z 64-bitowym kompilatorem i narzędziami](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) i ten wpis w witrynie Stack Overflow: [Jak Visual Studio ma używać łańcucha narzędzi natywnych amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Ten błąd może wystąpić, jeśli masz plik niewystarczające uprawnienia dostępu do *filename*. Może się to zdarzyć, jeśli możesz użyć konta zwykłego użytkownika i próba dostępu do plików biblioteki w katalogach chronionych systemu lub użyć plików skopiowanych z innym użytkownikom z uprawnieniami oryginalnego zestawu. Aby rozwiązać ten problem, należy przenieść plik do katalogu projektu zapisywalny. Jeśli plik znajduje się w katalogu zapisywalny, ale ma uprawnienia niedostępny, można użyć wiersza polecenia z uprawnieniami administratora i uruchom polecenie takeown.exe przejęcie na własność pliku.

Ten błąd może wystąpić, gdy nie masz wystarczająco dużo miejsca na dysku. Konsolidator używa plików tymczasowych w kilku przypadkach. Nawet jeśli masz wystarczającą ilość miejsca na dysku, bardzo dużych łącza można będzie mogła użyć lub fragmentu dostępnego miejsca na dysku. Należy rozważyć użycie [od (optymalizacje)](../../build/reference/opt-optimizations.md) opcja; wykonując przechodnie COMDAT eliminacji odczytuje wszystkie pliki obiektów wiele razy.

Jeśli *filename* nosi nazwę LNK*nnn*, czyli, nazwa_pliku, generowanych przez konsolidator pliku tymczasowego, określony w zmiennej środowiskowej TMP katalog nie istnieje lub może być więcej niż jeden katalog określona dla zmiennej środowiskowej TMP. Dla zmiennej środowiskowej TMP należy określić ścieżkę tylko jednemu katalogowi.
