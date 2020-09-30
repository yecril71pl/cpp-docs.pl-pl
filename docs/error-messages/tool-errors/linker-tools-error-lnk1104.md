---
title: Błąd narzędzi konsolidatora LNK1104
description: W tym artykule opisano błąd konsolidatora Microsoft C i C++ (MSVC) LNK1104, jego przyczyny i możliwe rozwiązania.
ms.date: 12/13/2019
f1_keywords:
- LNK1104
helpviewer_keywords:
- LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
ms.openlocfilehash: aa7bcf34cddfa24956d807131b3c484e7d580e73
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91506036"
---
# <a name="linker-tools-error-lnk1104"></a>Błąd narzędzi konsolidatora LNK1104

> nie można otworzyć pliku "*filename*"

Ten błąd jest zgłaszany, gdy konsolidator nie może otworzyć pliku, do odczytu lub do zapisu. Dwa najczęstsze przyczyny problemu to:

- Program jest już uruchomiony lub jest ładowany w debugerze, a

- ścieżki biblioteki są nieprawidłowe lub nie są opakowane podwójnymi cudzysłowami.

Istnieje wiele innych możliwych przyczyn tego błędu. Aby zawęzić je w dół, najpierw sprawdź, jaki rodzaj *nazwy* pliku nazywa się. Następnie w poniższych sekcjach znajdują się informacje ułatwiające zidentyfikowanie i rozwiązanie określonego problemu.

## <a name="cant-open-your-app-or-its-pdb-file"></a>Nie można otworzyć aplikacji lub jej pliku. pdb

### <a name="your-app-is-running-or-its-loaded-in-the-debugger"></a>Aplikacja jest uruchomiona lub jest załadowana w debugerze

Jeśli nazwa *pliku* to plik wykonywalny lub skojarzony plik. pdb, sprawdź, czy aplikacja jest już uruchomiona. Następnie sprawdź, czy jest on załadowany w debugerze. Aby rozwiązać ten problem, Zatrzymaj program i zwolnij go z debugera przed jego ponownym skompilowaniem. Jeśli aplikacja jest otwarta w innym programie, takim jak edytor zasobów, zamknij ją. Jeśli program nie odpowiada, może być konieczne użycie Menedżera zadań, aby zakończyć proces. Może być również konieczne zamknięcie i ponowne uruchomienie programu Visual Studio.

### <a name="your-app-is-locked-by-an-antivirus-scan"></a>Aplikacja została zablokowana przez skanowanie antywirusowe

Programy antywirusowe często tymczasowo blokują dostęp do nowo utworzonych plików, w szczególności plików wykonywalnych exe i. dll. Aby rozwiązać ten problem, spróbuj wykluczyć katalogi kompilacji projektu ze skanera antywirusowego.

## <a name="cant-open-a-microsoft-library-file"></a>Nie można otworzyć pliku biblioteki firmy Microsoft

### <a name="windows-libraries-such-as-kernel32lib"></a>Biblioteki systemu Windows, takie jak Kernel32. lib

Jeśli plik, który nie może zostać otwarty, jest jednym z plików biblioteki standardowej dostarczonej przez firmę Microsoft, takim jak *Kernel32. lib*, może wystąpić błąd konfiguracji projektu lub błąd instalacji. Upewnij się, że zainstalowano Windows SDK. Jeśli projekt wymaga innych bibliotek firmy Microsoft, takich jak MFC, upewnij się, że składniki MFC zostały zainstalowane także przez Instalatora programu Visual Studio. Możesz ponownie uruchomić Instalatora, aby dodać opcjonalne składniki w dowolnym momencie. Aby uzyskać więcej informacji, zobacz [modyfikowanie programu Visual Studio](/visualstudio/install/modify-visual-studio). Użyj karty **poszczególne składniki** w instalatorze, aby wybrać określone biblioteki i zestawy SDK.

### <a name="versioned-vcruntime-libraries"></a>Biblioteki vcruntime z wersjami

Jeśli komunikat o błędzie ma wersję biblioteki firmy Microsoft, taką jak *msvcr120. lib*, zestaw narzędzi platformy dla tej wersji kompilatora może nie być zainstalowany. Aby rozwiązać ten problem, dostępne są dwie opcje: Uaktualnij projekt do korzystania z bieżącego zestawu narzędzi platformy lub zainstaluj starszy zestaw narzędzi i skompiluj projekt bez zmian. Aby uzyskać więcej informacji, zobacz [uaktualnianie projektów z wcześniejszych wersji programu Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) i [Używanie natywnego wielu elementów docelowych w programie Visual Studio w celu kompilowania starych projektów](../../porting/use-native-multi-targeting.md).

### <a name="retail-debug-or-platform-specific-libraries"></a>Biblioteki detaliczne, debugowania lub specyficzne dla platformy

Ten błąd może wystąpić podczas pierwszej kompilacji nowej docelowej platformy lub konfiguracji, na przykład detalicznej lub ARM64. W środowisku IDE Sprawdź, czy jest zainstalowany zestaw **narzędzi platformy** i **wersja Windows SDK** określona na [stronie właściwości ogólne](../../build/reference/general-property-page-project.md) . Sprawdź również, czy wymagane biblioteki są dostępne w **katalogach bibliotek** określonych na [stronie właściwości Katalogi VC + +](../../build/reference/vcpp-directories-property-page.md). Sprawdź właściwości każdej konfiguracji, na przykład Debug, detaliczny, x86 lub ARM64. Jeśli jedna kompilacja działa, ale druga nie, porównaj ustawienia obu tych ustawień. Zainstaluj wszystkie brakujące wymagane narzędzia i biblioteki.

### <a name="the-vccorliblib-library"></a>Biblioteka vccorlib. lib

Nie ma bibliotek Spectre-z ograniczeniami dla aplikacji uniwersalnych systemu Windows (platformy UWP) ani składników. Jeśli komunikat o błędzie zawiera *vccorlib. lib*, być może włączono [/QSPECTRE](../../build/reference/qspectre.md) w projekcie platformy UWP. Wyłącz opcję kompilatora **/Qspectre** , aby rozwiązać ten problem. W programie Visual Studio Zmień właściwość **Spectre ograniczenia** . Znajduje się na stronie generowania **kodu C/C++**  >  **Code Generation** okna dialogowego **strony właściwości** projektu.

### <a name="libraries-in-projects-from-online-or-other-sources"></a>Biblioteki w projektach z Internetu lub innych źródeł

W przypadku skompilowania projektu skopiowanego z innego komputera lokalizacje instalacji biblioteki mogą się różnić. W przypadku kompilacji wiersza polecenia Sprawdź, czy zmienna środowiskowa LIB i ścieżki biblioteki są poprawnie ustawione dla kompilacji. W programie Visual Studio można wyświetlać i edytować bieżące ścieżki biblioteki ustawione na stronach właściwości projektu. Na stronie **Katalogi VC + +** wybierz formant listy rozwijanej dla właściwości **katalogi bibliotek** , a następnie wybierz pozycję **Edytuj**. Sekcja **Szacowana wartość** w oknie dialogowym **katalogi bibliotek** zawiera listę bieżących ścieżek przeszukanych plików bibliotek. Zaktualizuj te ścieżki, aby wskazywały biblioteki lokalne.

### <a name="updated-windows-sdk-libraries"></a>Zaktualizowano biblioteki Windows SDK

Ten błąd może wystąpić, gdy ścieżka programu Visual Studio do Windows SDK jest nieaktualna. Może się tak zdarzyć, Jeśli instalujesz nowszą Windows SDK niezależnie od Instalatora programu Visual Studio. Aby rozwiązać ten problem w środowisku IDE, zaktualizuj ścieżki określone na [stronie właściwości katalogów VC + +](../../build/reference/vcpp-directories-property-page.md). Ustaw wersję w ścieżce zgodną z nowym zestawem SDK. Jeśli używasz wiersz polecenia dla deweloperów, zaktualizuj plik wsadowy, który inicjuje zmienne środowiskowe z nowymi ścieżkami zestawu SDK. Ten problem można uniknąć przy użyciu Instalatora programu Visual Studio w celu zainstalowania zaktualizowanych zestawów SDK.

## <a name="cant-open-a-third-party-library-file"></a>Nie można otworzyć pliku biblioteki innej firmy

Istnieje kilka typowych przyczyn tego problemu:

- Ścieżka do pliku biblioteki może być niepoprawna lub nie została opakowana podwójnym cudzysłowem. Lub, możesz nie określić go do konsolidatora.

- Być może zainstalowano 32-bitową wersję biblioteki, ale tworzysz ją dla 64 bitów lub w inny sposób.

- Biblioteka może mieć zależności od innych bibliotek, które nie są zainstalowane.

Aby rozwiązać problem z ścieżką dla kompilacji wiersza polecenia, sprawdź, czy zmienna środowiskowa LIB jest ustawiona. Upewnij się, że zawiera ona ścieżki dla wszystkich używanych bibliotek oraz dla każdej kompilacji, którą tworzysz. W środowisku IDE ścieżki biblioteki są ustawiane przez właściwość katalogi katalogów **VC + +**  >  **Library Directories** . Upewnij się, że wszystkie katalogi zawierające potrzebne biblioteki są wymienione w tym miejscu dla każdej kompilacji, którą tworzysz.

Może być konieczne dostarczenie katalogu biblioteki, który zastąpi Katalog biblioteki standardowej. W wierszu polecenia Użyj opcji [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . W środowisku IDE Użyj właściwości **Dodatkowe katalogi biblioteki** we **właściwościach konfiguracji > konsolidatora >** stronie właściwości ogólnej dla projektu.

Upewnij się, że instalujesz każdą wersję biblioteki potrzebną dla kompilacji, którą tworzysz. Rozważ użycie narzędzia do zarządzania pakietami [vcpkg](../../build/vcpkg.md) w celu zautomatyzowania instalacji i konfiguracji wielu wspólnych bibliotek. Gdy jest to możliwe, najlepiej utworzyć własne kopie bibliotek innych firm. Następnie upewnij się, że wszystkie lokalne zależności bibliotek zostały utworzone dla tych samych konfiguracji co projekt.

## <a name="cant-open-a-file-built-by-your-project"></a>Nie można otworzyć pliku skompilowanego przez projekt

Ten błąd może pojawić się, jeśli *Nazwa pliku* nie istnieje jeszcze, gdy konsolidator próbuje uzyskać do niego dostęp. Może się to zdarzyć, gdy jeden projekt zależy od innego w rozwiązaniu, ale projekty są kompilowane w niewłaściwej kolejności. Aby rozwiązać ten problem, upewnij się, że odwołania do projektu są ustawione w projekcie, który używa tego pliku. Następnie brakujący plik zostanie skompilowany przed jego zainstalowaniem. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań w projektach Visual Studio C++](../../build/adding-references-in-visual-cpp-projects.md) i [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).

## <a name="cannot-open-file-cprogramobj"></a>Nie można otworzyć pliku "C: \\ program. obj"

Jeśli zobaczysz nazwę pliku *C: \\ program. obj* w komunikacie o błędzie, zawiń ścieżki biblioteki w podwójnych cudzysłowach. Ten błąd występuje, gdy nieopakowana ścieżka rozpoczynająca się od *C: \\ Program Files* jest przenoszona do konsolidatora. Nieopakowane ścieżki mogą również spowodować podobne błędy. Zwykle pokazują one nieoczekiwany plik. obj w katalogu głównym dysku.

Aby rozwiązać ten problem w przypadku kompilacji w wierszu polecenia, sprawdź parametry opcji [/LIBPATH](../../build/reference/libpath-additional-libpath.md) . Sprawdź również ścieżki określone w zmiennej środowiskowej LIB i ścieżki określone w wierszu polecenia. Pamiętaj, aby używać cudzysłowów podwójnych wokół wszystkich ścieżek zawierających spacje.

Aby rozwiązać ten problem w środowisku IDE, należy dodać podwójne cudzysłowy zgodnie z potrzebami dla następujących właściwości projektu:

- Właściwość **katalogi bibliotek** na stronie właściwości [konfiguracji, > Strona właściwości katalogów VC + +](../../build/reference/vcpp-directories-property-page.md) ,

- Właściwości **Dodatkowe katalogi biblioteki** we **właściwościach konfiguracji > konsolidator >** Strona właściwości ogólne,

- Właściwość **dodatkowe zależności** we **właściwościach konfiguracji > konsolidatora > stronie właściwości danych wejściowych** .

## <a name="other-common-issues"></a>Inne typowe problemy

### <a name="path-or-filename-issues"></a>Problemy z ścieżką lub nazwą pliku

Ten błąd może wystąpić, gdy nazwa pliku biblioteki lub ścieżka określona dla konsolidatora jest niepoprawna. Lub, jeśli ścieżka ma nieprawidłową specyfikację dysku. Znajdź problemy w wierszu polecenia lub w dowolnej dyrektywie [#pragma comment (lib, "library_name")](../../preprocessor/comment-c-cpp.md) . Sprawdź pisownię i rozszerzenie pliku, a następnie sprawdź, czy plik istnieje w określonej lokalizacji.

### <a name="parallel-build-synchronization"></a>Równoległa synchronizacja kompilacji

Jeśli używasz opcji kompilacji równoległej, program Visual Studio mógł zablokować plik w innym wątku. Aby rozwiązać ten problem, upewnij się, że ten sam obiekt kodu lub biblioteka nie została skompilowana w wielu projektach. Użyj zależności kompilacji lub odwołań do projektu, aby pobrać skompilowane pliki binarne w projekcie.

### <a name="additional-dependencies-specified-in-the-ide"></a>Dodatkowe zależności określone w IDE

Po określeniu poszczególnych bibliotek we właściwości **dodatkowe zależności** należy użyć spacji, aby oddzielić nazwy bibliotek. Nie używaj przecinków ani średników. Jeśli używasz elementu menu **Edytuj** , aby otworzyć okno dialogowe **dodatkowe zależności** , Użyj nowego wiersza do rozdzielenia nazw, a nie przecinków, średników ani spacji. Przy użyciu nowego wiersza można także określić ścieżki biblioteki w oknach dialogowych katalogi **bibliotek** i **dodatkowe biblioteki** .

### <a name="paths-that-are-too-long"></a>Zbyt długie ścieżki

Ten błąd może pojawić się, gdy ścieżka do *nazwy pliku* zostanie rozszerzona o więcej niż 260 znaków. W razie potrzeby zmień strukturę katalogów lub Skróć folder i nazwy plików, aby skrócić ścieżki.

### <a name="files-that-are-too-large"></a>Pliki, które są zbyt duże

Ten błąd może wystąpić, ponieważ plik jest zbyt duży. Biblioteki lub pliki obiektów o rozmiarze przekraczającym gigabajty mogą spowodować problemy związane z konsolidatorem 32-bitowym. Możliwym rozwiązaniem tego problemu jest użycie zestawu narzędzi 64-bitowego. Aby uzyskać więcej informacji na temat korzystania z 64-bitowego zestawu narzędzi w wierszu polecenia, zobacz [How to: Enable a 64-bit Visual C++ zestaw narzędzi w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Aby uzyskać informacje na temat korzystania z 64-bitowego zestawu narzędzi w IDE, zobacz [Korzystanie z programu MSBuild z kompilatorem i narzędziami 64-bitowymi](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project). Zapoznaj się również z tym Stack Overflow wpisem: [jak sprawić, aby program Visual Studio korzystał z natywnej amd64 łańcucha narzędzi](https://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).

### <a name="incorrect-file-permissions"></a>Nieprawidłowe uprawnienia do pliku

Ten błąd może wystąpić, jeśli masz niewystarczające uprawnienia do pliku *filename*. Może się tak zdarzyć, jeśli używasz zwykłego konta użytkownika do uzyskiwania dostępu do plików bibliotek w chronionych katalogach systemu. Lub, jeśli używasz plików skopiowanych z innych użytkowników, którzy nadal mają ustawione pierwotne uprawnienia. Aby rozwiązać ten problem, Przenieś plik do zapisywalnego katalogu projektu. Jeśli przeniesiony plik ma niedostępne uprawnienia, uruchom polecenie takeown.exe w oknie polecenia administratora, aby przejąć własność pliku.

### <a name="insufficient-disk-space"></a>Za mało miejsca na dysku

Ten błąd może wystąpić, gdy nie ma wystarczającej ilości miejsca na dysku. Konsolidator używa plików tymczasowych w kilku przypadkach. Nawet w przypadku wystarczającej ilości miejsca na dysku, duże łącze może obsłużyć lub zdefragmentować dostępne miejsce na dysku. Rozważ użycie opcji [/opt (optymalizacje)](../../build/reference/opt-optimizations.md) ; nieprzechodnia eliminacja COMDAT odczytuje wszystkie pliki obiektów wiele razy.

### <a name="problems-in-the-tmp-environment-variable"></a>Problemy w zmiennej środowiskowej TMP

Jeśli *Nazwa pliku* ma nazwę lnk*nnn*, jest to nazwa pliku wygenerowana przez konsolidator dla pliku tymczasowego. Katalog określony w zmiennej środowiskowej TMP może nie istnieć. Lub można określić więcej niż jeden katalog dla zmiennej środowiskowej TMP. Dla zmiennej środowiskowej TMP należy określić tylko jedną ścieżkę do katalogu.

## <a name="help-my-issue-isnt-listed-here"></a>Pomoc, mój problem nie jest tutaj wymieniony.

Jeśli żaden z wymienionych tu problemów nie ma zastosowania, możesz użyć narzędzi do przesyłania opinii w programie Visual Studio, aby uzyskać pomoc. W środowisku IDE przejdź do paska menu, a następnie wybierz pozycję **pomoc > Wyślij opinię > Zgłoś problem**. Lub Prześlij sugestię, korzystając z **pomocy > wysyłania opinii > wysłania sugestii**. Możesz również użyć witryny sieci Web Visual Studio C++ [Developer](https://developercommunity.visualstudio.com/spaces/62/index.html). Użyj go, aby wyszukać odpowiedzi na pytania i poprosił o pomoc. Aby uzyskać więcej informacji, zobacz [Jak zgłosić problem z zestawem narzędzi Visual C++ lub dokumentacją](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md).

Jeśli wykryto nowy sposób rozwiązania tego problemu, który należy dodać do tego artykułu, skontaktuj się z nami. Opinię można wysłać do nas za pomocą poniższego przycisku dla **tej strony**. Użyj go, aby utworzyć nowy problem w naszym [repozytorium GitHub dokumentacji języka C++](https://github.com/MicrosoftDocs/cpp-docs/issues). Dziękujemy.
