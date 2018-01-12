---
title: Kompilowania kodu C/C++ w wierszu polecenia | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c5780fb725ab9ccfbba189894c22c991c415f6c2
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="build-cc-code-on-the-command-line"></a>Kompilowania kodu C/C++ w wierszu polecenia

Można tworzyć aplikacje C i C++ w wierszu polecenia przy użyciu narzędzia, które są uwzględniane w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].

Po wybraniu jednej z obciążeń C++ w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Instalatora, instaluje zestaw narzędzi, zawierającą kompilatorów C/C++ linkery, i innych narzędzi do kompilacji. Te narzędzia są używane przez [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE, a ich można również w wierszu polecenia. Istnieją oddzielne kompilatory hostowanej x86 i hostowanej x64 i narzędzia do kompilowania kodu x86, x64 i cele ARM. Każdy zestaw narzędzi dla konkretnego źródłowa i docelowa architektura kompilacji jest przechowywany w jego własnej katalogu. Działała prawidłowo, te narzędzia wymaga kilku zmiennych w danym środowisku je dodać do ścieżki oraz ustawić obejmują plik, biblioteki i lokalizacje zestawu SDK. Aby ułatwić ustawić zmienne środowiskowe, Instalator tworzy pliki polecenia niestandardowych, znanej także jako pliki wsadowe, podczas instalacji. Jeden z tych plików polecenie można uruchomić w oknie wiersza polecenia, aby ustawić architektura określonej kompilacji. Dla wygody, Instalator tworzy także skróty w Start menu (lub strony początkowej w systemie Windows 8.x) rozpoczynających deweloperów systemu windows z wiersza polecenia przy użyciu tych plików polecenia, wszystkie zmienne środowiskowe wymagane są ustawione i gotowe do użycia. 

Zmienne środowiskowe wymagane są określone do instalacji i architektura kompilacji, wybierz i może ulec zmianie przez uaktualnienia i aktualizacje produktu. W związku z tym zdecydowanie zaleca się, użyj jednej z skróty zainstalowanych wiersza polecenia lub pliki poleceń zamiast ustawienia zmiennych środowiskowych w systemie Windows, samodzielnie. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).  

Procesami wiersza polecenia, pliki poleceń i skrótów wiersza polecenia, które są instalowane są zależne od procesor komputera i opcji wybranych podczas instalacji. Co najmniej z 32-bitowy hostowany x86 kompilacji kodu natywnego x86 32-bitowego i narzędzi dla wielu narzędzi, które kompilacji kodu natywnego x64 64-bitowego są zainstalowane. Jeśli masz 64-bitowego systemu Windows są również instalowane z 64-bitowy hostowany x64 kompilacji natywnego kodu 64-bitowego i narzędzi dla wielu narzędzi, które kompilacji kodu natywnego 32-bitowych. Jeśli użytkownik chce zainstalować opcjonalne narzędzia platformy uniwersalnej systemu Windows C++, narzędzia natywnego 32-bitowe i 64-bitowe, które kompilacji kodu ARM również są instalowane. Inne obciążenia mogą instalować dodatkowe narzędzia.

<a name="developer_command_prompt_shortcuts"></a>
## <a name="developer-command-prompt-shortcuts"></a>Skróty wiersza polecenia dewelopera

Skróty wiersza polecenia są zainstalowane w określonej wersji [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] folder, w Start menu. Poniżej przedstawiono listę skrótów wiersza polecenia podstawowe i architektur kompilacji, które obsługują:

- **Wiersz polecenia dla deweloperów** ustawia środowisko kompilacji 32-bitowego kodu macierzystego x86 za pomocą narzędzi 32-bitowy, x86 macierzystego.  
- **x86 wiersz polecenia narzędzi natywnego** ustawia środowisko kompilacji 32-bitowego kodu macierzystego x86 za pomocą narzędzi 32-bitowy, x86 macierzystego.  
- **x64 wiersz polecenia narzędzi natywnego** ustawia w środowisku używanie 64-bitowe, x64 natywnego narzędzia do kompilowania kodu 64-bitowe, x64 macierzystego.  
- **Wiersz polecenia narzędzi Cross x86_x64** ustawia w środowisku 32-bitowy, x86 native narzędzia do kompilowania kodu 64-bitowe, x64 native.  
- **Wiersz polecenia narzędzi Cross x64_x86** ustawia w środowisku używanie 64-bitowe, x64 natywnego narzędzia do kompilowania kodu 32-bitowy, x86 native.  

Rzeczywiste Start menu folderu i skrót nazwy różnią się zależnie od wersji [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] został zainstalowany i instalacji pseudonimu, jeśli zostanie ustawiona. Na przykład, jeśli masz program Visual Studio 2017 r zainstalowana i został przyznany instalacji pseudonim 15 ustęp 3, skrót do wiersza polecenia dewelopera nosi nazwę **wiersz polecenia dla programu VS 2017 (15 ustęp 3) deweloperów**, w folderze o nazwie  **Visual Studio 2017**. 

Jeśli po zainstalowaniu [Build Tools dla programu Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=840931) lub [Visual C++ 2015 kompilacji narzędzia](http://landinghub.visualstudio.com/visual-cpp-build-tools) edition, może istnieć tylko określonych native lub różnych narzędzi opcje wiersza polecenia dewelopera. 

<a name="developer_command_prompt"></a>
## <a name="to-open-a-developer-command-prompt-window"></a>Aby otworzyć okno wiersza polecenia dewelopera  
  
1.  Na pulpicie otwórz systemu Windows **Start** menu, a następnie przewiń do Znajdowanie i otwieranie folderu dla używanej wersji programu Visual Studio, na przykład **programu Visual Studio 2017**. W niektórych starszych wersji programu Visual Studio, skróty znajdują się w podfolderze o nazwie **programu Visual Studio Tools**.  
  
2.  W folderze, wybierz **wiersza polecenia dewelopera** dla używanej wersji programu Visual Studio. Ten skrót spowoduje uruchomienie używającej architektura kompilacji domyślne 32-bitowy, x86 natywnych narzędzi do tworzenia 32-bitowego kodu macierzystego x86 okno wiersza polecenia dewelopera. Jeśli wolisz architektura kompilacji innych niż domyślne, wybierz jedną z natywnego lub różnych narzędzi wierszy polecenia, aby określić Architektura źródłowa i docelowa. 

Szybszy sposób, aby otworzyć okno wiersza polecenia dewelopera jest wprowadzenie *wiersza polecenia dewelopera* w polu wyszukiwania na pulpicie, a następnie wybierz pożądany wynik.

<a name="developer_command_files"></a>
## <a name="developer-command-files-and-locations"></a>Pliki poleceń deweloperów i lokalizacje

Jeśli wolisz można ustawić środowiska architektura kompilacji w istniejących okno wiersza polecenia, można użyć jednego z plików polecenia utworzony przez Instalatora. Lokalizacja tych plików zależy od wersji [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] został zainstalowany, a w lokalizacji i nazewnictwa wyborów dokonanych podczas instalacji. Dla programu Visual Studio 2017 r. typowej instalacji na 64-bitowym komputerze znajduje się w \Program pliki (x86) \Microsoft Visual Studio\2017\\*wersji*, gdzie *wersji* może być społeczności Professional, Enterprise, BuildTools lub innym o podanej nazwie. Dla programu Visual Studio 2015 typowej instalacji znajduje się w \Program Files (x86) \Microsoft Visual Studio 14.0. 

Plik poleceń wiersza polecenia dewelopera podstawowego, VsDevCmd.bat, znajduje się w podkatalogu Common7\Tools katalogu instalacyjnego. Jeśli nie określono żadnych parametrów, to ustawienie środowiska i kompilacji architektura umożliwia utworzenie x86 32-bitowej obsługi narzędzia x86 native 32-bitowy kod.

Pliki dodatkowe polecenia są dostępne do konfigurowania architektury określonej kompilacji, w zależności od architektury procesorów i [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] obciążeń i opcje został zainstalowany. W programie Visual Studio 2017 r, znajdują się one w podkatalogu VC\Auxiliary\Build [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] katalogu instalacyjnego. W programie Visual Studio 2015, te znajdują się w VC, VC\bin lub VC\bin\\*architektury* podkatalogi katalogu instalacji, gdzie *architektury* jest jednym z natywnego lub między Opcje kompilatora. Te pliki poleceń Ustaw parametry i Wywołaj VsDevCmd.bat, aby skonfigurować środowisko architektura określonej kompilacji. Typowej instalacji mogą obejmować te pliki poleceń:

- **vcvars32.bat —** narzędzia do kompilacji x86 32-bitowych x86 native 32-bitowego kodu.  
- **vcvars64.bat** narzędzia do kompilacji x64 64-bitowych x64 natywnych 64-bitowego kodu.  
- **vcvarsx86_amd64.bat** korzystania z 32-bitowych x86 native krzyżowego narzędzi do kompilacji x64 64-bitowych kodu.  
- **vcvarsamd64_x86.bat** korzystania z 64-bitowych x64 native krzyżowego narzędzi do kompilacji x86 32-bitowy kod.  
- **vcvarsx86_arm.bat** korzystania z 32-bitowych x86 native krzyżowego narzędzi do kompilacji kodu ARM.  
- **vcvarsamd64_arm.bat** korzystania z 64-bitowych x64 native krzyżowego narzędzi do kompilacji kodu ARM.  
- **vcvarsall.bat** Użyj parametrów, aby określić hosta i architektury docelowej, a także opcje SDK i platformy. Wywołanie za pomocą `/help` parametr, aby uzyskać listę opcji.  

> [!CAUTION]
>  Plik vcvarsall.bat i inne pliki poleceń może się różnić między komputerami. Zastępuje uszkodzony lub plik vcvarsall.bat przy użyciu pliku z innego komputera. Uruchom ponownie [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] Instalatora, aby zastąpić brakujący plik.  
>   
> Plik vcvarsall.bat również różni się od poprzedniej wersji. Jeśli bieżącą wersję programu Visual C++ jest zainstalowany na komputerze, który ma także starszej wersji programu Visual C++, nie należy uruchamiać vcvarsall.bat lub innego pliku poleceń z różnych wersji w oknie wiersza polecenia.  
 
Najprostszym sposobem, aby określić architektury określonej kompilacji w istniejących okno polecenia jest używany plik vcvarsall.bat. Vcvarsall.bat umożliwia ustawianie zmiennych środowiskowych, aby skonfigurować wiersz polecenia dla natywnej kompilacji 32-bitowy lub 64-bitowej lub cross kompilacji x86, x64 lub procesorów ARM; objęcie Sklepu Windows, platforma uniwersalna systemu Windows lub platformy Windows Desktop; Aby określić, które zestaw Windows SDK użyty. i określ wersję zestawu narzędzi platformy. Jeśli podano w nim żadnych argumentów vcvarsall.bat konfiguruje zmiennych środowiskowych dla przy użyciu bieżącego macierzystego kompilatora 32-bitowego dla x86 cele pulpitu systemu Windows. Jednak można go skonfigurować dowolne natywnego lub między narzędzia kompilatora. Jeśli określisz konfiguracji kompilatora, która nie jest zainstalowany lub nie jest dostępna w kompilacji architektury komputera, zostanie wyświetlony komunikat o błędzie. W poniższej tabeli zamieszczono obsługiwana architektura argumentów:  
  
|Argument architektura Vcvarsall.bat|Kompilatora|Architektura komputera hosta|Architektura danych wyjściowych kompilacji|  
|----------------------------|--------------|----------------------------------|-------------------------------|  
|x86|x86 native 32-bitowych|x86, x64|x86|  
|x86\_amd64 lub x86\_x64|krzyżowe x64 na x86|x86, x64|X64|  
|x86_arm|ARM na x86 między|x86, x64|ARM|  
|amd64 lub x64|x64 native 64-bitowych|X64|X64|  
|AMD64\_x86 lub x64\_x86|x86 na x64 cross|X64|x86|  
|AMD64\_arm lub x64\_arm|ARM na x64 między|X64|ARM|  
  
Można użyć **przechowywania** lub **uwp** opcji, aby określić typ platformy, lub ani do określenia aplikacji komputerowej. Określenie wersji zestawu Windows SDK, użyj pełnej liczbę zestawu Windows 10 SDK 10.0.10240.0 lub określ 8.1 korzystanie z zestawu Windows 8.1 SDK. Umożliwia określenie zestawu narzędzi kompilatora Visual Studio 2015; 14.0 środowisko domyślnie używać zestawu narzędzi kompilatora Visual Studio 2017 r.

<a name="vcvarsall"></a>
## <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Aby skonfigurować środowisko kompilacji w istniejących okno wiersza polecenia  
  
1.  W wierszu polecenia należy użyć polecenia CD, aby zmienić do katalogu instalacyjnego programu Visual Studio. Następnie za pomocą dysku CD ponownie zmienić podkatalog, zawierający pliki polecenia specyficzne dla konfiguracji. Dla programu Visual Studio 2017 r jest podkatalog VC\Auxiliary\Build. Dla programu Visual Studio 2015 Użyj podkatalogu VC.  
  
1.  Aby skonfigurować to okno wiersza polecenia kompilacji kodu dla x86 za pomocą narzędzi 32-bitowych platform, w wierszu polecenia wprowadź:  
  
     `vcvarsall`  

1.  Aby skonfigurować to okno wiersza polecenia kompilacji kodu dla x64 za pomocą narzędzi 32-bitowych platform, w wierszu polecenia wprowadź:  
  
     `vcvarsall x86_amd64`  
  
1.  Aby skonfigurować to okno wiersza polecenia, aby 32-bitowego narzędzia do kompilowania kodu dla platformy ARM, w wierszu polecenia wpisz:  
  
     `vcvarsall x86_arm`  
  
1.  Aby skonfigurować to okno wiersza polecenia kompilacji kodu dla x64 za pomocą narzędzi 64-bitowych platform, w wierszu polecenia wprowadź:  
  
     `vcvarsall amd64`  
  
1.  Aby skonfigurować to okno wiersza polecenia kompilacji kodu dla x86 za pomocą narzędzi 64-bitowych platform, w wierszu polecenia wprowadź:  
  
     `vcvarsall amd64_x86`  
  
1.  Aby skonfigurować to okno wiersza polecenia, aby 64-bitowego narzędzia do kompilowania kodu dla platformy ARM, w wierszu polecenia wpisz:  
  
     `vcvarsall amd64_arm`  

Plik poleceń ustawia zmienne środowiskowe wymagane dla ścieżek narzędzia kompilacji, biblioteki i nagłówków. Po wykonaniu użyć tego okna wiersza polecenia do uruchomienia narzędzi i kompilatora wiersza polecenia.  
  
Jeśli używasz [DEVENV](/visualstudio/ide/reference/devenv-command-line-switches) dla kompilacji z wiersza polecenia środowiska ustawić vcvarsall.bat lub inne pliki poleceń nie wpływa na kompilacje, chyba że zostanie również **/useenv** opcji.  

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia
  
Aby zbudować projekt C/C++ w wierszu polecenia, można użyć tych narzędzi wiersza polecenia programu Visual C++:  
  
[CL](../build/reference/compiling-a-c-cpp-program.md)  
Kompilator (cl.exe) umożliwia kompilowanie i łączenie plików kodu źródłowego w aplikacji, biblioteki i bibliotek DLL.  
  
[Link](../build/reference/linking.md)  
Konsolidator (link.exe) umożliwia łączenie plików skompilowanych obiektów i bibliotek w aplikacji i bibliotek DLL.  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
Użyj programu MSBuild (msbuild.exe) do tworzenia projektów Visual C++ i [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] rozwiązania. Jest to równoważne uruchomiona **kompilacji** projektu lub **Kompiluj rozwiązanie** w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE.  
  
[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)  
Użyj DEVENV (devenv.exe) połączonych z przełącznikiem wiersza polecenia — na przykład **/Build** lub **/Clean**— do wykonania niektórych kompilacji polecenia bez wyświetlania [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] IDE.  
  
[NMAKE](../build/nmake-reference.md)  
Umożliwia automatyzację zadań, które kompilacji projektów Visual C++ przy użyciu tradycyjnych pliku reguł programu make NMAKE (nmake.exe).  
  
Podczas kompilowania w wierszu polecenia można uzyskać informacji o ostrzeżenia, błędy i komunikaty. Uruchom [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] , a następnie na pasku menu wybierz **pomocy**, **wyszukiwania**.  
  
## <a name="in-this-section"></a>W tej sekcji  

Artykuły w tej sekcji dokumentacji pokazują, jak tworzyć aplikacje w wierszu polecenia, opisano sposób dostosowywania środowiska kompilacji wiersza polecenia, użyj procesami 64-bitowe i docelowej x86, x64, ARM platform i pokazują, jak używać kompilacji wiersza polecenia narzędzia MSBuild i NMAKE.  
  
[Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)  
Podaje przykład pokazujący sposób tworzenia i skompilować prosty program w języku C++ w wierszu polecenia.  
  
[Wskazówki: Kompilowanie programu C w wierszu polecenia](../build/walkthrough-compile-a-c-program-on-the-command-line.md)  
Opisuje sposób kompilowania program napisany w języku programowania C.  
  
[Przewodnik: kompilowanie programu w języku C++/CLI w wierszu polecenia](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)  
Opisuje sposób tworzenia i skompilować C + +/ CLI program, który używa programu .NET Framework.  
  
[Przewodnik: kompilowanie programu w języku C++/CX w wierszu polecenia](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)  
Opisuje sposób tworzenia i skompilować C + +/ CX program, który używa środowiska wykonawczego systemu Windows.  
  
[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)  
Opisuje sposób uruchamiania okno wiersza polecenia, zawierający zmienne środowiskowe wymagane dla kompilacji z wiersza polecenia kierowanych x86, x64 oraz ARM przy użyciu 32-bitowy lub 64-bitowego zestawu narzędzi platformy.  
  
[NMAKE — dokumentacja](../build/nmake-reference.md)  
Zawiera łącza do artykułów, które opisują Program obsługi narzędzie Microsoft (NMAKE. WYWOŁANIE PLIKU EXE).  
  
[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)  
Zawiera łącza do artykułów, które omówiono sposób użycia MSBuild.EXE.  
  
## <a name="related-sections"></a>Sekcje pokrewne  

[/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](../build/reference/md-mt-ld-use-run-time-library.md)  
Opisuje sposób korzystać z tych opcji kompilatora przy użyciu biblioteki wykonawcze debugowania i wydania.  
  
[Opcje kompilatora C/C++](../build/reference/compiler-options.md)  
Zawiera łącza do artykułów, które opcje kompilatora C i C++ i CL.exe.  
  
[Opcje konsolidatora](../build/reference/linker-options.md)  
Zawiera łącza do artykułów, które opcje konsolidatora i LINK.exe.  
  
[Narzędzia kompilacji C/C++](../build/reference/c-cpp-build-tools.md)  
Zawiera łącza do C/C++ kompilacji narzędzia, które są uwzględniane w [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Zobacz też  

[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)