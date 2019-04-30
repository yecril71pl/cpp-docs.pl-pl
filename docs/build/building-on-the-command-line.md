---
title: Możesz używać zestawu narzędzi MSVC z wiersza polecenia — Visual Studio
description: Za pomocą łańcucha narzędzi kompilatora C++ firmy Microsoft (MSVC) z wiersza polecenia, poza Visual Studio IDE.
ms.custom: conceptual
ms.date: 12/10/2018
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 21d1c9063a1d6dd154de8d2caca913ea3fd0ce37
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342159"
---
# <a name="use-the-msvc-toolset-from-the-command-line"></a>Możesz używać zestawu narzędzi MSVC z wiersza polecenia

Możesz tworzyć aplikacje C i C++, w wierszu polecenia, za pomocą narzędzi, które znajdują się w programie Visual Studio. Możesz również pobrać zestaw narzędzi kompilatora jako autonomiczny pakiet z [Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721).

## <a name="how-to-use-the-command-line-tools"></a>Jak używać narzędzi wiersza polecenia

Po wybraniu obciążenia języka C++ w Instalatorze programu Visual Studio program Visual Studio *zestawu narzędzi platformy*. Zestaw narzędzi platformy oferuje narzędzia do C i C++ dla określonej wersji programu Visual Studio, w tym Kompilatory języka C/C++, wiązania, asemblerów i inne narzędzia do kompilacji, a także zgodnych bibliotek. Możliwość używania wszystkich tych narzędzi w wierszu polecenia, a następnie są one także używane wewnętrznie przez program Visual Studio IDE. Istnieją osobne hostowanych x86 i hostowane x64 kompilatory i narzędzia do kompilowania kodu dla x86 x 64, ARM i elementów docelowych architektury ARM64. Każdy zestaw narzędzi dla określonej architektury kompilacji źródłowa i docelowa są przechowywane w katalogu swój własny.

Zestawy narzędzi kompilatora, które są zainstalowane, zależą od procesor komputera i opcji wybranych podczas instalacji. Co najmniej 32-bitowy hostowany x86 kompilacji kodu x86 natywne 32-bitowego, które obejmujące wiele narzędzi, które kompilacji kodu x64 natywnych 64-bitowego są zainstalowane narzędzia. Jeśli masz Windows 64-bitowych, instalowane są również narzędzi hostowanych x64 64-bitowych, które tworzenie kodu natywnego 64-bitowych oraz wielu narzędzi, które są kompilowane w 32-bitowego kodu natywnego. Jeśli zdecydujesz się zainstalować opcjonalnych narzędzi C++ Universal Windows Platform, narzędzi natywne 32-bitowych i 64-bitowych, które kompilowanie kodu ARM również są instalowane. Inne obciążenia mogą instalować dodatkowe narzędzia.

## <a name="environment-variables-and-developer-command-prompts"></a>Zmienne środowiskowe i wiersz polecenia dla deweloperów

Do prawidłowego działania narzędzia wymaga kilku określonych zmiennych środowiskowych do skonfigurowania. Są one używane, aby dodać je do ścieżki i ustawienie zawierają plik, biblioteki i lokalizacje zestawów SDK. Ułatwia do ustawiania tych zmiennych środowiskowych, Instalator tworzy niestandardowe *pliki poleceń*, lub wsadowe pliki, podczas instalacji. Jeden z tych plików polecenia można uruchomić w oknie wiersza polecenia, aby ustawić konkretnego hosta i architektury kompilacji docelowej, wersja zestawu Windows SDK, platformy docelowej i zestawu narzędzi platformy. Dla wygody Instalator tworzy skróty w menu Start rozpoczęcia okna wiersza polecenia dla deweloperów przy użyciu tych plików poleceń, więc wszystkie zmienne środowiskowe wymagane są ustawione i gotowe do użycia.

Zmienne środowiskowe wymagane są określone, do instalacji i architektura kompilacji, wybierz i może ulec zmianie, uaktualnienia i aktualizacje produktów. Dlatego zdecydowanie zaleca się używać skróty zainstalowany wiersz polecenia lub pliki poleceń zamiast ustawienia zmiennych środowiskowych w Windows samodzielnie. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md).

## <a name="developer_command_prompt_shortcuts"></a> Skróty wiersza polecenia dla deweloperów

Skróty wiersza polecenia są instalowane w folderze specyficzny dla wersji programu Visual Studio w Start menu. Poniżej przedstawiono listę skrótów podstawowy wiersza polecenia i architektur kompilacji, które obsługują:

- **Wiersz polecenia dla deweloperów** -ustawia środowisko do korzystania z 32-bitowy, macierzysty x86 narzędzia do kompilowania kodu 32-bitowy, macierzysty x86.
- **x86 natywnych wiersz polecenia narzędzi** -ustawia środowisko do korzystania z 32-bitowy, macierzysty x86 narzędzia do kompilowania kodu 32-bitowy, macierzysty x86.
- **x64 natywnych wiersz polecenia narzędzi** -ustawia środowisko do korzystania z 64-bitowych, x64 natywnych narzędzi do kompilowania kodu 64-bitowy, macierzysty x64.
- **Wiersz polecenia narzędzi x86_x64 Cross** -ustawia środowisko do korzystania z 32-bitowy, macierzysty x86 narzędzia do kompilowania kodu 64-bitowy, macierzysty x64.
- **Wiersz polecenia narzędzi x64_x86 Cross** -ustawia środowisko do korzystania z 64-bitowych, x64 natywnych narzędzi do kompilowania kodu 32-bitowy, macierzysty x86.

Rzeczywiste Start menu folderu i skrót nazwy różnią się w zależności od wersji programu Visual Studio został zainstalowany i instalacja pseudonim, jeśli zostanie ustawiona. Na przykład, jeśli masz program Visual Studio 2017, a został podany jej instalacji pseudonim *Podgląd*, nosi nazwę skrót do wiersza polecenia dla deweloperów **wiersz polecenia programisty dla programu VS 2017 (wersja zapoznawcza)**, w folderze o nazwie **programu Visual Studio 2017**.

Jeśli po zainstalowaniu [Build Tools for Visual Studio 2017](https://go.microsoft.com/fwlink/p/?linkid=875721) (który zawiera również zestaw narzędzi kompilatora Visual Studio 2015 Update 3), tylko natywne architektury lub dla wielu narzędzi wiersza polecenia dla deweloperów, opcje są zainstalowane , a nie ogólny **wiersz polecenia dla deweloperów** skrótów.

## <a name="developer_command_prompt"></a> Aby otworzyć okno wiersza polecenia dla deweloperów

1. Na pulpicie otwórz Windows **Start** menu, a następnie przewiń, aby znaleźć i otworzyć folder dla używanej wersji programu Visual Studio, na przykład **programu Visual Studio 2017**. W niektórych starszych wersjach programu Visual Studio, skróty znajdują się w podfolderze o nazwie **Visual Studio Tools**.

1. W folderze, wybierz **wiersz polecenia dla deweloperów** dla używanej wersji programu Visual Studio. Ten skrót uruchamia okno wiersza polecenia dewelopera, który korzysta z architektury kompilacji domyślnej, 32-bitowy, x86 natywnych narzędzi do kompilowania kodu 32-bitowy, macierzysty x86. Jeśli wolisz architektury kompilacji innych niż domyślne, wybierz jedną z natywnym lub wielu narzędzi wiersz polecenia, aby określić architektury źródłowa i docelowa.

Szybszy sposób, aby otworzyć okno wiersza polecenia dewelopera polega na przejściu *wiersz polecenia dla deweloperów* w polu wyszukiwania na pulpicie, a następnie wybierz żądany wynik.

## <a name="developer_command_file_locations"></a> Lokalizacje pliku polecenia dla deweloperów

Jeśli wolisz skonfigurować środowisku architektury kompilacji w istniejącym oknie wiersza polecenia, można użyć jednego z poleceń (pliki wsadowe) utworzony przez Instalatora można ustawić wymagane środowisko. Zalecane tylko można to zrobić w nowym oknie wiersza polecenia i nie zalecamy nowsze Przełącz środowiska, w tym samym oknie wiersza polecenia. Lokalizacja tych plików zależy od wersji programu Visual Studio został zainstalowany oraz lokalizacji i opcji nazewnictwa, wprowadzone podczas instalacji. Dla programu Visual Studio 2017, typowej instalacji na komputerze 64-bitowym znajduje się w \Program pliki (x86) \Microsoft Visual Studio\2017\\*wersji*, gdzie *wersji* może być społeczności Professional, Enterprise, BuildTools lub innego o podanej nazwie. Dla programu Visual Studio 2015 lokalizacja typowej instalacji znajduje się w \Program Files (x86) \Microsoft Visual Studio 14.0.

Plik polecenia wiersza polecenia głównego dewelopera, VsDevCmd.bat, znajduje się w podkatalogu Common7\Tools w katalogu instalacji. Gdy nie określono żadnych parametrów, to ustawienie środowiska, a źródłowa i docelowa architektura, aby użyć narzędzia x86 natywne 32-bitowy do budowania x86 32-bitowych kompilacji kodu.

Pliki dodatkowe polecenia są dostępne do skonfigurowania architektury konkretnej kompilacji, w zależności od architektury procesora i obciążeń programu Visual Studio i opcje, które zostały zainstalowane. W programie Visual Studio 2017 te znajdują się w podkatalogu VC\Auxiliary\Build katalogu instalacyjnego programu Visual Studio. W programie Visual Studio 2015, te znajdują się w VC, VC\bin lub VC\bin\\*architektury* podkatalogi katalogu instalacyjnego, gdzie *architektury* jest jednym z natywnych lub Kompilator krzyżowy opcje. Te pliki poleceń Ustawianie parametrów domyślnych i wywołuj VsDevCmd.bat, aby skonfigurować środowisko architektury określonej kompilacji. Typowej instalacji mogą zawierać te pliki poleceń:

|Plik polecenia|Źródłowa i docelowa architektury|
|---|---|
|**vcvars32.bat**| Narzędzia do kompilacji x86 32-bitowych x86 natywne 32-bitowego kodu.|
|**vcvars64.bat**| Narzędzia do kompilacji x64 64-bitowych x64 natywnych 64-bitowego kodu.|
|**vcvarsx86_amd64.bat**| Tworzenie x64 64-bitowych za pomocą narzędzi między x86 natywne 32-bitowy kod.|
|**vcvarsamd64_x86.bat**| Kompilacji x86 32-bitowego za pomocą narzędzi między x64 natywnych 64-bitowego kodu.|
|**vcvarsx86_arm.bat**| Użyj narzędzia między x86 natywne 32-bitowy do kompilowania kodu ARM.|
|**vcvarsamd64_arm.bat**| Narzędzia 64-bitowego natywnego x64 krzyżowego do kompilowania kodu ARM.|
|**vcvarsall.bat**| Użyj parametrów, aby określić hosta i docelowych architektur, jak również opcje zestawu SDK i platform. Aby uzyskać listę obsługiwanych opcji wywoływanie za pomocą **/help** parametru.|

> [!CAUTION]
> Plik vcvarsall.bat i inne pliki poleceń programu Visual Studio może się różnić między komputerami. Zastępuje uszkodzony lub plik vcvarsall.bat przy użyciu pliku z innego komputera. Uruchom ponownie Instalatora programu Visual Studio, aby zastąpić brakujący plik.
>
> Plik vcvarsall.bat również różni się od wersji. Jeśli bieżącą wersję programu Visual Studio jest zainstalowany na komputerze, który ma także wcześniejszej wersji programu Visual Studio, nie należy uruchamiać vcvarsall.bat lub inny plik polecenia programu Visual Studio z różnych wersji, w tym samym oknie wiersza polecenia.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Korzystaj z narzędzi deweloperskich w istniejącym oknie polecenia

Jest to najprostszy sposób określić architektury konkretnej kompilacji w istniejącym oknie polecenia przy użyciu pliku vcvarsall.bat. Można użyć vcvarsall.bat do ustawiania zmiennych środowiskowych, aby skonfigurować wiersza polecenia, kompilacja kodu natywnego, 32-bitową lub 64-bitowych lub kompilacji x86, x64 lub procesory ARM; pod kątem Microsoft Store, Universal Windows Platform lub platformy Windows Desktop; Aby określić, które zestaw Windows SDK ma używać; i określ wersję zestawu narzędzi platformy. Jeśli są podane żadne argumenty, vcvarsall.bat konfiguruje zmienne środowiskowe do używania bieżącej 32-bitowego natywnego kompilatora dla x86 cele pulpitu Windows. Jednak służy ona do skonfigurowania wszystkich macierzyste lub cross tools kompilatora. Jeśli określisz konfigurację kompilatora, która nie jest zainstalowany lub jest niedostępna w architekturze Twojego komputera kompilacji, jest wyświetlany komunikat o błędzie.

### <a name="vcvarsall-syntax"></a>Składnia vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver=**_vcversion_]

*Architektura*<br/>
Ten opcjonalny argument określa z architekturą źródłowa i docelowa do użycia. Jeśli *architektury* nie jest określona, używane jest domyślne środowisko kompilacji. Obsługiwane są następujące argumenty:

|*Architektura*|Kompilator|Architektura komputera hosta|Architektura obiektów wyjściowych (docelowy) kompilacji|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 natywne 32-bitowe|x86, x64|x86|
|**x86\_amd64** lub **x86\_x64**|x64 na x86 cross|x86, x64|X64|
|**x86_arm**|ARM na x86 cross|x86, x64|ARM|
|**x86_arm64**|ARM64 na x86 cross|x86, x64|ARM64|
|**AMD64** lub **x64**|x64 natywne 64-bitowe|X64|X64|
|**AMD64\_x86** lub **x64\_x86**|x86 na x64 cross|X64|x86|
|**AMD64\_ramię** lub **x64\_ramię**|ARM na x64 cross|X64|ARM|
|**AMD64\_arm64** lub **x64\_arm64**|ARM64 na x64 cross|X64|ARM64|

*platform_type*<br/>
Ten opcjonalny argument umożliwia określenie **przechowywania** lub **platformy uniwersalnej systemu Windows** jako typ platformy. Domyślnie środowisko jest ustawiona do tworzenia aplikacji pulpitu i konsoli.

*winsdk_version*<br/>
Opcjonalnie określa wersję zestawu Windows SDK do użycia. Domyślnie jest używana najnowsza wersja zainstalowanego zestawu Windows SDK. Aby określić wersję zestawu Windows SDK, można użyć pełny numer zestawu Windows 10 SDK takich jak **10.0.10240.0**, lub określ **8.1** korzystania z zestawu SDK Windows 8.1.

*vcversion*<br/>
Opcjonalnie określa zestaw narzędzi kompilatora Visual Studio do użycia. Domyślnie środowisko ustawiono użycie bieżącego zestawu narzędzi kompilatora Visual Studio 2017. Użyj **-vcvars_ver = 14.0** określić zestaw narzędzi kompilatora Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Aby skonfigurować środowisko kompilacji w istniejącym oknie wiersza polecenia

1. W wierszu polecenia należy użyć polecenia CD, aby zmienić do katalogu instalacyjnego programu Visual Studio. Następnie należy użyć dysku CD ponownie zmienić w podkatalogu, który zawiera pliki poleceń specyficznych dla konfiguracji. Dla programu Visual Studio 2017 jest podkatalog VC\Auxiliary\Build. Visual Studio 2015 można użyć w podkatalogu VC.

1. Wprowadź polecenie w środowisku preferowanych dla deweloperów. Na przykład aby skompilować kod ARM dla platformy uniwersalnej systemu Windows na platformie 64-bitowej przy użyciu najnowszy zestaw Windows SDK i zestaw narzędzi kompilatora Visual Studio 2017 RTM, należy użyć ten wiersz polecenia:

   `vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10`

## <a name="create-your-own-command-prompt-shortcut"></a>Tworzenie własnych skrót do wiersza polecenia

Jeśli możesz otworzyć okno dialogowe właściwości dla jednego z istniejących skrótów wiersza polecenia dla deweloperów, zostanie wyświetlony element docelowy polecenia używane. Na przykład, obiekt docelowy **x64 natywnych narzędzi wiersza polecenia dla programu VS 2017** skrót jest podobny do:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

Ustaw pliki wsadowe architektury *architektury* vcvarsall.bat parametr i wywołania. Można przekazać te same opcje dodatkowe do tych plików usługi batch, należy wprowadzić do vcvarsall.bat lub może po prostu wywołać vcvarsall.bat bezpośrednio. Aby określić parametry skrótu polecenia, należy dodać je na końcu polecenia w podwójne cudzysłowy. Na przykład aby skonfigurować skrót do kompilowania kodu ARM dla platformy uniwersalnej systemu Windows na platformie 64-bitowej przy użyciu najnowszy zestaw Windows SDK i zestaw narzędzi kompilatora Visual Studio 2017 RTM, użyć ciągu ten element docelowy polecenia w nim:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.10"`

Należy dostosować ścieżkę, aby odzwierciedlała katalogu instalacji programu Visual Studio.

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia

Aby utworzyć projekt języka C/C++ w wierszu polecenia, program Visual Studio udostępnia te narzędzia wiersza polecenia:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Aby skompilować i połączyć pliki kodu źródłowego aplikacji, bibliotek i bibliotek DLL, należy użyć kompilatora (cl.exe).

[Link](reference/linking.md)<br/>
Usługa łączący (link.exe) umożliwia łączenie pliki skompilowanych obiektów i bibliotek, aplikacji i bibliotek DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Do konfigurowania kompilacji i pośrednio wywołania zestawu narzędzi, należy użyć programu MSBuild (msbuild.exe) i plik projektu (.vcxproj). Jest to równoważne do uruchomione **kompilacji** projektu lub **Kompiluj rozwiązanie** polecenia w środowisku IDE programu Visual Studio. Uruchamianie programu MSBuild z wiersza polecenia to zaawansowany scenariusz i zazwyczaj nie zaleca się.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Użyj DEVENV (devenv.exe) w połączeniu z przełącznikiem wiersza polecenia — na przykład **/Build** lub **/Clean**— do wykonywania pewnych tworzenia poleceń bez wyświetlania środowiska IDE programu Visual Studio. Ogólnie rzecz biorąc to preferowane przez korzystanie z programu MSBuild bezpośrednio, ponieważ można pozwolić, aby program Visual Studio Obsługa komplikacje związane z programu MSBuild.

[NMAKE](reference/nmake-reference.md)<br/>
Użyj NMAKE (nmake.exe) na Windows do tworzenia projektów C++ opartych na tradycyjnych pliku reguł programu make.

Podczas kompilowania w wierszu polecenia polecenie F1 nie jest dostępna dla natychmiastowa pomoc. Zamiast tego można użyć aparatu wyszukiwania, aby uzyskać informacje na temat ostrzeżenia, błędy i komunikaty lub możesz użyć plików pomocy w trybie offline. Aby użyć wyszukiwania w [docs.microsoft.com](https://docs.microsoft.com/cpp/), wprowadź ciąg wyszukiwania w polu wyszukiwania w górnej części strony.

## <a name="in-this-section"></a>W tej sekcji

Artykuły w tej sekcji dokumentacji pokazano, jak tworzyć aplikacje w wierszu polecenia, opisano sposób dostosowywania środowiska kompilacji wiersza polecenia, użyj zestawy narzędzi 64-bitowych i docelowej x86, x64, platformach ARM i pokazują, jak za pomocą wiersza polecenia kompilacji narzędzia MSBuild i NMAKE.

[Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Zapewnia przykładowi, który pokazuje, jak utworzyć i skompilować prosty program w języku C++ w wierszu polecenia.

[Przewodnik: Kompilowanie programu C w wierszu polecenia](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
W tym artykule opisano sposób kompilowania program napisany w języku programowania C.

[Przewodnik: kompilowanie programu w języku C++/CLI w wierszu polecenia](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
W tym artykule opisano sposób tworzenia i skompilować C++sposób niezamierzony program, który używa .NET Framework.

[Przewodnik: kompilowanie programu w języku C++/CX w wierszu polecenia](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
W tym artykule opisano sposób tworzenia i skompilować C++/CX program, który używa środowiska wykonawczego Windows.

[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
W tym artykule opisano, jak uruchomić okno wiersza polecenia, który ma zmienne środowiskowe wymagane, ustaw dla kompilacji z wiersza polecenia, których platformą docelową x86, x64 i ARM platform przy użyciu 32-bitową lub 64-bitowego zestawu narzędzi.

[NMAKE — dokumentacja](reference/nmake-reference.md)<br/>
Oferuje łącza do artykułów, które opisują Program obsługi narzędzia Microsoft (NMAKE. Z ROZSZERZENIEM EXE).

[Program MSBuild w wierszu polecenia — C++](msbuild-visual-cpp.md)<br/>
Zawiera łącza do artykułów opisujących sposób użyć msbuild.exe w wierszu polecenia.

## <a name="related-sections"></a>Sekcje pokrewne

[/MD, /MT, /LD (Korzystaj z bibliotek wykonawczych)](reference/md-mt-ld-use-run-time-library.md)<br/>
Opisuje sposób używania tych opcji kompilatora za pomocą biblioteki wykonawczej debugowania lub wydania.

[Opcje kompilatora C/C++](reference/compiler-options.md)<br/>
Zawiera łącza do artykułów, które omówiono opcje kompilatora C i C++ i CL.exe.

[Opcje konsolidatora MSVC](reference/linker-options.md)<br/>
Zawiera łącza do artykułów, które omówiono opcje konsolidatora i LINK.exe.

[MSVC dodatkowe narzędzia do kompilacji](reference/c-cpp-build-tools.md)<br/>
Zawiera łącza do C/C++ kompilacji narzędzia, które znajdują się w programie Visual Studio.

## <a name="see-also"></a>Zobacz także

[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)