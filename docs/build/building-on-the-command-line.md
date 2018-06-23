---
title: Kompilowania kodu C/C++ w wierszu polecenia | Dokumentacja firmy Microsoft
ms.custom: conceptual
ms.date: 06/21/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 241a7ae0d7f6c1adf269370301b39a3267440995
ms.sourcegitcommit: e013acba70aa29fed60ae7945162adee23e19c3b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36322319"
---
# <a name="build-cc-code-on-the-command-line"></a>Kompilowania kodu C/C++ w wierszu polecenia

Można tworzyć aplikacje C i C++ w wierszu polecenia, za pomocą narzędzia, które są uwzględniane w programie Visual Studio.

## <a name="how-to-get-the-command-line-tools"></a>Jak uzyskać narzędzi wiersza polecenia

Po wybraniu obciążeń C++ w Instalatorze programu Visual Studio instalacji programu Visual Studio *zestaw narzędzi platformy*. Zestaw narzędzi platformy zawiera narzędzia C i C++ dla określonej wersji programu Visual Studio, w tym kompilatory C/C++, linkery, asemblerów i inne narzędzia kompilacji, a także zgodnych bibliotek. Możliwość używania wszystkich tych narzędzi w wierszu polecenia, a następnie są one również używane wewnętrznie przez środowiska IDE programu Visual Studio. Istnieją oddzielne kompilatory hostowanej x86 i hostowanej x64 i narzędzia umożliwiające tworzenie kodu dla x86 x 64, ARM i ARM64 obiektów docelowych. Każdy zestaw narzędzi dla konkretnego źródłowa i docelowa architektura kompilacji jest przechowywany w jego własnej katalogu.

Działała prawidłowo, narzędzia wymaga kilku zmiennych w danym środowisku, należy ustawić wartość. Są one używane, aby dodać je do ścieżki oraz ustawić obejmują plik, biblioteki i lokalizacje zestawu SDK. Aby ułatwić ustawić zmienne środowiskowe, Instalator tworzy dostosowany *pliki poleceń*, lub pliki, wsadowe podczas instalacji. Jeden z tych plików polecenie można uruchomić w oknie wiersza polecenia, aby ustawić konkretnego hosta i Architektura docelowa kompilacji, wersja zestawu Windows SDK, platformy docelowej i zestawu narzędzi platformy. Dla wygody, Instalator tworzy także skróty w Start menu (lub strony początkowej w systemie Windows 8.x) rozpoczynających deweloperów systemu windows z wiersza polecenia przy użyciu tych plików polecenia, wszystkie zmienne środowiskowe wymagane są ustawione i gotowe do użycia.

Zmienne środowiskowe wymagane są określone do instalacji i architektura kompilacji, wybierz i może ulec zmianie przez uaktualnienia i aktualizacje produktu. W związku z tym zdecydowanie zaleca się, użyj jednej z skróty zainstalowanych wiersza polecenia lub pliki poleceń zamiast ustawienia zmiennych środowiskowych w systemie Windows, samodzielnie. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md).

Procesami wiersza polecenia, pliki poleceń i skrótów wiersza polecenia, które są instalowane są zależne od procesor komputera i opcji wybranych podczas instalacji. Co najmniej z 32-bitowy hostowany x86 kompilacji kodu natywnego x86 32-bitowego i narzędzi dla wielu narzędzi, które kompilacji kodu natywnego x64 64-bitowego są zainstalowane. Jeśli masz 64-bitowego systemu Windows są również instalowane z 64-bitowy hostowany x64 kompilacji natywnego kodu 64-bitowego i narzędzi dla wielu narzędzi, które kompilacji kodu natywnego 32-bitowych. Jeśli użytkownik chce zainstalować opcjonalne narzędzia platformy uniwersalnej systemu Windows C++, narzędzia natywnego 32-bitowe i 64-bitowe, które kompilacji kodu ARM również są instalowane. Inne obciążenia mogą instalować dodatkowe narzędzia.

## <a name="developer-command-prompt-shortcuts"></a>Skróty wiersza polecenia dewelopera

Skróty wiersza polecenia są instalowane w folderze określonej wersji programu Visual Studio w Start menu. Poniżej przedstawiono listę skrótów wiersza polecenia podstawowe i architektur kompilacji, które obsługują:

- **Wiersz polecenia dla deweloperów** -ustawia środowisko kompilacji 32-bitowego kodu macierzystego x86 za pomocą narzędzi 32-bitowy, x86 macierzystego.
- **x86 wiersz polecenia narzędzi natywnego** -ustawia środowisko kompilacji 32-bitowego kodu macierzystego x86 za pomocą narzędzi 32-bitowy, x86 macierzystego.
- **x64 wiersz polecenia narzędzi natywnego** -ustawia w środowisku używanie 64-bitowe, x64 natywnego narzędzia do kompilowania kodu 64-bitowe, x64 macierzystego.
- **Wiersz polecenia narzędzi Cross x86_x64** -ustawia w środowisku 32-bitowy, x86 native narzędzia do kompilowania kodu 64-bitowe, x64 native.
- **Wiersz polecenia narzędzi Cross x64_x86** -ustawia w środowisku używanie 64-bitowe, x64 natywnego narzędzia do kompilowania kodu 32-bitowy, x86 native.

Rzeczywiste Start menu folderu skrótów nazwy i zależy od wersji programu Visual Studio został zainstalowany i instalacja pseudonimu, jeśli zostanie ustawiona. Na przykład, jeśli masz program Visual Studio 2017 r zainstalowany, a został podany jej instalacji pseudonim *Podgląd*, nosi nazwę skrót do wiersza polecenia dewelopera **wiersz polecenia dla programu VS 2017 (wersja zapoznawcza)deweloperów**, w folderze o nazwie **programu Visual Studio 2017**.

Jeśli po zainstalowaniu [Build Tools dla programu Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721) (która także obejmuje zestaw narzędzi kompilatora Visual Studio 2015 Update 3), tylko architektury native lub różnych narzędzi wiersza polecenia dewelopera opcje są zainstalowane , a nie ogólne **wiersza polecenia dewelopera** skrótów.

<a name="developer_command_prompt"></a>
### <a name="to-open-a-developer-command-prompt-window"></a>Aby otworzyć okno wiersza polecenia dewelopera

1. Na pulpicie otwórz systemu Windows **Start** menu, a następnie przewiń do Znajdowanie i otwieranie folderu dla używanej wersji programu Visual Studio, na przykład **programu Visual Studio 2017**. W niektórych starszych wersji programu Visual Studio, skróty znajdują się w podfolderze o nazwie **programu Visual Studio Tools**.

1. W folderze, wybierz **wiersza polecenia dewelopera** dla używanej wersji programu Visual Studio. Ten skrót spowoduje uruchomienie używającej architektura kompilacji domyślne 32-bitowy, x86 natywnych narzędzi do tworzenia 32-bitowego kodu macierzystego x86 okno wiersza polecenia dewelopera. Jeśli wolisz architektura kompilacji innych niż domyślne, wybierz jedną z natywnego lub różnych narzędzi wierszy polecenia, aby określić Architektura źródłowa i docelowa.

Szybszy sposób, aby otworzyć okno wiersza polecenia dewelopera jest wprowadzenie *wiersza polecenia dewelopera* w polu wyszukiwania na pulpicie, a następnie wybierz pożądany wynik.

## <a name="developer-command-files-and-locations"></a>Pliki poleceń deweloperów i lokalizacje

Jeśli wolisz można ustawić środowiska architektura kompilacji w istniejących okno wiersza polecenia, można użyć jednego z poleceń (pliki wsadowe) utworzone przez Instalatora można ustawić wymaganych środowiska. Tylko zalecamy to zrobić w nowym oknie wiersza polecenia i nie zalecamy nowsze przełącznikami w tym samym oknie poleceń. Lokalizacja tych plików zależy od wersji programu Visual Studio zostały zainstalowane oraz lokalizacji i opcji nazewnictwa, wprowadzonych podczas instalacji. Dla programu Visual Studio 2017 r. typowej instalacji na 64-bitowym komputerze znajduje się w \Program pliki (x86) \Microsoft Visual Studio\2017\\*wersji*, gdzie *wersji* może być społeczności Professional, Enterprise, BuildTools lub innym o podanej nazwie. Dla programu Visual Studio 2015 typowej instalacji znajduje się w \Program Files (x86) \Microsoft Visual Studio 14.0.

Plik poleceń wiersza polecenia dewelopera podstawowego, VsDevCmd.bat, znajduje się w podkatalogu Common7\Tools katalogu instalacyjnego. Nie określono żadnych parametrów, to ustawia środowisko i źródłowa i docelowa kompilowania architektura umożliwia utworzenie x86 32-bitowej obsługi narzędzia x86 native 32-bitowy kod.

Pliki dodatkowe polecenia są dostępne do konfigurowania architektury określonej kompilacji, w zależności od architektury procesorów i obciążeń programu Visual Studio i opcje zainstalowane. W programie Visual Studio 2017 r. te znajdują się w podkatalogu VC\Auxiliary\Build katalogu instalacyjnego programu Visual Studio. W programie Visual Studio 2015, te znajdują się w VC, VC\bin lub VC\bin\\*architektury* podkatalogi katalogu instalacji, gdzie *architektury* jest jednym z natywnego lub Opcje kompilatora między. Te pliki poleceń Ustawianie parametrów domyślnych i Wywołaj VsDevCmd.bat, aby skonfigurować środowisko architektura określonej kompilacji. Typowej instalacji mogą obejmować te pliki poleceń:

|Plik poleceń|Architektura źródłowa i docelowa|
|---|---|
|**vcvars32.bat**| Narzędzia do kompilacji x86 32-bitowych x86 native 32-bitowego kodu.|
|**vcvars64.bat**| Narzędzia do kompilacji x64 64-bitowych x64 natywnych 64-bitowego kodu.|
|**vcvarsx86_amd64.bat**| Korzystania z 32-bitowych x86 native krzyżowego narzędzi do kompilacji x64 64-bitowych kodu.|
|**vcvarsamd64_x86.bat**| Korzystania z 64-bitowych x64 native krzyżowego narzędzi do kompilacji x86 32-bitowy kod.|
|**vcvarsx86_arm.bat**| Korzystania z 32-bitowych x86 native krzyżowego narzędzi do kompilacji kodu ARM.|
|**vcvarsamd64_arm.bat**| Za pomocą narzędzi krzyżowego x64 natywnych 64-bitowych kompilacji kodu ARM.|
|**vcvarsall.bat**| Użyj parametrów, aby określić hosta i architektury docelowej, a także opcje SDK i platformy. Aby uzyskać listę obsługiwanych opcji, należy wywołać przy użyciu **/help** parametru.|

> [!CAUTION]
> Plik vcvarsall.bat i inne pliki poleceń Visual Studio może się różnić między komputerami. Zastępuje uszkodzony lub plik vcvarsall.bat przy użyciu pliku z innego komputera. Uruchom ponownie Instalator programu Visual Studio, aby zastąpić brakujący plik.
>
> Plik vcvarsall.bat również różni się od poprzedniej wersji. Jeśli na komputerze, który ma także wcześniejszej wersji programu Visual Studio jest zainstalowana bieżąca wersja programu Visual Studio, nie uruchamiaj vcvarsall.bat lub innego pliku polecenia programu Visual Studio z różnych wersji w oknie wiersza polecenia.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Użyj narzędzi deweloperskich w istniejącym oknie polecenia

Najprostszym sposobem, aby określić architektury określonej kompilacji w istniejących okno polecenia jest używany plik vcvarsall.bat. Vcvarsall.bat umożliwia ustawianie zmiennych środowiskowych, aby skonfigurować wiersz polecenia dla natywnej kompilacji 32-bitowy lub 64-bitowej lub cross kompilacji x86, x64 lub procesorów ARM; objęcie Microsoft Store, platformy uniwersalnej systemu Windows lub platformy Windows Desktop; Aby określić, które zestaw Windows SDK użyty. i określ wersję zestawu narzędzi platformy. Jeśli podano w nim żadnych argumentów vcvarsall.bat konfiguruje zmiennych środowiskowych dla przy użyciu bieżącego macierzystego kompilatora 32-bitowego dla x86 cele pulpitu systemu Windows. Jednak można go skonfigurować dowolne natywnego lub między narzędzia kompilatora. Jeśli określisz konfiguracji kompilatora, która nie jest zainstalowany lub nie jest dostępna w kompilacji architektury komputera, zostanie wyświetlony komunikat o błędzie.

### <a name="vcvarsall-syntax"></a>Składnia vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*Architektura*<br/>
Ten opcjonalny argument określa Architektura źródłowa i docelowa do użycia. Jeśli *architektura* nie zostanie określony, używany jest domyślnym środowisku kompilacji. Obsługiwane są następujące argumenty:

|*Architektura*|Kompilatora|Architektura komputera hosta|Tworzenie architektury danych wyjściowych (docelowy)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 native 32-bitowych|x86, x64|x86|
|**x86\_amd64** lub **x86\_x64**|krzyżowe x64 na x86|x86, x64|X64|
|**x86_arm**|ARM na x86 między|x86, x64|ARM|
|**x86_arm64**|ARM64 na x86 między|x86, x64|ARM64|
|**AMD64** lub **x64**|x64 native 64-bitowych|X64|X64|
|**AMD64\_x86** lub **x64\_x86**|x86 na x64 cross|X64|x86|
|**AMD64\_arm** lub **x64\_arm**|ARM na x64 między|X64|ARM|
|**AMD64\_arm64** lub **x64\_arm64**|ARM64 na x64 między|X64|ARM64|

*platform_type*<br/>
Ten opcjonalny argument pozwala na określenie **przechowywania** lub **platformy uniwersalnej systemu Windows** jako typ platformy. Środowisko domyślnie do tworzenia aplikacji konsoli lub pulpitu.

*winsdk_version*<br/>
Opcjonalnie określa wersję zestawu Windows SDK do użycia. Domyślnie jest używana najnowsza wersja zainstalowanego zestawu Windows SDK. Określ wersję zestawu Windows SDK, umożliwia pełny numer zestawu Windows 10 SDK takich jak **10.0.10240.0**, lub określ **8.1** korzystanie z zestawu Windows 8.1 SDK.

*vcversion*<br/>
Opcjonalnie określa zestawu narzędzi kompilatora Visual Studio do użycia. Domyślnie środowisko ustawiono Użyj bieżącego zestawu narzędzi kompilatora Visual Studio 2017 r. Użyj **-vcvars_ver = 14.0** do określenia zestawu narzędzi kompilatora Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Aby skonfigurować środowisko kompilacji w istniejących okno wiersza polecenia

1. W wierszu polecenia należy użyć polecenia CD, aby zmienić do katalogu instalacyjnego programu Visual Studio. Następnie za pomocą dysku CD ponownie zmienić podkatalog, zawierający pliki polecenia specyficzne dla konfiguracji. Dla programu Visual Studio 2017 r jest podkatalog VC\Auxiliary\Build. Dla programu Visual Studio 2015 Użyj podkatalogu VC.

1. Wprowadź polecenie dla danego środowiska dewelopera preferowany. Na przykład kompilacji kodu ARM dla platformy uniwersalnej systemu Windows w 64-bitowej platformy przy użyciu najnowszej wersji zestawu Windows SDK i zestawu narzędzi kompilatora Visual Studio 2017 RTM, należy użyć ten wiersz polecenia:

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>Tworzenie własnych skrótów wiersza polecenia

Po otwarciu okna dialogowego właściwości dla jednego z istniejących skrótów wiersza polecenia dewelopera widać elemencie docelowym polecenia używane. Na przykład element docelowy dla **x64 natywnego narzędzia wiersza polecenia VS 2017** skrót jest polecenie podobne do następującego:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

Ustaw pliki wsadowe architektury *architektura* vcvarsall.bat parametr i wywołania. Jako użytkownik przejdzie do vcvarsall.bat, albo można po prostu Wywołaj vcvarsall.bat bezpośrednio do tych plików wsadowych można przekazać te same opcje dodatkowe. Aby określić parametry skrótu polecenia, należy je dodać do końca polecenia w cudzysłów podwójny. Na przykład aby skonfigurować skrót do kompilacji kodu ARM dla platformy uniwersalnej systemu Windows w 64-bitowej platformy przy użyciu najnowszej wersji zestawu Windows SDK i narzędzi kompilatora Visual Studio 2017 RTM użyć przypominać ten element docelowy polecenia w nim:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

Należy zmienić ścieżkę do uwzględnienia w katalogu instalacji programu Visual Studio.

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia

Aby utworzyć projekt C/C++ w wierszu polecenia, program Visual Studio udostępnia te narzędzia wiersza polecenia:

[CL](../build/reference/compiling-a-c-cpp-program.md)<br/>
Kompilator (cl.exe) umożliwia kompilowanie i łączenie plików kodu źródłowego w aplikacji, biblioteki i bibliotek DLL.

[Link](../build/reference/linking.md)<br/>
Konsolidator (link.exe) umożliwia łączenie plików skompilowanych obiektów i bibliotek w aplikacji i bibliotek DLL.

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Użyj programu MSBuild (msbuild.exe) do tworzenia projektów Visual C++ i rozwiązania Visual Studio. Jest to równoważne uruchomiona **kompilacji** projektu lub **Kompiluj rozwiązanie** w środowisku IDE programu Visual Studio.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Użyj DEVENV (devenv.exe) połączonych z przełącznikiem wiersza polecenia — na przykład **/Build** lub **/Clean**— do wykonania niektórych kompilacji polecenia bez wyświetlania środowiska IDE programu Visual Studio.

[NMAKE](../build/nmake-reference.md)<br/>
Umożliwia automatyzację zadań, które kompilacji projektów Visual C++ przy użyciu tradycyjnych pliku reguł programu make NMAKE (nmake.exe).

Podczas kompilowania w wierszu polecenia polecenie F1 nie jest dostępna dla natychmiastowa pomoc. Zamiast tego można uzyskać informacje na temat ostrzeżenia, błędy i komunikaty, aparat wyszukiwania lub skorzystać pliki pomocy w trybie offline. Aby użyć funkcji wyszukiwania w [docs.microsoft.com](https://docs.microsoft.com/cpp/), wprowadź ciąg wyszukiwania w polu wyszukiwania w górnej części strony.

## <a name="in-this-section"></a>W tej sekcji

Artykuły w tej sekcji dokumentacji pokazują, jak tworzyć aplikacje w wierszu polecenia, opisano sposób dostosowywania środowiska kompilacji wiersza polecenia, użyj procesami 64-bitowe i docelowej x86, x64, ARM platform i pokazują, jak używać kompilacji wiersza polecenia narzędzia MSBuild i NMAKE.

[Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Podaje przykład pokazujący sposób tworzenia i skompilować prosty program w języku C++ w wierszu polecenia.

[Wskazówki: Kompilowanie programu C w wierszu polecenia](../build/walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Opisuje sposób kompilowania program napisany w języku programowania C.

[Przewodnik: kompilowanie programu w języku C++/CLI w wierszu polecenia](../build/walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Opisuje sposób tworzenia i skompilować C + +/ CLI program, który używa programu .NET Framework.

[Przewodnik: kompilowanie programu w języku C++/CX w wierszu polecenia](../build/walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Opisuje sposób tworzenia i skompilować C + +/ CX program, który używa środowiska wykonawczego systemu Windows.

[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](../build/setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Opisuje sposób uruchamiania okno wiersza polecenia, zawierający zmienne środowiskowe wymagane dla kompilacji z wiersza polecenia kierowanych x86, x64 oraz ARM przy użyciu 32-bitowy lub 64-bitowego zestawu narzędzi platformy.

[NMAKE — dokumentacja](../build/nmake-reference.md)<br/>
Zawiera łącza do artykułów, które opisują Program obsługi narzędzie Microsoft (NMAKE. WYWOŁANIE PLIKU EXE).

[MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)<br/>
Zawiera łącza do artykułów, które omówiono sposób użycia MSBuild.EXE.

## <a name="related-sections"></a>Sekcje pokrewne

[/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](../build/reference/md-mt-ld-use-run-time-library.md)<br/>
Opisuje sposób korzystać z tych opcji kompilatora przy użyciu biblioteki wykonawcze debugowania i wydania.

[Opcje kompilatora C/C++](../build/reference/compiler-options.md)<br/>
Zawiera łącza do artykułów, które opcje kompilatora C i C++ i CL.exe.

[Opcje konsolidatora](../build/reference/linker-options.md)<br/>
Zawiera łącza do artykułów, które opcje konsolidatora i LINK.exe.

[Narzędzia kompilacji C/C++](../build/reference/c-cpp-build-tools.md)<br/>
Zawiera łącza do C/C++ kompilacji narzędzia, które są uwzględniane w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

[Kompilowanie programów C/C++](../build/building-c-cpp-programs.md)