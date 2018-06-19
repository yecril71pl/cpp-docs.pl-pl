---
title: Wprowadzenie do języka Visual C++ dla użytkowników systemu UNIX | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/01/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f05d7d3d3d3fd6b40a5477b7765b89409747d3ce
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845869"
---
# <a name="introduction-to-visual-c-for-unix-users"></a>Wprowadzenie do programu Visual C++ dla użytkowników systemu UNIX

Ten temat zawiera informacje dla użytkowników systemu UNIX, które są nowe w programie Visual Studio i chcesz stać się wykorzystują C++ i Visual Studio programowanie środowiska IDE (Integrated).
  
## <a name="getting-started-on-the-command-line"></a>Wprowadzenie do korzystania z wiersza polecenia  

Kompilator języka C++ w wierszu polecenia można użyć w podobny sposób, że używasz środowiska wiersza polecenia systemu UNIX. Kompiluj z wiersza polecenia przy użyciu wiersza polecenia kompilatora C i C++ (CL. Wywołanie pliku EXE), konsolidatora (łącze. EXE) i innych narzędzi, takich jak NMAKE. EXE, wersja Microsoft UNIX należy narzędzie.  
  
W systemie UNIX polecenia są instalowane w folderze wspólne, takie jak katalogu/usr. W programie Visual Studio narzędzia wiersza polecenia są zainstalowane w katalogu instalacji programu Visual Studio w podkatalogu VC\bin i jego podkatalogach. W przeciwieństwie do systemu UNIX te narzędzia nie są dostępne w oknie wiersza polecenia zwykły. Aby użyć narzędzia wiersza polecenia, użyj skrótu wiersza polecenia dewelopera lub uruchom plik takich jak vcvarsall.bat poleceń dewelopera. To ustawienie ścieżkę i inne zmienne środowiskowe, które są niezbędne do kompilacji C++ programów z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [kodu kompilacji C/C++ w wierszu polecenia](../build/building-on-the-command-line.md) i [wskazówki: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md).  
  
Aby otworzyć skrót do wiersza polecenia dewelopera, wprowadź *wiersza polecenia dewelopera* na pulpicie wyszukiwania sterowania i wybierz polecenie **wiersz polecenia dla deweloperów** wynik dla używanej wersji programu Visual Studio. Aby wybrać developer wiersza polecenia, który jest wstępnie skonfigurowany do określonego hosta i Architektura docelowa, otwórz **Start** menu (ikona Windows rogu pulpitu), a następnie przewiń do folderu dla używanej wersji programu Visual Studio , takich jak **programu Visual Studio 2017**. Otwórz folder, a następnie wybierz skrót do wiersza polecenia dla architektury preferowanych źródłowa i docelowa.
  
Aby móc korzystać z bardziej zaawansowane funkcje, takie jak debuger programu Visual Studio, uzupełniania kodu IntelliSense wyszukiwania i instrukcji, wizualnych projektantów projektu zarządzania i itd., należy użyć środowiska IDE programu Visual Studio.  
  
## <a name="debugging-your-code"></a>Debugowanie kodu  

Jeśli używasz wiersza polecenia i uruchomienia aplikacji na deweloperskiej stacji roboczej, zostanie wyświetlone okno dialogowe, aby uruchomić [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] debugera jest wyświetlane, gdy kod napotka naruszenie dostępu do pamięci, nieobsługiwany wyjątek lub innych nieodwracalny błędy. Jeśli klikniesz przycisk **OK**, następnie środowisko projektowe Visual Studio została uruchomiona i debuger zostanie otwarty do punktu awarii. Istnieje możliwość debugowania aplikacji w ten sposób i w takim przypadku kod źródłowy czy jest dostępna, jeśli skompilowane z [/z7, / zi, /ZI (Format informacji debugowania)](../build/reference/z7-zi-zi-debug-information-format.md) przełącznika. Aby uzyskać więcej informacji, zobacz [debugowanie kodu natywnego](/visualstudio/debugger/debugging-native-code) i [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="using-the-development-environment"></a>Używanie środowiska projektowania  

Jest łatwiejsze w środowisku programistycznym do edycji i kompilacji kodu źródłowego *projektu*. Projekt jest kolekcją źródła i powiązane pliki, które zostanie skompilowany w pojedynczą jednostkę, takich jak biblioteką lub plikiem wykonywalnym. Projekt zawiera także informacji na temat sposobu plików ma zostać utworzony. Informacje o projekty są przechowywane w pliku projektu z .prj rozszerzenia.  
  
Aplikacja, która składa się z wielu bibliotek i plików wykonywalnych, każdy potencjalnie skompilowanej za pomocą innego zbioru opcji kompilatora lub nawet w innym języku, są przechowywane w wielu projektach, które są częścią pojedynczej *rozwiązania*. Rozwiązanie to Abstrakcja dla kontenera zgrupować wielu projektów. Informacje o rozwiązaniach są przechowywane w pliku rozwiązania z .sln rozszerzenia. Aby uzyskać więcej informacji, zobacz [rozwiązania i projekty w programie Visual Studio](/visualstudio/ide/solutions-and-projects-in-visual-studio) i [za pomocą środowiska IDE programu Visual Studio dla programowania w języku C++ pulpitu](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md).  
  
## <a name="importing-your-existing-code"></a>Importowanie istniejącego kodu 
 
Kompilator języka C++ można użyć do tworzenia istniejący kod, który jest skonfigurowany do kompilacji z lub bez pliku reguł programu make i umieszcza je w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] projektu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu C++ z istniejącego kodu](../ide/how-to-create-a-cpp-project-from-existing-code.md).  
  
## <a name="creating-a-new-project"></a>Tworzenie nowego projektu  

Można tworzyć nowe projekty w środowisku programistycznym. Program Visual Studio udostępnia wiele szablonów, które zapewniają standardowego kodu dla różnych popularnych projektów. Kreatorzy aplikacji służy do generowania projektów z opisanych kodu dla różnych typów aplikacji.  
  
Pusty projekt można rozpoczynać przy użyciu **Kreatora aplikacji konsoli (Win32)**. Wybierz **pusty projekt** pole wyboru. Nowe i istniejące pliki można następnie dodać do projektu później.  
  
Podczas tworzenia projektu, nazwę projektu. Domyślnie nazwa projektu jest równe nazwę biblioteki dołączanej (dynamicznie DLL) lub pliku wykonywalnego, który jest kompilacji z projektu. Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).  
  
## <a name="microsoft-specific-modifiers"></a>Modyfikatory specyficzne dla firmy Microsoft  

Kompilator Microsoft Visual C++ implementuje wiele rozszerzeń standardu C++ język programowania obsługę programowania w języku systemu operacyjnego. Te rozszerzenia są używane, aby określić atrybuty klasy magazynu, funkcja Konwencje wywoływania i adresowanie, między innymi na podstawie. Aby uzyskać pełną listę wszystkich obsługiwanych rozszerzeń języka C++, zobacz [Modyfikatory specyficzne dla firmy Microsoft](../cpp/microsoft-specific-modifiers.md).  
  
Wszystkie rozszerzenia języka C++ specyficzne dla firmy Microsoft można wyłączyć za pomocą **/Za** — opcja kompilatora. Ta opcja jest zalecana, jeśli chcesz napisać kod do uruchamiania na wielu platformach. Aby uzyskać więcej informacji na temat **/Za** — opcja kompilatora, zobacz [/Za, /Ze (Wyłącz rozszerzenia językowe)](../build/reference/za-ze-disable-language-extensions.md). Aby uzyskać więcej informacji na temat zgodności kompilatora C++, zobacz [Visual zgodność języka C++](../visual-cpp-language-conformance.md) i [niestandardowe zachowanie](../cpp/nonstandard-behavior.md).  
  
## <a name="precompiled-headers"></a>Prekompilowane nagłówki  

Kompilatory języka Microsoft C i C++ opcje dla wstępnej kompilacji dowolnego kodu języka C lub C++, w tym kodu wbudowanego. Tej funkcji wydajności można skompilować stabilna treści kodu, przechowywać skompilowanej kodu w pliku i, podczas kolejnych kompilacjach połączyć prekompilowany kod z kodem, który jest nadal w fazie projektowania. Każda kolejne Kompilacja trwa krócej, ponieważ stabilna kodu nie muszą być ponownie kompilowane.  
  
Domyślnie wszystkie wstępnie skompilowanym kodu jest określona w plikach **stdafx.h** i **stdafx.cpp**. **Nowy projekt** Kreator automatycznie utworzy te pliki dla Ciebie, jeśli nie wyłączysz **Prekompilowanego nagłówka** opcji. Aby uzyskać więcej informacji na prekompilowanych nagłówków, zobacz [tworzenie prekompilowanych plików nagłówka](../build/reference/creating-precompiled-header-files.md).  
  
## <a name="related-sections"></a>Sekcje pokrewne  

Aby uzyskać więcej informacji, zobacz [eksportowanie z systemu UNIX do Win32](../porting/porting-from-unix-to-win32.md).  
  
## <a name="see-also"></a>Zobacz też  

[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)