---
title: Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX
ms.date: 09/01/2017
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 7f73e51e02eafe46c279a8f828803912d8cd190a
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631693"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX

Ten temat zawiera informacje dla użytkowników systemu UNIX, którzy są nowością w programie Visual Studio i chcą C++ wydajnie pracować z programem i zintegrowanym środowiskiem programistycznym (IDE) programu Visual Studio.

## <a name="getting-started-on-the-command-line"></a>Wprowadzenie w wierszu polecenia

Możesz użyć C++ kompilatora z wiersza polecenia w podobny sposób, jak używać środowiska wiersza polecenia systemu UNIX. Kompilowanie z wiersza polecenia przy użyciu wiersza polecenia C i C++ kompilatora (CL. EXE), konsolidator (LINK. EXE) i innych narzędzi, w tym NMAKE. EXE, wersja firmy Microsoft dla narzędzia do wprowadzania w systemie UNIX.

W systemie UNIX polecenia są instalowane w folderze wspólnym, takim jak/usr/bin. W programie Visual Studio narzędzia wiersza polecenia są instalowane w katalogu instalacyjnym programu Visual Studio w podkatalogu VC\bin i jego podkatalogach. W przeciwieństwie do systemu UNIX te narzędzia nie są dostępne w zwykłym oknie wiersza polecenia. Aby użyć narzędzi wiersza polecenia, użyj skrótu wiersza polecenia dla deweloperów lub uruchom plik poleceń dewelopera, taki jak vcvarsall. bat. Powoduje to skonfigurowanie ścieżki i innych zmiennych środowiskowych, które są niezbędne do C++ kompilowania programów z wiersza polecenia. Aby uzyskać więcej informacji, zobacz [KompilowanieC++ C/Code w wierszu polecenia](../build/building-on-the-command-line.md) i [instruktażu: Kompilowanie programu C++ natywnego w wierszu](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)polecenia.

Aby otworzyć skrót do wiersza polecenia dla deweloperów, wprowadź *wiersz polecenia dewelopera* w kontrolce wyszukiwanie na pulpicie i wybierz **wiersz polecenia dla deweloperów** wynik dla używanej wersji programu Visual Studio. Aby wybrać wiersz polecenia dla deweloperów, który jest wstępnie skonfigurowany dla określonego hosta i architektury docelowej, otwórz menu **Start** (ikonę systemu Windows w rogu pulpitu), a następnie przewiń do folderu dla używanej wersji programu Visual Studio, np. **Visual Studio 2017**. Otwórz folder i wybierz skrót do wiersza polecenia dla preferowanego hosta i architektury docelowej.

Aby skorzystać z bardziej zaawansowanych funkcji, takich jak debuger programu Visual Studio, wyszukiwanie kodu IntelliSense i Uzupełnianie składni, wizualne wizualizacje, zarządzanie projektami itd., należy użyć środowiska IDE programu Visual Studio.

## <a name="debugging-your-code"></a>Debugowanie kodu

Jeśli używasz wiersza polecenia i uruchamiasz aplikacje na stacji roboczej deweloperskiej, zobaczysz, że okno dialogowe, w którym uruchamiasz debuger programu Visual Studio, jest wyświetlane, gdy kod napotyka naruszenie dostępu do pamięci, nieobsłużony wyjątek lub inne niemożliwy do odzyskania Błędy. Jeśli klikniesz przycisk **OK**, środowisko deweloperskie programu Visual Studio zostanie uruchomione, a debuger zostanie otwarty w punkcie awarii. W ten sposób można debugować aplikacje w ten sposób, a w tym przypadku kod źródłowy będzie dostępny tylko wtedy, gdy został skompilowany za pomocą przełącznika [/Z7,/Zi,/ZI (format informacji o debugowaniu)](../build/reference/z7-zi-zi-debug-information-format.md) . Aby uzyskać więcej informacji, zobacz [Debugowanie kodu natywnego](/visualstudio/debugger/debugging-native-code) i [Używanie środowiska IDE programu C++ Visual Studio do tworzenia aplikacji klasycznych](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="using-the-development-environment"></a>Korzystanie ze środowiska programistycznego

Łatwiej jest używać środowiska programistycznego do edytowania i kompilowania kodu źródłowego w *projekcie*. Projekt jest kolekcją źródłowych i powiązanych plików, które zostaną skompilowane w jednej jednostce, takiej jak biblioteka lub plik wykonywalny. Projekt zawiera również informacje na temat sposobu kompilowania plików. Informacje o projektach są przechowywane w pliku projektu z rozszerzeniem. prj.

Aplikacja, która składa się z wielu bibliotek i plików wykonywalnych, z których każdy może być zbudowany przy użyciu innego zestawu opcji kompilatora lub nawet w innym języku, są przechowywane w wielu projektach, które są częścią jednego *rozwiązania*. Rozwiązanie jest abstrakcją kontenera, aby zgrupować wiele projektów jednocześnie. Informacje o rozwiązaniach są przechowywane w pliku rozwiązania z rozszerzeniem sln. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) oraz [Korzystanie z programu Visual C++ Studio IDE do tworzenia aplikacji klasycznych](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="importing-your-existing-code"></a>Importowanie istniejącego kodu

Można użyć C++ kompilatora, aby skompilować istniejący kod, który jest skonfigurowany do kompilowania z lub bez pliku reguł programu make, i umieścić go w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Utwórz C++ projekt na podstawie istniejącego kodu](../build/how-to-create-a-cpp-project-from-existing-code.md).

## <a name="creating-a-new-project"></a>Tworzenie nowego projektu

Możesz tworzyć nowe projekty w środowisku deweloperskim. Program Visual Studio udostępnia wiele szablonów, które udostępniają standardowy kod dla różnych wspólnych projektów. Za pomocą kreatorów aplikacji można generować projekty z konturami kodu dla różnych typów aplikacji.

Możesz rozpocząć od pustego projektu za pomocą **Kreatora aplikacji konsolowej (Win32)** . Zaznacz pole wyboru **pusty projekt** . Następnie można później dodać nowe i istniejące pliki do projektu.

Podczas tworzenia projektu należy nazwać projekt. Domyślnie nazwa projektu jest równa nazwie biblioteki dołączanej dynamicznie (DLL) lub pliku wykonywalnego kompilowanego z projektu. Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).

## <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft

Kompilator firmy C++ Microsoft implementuje kilka rozszerzeń standardowego C++ języka programowania, aby obsługiwać Programowanie dla systemów operacyjnych Windows. Rozszerzenia te służą do określania atrybutów klasy magazynu, konwencji wywoływania funkcji i adresowania na podstawie innych elementów. Aby uzyskać pełną listę wszystkich obsługiwanych C++ rozszerzeń, zobacz Modyfikatory [specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).

Wszystkie rozszerzenia specyficzne dla firmy Microsoft można wyłączyć do C++ programu przy użyciu `/Za` opcji kompilatora. Ta opcja jest zalecana, jeśli chcesz napisać kod do uruchomienia na wielu platformach. Aby uzyskać więcej informacji na `/Za` temat opcji kompilatora, zobacz [/za,/ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md). Aby uzyskać więcej informacji C++ na temat zgodności kompilatora, zobacz [zgodność C++ języka wizualnego](../overview/visual-cpp-language-conformance.md) i [niestandardowe zachowanie](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>Wstępnie skompilowane nagłówki

Język Microsoft C i C++ kompilatory udostępniają opcje wstępnego kompilowania dowolnych języków C lub C++ Code, w tym kodu wbudowanego. Korzystając z tej funkcji wydajności, można skompilować stabilną treść kodu, przechowywać skompilowany stan kodu w pliku i, podczas kolejnych kompilacji, połączyć wstępnie skompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejna kompilacja jest szybsza, ponieważ stabilny kod nie musi być ponownie kompilowany.

Domyślnie cały skompilowany kod jest określony w plikach *PCH. h* i *PCH. cpp* (*stdafx. h* i *stdafx. cpp* w programie Visual Studio 2017 i wcześniejszych). Kreator **nowego projektu** automatycznie utworzy te pliki, chyba że usuniesz opcję prekompilowanego **nagłówka** . Aby uzyskać więcej informacji na temat prekompilowanych nagłówków, zobacz [Tworzenie prekompilowanych plików nagłówkowych](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz [przenoszenie z systemu UNIX do Win32](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Zobacz także

[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)
