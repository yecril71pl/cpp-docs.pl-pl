---
title: Korzystanie z programu Microsoft C++ zestaw narzędzi z wiersza polecenia
description: Za pomocą łańcucha narzędzi kompilatora C++ firmy Microsoft (MSVC) z wiersza polecenia, poza Visual Studio IDE.
ms.custom: conceptual
ms.date: 06/06/2019
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: b5e9bf266d79ee86cae84535641a52c7c52be391
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821141"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Korzystanie z programu Microsoft C++ zestaw narzędzi z wiersza polecenia

Możesz tworzyć aplikacje C i C++, w wierszu polecenia, za pomocą narzędzi, które znajdują się w programie Visual Studio. Microsoft C++ zestaw narzędzi kompilatora (MSVC) jest również dostępny do pobrania jako autonomiczny pakiet z [program Visual Studio pobiera](https://visualstudio.microsoft.com/downloads/) strony. Tego część **Build Tools for Visual Studio** pakietu. Można wybrać pobrać narzędzia niezbędne do C++ rozwoju.

## <a name="how-to-use-the-command-line-tools"></a>Jak używać narzędzi wiersza polecenia

Po wybraniu obciążenia języka C++ w Instalatorze programu Visual Studio program Visual Studio *zestawu narzędzi platformy*. Zestaw narzędzi platformy ma wszystkie C i C++ narzędzi dla określonej wersji programu Visual Studio. Narzędzia te obejmują C /C++ kompilatory, wiązania i asemblerów oraz inne narzędzia do kompilacji i zgodnych bibliotek. W wierszu polecenia, można użyć wszystkich tych narzędzi. Są one także używane wewnętrznie środowiska IDE programu Visual Studio. Istnieją osobne kompilatory hostowanych x86 i hostowane x64 i narzędzia do tworzenia kodu dla x86 x 64, ARM i ARM64 elementów docelowych. Każdy zestaw narzędzi dla określonej architektury kompilacji źródłowa i docelowa są przechowywane w katalogu swój własny.

Do prawidłowego działania narzędzia wymaga kilku określonych zmiennych środowiskowych do skonfigurowania. Te zmienne są używane do dodawania narzędzia do ścieżki i ustawienie obejmują plik, biblioteki i lokalizacje zestawów SDK. Ułatwia do ustawiania tych zmiennych środowiskowych, Instalator tworzy niestandardowe *pliki poleceń*, lub wsadowe pliki, podczas instalacji. Możesz uruchomić jeden z tych plików polecenie, aby ustawić konkretnego hosta i architektury kompilacji docelowej, wersja zestawu Windows SDK i narzędzi platformy. Dla wygody Instalator tworzy skróty w Start menu. Skróty Uruchom wiersz polecenia dla deweloperów w systemie windows przy użyciu tych plików poleceń dla określonej kombinacji źródłowa i docelowa. Poniższe skróty upewnij się, że wszystkie zmienne środowiskowe wymagane są ustawione i gotowe do użycia.

Zmienne środowiskowe wymagane są określone, do instalacji i architektury kompilacji, który wybierzesz. Również one mogą zostać zmienione przez uaktualnienia i aktualizacje produktów. Dlatego zaleca się przy użyciu pliku polecenie lub skrótu zainstalowany wiersz polecenia, zamiast ustawienia zmiennych środowiskowych, samodzielnie. Aby uzyskać więcej informacji, zobacz [Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md).

Zestawy narzędzi, pliki poleceń i skróty zainstalowane są zależne od procesor komputera i opcji wybranych podczas instalacji. Narzędzia hostowane x86 i wielu narzędzi, które kompilowanie x86 i x64 kodu są zawsze instalowane. W przypadku 64-bitowych Windows narzędzi hostowanych x64 oraz wielu narzędzi, które kompilowanie kodu x86 i x64 są również instalowane. Jeśli zdecydujesz się opcjonalny C++ Universal Windows Platform tools, a następnie x86 i x64 narzędzia, które kompilowanie kodu ARM i ARM64 również zainstalowane. Inne obciążenia mogą instalować dodatkowe narzędzia.

## <a name="developer_command_prompt_shortcuts"></a> Skróty wiersza polecenia dla deweloperów

Skróty wiersza polecenia są instalowane w folderze specyficzny dla wersji programu Visual Studio w Start menu. Poniżej przedstawiono listę skrótów podstawowy wiersza polecenia i architektur kompilacji, które obsługują:

- **Wiersz polecenia dla deweloperów** -ustawia środowisko do korzystania z 32-bitowy, macierzysty x86 narzędzia do kompilowania kodu 32-bitowy, macierzysty x86.
- **x86 natywnych wiersz polecenia narzędzi** -ustawia środowisko do korzystania z 32-bitowy, macierzysty x86 narzędzia do kompilowania kodu 32-bitowy, macierzysty x86.
- **x64 natywnych wiersz polecenia narzędzi** -ustawia środowisko do korzystania z 64-bitowych, x64 natywnych narzędzi do kompilowania kodu 64-bitowy, macierzysty x64.
- **Wiersz polecenia narzędzi x86_x64 Cross** -ustawia środowisko do korzystania z 32-bitowy, macierzysty x86 narzędzia do kompilowania kodu 64-bitowy, macierzysty x64.
- **Wiersz polecenia narzędzi x64_x86 Cross** -ustawia środowisko do korzystania z 64-bitowych, x64 natywnych narzędzi do kompilowania kodu 32-bitowy, macierzysty x86.

::: moniker range=">= vs-2019"

Nazwy folderu oraz skrót menu Start zależy od zainstalowanej wersji programu Visual Studio. Jeśli ustawisz jeden mogą także zależeć od instalacji **pseudonim**. Na przykład, załóżmy, że został zainstalowany program Visual Studio 2019 r i nadać mu pseudonim *najnowsze*. Skrót do wiersza polecenia dla deweloperów nosi nazwę **wiersz polecenia programisty dla programu VS (Najnowsza wersja) 2019 r**, w folderze o nazwie **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Nazwy folderu oraz skrót menu Start zależy od zainstalowanej wersji programu Visual Studio. Jeśli ustawisz jeden mogą także zależeć od instalacji **pseudonim**. Na przykład, załóżmy, że został zainstalowany program Visual Studio 2017 i nadać mu pseudonim *najnowsze*. Skrót do wiersza polecenia dla deweloperów nosi nazwę **wiersz polecenia programisty dla programu VS 2017 (Najnowsza wersja)** , w folderze o nazwie **programu Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Nazwy folderu oraz skrót menu Start zależy od zainstalowanej wersji programu Visual Studio. Na przykład załóżmy, że zainstalowano program Visual Studio 2015. Skrót do wiersza polecenia dla deweloperów nosi nazwę **wiersz polecenia programisty dla programu VS 2015**.

::: moniker-end

## <a name="developer_command_prompt"></a> Aby otworzyć okno wiersza polecenia dla deweloperów

1. Na pulpicie otwórz Windows **Start** menu, a następnie przewiń, aby znaleźć i otworzyć folder dla używanej wersji programu Visual Studio, na przykład **Visual Studio 2019**.

1. W folderze, wybierz **wiersz polecenia dla deweloperów** dla używanej wersji programu Visual Studio. Ten skrót uruchamia okno wiersza polecenia dewelopera, który korzysta z architektury kompilacji domyślnej, 32-bitowy, x86 natywnych narzędzi do kompilowania kodu 32-bitowy, macierzysty x86. Jeśli wolisz architektury kompilacji innych niż domyślne, wybierz jedną z natywnym lub wielu narzędzi wiersz polecenia, aby określić architektury źródłowa i docelowa.

Szybszy sposób otworzyć wiersz polecenia dla deweloperów, wprowadź *wiersz polecenia dla deweloperów* w polu wyszukiwania na pulpicie. Następnie wybierz żądanych wyników.

## <a name="developer_command_file_locations"></a> Lokalizacje pliku polecenia dla deweloperów

Jeśli wolisz skonfigurować środowisko budowania w istniejącym oknie wiersza polecenia, można użyć jednego z plików polecenia utworzony przez Instalatora. Zaleca się, że ustawisz środowisko w nowym oknie wiersza polecenia. Nie zalecamy nowsze Przełącz środowiska, w tym samym oknie wiersza polecenia.

::: moniker range=">= vs-2019"

Lokalizacja pliku polecenia zależy od wersji programu Visual Studio został zainstalowany oraz od opcji wybranych podczas instalacji. Dla programu Visual Studio 2019 r, typowej instalacji w systemie 64-bitowych znajduje się w \\Program Files (x86)\\programu Microsoft Visual Studio\\2019\\*wersji*. *Wersja* może być Community, Professional, Enterprise, BuildTools lub innego pseudonim wprowadzone.

::: moniker-end
::: moniker range="= vs-2017"

Lokalizacja pliku polecenia zależy od wersji programu Visual Studio został zainstalowany oraz od opcji wybranych podczas instalacji. Dla programu Visual Studio 2017, typowej instalacji w systemie 64-bitowych znajduje się w \\Program Files (x86)\\programu Microsoft Visual Studio\\2017\\*wersji*. *Wersja* może być Community, Professional, Enterprise, BuildTools lub innego pseudonim wprowadzone.

::: moniker-end
::: moniker range="< vs-2017"

Lokalizacja pliku polecenia zależy od wersji programu Visual Studio i w katalogu instalacyjnym. Dla programu Visual Studio 2015 typowej instalacji znajduje się w \\Program Files (x86)\\programu Microsoft Visual Studio 14.0.

::: moniker-end

Plik polecenia wiersza polecenia głównego dewelopera, VsDevCmd.bat, znajduje się w Common7\\podkatalogu narzędzia. Nie określono żadnych parametrów, ustawia środowisko pod kątem użycia x86 natywnych narzędzi do tworzenia x86 32-bitowego kodu.

::: moniker range=">= vs-2017"

Więcej plików polecenia są dostępne do skonfigurowania architektury konkretnej kompilacji. Dostępne pliki poleceń są zależne od pakiety robocze programu Visual Studio i opcji, którą zainstalowałeś. W programie Visual Studio 2017 i Visual Studio 2019 r znajdziesz je w VC\\pomocnicze\\Tworzenie podkatalogu.

::: moniker-end
::: moniker range="< vs-2017"

Więcej plików polecenia są dostępne do skonfigurowania architektury konkretnej kompilacji. Dostępne pliki poleceń są zależne od pakiety robocze programu Visual Studio i opcji, którą zainstalowałeś. W programie Visual Studio 2015, znajdują się one w VC VC\\bin lub VC\\bin\\*architektury* podkatalogi, gdzie *architektury* jest jednym z natywnych lub Kompilator krzyżowy opcje.

::: moniker-end

Te pliki poleceń Ustawianie parametrów domyślnych i wywołuj VsDevCmd.bat, aby skonfigurować środowisko architektury określonej kompilacji. Typowej instalacji mogą zawierać te pliki poleceń:

|Plik polecenia|Źródłowa i docelowa architektury|
|---|---|
|**vcvars32.bat**| Narzędzia do kompilacji x86 32-bitowych x86 natywne 32-bitowego kodu.|
|**vcvars64.bat**| Narzędzia do kompilacji x64 64-bitowych x64 natywnych 64-bitowego kodu.|
|**vcvarsx86_amd64.bat**| Tworzenie x64 64-bitowych za pomocą narzędzi między x86 natywne 32-bitowy kod.|
|**vcvarsamd64_x86.bat**| Kompilacji x86 32-bitowego za pomocą narzędzi między x64 natywnych 64-bitowego kodu.|
|**vcvarsx86_arm.bat**| Użyj narzędzia między x86 natywne 32-bitowy do kompilowania kodu ARM.|
|**vcvarsamd64_arm.bat**| Narzędzia 64-bitowego natywnego x64 krzyżowego do kompilowania kodu ARM.|
|**vcvarsall.bat**| Użyj parametrów, aby określić architektury źródłowa i docelowa zestawu Windows SDK i możliwości platformy. Aby uzyskać listę obsługiwanych opcji wywoływanie za pomocą **/help** parametru.|

> [!CAUTION]
> Plik vcvarsall.bat i inne pliki poleceń programu Visual Studio może się różnić między komputerami. Zastępuje uszkodzony lub plik vcvarsall.bat przy użyciu pliku z innego komputera. Uruchom ponownie Instalatora programu Visual Studio, aby zastąpić brakujący plik.
>
> Plik vcvarsall.bat również różni się od wersji. Jeśli bieżącą wersję programu Visual Studio jest zainstalowany na komputerze, który ma także wcześniejszej wersji programu Visual Studio, nie należy uruchamiać vcvarsall.bat lub inny plik polecenia programu Visual Studio z różnych wersji, w tym samym oknie wiersza polecenia.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Korzystaj z narzędzi deweloperskich w istniejącym oknie polecenia

Jest to najprostszy sposób określić architektury konkretnej kompilacji w istniejącym oknie polecenia przy użyciu pliku vcvarsall.bat. Użyć vcvarsall.bat do ustawiania zmiennych środowiskowych, aby skonfigurować wiersz polecenia dla natywnej kompilacji 32-bitową lub 64-bitowych. Argumenty umożliwiają określenie kompilacji do x86 x 64, ARM, lub procesorów ARM64. Można kierować platformy Microsoft Store, Universal Windows Platform lub Windows Desktop. Można również określić, które zestaw Windows SDK ma używać i wybierz wersję zestawu narzędzi platformy.

Gdy jest używana bez argumentów, vcvarsall.bat konfiguruje zmienne środowiskowe na potrzeby bieżącego kompilatora x86 natywne 32-bitowa Windows Desktop cele. Można dodawać argumenty, aby skonfigurować środowisko pod kątem użycia, wszystkie macierzyste lub cross tools kompilatora. vcvarsall.bat wyświetli komunikat o błędzie, jeśli określisz konfigurację, która nie jest zainstalowany lub jest dostępny na komputerze.

### <a name="vcvarsall-syntax"></a>Składnia vcvarsall

> **vcvarsall.bat** [*architecture*] [*platform_type*] [*winsdk_version*] [ **-vcvars_ver=** _vcversion_]

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
Opcjonalnie określa zestaw narzędzi kompilatora Visual Studio do użycia. Domyślnie środowisko ustawiono użycie bieżącego zestawu narzędzi kompilatora Visual Studio.

::: moniker range=">= vs-2019"

Użyj **-vcvars_ver = 14.2 x .yyyyy** do określenia określoną wersję zestawu narzędzi kompilatora Visual Studio 2019 r.

Użyj **-vcvars_ver = 14.16** do określenia najnowszej wersji zestawu narzędzi kompilatora Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Użyj **-vcvars_ver = 14.16** do określenia najnowszej wersji zestawu narzędzi kompilatora Visual Studio 2017.

Użyj **-vcvars_ver = 14.1 x .yyyyy** do określenia określoną wersję zestawu narzędzi kompilatora Visual Studio 2017.

::: moniker-end

Użyj **-vcvars_ver = 14.0** określić zestaw narzędzi kompilatora Visual Studio 2015.

<a name="vcvarsall"></a>
#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a>Aby skonfigurować środowisko kompilacji w istniejącym oknie wiersza polecenia

1. W wierszu polecenia należy użyć polecenia CD, aby zmienić do katalogu instalacyjnego programu Visual Studio. Następnie należy użyć dysku CD ponownie zmienić w podkatalogu, który zawiera pliki poleceń specyficznych dla konfiguracji. W przypadku 2019 usługi Visual Studio i Visual Studio 2017, użyj *VC\\pomocnicze\\kompilacji* podkatalogu. W przypadku programu Visual Studio 2015, użyj *VC* podkatalogu.

1. Wprowadź polecenie w środowisku preferowanych dla deweloperów. Na przykład podczas tworzenia kodu ARM dla platformy uniwersalnej systemu Windows na platformie 64-bitowego za pomocą najnowszy zestaw Windows SDK i programu Visual Studio zestaw narzędzi kompilatora, należy użyć ten wiersz polecenia:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Tworzenie własnych skrót do wiersza polecenia

::: moniker range=">= vs-2019"

Otwórz okno dialogowe właściwości skrót do wiersza polecenia dla deweloperów wyświetlić element docelowy polecenia używane. Na przykład, obiekt docelowy **x64 natywnych wiersz polecenia narzędzi dla programu VS 2019** skrót jest podobny do:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Otwórz okno dialogowe właściwości skrót do wiersza polecenia dla deweloperów wyświetlić element docelowy polecenia używane. Na przykład, obiekt docelowy **x64 natywnych narzędzi wiersza polecenia dla programu VS 2017** skrót jest podobny do:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Otwórz okno dialogowe właściwości skrót do wiersza polecenia dla deweloperów wyświetlić element docelowy polecenia używane. Na przykład, obiekt docelowy **VS2015 x64 natywnych wiersz polecenia narzędzi** skrót jest podobny do:

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64`

::: moniker-end

Ustaw pliki wsadowe architektury *architektury* vcvarsall.bat parametr i wywołania. Można przekazać te same opcje do tych plików usługi batch, należy wprowadzić do vcvarsall.bat lub może po prostu wywołać vcvarsall.bat bezpośrednio. Aby określić parametry skrótu polecenia, należy dodać je na końcu polecenia w podwójne cudzysłowy. Na przykład w tym miejscu to skrót do kompilowania kodu ARM dla platformy uniwersalnej systemu Windows na platformie 64-bitowego za pomocą najnowszy zestaw Windows SDK. Aby użyć wcześniej zestaw narzędzi kompilatora, określ numer wersji. Użyj podobny do tego obiektu docelowego polecenia w nim:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.16"`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat amd64_arm uwp -vcvars_ver=14.0"`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k ""C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat"" amd64 -vcvars_ver=12.0`

::: moniker-end

Dostosuj ścieżkę, aby odzwierciedlała katalogu instalacji programu Visual Studio. Plik vcvarsall.bat zawiera dodatkowe informacje na temat numery określonej wersji.

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia

Do kompilacji C /C++ projektu w wierszu polecenia programu Visual Studio udostępnia te narzędzia wiersza polecenia:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Aby skompilować i połączyć pliki kodu źródłowego aplikacji, bibliotek i bibliotek DLL, należy użyć kompilatora (cl.exe).

[Link](reference/linking.md)<br/>
Usługa łączący (link.exe) umożliwia łączenie pliki skompilowanych obiektów i bibliotek, aplikacji i bibliotek DLL.

[MSBuild](msbuild-visual-cpp.md)<br/>
Do konfigurowania kompilacji i pośrednio wywołania zestawu narzędzi, należy użyć programu MSBuild (msbuild.exe) i plik projektu (.vcxproj). Jest to równoważne do uruchomione **kompilacji** projektu lub **Kompiluj rozwiązanie** polecenia w środowisku IDE programu Visual Studio. Uruchamianie programu MSBuild z wiersza polecenia to zaawansowany scenariusz i nie często jest to zalecane.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Użyj DEVENV (devenv.exe) w połączeniu z przełącznikiem wiersza polecenia takich jak **/Build** lub **/Clean** do wykonania niektórych tworzenia poleceń bez wyświetlania środowiska IDE programu Visual Studio. Ogólnie rzecz biorąc DEVENV jest preferowany korzystanie z programu MSBuild bezpośrednio, ponieważ można pozwolić, aby obsłużyć komplikacje związane z programu MSBuild z programu Visual Studio.

[NMAKE](reference/nmake-reference.md)<br/>
Użyj NMAKE (nmake.exe) na Windows do tworzenia projektów C++ opartych na tradycyjnych pliku reguł programu make.

Podczas kompilowania w wierszu polecenia polecenie F1 jest niedostępna dla natychmiastowa pomoc. Zamiast tego można użyć aparatu wyszukiwania, aby uzyskać informacje na temat ostrzeżenia, błędy i komunikaty lub możesz użyć plików pomocy w trybie offline. Aby użyć wyszukiwania w [docs.microsoft.com](https://docs.microsoft.com/cpp/), użyj pola wyszukiwania w górnej części strony.

## <a name="in-this-section"></a>W tej sekcji

Następujące artykuły pokazują, jak tworzyć aplikacje w wierszu polecenia i opisano sposób dostosowywania środowiska kompilacji wiersza polecenia. Niektóre pokazują, jak używać 64-bitowych zestawy narzędzi i określania elementów docelowych x86 x 64, ARM, ARM64 platformy i. Zawierają one również opis korzystania z narzędzi wiersza polecenia kompilacji MSBuild i NMAKE.

[Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Zapewnia przykładowi, który pokazuje, jak utworzyć i skompilować C++ programu w wierszu polecenia.

[Przewodnik: Kompilowanie programu C w wierszu polecenia](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
W tym artykule opisano sposób kompilowania program napisany w języku programowania C.

[Przewodnik: kompilowanie programu w języku C++/CLI w wierszu polecenia](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
W tym artykule opisano sposób tworzenia i skompilować C++sposób niezamierzony program, który używa .NET Framework.

[Przewodnik: kompilowanie programu w języku C++/CX w wierszu polecenia](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
W tym artykule opisano sposób tworzenia i skompilować C++/CX program, który używa środowiska wykonawczego Windows.

[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Jak ustawić zmienne środowiskowe można użyć 32-bitową lub 64-bitowego zestawu narzędzi do obiektu docelowego x86, x64, ARM, ARM64 platformy i.

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
