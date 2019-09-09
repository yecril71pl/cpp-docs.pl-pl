---
title: Błąd narzędzi konsolidatora LNK1104
ms.date: 09/06/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: f3effd9054954a90f69c5b18d8f099e6d705d9a3
ms.sourcegitcommit: 7babce70714242cf498ca811eec3695fad3abd03
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/09/2019
ms.locfileid: "70808837"
---
# <a name="linker-tools-error-lnk1104"></a>Błąd narzędzi konsolidatora LNK1104

> nie można otworzyć pliku "*filename*"

Konsolidator nie może otworzyć określonego pliku. Najczęstszymi przyczynami tego problemu jest to, że plik jest używany lub zablokowany przez inny proces. Prawdopodobnie plik nie istnieje lub nie można go znaleźć w jednym z katalogów szukanych przez konsolidatora. Lub nie masz wystarczających uprawnień, aby uzyskać dostęp do pliku. Mniej często zabrakło miejsca na dysku, plik może być zbyt duży lub ścieżka do pliku może być za długa.

## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania

Ten błąd może wystąpić, gdy konsolidator próbuje otworzyć plik do odczytu lub do zapisu. Aby zawęzić możliwe przyczyny, należy najpierw sprawdzić rodzaj pliku. Następnie w poniższych sekcjach znajdują się informacje ułatwiające zidentyfikowanie i rozwiązanie określonego problemu.

### <a name="cant-open-your-app-or-its-pdb-file"></a>Nie można otworzyć aplikacji lub jej pliku. pdb

Jeśli nazwa pliku jest plikiem wykonywalnym kompilowanym przez projekt lub skojarzonym plikiem. pdb, najbardziej typową przyczyną jest to, że aplikacja jest już uruchomiona podczas próby jej odbudowania lub załadowana w debugerze. Aby rozwiązać ten problem, Zatrzymaj program i zwolnij go z debugera przed jego ponownym skompilowaniem. Jeśli aplikacja jest otwarta w innym programie, takim jak edytor zasobów, zamknij ją. W skrajnych przypadkach może być konieczne użycie Menedżera zadań do zakończenia procesu lub zatrzymanie i ponowne uruchomienie programu Visual Studio.

Programy antywirusowe często tymczasowo blokują dostęp do nowo utworzonych plików, w szczególności plików wykonywalnych exe i. dll. Aby rozwiązać ten problem, spróbuj wykluczyć katalogi kompilacji projektu ze skanera antywirusowego.

### <a name="cant-open-a-microsoft-library-file"></a>Nie można otworzyć pliku biblioteki firmy Microsoft

Jeśli plik, który nie może zostać otwarty, jest jednym z plików biblioteki standardowej dostarczonej przez firmę Microsoft, takim jak Kernel32. lib, może wystąpić błąd konfiguracji projektu lub błąd instalacji. Sprawdź, czy zainstalowano Windows SDK i czy projekt wymaga innych bibliotek firmy Microsoft, takich jak MFC, upewnij się, że składniki MFC zostały zainstalowane także przez Instalatora programu Visual Studio. Możesz ponownie uruchomić Instalatora, aby dodać opcjonalne składniki w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [modyfikowanie programu Visual Studio](/visualstudio/install/modify-visual-studio). Użyj karty poszczególne składniki w instalatorze, aby wybrać określone biblioteki i zestawy SDK.

Nie ma bibliotek Spectre-z ograniczeniami dla aplikacji uniwersalnych systemu Windows (platformy UWP) ani składników. Jeśli raport o błędach zawiera plik *vccorlib. lib* , możesz włączyć [/QSPECTRE](../../build/reference/qspectre.md) w projekcie platformy UWP. Wyłącz opcję kompilatora **/Qspectre** , aby rozwiązać ten problem. W programie Visual Studio Zmień właściwość **Spectre ograniczenia** , która znajduje się na stronie**generowania kodu**  >  **C/C++** w oknie dialogowym **strony właściwości** projektu.

Jeśli tworzysz projekt, który został utworzony przy użyciu starszej wersji programu Visual Studio, zestaw narzędzi platformy i biblioteki dla tej wersji mogą nie być zainstalowane. Jeśli komunikat o błędzie występuje w przypadku nazwy biblioteki o wersji, takiej jak pliku msvcr100. lib, prawdopodobnie jest to przyczyną problemu. Aby rozwiązać ten problem, dostępne są dwie opcje: można uaktualnić projekt, aby użyć aktualnie zainstalowanego zestawu narzędzi platformy, lub można zainstalować starszy zestaw narzędzi i skompilować projekt bez zmian. Aby uzyskać więcej informacji, zobacz [uaktualnianie projektów ze starszych wersji C++ wizualizacji](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) i [Używanie natywnego wielu elementów docelowych w programie Visual Studio w celu kompilowania starych projektów](../../porting/use-native-multi-targeting.md).

Jeśli ten błąd wystąpi podczas kompilowania nowej docelowej platformy lub konfiguracji, biblioteki dla tej konfiguracji projektu lub zestawu narzędzi platformy mogą nie być zainstalowane. Sprawdź, czy jest zainstalowany zestaw **narzędzi platformy** i **wersja Windows SDK** określona na [stronie właściwości ogólnych](../../build/reference/general-property-page-project.md) projektu, i sprawdź, czy wymagane biblioteki są dostępne w **katalogach bibliotek** określonych w [Strona właściwości Katalogi VC + +](../../build/reference/vcpp-directories-property-page.md) dla ustawień konfiguracji. Istnieją oddzielne ustawienia konfiguracji debugowania i sprzedaży detalicznej, a także konfiguracje 32-bitowe i 64-bitowe, dlatego jeśli jedna kompilacja działa, ale inna powoduje błąd, upewnij się, że ustawienia są poprawne, a wymagane narzędzia i biblioteki są zainstalowane dla każdego utworzona konfiguracja.

Jeśli używasz środowiska IDE programu Visual Studio do kompilowania projektu skopiowanego z innego komputera, lokalizacje instalacji bibliotek mogą się różnić. Sprawdź właściwości **katalogi bibliotek** na [stronie właściwości Katalogi VC + +](../../build/reference/vcpp-directories-property-page.md) dla projektu i zaktualizuj je w razie potrzeby. Aby wyświetlić i edytować bieżącą ścieżkę biblioteki ustawioną w IDE, wybierz formant listy rozwijanej dla właściwości **katalogi bibliotek** i wybierz polecenie **Edytuj**. Sekcja **Szacowana wartość** w oknie dialogowym **katalogi bibliotek** zawiera listę bieżących ścieżek przeszukanych plików bibliotek.

Ten błąd może również wystąpić, gdy ścieżka do Windows SDK jest nieaktualna. Jeśli zainstalowano wersję Windows SDK, która jest nowsza niż wersja programu Visual Studio, upewnij się, że ścieżki określone na [stronie właściwości Katalogi VC + +](../../build/reference/vcpp-directories-property-page.md) są aktualizowane w taki sposób, aby odpowiadały nowemu zestawowi SDK. W przypadku korzystania z wiersz polecenia dla deweloperów upewnij się, że plik wsadowy inicjujący zmienne środowiskowe został zaktualizowany dla nowych ścieżek zestawu SDK. Ten problem można uniknąć przy użyciu Instalatora programu Visual Studio w celu zainstalowania zaktualizowanych zestawów SDK.

### <a name="cannot-open-a-third-party-library-file"></a>Nie można otworzyć pliku biblioteki innej firmy

Istnieje kilka typowych przyczyn tego problemu:

- Ścieżka do pliku biblioteki może być niepoprawna lub nie została określona dla konsolidatora.

- Być może zainstalowano 32-bitową wersję biblioteki, ale tworzysz dla 64-bitów lub na odwrót.

- Biblioteka może mieć zależności od innych bibliotek, które nie są zainstalowane.

Aby naprawić problem ze ścieżką, sprawdź, czy zmienna środowiskowa LIB jest ustawiona i zawiera wszystkie katalogi dla używanych bibliotek, dla każdej kompilacji, którą tworzysz. W środowisku IDE zmienna LIB jest ustawiana za pomocą właściwości **katalogi bibliotek** na [stronie właściwości katalogów VC + +](../../build/reference/vcpp-directories-property-page.md). Upewnij się, że wszystkie katalogi zawierające potrzebne biblioteki są wymienione w tym miejscu dla każdej kompilacji, którą tworzysz.

Jeśli konieczne jest podanie katalogu biblioteki, który zastępuje Katalog biblioteki standardowej, można użyć opcji [/LIBPATH](../../build/reference/libpath-additional-libpath.md) w wierszu polecenia lub w IDE, można użyć właściwości **Dodatkowe katalogi biblioteki** we **właściwościach konfiguracji. > Konsolidatora >** strony właściwości ogólnej dla projektu.

Upewnij się, że masz zainstalowaną każdą wersję biblioteki potrzebną dla utworzonych konfiguracji. Rozważ użycie narzędzia do zarządzania pakietami [vcpkg](../../vcpkg.md) w celu zautomatyzowania instalacji i konfiguracji wielu wspólnych bibliotek. Gdy jest to możliwe, najlepiej utworzyć własne kopie bibliotek innych firm, aby upewnić się, że wszystkie lokalne zależności są wymagane przez biblioteki i zostały skompilowane dla tych samych konfiguracji co projekt.

### <a name="cannot-open-a-file-built-by-your-project"></a>Nie można otworzyć pliku skompilowanego przez projekt

Ten błąd może pojawić się, jeśli *Nazwa* pliku została skompilowana przez rozwiązanie, ale jeszcze nie istnieje, gdy konsolidator próbuje uzyskać do niego dostęp. Taka sytuacja może wystąpić, gdy jeden projekt zależy od innego projektu, ale projekty nie są kompilowane w poprawnej kolejności. Aby rozwiązać ten problem, upewnij się, że odwołania do projektu są ustawione w projekcie, który używa tego pliku, tak aby brakujący plik został skompilowany przed wymaganiem. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań w projektach C++ programu Visual Studio](../../build/adding-references-in-visual-cpp-projects.md) i [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

### <a name="cannot-open-file-cprogramobj"></a>Nie można otworzyć pliku "C\\: program. obj"

Jeśli zostanie wyświetlony ten błąd lub podobny błąd dotyczący nieoczekiwanego pliku. obj w katalogu głównym dysku, ten problem niemal odnosi się do ścieżki biblioteki, która nie jest opakowana podwójny cudzysłów.

Aby rozwiązać ten problem z kompilacjami w wierszu polecenia, należy sprawdzić parametry opcji [/LIBPATH](../../build/reference/libpath-additional-libpath.md) , ścieżki określone w zmiennej środowiskowej LIB i ścieżki określone w wierszu polecenia, a następnie użyć cudzysłowu podwójnego wokół wszystkich ścieżek zawierających spacje.

Aby rozwiązać ten problem w środowisku IDE, sprawdź Właściwość **katalogi bibliotek** na stronie właściwości [konfiguracji > VC + +](../../build/reference/vcpp-directories-property-page.md) Strona właściwości katalogi i właściwości **Dodatkowe katalogi** w **właściwościach konfiguracji > konsolidator Strona właściwości ogólne >** i Właściwość **dodatkowe zależności** we **właściwościach konfiguracji > konsolidatora > dane wejściowe** dla projektu. Upewnij się, że wszystkie ścieżki katalogów zawierające potrzebne biblioteki są ujęte w podwójny cudzysłów w razie potrzeby.

### <a name="other-common-issues"></a>Inne typowe problemy

Ten błąd może wystąpić, gdy nazwa pliku biblioteki lub ścieżka określona dla konsolidatora w wierszu polecenia lub w [#pragma komentarz (lib, "library_name")](../../preprocessor/comment-c-cpp.md) jest niepoprawna lub ścieżka ma nieprawidłową specyfikację dysku. Sprawdź pisownię i rozszerzenie pliku, a następnie sprawdź, czy plik istnieje w określonej lokalizacji.

Plik może być otwarty przez inny program, a konsolidator nie może zapisywać w nim. Programy antywirusowe często tymczasowo blokują dostęp do nowo utworzonych plików. Aby rozwiązać ten problem, spróbuj wykluczyć katalogi kompilacji projektu ze skanera antywirusowego.

Jeśli używasz opcji kompilacji równoległej, możliwe jest, że program Visual Studio zablokował plik w innym wątku. Aby rozwiązać ten problem, upewnij się, że nie kompilujesz tego samego obiektu kodu lub biblioteki w wielu projektach i używasz zależności kompilacji lub odwołań do projektu, aby pobrać skompilowane pliki binarne w projekcie.

Po określeniu poszczególnych bibliotek we właściwości **dodatkowe zależności** należy użyć spacji do oddzielenia nazw bibliotek, a nie przecinków lub średników. Jeśli używasz elementu menu **Edytuj** , aby otworzyć okno dialogowe **dodatkowe zależności** , Użyj nowego wiersza do rozdzielenia nazw, a nie przecinków, średników ani spacji. Przy użyciu nowego wiersza można także określić ścieżki biblioteki w oknach dialogowych katalogi **bibliotek** i **dodatkowe biblioteki** .

Ten błąd może pojawić się, gdy ścieżka do *nazwy pliku* zostanie rozszerzona o więcej niż 260 znaków. Zmień nazwy lub ponownie Rozmieść strukturę katalogów, jeśli jest to konieczne, aby skrócić ścieżki do wymaganych plików.

Ten błąd może wystąpić, ponieważ plik jest zbyt duży. Biblioteki lub pliki obiektów o rozmiarze przekraczającym gigabajty mogą spowodować problemy związane z konsolidatorem 32-bitowym. Możliwym rozwiązaniem tego problemu jest użycie zestawu narzędzi 64-bitowego. Aby uzyskać więcej informacji o tym, jak to zrobić za pomocą wiersza polecenia [, zobacz How to: Włącz 64-bitowy zestaw narzędzi C++ wizualnych w wierszu](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)polecenia. Aby uzyskać informacje o tym, jak to zrobić w środowisku IDE, zobacz [Korzystanie z programu MSBuild z 64-bitowym kompilatorem i narzędziami](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) oraz tym Stack Overflow post: [Jak w programie Visual Studio używać natywnej metody amd64 łańcucha narzędzi](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

Ten błąd może wystąpić, jeśli masz niewystarczające uprawnienia do pliku *filename*. Taka sytuacja może wystąpić, jeśli używasz zwykłego konta użytkownika i podjęto próbę uzyskania dostępu do plików bibliotek w chronionych katalogach systemu lub Użyj plików skopiowanych z innych użytkowników, którzy mają ustawione oryginalne uprawnienia. Aby rozwiązać ten problem, Przenieś plik do zapisywalnego katalogu projektu. Jeśli plik znajduje się w katalogu zapisywalnym, ale ma uprawnienia niedostępności, można użyć wiersza polecenia administratora i uruchomić polecenie takeown. exe, aby przejąć własność pliku.

Ten błąd może wystąpić, gdy nie ma wystarczającej ilości miejsca na dysku. Konsolidator używa plików tymczasowych w kilku przypadkach. Nawet w przypadku wystarczającej ilości miejsca na dysku bardzo duże łącze może wymusić wyczerpanie lub fragmentację dostępnego miejsca na dysku. Rozważ użycie opcji [/opt (optymalizacje)](../../build/reference/opt-optimizations.md) ; nieprzechodnia eliminacja COMDAT odczytuje wszystkie pliki obiektów wiele razy.

Jeśli *Nazwa pliku* to lnk*nnn*, która jest nazwą pliku wygenerowaną przez konsolidator dla pliku tymczasowego, katalog określony w zmiennej środowiskowej tmp może nie istnieć lub można określić więcej niż jeden katalog dla zmiennej środowiskowej tmp. Dla zmiennej środowiskowej TMP należy określić tylko jedną ścieżkę do katalogu.
