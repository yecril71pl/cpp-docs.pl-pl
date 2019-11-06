---
title: Wprowadzenie do firmy C++ Microsoft dla użytkowników systemu UNIX
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 791c513553acbd300204746ae1e1dddf7a3ae5c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626998"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>Wprowadzenie do firmy C++ Microsoft dla użytkowników systemu UNIX

Ten temat zawiera informacje dla użytkowników wszystkich wersji systemu UNIX, które są nowe dla programu Visual Studio i chcą pracować C++ wydajnie z poziomu wiersza polecenia lub programu Visual Studio. Możesz użyć programu Visual Studio z kompilatorem C++ firmy Microsoft, aby kierować do systemu Windows. Możesz również użyć środowiska IDE programu Visual Studio z programem w zatoce lub Clang w środowiskach UNIX, takich jak maszyny wirtualne z systemem Linux, MinGW-W64 i podsystem Windows dla systemu Linux. Aby można C++ było korzystać z programu Visual Studio, należy zainstalować **Programowanie na pulpicie z C++**  obciążeniem. Otwórz Instalator programu Visual Studio, aby zainstalować obciążenie lub dodać lub usunąć opcjonalne składniki. Należy również zainstalować **wdrażanie systemu Linux C++ przy użyciu** obciążenia, jeśli będzie ono ukierunkowane na zdalny komputer z systemem Linux. W przypadku tworzenia aplikacji dla systemu Android lub iOS należy zainstalować **Programowanie aplikacji mobilnych za pomocą C++**  obciążenia.

## <a name="getting-started-on-the-command-line"></a>Wprowadzenie do wiersza polecenia

Możesz użyć kompilatora Microsoft C++ z wiersza polecenia w podobny sposób, jak używać środowiska wiersza polecenia systemu UNIX. Kompilowanie z wiersza polecenia przy użyciu wiersza polecenia C i C++ kompilatora (CL. EXE), konsolidator (LINK. EXE) i innych narzędzi, w tym NMAKE. EXE, wersja firmy Microsoft dla narzędzia do wprowadzania w systemie UNIX.

W systemie UNIX polecenia są instalowane w folderze wspólnym, takim jak/usr/bin. W programie Visual Studio narzędzia wiersza polecenia są instalowane w katalogu instalacyjnym programu Visual Studio w podkatalogu VC\bin i jego podkatalogach. W przeciwieństwie do systemu UNIX te narzędzia nie są dostępne w zwykłym oknie wiersza polecenia. Aby użyć narzędzi wiersza polecenia, należy użyć specjalnego wiersza polecenia dewelopera, który konfiguruje ścieżkę i inne zmienne środowiskowe, które są niezbędne do kompilowania C++ programów. Aby uzyskać więcej informacji, zobacz Kompilowanie [C/C++ Code w wierszu polecenia](../build/building-on-the-command-line.md) i [instruktażu: kompilowanie programu natywnego C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

## <a name="debugging-your-code"></a>Debugowanie kodu

Możesz użyć debugera programu Visual Studio dla projektów firmy C++ Microsoft z wiersza polecenia lub z poziomu środowiska IDE. Kompiluj przy użyciu przełącznika [/Z7,/Zi,/ZI (Debug Information Format),](../build/reference/z7-zi-zi-debug-information-format.md) aby umożliwić krokowe przechodzenie przez źródła. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu natywnego](/visualstudio/debugger/debugging-native-code) i [Używanie środowiska IDE programu C++ Visual Studio do tworzenia aplikacji klasycznych](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

W przypadku programów skompilowanych za pomocą usługi w zatoce lub Clang program Visual Studio wywołuje GDB, LLDB lub dowolny niestandardowy debuger, który określisz.

## <a name="visual-studio-project-system"></a>System projektu programu Visual Studio

System projektu programu Visual Studio nosi nazwę MSBuild. Używa plików projektu w formacie XML; C++ pliki projektu mają rozszerzenie. vcxproj. Aplikacja, która składa się z wielu bibliotek i plików wykonywalnych, z których każdy może być zbudowany przy użyciu innego zestawu opcji kompilatora lub nawet w innym języku, są przechowywane w wielu projektach, które są częścią jednego *rozwiązania*. Rozwiązanie jest abstrakcją kontenera, aby zgrupować wiele projektów jednocześnie. Informacje o rozwiązaniach są przechowywane w pliku rozwiązania z rozszerzeniem sln. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) oraz [Korzystanie z programu Visual C++ Studio IDE do tworzenia aplikacji klasycznych](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Z menu głównego wybierz kolejno pozycje **plik** > **Nowy** > **projekt** , aby wyświetlić dostępne szablony projektów programu Visual Studio.

Począwszy od programu Visual Studio 2017, dodano obsługę projektów CMake, a także opcje używania kompilatora Microsoft C++ z dowolnym dowolnym systemem kompilacji lub z luźnym folderem plików źródłowych i bez plików projektu. Aby uzyskać więcej informacji, zobacz [CMAKE projects in Visual Studio](../build/cmake-projects-in-visual-studio.md) i [Otwórz projekty folderu w programie Visual Studio](../build/open-folder-projects-cpp.md).

## <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft

Kompilator firmy C++ Microsoft implementuje kilka rozszerzeń standardowego C++ języka programowania, aby obsługiwać Programowanie dla systemów operacyjnych Windows. Rozszerzenia te służą do określania atrybutów klasy magazynu, konwencji wywoływania funkcji i adresowania na podstawie innych elementów. Aby uzyskać pełną listę wszystkich obsługiwanych C++ rozszerzeń, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).

Wszystkie rozszerzenia specyficzne dla firmy Microsoft można wyłączyć do C++ programu przy użyciu opcji kompilatora `/Za`. Ta opcja jest zalecana, jeśli chcesz napisać kod do uruchomienia na wielu platformach. Aby uzyskać więcej informacji na temat opcji kompilatora `/Za`, zobacz [/za,/ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md). Aby uzyskać więcej informacji C++ na temat zgodności kompilatora, zobacz [tabela C++ zgodność języka firmy Microsoft](../overview/visual-cpp-language-conformance.md) i [zachowanie niestandardowe](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>Wstępnie skompilowane nagłówki

Język Microsoft C i C++ kompilatory udostępniają opcje wstępnego kompilowania dowolnych języków C lub C++ Code, w tym kodu wbudowanego. Korzystając z tej funkcji wydajności, można skompilować stabilną treść kodu, przechowywać skompilowany stan kodu w pliku i, podczas kolejnych kompilacji, połączyć wstępnie skompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejna kompilacja jest szybsza, ponieważ stabilny kod nie musi być ponownie kompilowany.

Domyślnie cały skompilowany kod jest określony w plikach *PCH. h* i *PCH. cpp* (*stdafx. h* i *stdafx. cpp* w programie Visual Studio 2017 i wcześniejszych). Aby uzyskać więcej informacji na temat prekompilowanych nagłówków, zobacz [Tworzenie prekompilowanych plików nagłówkowych](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz [Uruchamianie programów systemu Linux w systemie Windows](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Zobacz także

[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)
