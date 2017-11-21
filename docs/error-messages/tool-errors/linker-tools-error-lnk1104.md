---
title: "Błąd narzędzi konsolidatora LNK1104 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK1104
dev_langs: C++
helpviewer_keywords: LNK1104
ms.assetid: 9ca6f929-0efc-4055-8354-3cf5b4e636dc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ebc0b23a7d92c94373b9ae5be01a0ef50476e433
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-error-lnk1104"></a>Błąd narzędzi konsolidatora LNK1104
Nie można otworzyć pliku "*filename*"  
  
Konsolidator nie można otworzyć określonego pliku.  
  
## <a name="possible-causes-and-solutions"></a>Możliwe przyczyny i rozwiązania
  
Ten błąd może wystąpić, jeśli konsolidator próbuje otworzyć pliku do odczytu lub zapisu. Najbardziej typowe przyczyny tego problemu są, że plik nie istnieje, nie można znaleźć w jednym z katalogów konsolidator wyszukuje, lub jest w użyciu i zablokowany przez inny proces. Rzadziej mógł zostać uruchomiony mało miejsca na dysku, plik może być zbyt duża, ścieżka do pliku może być zbyt długa lub nie masz uprawnienia dostępu do tego pliku.  

Sprawdź, czy jeden z tych typowe problemy:  

-   Aplikacja jest już uruchomione podczas próby skompilować go ponownie. W przypadku pliku, którego nie można otworzyć plik wykonywalny lub plik debugowania, takie jak .pdb, jest typową przyczyną. Aby rozwiązać ten problem, należy zatrzymać program i zwolnić ją z debugera przed zbudowaniem go ponownie.  
  
-   Plik *filename* jest konstruowany przez rozwiązania, ale jeszcze nie istnieje, gdy konsolidator spróbuje uzyskać do niego dostęp. Może się to zdarzyć, gdy jeden projekt jest zależny od innego projektu w celu utworzenia tego pliku, ale projekty nie są tworzone we właściwej kolejności. Aby rozwiązać ten problem, upewnij się, odwołania projektu są ustawione w projekcie, który używa pliku, więc brakujący plik jest skompilowane zanim jest wymagana. Aby uzyskać więcej informacji, zobacz [Dodawanie odwołań do projektów Visual C++](../../ide/adding-references-in-visual-cpp-projects.md) i [Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project).  
  
-   Nazwa pliku lub ścieżka określona w wierszu polecenia lub w dyrektywie #pragma lib jest niepoprawny lub ścieżka zawiera nieprawidłowe określenie dysku. Sprawdź pisownię i sprawdź, czy plik istnieje w określonej lokalizacji.  
  
-   Jeśli używasz programu Visual Studio IDE do kompilacji projektu, który został skopiowany z innego komputera, lokalizacje instalacji biblioteki mogą się różnić. Sprawdź właściwość katalogi bibliotek na [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md) i zaktualizuj ją w razie potrzeby. Aby wyświetlić i edytować bieżącej ścieżki biblioteki w IDE, wybierz kontrolka listy rozwijanej dla właściwości katalogi bibliotek, a następnie wybierz polecenie **Edytuj**. **Obliczyć wartość** sekcja okna dialogowego katalogi bibliotek zawiera informacje o bieżącej ścieżki wyszukiwane pliki biblioteki.  
  
-   Jeśli tworzysz projekt, który został utworzony przy użyciu starszej wersji programu Visual Studio, zestaw narzędzi platformy i biblioteki dla tej wersji może nie być nie zainstalowana. Aby rozwiązać ten problem, dostępne są dwie opcje: można uaktualnić projektu do bieżącego zestawu narzędzi platformy w zainstalowaniu lub można zainstalować starszej zestaw narzędzi i tworzenie projektu bez zmian. Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów z wcześniejszych wersji programu Visual C++](../../porting/upgrading-projects-from-earlier-versions-of-visual-cpp.md) i [Użyj natywnego wielowersyjności kodu w programie Visual Studio do kompilacji projektów starego](../../porting/use-native-multi-targeting.md).
  
-   Nie zainstalowano bibliotek dla bieżącej konfiguracji projektu lub zestaw narzędzi platformy. Sprawdź, czy określony zestaw narzędzi platformy i zestaw Windows SDK w [stronę Ogólne właściwości](../../ide/general-property-page-project.md) projektu są zainstalowane, a następnie sprawdź, czy wymagane biblioteki są dostępne w katalogach biblioteki określonych w [ Strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md) ustawień konfiguracji. Istnieją oddzielne ustawienia dla konfiguracji debugowania i handlowych, jeśli jednego kompilacji działa, ale druga spowoduje wystąpienie błędu, należy się, że ustawienia są poprawne i wymagane narzędzia i biblioteki są zainstalowane dla obydwu konfiguracji.  
  
-   Ścieżka do zestawu Windows SDK jest nieaktualna. Jeśli zainstalowano wersję zestawu Windows SDK, która jest nowsza od używanej wersji programu Visual Studio, upewnij się, że ścieżki określona w [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md) są aktualizowane zgodnie z nowego zestawu SDK. Korzystając z wiersza polecenia dewelopera, upewnij się, że plik wsadowy inicjuje zmienne środowiskowe Zaktualizowano nowe ścieżki zestawu SDK.  
  
-   Inny program może mieć plik jest otwarty i konsolidator nie może zapisywać do niego. Programy antywirusowe często tymczasowo zablokować dostęp do nowo utworzonych plików. Aby rozwiązać ten problem, spróbuj wykluczanie katalogów kompilacji projektu skanera antywirusowego.  
  
-   Jeśli używasz opcji równoległych kompilacji jest możliwe, że program Visual Studio został zablokowany w pliku w innym wątku. Aby rozwiązać ten problem, sprawdź nie utworzenie tego samego obiektu kodu lub biblioteki w wielu projektach, i użyj zależności kompilacji lub odwołania projektu do odebrania skompilowanych plików binarnych w projekcie.  
  
-   Masz niepoprawne zmiennej środowiskowej LIB. W kompilacjach wiersza polecenia Sprawdź, czy lib — zmienna środowiskowa jest ustawiona i zawiera wszystkie katalogi bibliotek, którego używasz. W środowisku IDE programu lib — zmienna jest określona przez właściwość katalogi bibliotek na [strona właściwości katalogów VC ++](../../ide/vcpp-directories-property-page.md). Upewnij się, że wszystkie katalogi, które zawiera bibliotek, które są potrzebne są wyświetlane tutaj. Jeśli należy podać katalog biblioteki który zastępuje katalog biblioteki standardowej, możesz użyć [/libpath](../../build/reference/libpath-additional-libpath.md)) opcja wiersza polecenia lub właściwości dodatkowe katalogi bibliotek na stronie właściwości konsolidatora dla projektu.  
  
-   Podczas określania poszczególnych bibliotekach w oknie dialogowym stron właściwości projektu, nazwy biblioteki muszą być oddzielone spacji, przecinków nie.  
  
-   Ścieżka do *filename* rozwijany do więcej niż 260 znaków. Zmiana nazw lub rozmieszczanie struktury katalogów, w razie potrzeby w celu skrócenia ścieżki do wymaganych plików.  
  
-   Plik jest zbyt duży. Biblioteki lub obiekt pliki więcej niż gigabajt rozmiar może powodować problemy dla konsolidator 32-bitowy. Możliwe rozwiązanie tego problemu polega na użyciu zestawu narzędzi 64-bitowych. Aby uzyskać więcej informacji na temat w tym celu w wierszu polecenia, zobacz [porady: Włączanie 64-bitowych Visual C++ narzędzi w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md). Aby uzyskać informacje, jak to zrobić w środowisku IDE, zobacz [przy użyciu programu MSBuild z 64-bitowych narzędzi i kompilatora](../../build/walkthrough-using-msbuild-to-create-a-visual-cpp-project.md#using-msbuild-to-build-your-project) i ten wpis przepełnienie stosu: [jak Visual Studio Użyj łańcuchem narzędzi natywnego amd64](http://stackoverflow.com/questions/19820718/how-to-make-visual-studio-use-the-native-amd64-toolchain/23793055).  
  
-   Masz niewystarczające uprawnień dostępu do *filename*. Może się to zdarzyć, jeśli dostęp do plików biblioteki w katalogach chronionych system, lub użyj plików skopiowanych z innych użytkowników, którzy mają uprawnienia oryginalnego ustawić. Aby rozwiązać ten problem, należy przenieść plik do katalogu projektu zapisywalny. Jeśli plik znajduje się w katalogu zapisywalny, ale ma uprawnienia niedostępne, można użyć wiersza polecenia z uprawnieniami administratora i uruchom polecenie takeown.exe, aby przejąć na własność pliku.  
  
-   Nie ma wystarczającej ilości wolnego miejsca. Konsolidator używa pliki tymczasowe w kilku przypadkach. Nawet jeśli masz wystarczającą ilość miejsca na dysku, bardzo dużych łącza można warstwę lub fragmentu dostępne miejsce na dysku. Należy rozważyć użycie [od (optymalizacje)](../../build/reference/opt-optimizations.md) opcja; czynności odczyty eliminacji przechodnie comdat wszystkie pliki obiektów wiele razy.  
  
-   Jeśli *filename* nosi nazwę LNK*n*, która jest generowanych przez konsolidator pliku tymczasowego pliku, w zmiennej środowiskowej TMP podany katalog nie istnieje, lub więcej niż jedną Katalog może być określona dla zmiennej środowiskowej TMP. Dla zmiennej środowiskowej TMP powinna zostać określona ścieżka tylko jeden katalog.  
  
-   Jeśli komunikat o błędzie dla nazwy biblioteki, a ostatnio przenieść plik .mak z poprzednich programistycznej Microsoft Visual C++, biblioteki może nie być już prawidłowe. Upewnij się, że nazwa biblioteki jest poprawna i nadal istnieje w określonej lokalizacji lub zaktualizować ścieżka LIB, aby wskazywał nową lokalizację.  
