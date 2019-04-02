---
title: Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX
ms.date: 09/01/2017
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 2b0736bca9cc0b67f9ea8ac83dc18fadaeefdb3c
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58780824"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX

Ten temat zawiera informacje dla użytkowników systemu UNIX, które są nowe w programie Visual Studio i chcesz stać się za pomocą języka C++ i Visual Studio rozwoju środowiska IDE (Integrated).

## <a name="getting-started-on-the-command-line"></a>Rozpoczynanie pracy z wiersza polecenia

Kompilator języka C++ z poziomu wiersza polecenia można użyć w podobny sposób, w których możesz użyć środowisko wiersza polecenia systemu UNIX. Kompilujesz z wiersza polecenia przy użyciu wiersza polecenia kompilatora C i C++ (CL. Z rozszerzeniem EXE), program łączący (LINK. Z rozszerzeniem EXE) i innych narzędzi, takich jak NMAKE. Plik EXE, Microsoft wersję UNIX należy narzędzia.

W systemie UNIX poleceń są instalowane w folderze wspólne, takie jak sfw. W programie Visual Studio narzędzia wiersza polecenia są instalowane w katalogu instalacji programu Visual Studio w podkatalogu VC\bin i jego podkatalogach. W przeciwieństwie do systemu UNIX narzędzia te nie są dostępne w oknie zwykłych wiersza polecenia. Aby użyć narzędzia wiersza polecenia, użyj skrót do wiersza polecenia dla deweloperów lub uruchom Deweloper polecenia plików, takich jak vcvarsall.bat. Spowoduje to utworzenie ścieżkę i inne zmienne środowiskowe, które są niezbędne do kompilowania programów C++ z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) i [instruktażu: Kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).

Otwórz skrót do wiersza polecenia dla deweloperów, wprowadź *wiersz polecenia dla deweloperów* w programie desktop wyszukiwania kontrolki, a następnie wybierz **wiersz polecenia dla deweloperów** wynik dla używanej wersji programu Visual Studio. Aby wybrać wiersz polecenia dla deweloperów, który został wstępnie skonfigurowany dla określonego hosta i Architektura docelowa, otwórz **Start** menu (ikona Windows rogu pulpitu), a następnie przewiń do folderu dla używanej wersji programu Visual Studio , takich jak **programu Visual Studio 2017**. Otwórz folder, a następnie wybierz skrót do wiersza polecenia dla Twojego preferowanego Architektura źródłowa i docelowa.

Aby skorzystać z bardziej zaawansowane funkcje, takie jak debugera programu Visual Studio, uzupełniania kodu IntelliSense wyszukiwania i instrukcji, projektantów wizualnych, zarządzanie projektem, a itd., należy użyć programu Visual Studio IDE.

## <a name="debugging-your-code"></a>Debugowanie kodu

Jeśli za pomocą wiersza polecenia i uruchamiać aplikacje na deweloperskiej stacji roboczej, zostanie wyświetlony, wyświetlane jest okno dialogowe, aby uruchomić debuger programu Visual Studio, gdy kod napotka naruszenie zasad dostępu do pamięci, nieobsługiwany wyjątek lub innych nieodwracalny błędy. Jeśli klikniesz **OK**, następnie środowiska programistycznego Visual Studio jest uruchomiony i otworzy debuger do punktu awarii. Istnieje możliwość debugowania aplikacji w ten sposób, a w tym przypadku kodu źródłowego tylko będą dostępne, jeśli skompilowany przy użyciu [/z7, / zi, /ZI (Format informacji debugowania)](../build/reference/z7-zi-zi-debug-information-format.md) przełącznika. Aby uzyskać więcej informacji, zobacz [debugowanie kodu natywnego](/visualstudio/debugger/debugging-native-code) i [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="using-the-development-environment"></a>Używanie środowiska programistycznego

Jest łatwiejszy w użyciu środowisko programistyczne do edytowania i kompilowania kodu źródłowego *projektu*. Projekt jest kolekcją źródła i powiązane pliki, które zostaną skompilowane w pojedynczą jednostkę, np. biblioteki lub pliku wykonywalnego. Projekt zawiera także informacji na temat sposobu pliki mają być tworzone. Informacje o projektach są przechowywane w pliku projektu za pomocą .prj rozszerzenia.

Aplikacja, która składa się z wielu biblioteki i pliki wykonywalne, każdy potencjalnie utworzonych za pomocą innego zestawu opcji kompilatora lub nawet w innym języku, są przechowywane w wielu projektach, które są częścią pojedynczej *rozwiązania*. To rozwiązanie jest klasą abstrakcyjną dla kontenera, grupy wraz z wielu projektów. Informacje o rozwiązaniach są przechowywane w pliku rozwiązania przy użyciu rozszerzenia .sln. Aby uzyskać więcej informacji, zobacz [rozwiązań i projektów w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) i [przy użyciu programu Visual Studio IDE dla programowanie aplikacji klasycznych w języku C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).

## <a name="importing-your-existing-code"></a>Importowanie istniejącego kodu

Kompilator języka C++ umożliwia tworzenie istniejący kod, który jest skonfigurowany do kompilowania z użyciem lub bez pliku reguł programu make i umieścić go w projekcie programu Visual Studio. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektu C++ z istniejącego kodu](../build/how-to-create-a-cpp-project-from-existing-code.md).

## <a name="creating-a-new-project"></a>Tworzenie nowego projektu

Można utworzyć nowych projektów w środowisku programistycznym. Visual Studio zawiera wiele szablonów, które zapewniają standardowy kod dla różnych popularnych projektów. Kreator aplikacji może zostać użyty do generowania projektów z opisanych kodu dla różnych typów aplikacji.

Można uruchomić z pusty projekt za pomocą **Kreatora aplikacji konsoli (Win32)**. Wybierz **pusty projekt** pole wyboru. Nowe i istniejące pliki można następnie dodać do projektu później.

Podczas tworzenia projektu, nazwę projektu. Domyślnie nazwa projektu jest równe nazwę biblioteki dołączanej (dynamicznie DLL) lub pliku wykonywalnego, który jest kompilacji z projektu. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).

## <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft

Kompilator Microsoft Visual C++ implementuje kilka rozszerzeń do standardowego języka programowania C++ do obsługi programowania dla systemów operacyjnych Windows. Te rozszerzenia są używane, aby określić atrybuty klasy magazynu, funkcji, Konwencje wywoływania i adresowanie, między innymi na podstawie. Aby uzyskać pełną listę wszystkich obsługiwanych rozszerzeń języka C++, zobacz [Modyfikatory specyficzne dla Microsoft](../cpp/microsoft-specific-modifiers.md).

Wszystkie rozszerzenia charakterystyczne dla Microsoft c++ można wyłączyć za pomocą `/Za` — opcja kompilatora. Ta opcja jest zalecana, jeśli chcesz napisać kod do uruchamiania na wielu platformach. Aby uzyskać więcej informacji na temat `/Za` — opcja kompilatora, zobacz [/za, /Ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md). Aby uzyskać więcej informacji na temat zgodności kompilatora języka C++, zobacz [Visual zgodność języka C++](../overview/visual-cpp-language-conformance.md) i [niestandardowe zachowanie](../cpp/nonstandard-behavior.md).

## <a name="precompiled-headers"></a>Prekompilowane nagłówki

Kompilatory Microsoft C i C++ zapewnia opcje dla wstępnej kompilacji kodu C lub C++, łącznie z kodem wbudowanego. Dzięki tej funkcji wydajności można skompilować stabilne treść kodu, zapisanie skompilowanej kodu w pliku i, podczas kolejnych kompilacjach łączyć wstępnie skompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejne kompilacja jest szybsza, ponieważ stabilnym kodem nie musi być ponownie kompilowane.

Domyślnie wszystkie wstępnie skompilowany kod jest określona w pliku plików stdafx.h i stdafx.cpp. **Nowy projekt** Kreator automatycznie utworzy pliki te można o ile nie wyłączysz **prekompilowany nagłówek** opcji. Aby uzyskać więcej informacji na temat wstępnie skompilowanych nagłówków, zobacz [tworzenie prekompilowanych plików nagłówka](../build/creating-precompiled-header-files.md).

## <a name="related-sections"></a>Sekcje pokrewne

Aby uzyskać więcej informacji, zobacz [eksportowanie z systemu UNIX do Win32](../porting/porting-from-unix-to-win32.md).

## <a name="see-also"></a>Zobacz także

[Projekty i systemy kompilacji](../build/projects-and-build-systems-cpp.md)
