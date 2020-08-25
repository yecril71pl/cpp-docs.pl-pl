---
title: Używanie zestawu narzędzi platformy Microsoft C++ w wierszu polecenia
description: Użyj zestawu narzędzi kompilatora Microsoft C++ (MSVC) z wiersza polecenia poza środowiskiem IDE programu Visual Studio.
ms.custom: conceptual
ms.date: 04/21/2020
helpviewer_keywords:
- command-line builds [C++]
- compiling source code [C++], command line
- builds [C++], command-line
- command line [C++], building from
- command line [C++], compilers
ms.assetid: 7ca9daed-a003-4162-842d-908f79058365
ms.openlocfilehash: 1fe8e59c85e0c6b00bff4de639267a44c6ae369e
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838805"
---
# <a name="use-the-microsoft-c-toolset-from-the-command-line"></a>Używanie zestawu narzędzi platformy Microsoft C++ w wierszu polecenia

Możesz tworzyć aplikacje C i C++ w wierszu polecenia, korzystając z narzędzi zawartych w programie Visual Studio. Zestaw narzędzi kompilatora języka Microsoft C++ (MSVC) jest również pobierany jako pakiet autonomiczny. Nie musisz instalować środowiska IDE programu Visual Studio, jeśli nie planujesz go używać.

> [!NOTE]
> W tym artykule opisano sposób konfigurowania środowiska do korzystania z pojedynczych kompilatorów, linków, bibliotekarza i innych podstawowych narzędzi. Natywny system kompilacji projektu, MSBuild nie używa środowiska zgodnie z opisem w tym artykule. Aby uzyskać więcej informacji na temat korzystania z programu MSBuild z wiersza polecenia, zobacz [MSBuild w wierszu polecenia-C++](msbuild-visual-cpp.md).

## <a name="download-and-install-the-tools"></a>Pobieranie i Instalowanie narzędzi

Jeśli zainstalowano program Visual Studio i obciążenie języka C++, masz wszystkie narzędzia wiersza polecenia. Aby uzyskać informacje na temat instalowania języków C++ i Visual Studio, zobacz [Install c++ Support in Visual Studio](vscpp-step-0-installation.md). Jeśli potrzebujesz tylko zestawu narzędzi wiersza polecenia, Pobierz [Narzędzia do kompilacji dla programu Visual Studio](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019). Po uruchomieniu pobranego pliku wykonywalnego program aktualizuje i uruchamia Instalator programu Visual Studio. Aby zainstalować tylko potrzebne narzędzia do programowania w języku C++, wybierz obciążenie **narzędzi kompilacji c++** . Można wybrać opcjonalne biblioteki i zestawy narzędzi do uwzględnienia w obszarze **szczegóły instalacji**. Aby skompilować kod przy użyciu zestawów narzędzi programu Visual Studio 2015 lub 2017, wybierz opcjonalne narzędzia do kompilacji MSVC wersji 140 lub MSVC najnowsze 141. Po spełnieniu wybranych opcji wybierz pozycję **Zainstaluj**.

## <a name="how-to-use-the-command-line-tools"></a>Jak używać narzędzi wiersza polecenia

Po wybraniu jednego z obciążeń C++ w Instalator programu Visual Studio zainstaluje zestaw *narzędzi platformy*programu Visual Studio. Zestaw narzędzi platformy ma wszystkie narzędzia C i C++ dla określonej wersji programu Visual Studio. Narzędzia te obejmują kompilatory C/C++, linki, asemblery oraz inne narzędzia do kompilacji i zgodne biblioteki. Wszystkie z tych narzędzi można użyć w wierszu polecenia. Są one również używane wewnętrznie przez środowisko IDE programu Visual Studio. Istnieją oddzielne kompilatory i narzędzia obsługiwane przez architekturę x86, które umożliwiają tworzenie kodu dla obiektów docelowych x86, x64, ARM i ARM64. Każdy zestaw narzędzi dla określonego hosta i docelową architekturę kompilacji jest przechowywany w jego własnym katalogu.

Aby można było poprawnie działać, narzędzia wymagają określenia kilku określonych zmiennych środowiskowych. Te zmienne służą do dodawania narzędzi do ścieżki oraz do ustawiania plików dołączanych, plików bibliotek i lokalizacji zestawu SDK. Aby ułatwić ustawienie tych zmiennych środowiskowych, Instalator tworzy niestandardowe *pliki poleceń*lub pliki wsadowe podczas instalacji. Można uruchomić jeden z tych plików poleceń, aby ustawić określony host i docelową architekturę kompilacji, wersję Windows SDK i zestaw narzędzi platformy. Dla wygody Instalator tworzy również skróty w menu Start. Skróty uruchamiają okna wiersza polecenia dla deweloperów, używając tych plików poleceń dla określonych kombinacji hosta i celu. Te skróty zapewniają, że wszystkie wymagane zmienne środowiskowe są ustawione i gotowe do użycia.

Wymagane zmienne środowiskowe są specyficzne dla danej instalacji i wybranej architektury kompilacji. Mogą być również zmieniane przez aktualizacje lub uaktualnienia produktów. Dlatego zalecamy użycie zainstalowanego skrótu wiersza polecenia lub pliku poleceń, zamiast samodzielnie ustawić zmienne środowiskowe. Aby uzyskać więcej informacji, zobacz [Ustawianie zmiennych dotyczących ścieżki i środowiska dla kompilacji w wierszu polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md).

Zestawy narzędzi, pliki poleceń i skróty są instalowane zależnie od procesora komputera i opcji wybranych podczas instalacji. Narzędzia obsługiwane przez architekturę x86 i narzędzia krzyżowe, które tworzą kod x86 i x64, są zawsze zainstalowane. Jeśli masz 64-bitowy system Windows, instalowane są także narzędzia i narzędzia obsługiwane przez procesor x64, które tworzą kod x86 i x64. Jeśli wybierzesz opcjonalne narzędzia platforma uniwersalna systemu Windows języka C++, zostaną również zainstalowane narzędzia x86 i x64, które tworzą kod ARM i ARM64. Inne obciążenia mogą instalować dodatkowe narzędzia.

## <a name="developer-command-prompt-shortcuts"></a><a name="developer_command_prompt_shortcuts"></a> Skróty do wiersza polecenia dla deweloperów

Skróty wiersza polecenia są instalowane w folderze programu Visual Studio specyficznym dla wersji. Poniżej znajduje się lista podstawowych skrótów wiersza polecenia i architektury kompilacji, które obsługują:

- **Wiersz polecenia dla deweloperów** — ustawia środowisko do używania 32-bitowych, x86-Native narzędzi do tworzenia 32-bitowego kodu x86.
- **wiersz polecenia narzędzi x86 Native Tools** — ustawia środowisko do używania 32-bitowych, x86-Native narzędzi do tworzenia 32-bitowego kodu x86.
- **wiersz polecenia narzędzi x64 Native Tools** — ustawia środowisko do używania 64-bitowych, 64-natywnych narzędzi do kompilowania 64-bitowego, 64-natywnego kodu.
- **wiersz polecenia narzędzi x86_x64 Cross Tools** — ustawia środowisko do używania 32-bitowych, x86-Native narzędzi do kompilowania 64-bitowego, 64-natywnego kodu.
- **wiersz polecenia narzędzi x64_x86 Cross Tools** — ustawia środowisko do używania 64-bitowych, 64-natywnych narzędzi do tworzenia 32-bitowego kodu x86.

::: moniker range=">= vs-2019"

Folder menu Start i nazwy skrótów różnią się w zależności od zainstalowanej wersji programu Visual Studio. Jeśli je ustawisz, zależą również od **pseudonimu**instalacji. Załóżmy na przykład, że zainstalowano program Visual Studio 2019 i został on przydomek do *najnowszej wersji*. Skrót do wiersza polecenia dla deweloperów ma nazwę **wiersz polecenia dla deweloperów dla programu VS 2019 (Najnowsza wersja)** w folderze o nazwie **Visual Studio 2019**.

::: moniker-end
::: moniker range="= vs-2017"

Folder menu Start i nazwy skrótów różnią się w zależności od zainstalowanej wersji programu Visual Studio. Jeśli je ustawisz, zależą również od **pseudonimu**instalacji. Załóżmy na przykład, że zainstalowano program Visual Studio 2017 i został on przydomek do *najnowszej wersji*. Skrót do wiersza polecenia dla deweloperów ma nazwę **wiersz polecenia dla deweloperów dla programu VS 2017 (Najnowsza wersja)** w folderze o nazwie **Visual Studio 2017**.

::: moniker-end
::: moniker range="< vs-2017"

Folder menu Start i nazwy skrótów różnią się w zależności od zainstalowanej wersji programu Visual Studio. Załóżmy na przykład, że zainstalowano program Visual Studio 2015. Skrót do wiersza polecenia dla deweloperów ma nazwę **wiersz polecenia dla deweloperów dla programu VS 2015**.

::: moniker-end

### <a name="to-open-a-developer-command-prompt-window"></a><a name="developer_command_prompt"></a> Aby otworzyć okno wiersza polecenia dla deweloperów

1. Na pulpicie Otwórz menu **Start** systemu Windows, a następnie przewiń, aby znaleźć i otworzyć folder dla używanej wersji programu Visual Studio, na przykład **Visual Studio 2019**.

1. W folderze wybierz **wiersz polecenia dla deweloperów** dla używanej wersji programu Visual Studio. Ten skrót uruchamia okno wiersza polecenia dla deweloperów, które używa domyślnej architektury kompilacji o 32-bitowej, x86-Native Tools do kompilowania 32-bitowego kodu x86. Jeśli wolisz niedomyślną architekturę kompilacji, wybierz jedną z poleceń narzędzia natywnego lub krzyżowego, aby określić architekturę hosta i docelową.

Aby jeszcze szybszy otworzyć wiersz polecenia dewelopera, wprowadź *wiersz polecenia dewelopera* w polu wyszukiwania na pulpicie. Następnie wybierz żądany wynik.

## <a name="developer-command-file-locations"></a><a name="developer_command_file_locations"></a> Lokalizacje plików poleceń deweloperskich

Jeśli wolisz ustawić środowisko kompilacji w istniejącym oknie wiersza polecenia, możesz użyć jednego z plików poleceń utworzonych przez Instalatora. Zalecamy ustawienie środowiska w nowym oknie wiersza polecenia. Nie zalecamy później przełączania środowisk w tym samym oknie poleceń.

::: moniker range=">= vs-2019"

Lokalizacja pliku poleceń zależy od zainstalowanej wersji programu Visual Studio i opcji dostępnych podczas instalacji. W przypadku programu Visual Studio 2019 typowa lokalizacja instalacji w systemie 64-bitowym jest w \\ plikach Program Files (x86) \\ Microsoft Visual Studio \\ 2019 \\ *Edition*. *Wersja* może być Community, Professional, Enterprise, BuildTools lub inną dostarczoną pseudonimem.

::: moniker-end
::: moniker range="= vs-2017"

Lokalizacja pliku poleceń zależy od zainstalowanej wersji programu Visual Studio i opcji dostępnych podczas instalacji. W przypadku programu Visual Studio 2017 typowa lokalizacja instalacji w systemie 64-bitowym jest w \\ plikach Program Files (x86) \\ Microsoft Visual Studio \\ 2017 \\ *Edition*. *Wersja* może być Community, Professional, Enterprise, BuildTools lub inną dostarczoną pseudonimem.

::: moniker-end
::: moniker range="< vs-2017"

Lokalizacja pliku poleceń zależy od wersji programu Visual Studio i katalogu instalacyjnego. W przypadku programu Visual Studio 2015 typowa lokalizacja instalacji to w \\ plikach programowych (x86) \\ Microsoft Visual Studio 14,0.

::: moniker-end

Podstawowy plik poleceń wiersza polecenia dla deweloperów, VsDevCmd.bat, znajduje się w \\ podkatalogu Tools Common7. Jeśli nie określono parametrów, ustawia środowisko do używania narzędzi x86-native do kompilowania 32-bitowego kodu x86.

::: moniker range=">= vs-2017"

Więcej plików poleceń jest dostępnych do skonfigurowania określonych architektur kompilacji. Dostępne pliki poleceń zależą od obciążeń i opcji programu Visual Studio, które zostały zainstalowane. W programie Visual Studio 2017 i Visual Studio 2019 znajdują się one w \\ \\ podkatalogu kompilacji pomocniczej VC.

::: moniker-end
::: moniker range="< vs-2017"

Więcej plików poleceń jest dostępnych do skonfigurowania określonych architektur kompilacji. Dostępne pliki poleceń zależą od obciążeń i opcji programu Visual Studio, które zostały zainstalowane. W programie Visual Studio 2015 znajdują się one w \\ podkatalogach VC, VC lub \\ VC \\ *architektury* bin, gdzie *Architecture* jest jedną z opcji macierzystych lub międzykompilatorowych.

::: moniker-end

Te pliki poleceń ustawiają domyślne parametry i Wywołaj VsDevCmd.bat, aby skonfigurować określone środowisko architektury kompilacji. Typowa instalacja może obejmować następujące pliki poleceń:

|Plik polecenia|Architektury hosta i celu|
|---|---|
|**vcvars32.bat**| Do kompilowania kodu 32-bitowym x86 można używać narzędzi 32-bitowych x86-Native.|
|**vcvars64.bat**| Do kompilowania kodu 64-bitowego x64 Użyj narzędzi 64-bitowych x64-Native.|
|**vcvarsx86_amd64.bat**| Do kompilowania kodu 64-bitowego x64 należy użyć 32-bitowych narzędzi międzynatywnych platformy x86.|
|**vcvarsamd64_x86.bat**| Użyj 64-bitowego 64-macierzystego narzędzia krzyżowe, aby skompilować 32-bitowy kod x86.|
|**vcvarsx86_arm.bat**| Aby skompilować kod ARM, użyj 32-bitowych międzyfirmowych narzędzi dla wielu procesorów x86.|
|**vcvarsamd64_arm.bat**| Użyj 64-bitowego 64-natywnych narzędzi do obsługi wielu procesorów, aby skompilować kod ARM.|
|**vcvarsall.bat**| Użyj parametrów, aby określić architektury hosta i celu, Windows SDK i opcje platformy. Aby zapoznać się z listą obsługiwanych opcji, należy wywołać parametr **/help** .|

> [!CAUTION]
> Plik vcvarsall.bat i inne pliki poleceń programu Visual Studio mogą się różnić od komputera do komputera. Nie zamieniaj brakującego lub uszkodzonego pliku vcvarsall.bat przy użyciu pliku z innego komputera. Uruchom ponownie Instalatora programu Visual Studio, aby zastąpić brakujący plik.
>
> Plik vcvarsall.bat również różni się od wersji do wersji. Jeśli bieżąca wersja programu Visual Studio jest zainstalowana na komputerze, który ma również starszą wersję programu Visual Studio, nie należy uruchamiać vcvarsall.bat ani innego pliku poleceń programu Visual Studio z różnych wersji w tym samym oknie wiersza polecenia.

## <a name="use-the-developer-tools-in-an-existing-command-window"></a>Korzystanie z narzędzi deweloperskich w istniejącym oknie poleceń

Najprostszym sposobem określenia konkretnej architektury kompilacji w istniejącym oknie polecenia jest użycie pliku vcvarsall.bat. Użyj vcvarsall.bat, aby ustawić zmienne środowiskowe, aby skonfigurować wiersz polecenia dla kompilacji natywnej 32-bitowej lub 64-bitowej. Argumenty umożliwiają określenie wielu kompilacji na procesorach x86, x64, ARM lub ARM64. Można kierować Microsoft Store, platforma uniwersalna systemu Windows lub platform klasycznych Windows. Możesz nawet określić, który Windows SDK używać, i wybrać wersję zestawu narzędzi platformy.

Gdy jest używany bez argumentów, vcvarsall.bat konfiguruje zmienne środowiskowe, aby użyć bieżącego kompilatora x86-Native dla 32-bitowych elementów docelowych pulpitu systemu Windows. Można dodać argumenty, aby skonfigurować środowisko do korzystania z dowolnego narzędzia kompilatora natywnego lub krzyżowego. vcvarsall.bat wyświetla komunikat o błędzie w przypadku określenia konfiguracji, która nie jest zainstalowana lub jest niedostępna na komputerze.

### <a name="vcvarsall-syntax"></a>Składnia vcvarsall

> **vcvarsall.bat** [*architektura*] [*platform_type*] [*winsdk_version*] [**-vcvars_ver =**_vcversion_]

*Będąc*<br/>
Ten opcjonalny argument określa architekturę hosta i docelowy do użycia. Jeśli *Architektura* nie jest określona, używane jest domyślne środowisko kompilacji. Te argumenty są obsługiwane:

|*Będąc*|Compiler|Architektura komputera hosta|Architektura kompilacji danych wyjściowych (target)|
|----------------------------|--------------|----------------------------------|-------------------------------|
|**x86**|x86 32-bitowy natywny|x86, x64|x86|
|**x86 \_ amd64** lub **x86 \_ x64**|x64 w przypadku procesora x86|x86, x64|x64|
|**x86_arm**|ARM na procesorze x86|x86, x64|ARM|
|**x86_arm64**|ARM64 na procesorze x86|x86, x64|ARM64|
|**amd64** lub **x64**|x64 64-bitowe natywne|x64|x64|
|**amd64 \_ x86** lub **x64 \_ x86**|x86 na x64 krzyżowe|x64|x86|
|**amd64 \_ ARM** lub **x64 \_ ARM**|ARM na x64|x64|ARM|
|**amd64 \_ arm64** lub **x64 \_ arm64**|ARM64 na x64|x64|ARM64|

*platform_type*<br/>
Ten opcjonalny argument umożliwia określenie **sklepu** lub **platformy UWP** jako typu platformy. Domyślnie środowisko jest ustawione na potrzeby kompilowania aplikacji klasycznych lub konsolowych.

*winsdk_version*<br/>
Opcjonalnie określa wersję Windows SDK, która ma być używana. Domyślnie jest używana najnowsza Windows SDK. Aby określić wersję Windows SDK, można użyć pełnego numeru zestawu SDK systemu Windows 10, takiego jak **10.0.10240.0**, lub określić **8,1** , aby użyć zestawu Windows 8.1 SDK.

*vcversion*<br/>
Opcjonalnie określa zestaw narzędzi kompilatora programu Visual Studio, który ma być używany. Domyślnie środowisko jest skonfigurowane do korzystania z bieżącego zestawu narzędzi kompilatora programu Visual Studio.

::: moniker range=">= vs-2019"

Użyj **-vcvars_ver = 14.2 x. rrrr** , aby określić określoną wersję zestawu narzędzi kompilatora programu Visual Studio 2019.

Użyj **-vcvars_ver = 14.16** , aby określić najnowszą wersję zestawu narzędzi kompilatora programu Visual Studio 2017.

::: moniker-end
::: moniker range="= vs-2017"

Użyj **-vcvars_ver = 14.16** , aby określić najnowszą wersję zestawu narzędzi kompilatora programu Visual Studio 2017.

Użyj **-vcvars_ver = 14,1 x. rrrr** , aby określić określoną wersję zestawu narzędzi kompilatora programu Visual Studio 2017.

::: moniker-end

Użyj **-vcvars_ver = 14.0** , aby określić zestaw narzędzi kompilatora programu Visual Studio 2015.

#### <a name="to-set-up-the-build-environment-in-an-existing-command-prompt-window"></a><a name="vcvarsall"></a> Aby skonfigurować środowisko kompilacji w istniejącym oknie wiersza polecenia

1. W wierszu polecenia Użyj polecenia CD, aby przejść do katalogu instalacyjnego programu Visual Studio. Następnie ponownie Użyj dysku CD, aby przejść do podkatalogu, który zawiera pliki poleceń specyficznych dla konfiguracji. W przypadku programów Visual Studio 2019 i Visual Studio 2017 należy użyć podkatalogu * \\ \\ kompilacji pomocniczej VC* . Dla programu Visual Studio 2015 Użyj podkatalogu *VC* .

1. Wprowadź polecenie dla preferowanego środowiska deweloperskiego. Na przykład, aby skompilować kod ARM dla platformy UWP na platformie 64-bitowej przy użyciu najnowszych Windows SDK i zestawu narzędzi kompilatora programu Visual Studio, użyj tego wiersza polecenia:

   `vcvarsall.bat amd64_arm uwp`

## <a name="create-your-own-command-prompt-shortcut"></a>Utwórz własny skrót do wiersza polecenia

::: moniker range=">= vs-2019"

Otwórz okno dialogowe właściwości dla skrótu wiersza polecenia dla deweloperów, aby zobaczyć użyty obiekt docelowy polecenia. Na przykład element docelowy dla skrótu **wiersz polecenia narzędzi x64 Native Tools dla programu VS 2019** to coś podobnego do:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="= vs-2017"

Otwórz okno dialogowe właściwości dla skrótu wiersza polecenia dla deweloperów, aby zobaczyć użyty obiekt docelowy polecenia. Na przykład element docelowy dla skrótu **wiersz polecenia narzędzi x64 Native Tools dla programu VS 2017** to coś podobnego do:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvars64.bat"`

::: moniker-end
::: moniker range="< vs-2017"

Otwórz okno dialogowe właściwości dla skrótu wiersza polecenia dla deweloperów, aby zobaczyć użyty obiekt docelowy polecenia. Na przykład obiekt docelowy skrótu **programu vs2015 wiersz polecenia narzędzi x64 Native Tools** jest coś podobnego do:

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64`

::: moniker-end

Pliki wsadowe specyficzne dla architektury ustawiają parametr *architektury* i vcvarsall.bat wywołań. Te same opcje można przekazać do tych plików wsadowych, co zostało przekazane do vcvarsall.bat lub można tylko wywołać vcvarsall.bat bezpośrednio. Aby określić parametry dla własnego skrótu polecenia, Dodaj je na końcu polecenia w podwójnym cudzysłowie. Na przykład Oto skrót do kompilowania kodu ARM dla platformy UWP na platformie 64-bitowej przy użyciu najnowszej Windows SDK. Aby użyć wcześniejszego zestawu narzędzi kompilatora, określ numer wersji. Użyj podobnej do tego celu polecenia w skrócie:

::: moniker range=">= vs-2019"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.16`

::: moniker-end
::: moniker range="= vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio\2017\Community\VC\Auxiliary\Build\vcvarsall.bat" amd64_arm uwp -vcvars_ver=14.0`

::: moniker-end
::: moniker range="< vs-2017"

`%comspec% /k "C:\Program Files (x86)\Microsoft Visual Studio 14.0\VC\vcvarsall.bat" amd64 -vcvars_ver=12.0`

::: moniker-end

Dostosuj ścieżkę, aby odzwierciedlała katalog instalacyjny programu Visual Studio. Plik vcvarsall.bat zawiera dodatkowe informacje o określonych numerach wersji.

## <a name="command-line-tools"></a>Narzędzia wiersza polecenia

Aby skompilować projekt C/C++ w wierszu polecenia, program Visual Studio udostępnia następujące narzędzia wiersza polecenia:

[CL](reference/compiling-a-c-cpp-program.md)<br/>
Użyj kompilatora (cl.exe) do kompilowania i łączenia plików kodu źródłowego w aplikacje, biblioteki i biblioteki DLL.

[Łącze](reference/linking.md)<br/>
Użyj konsolidatora (link.exe), aby połączyć skompilowane pliki i biblioteki obiektów w aplikacje i biblioteki DLL.

[NMAKE](reference/nmake-reference.md)<br/>
Używaj NMAKE (nmake.exe) w systemie Windows do kompilowania projektów C++ opartych na tradycyjnym pliku reguł programu make.

Gdy kompilujesz w wierszu polecenia, polecenie F1 nie jest dostępne do natychmiastowej pomocy. Zamiast tego można użyć aparatu wyszukiwania, aby uzyskać informacje dotyczące ostrzeżeń, błędów i komunikatów. Możesz również pobrać pliki pomocy w trybie offline i korzystać z nich. Aby użyć wyszukiwania w docs.microsoft.com, wprowadź zapytanie w polu wyszukiwania w górnej części dowolnego artykułu.

## <a name="command-line-project-management-tools"></a>Narzędzia do zarządzania projektami w wierszu polecenia

Środowisko IDE programu Visual Studio używa natywnego systemu kompilacji projektu opartego na programie MSBuild. Można wywołać program MSBuild bezpośrednio lub użyć natywnego systemu projektu bez użycia środowiska IDE:

[MSBuild](msbuild-visual-cpp.md)<br/>
Użyj programu MSBuild (msbuild.exe) i pliku projektu (. vcxproj), aby skonfigurować kompilację i wywoływać zestaw narzędzi pośrednio. Jest to odpowiednik uruchomienia polecenia **Kompiluj** projekt lub **Kompiluj rozwiązanie** w środowisku IDE programu Visual Studio. Uruchamianie programu MSBuild z wiersza polecenia jest zaawansowanym scenariuszem i nie jest często zalecane. Począwszy od programu Visual Studio w wersji 16,5, MSBuild nie używa środowiska wiersza polecenia do sterowania używanym zestawem narzędzi i bibliotekami.

[DEVENV](/visualstudio/ide/reference/devenv-command-line-switches)<br/>
Użyj DEVENV (devenv.exe) połączonej z przełącznikiem wiersza polecenia, takim jak **/Build** lub **/Clean** , aby wykonać niektóre polecenia kompilacji bez wyświetlania środowiska IDE programu Visual Studio. Ogólnie rzecz biorąc, DEVENV jest preferowana bezpośrednio przy użyciu programu MSBuild, ponieważ program Visual Studio może obsłużyć złożoność programu MSBuild. Począwszy od programu Visual Studio w wersji 16,5, DEVENV nie używa środowiska wiersza polecenia do sterowania używanym zestawem narzędzi i bibliotekami.

## <a name="in-this-section"></a>W tej sekcji

W tych artykułach przedstawiono sposób tworzenia aplikacji w wierszu polecenia i opisywania sposobu dostosowywania środowiska kompilacji wiersza polecenia. Niektóre pokazują, jak korzystać z 64-bitowych zestawów narzędzi oraz docelowa Platforma procesorów x86, x64, ARM i ARM64. Opisują także użycie narzędzi do kompilowania wiersza polecenia MSBuild i NMAKE.

[Przewodnik: kompilowanie natywnego programu C++ w wierszu polecenia](walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)<br/>
Zawiera przykład pokazujący sposób tworzenia i kompilowania programu w języku C++ w wierszu polecenia.

[Przewodnik: Kompilowanie programu w języku C w wierszu polecenia](walkthrough-compile-a-c-program-on-the-command-line.md)<br/>
Opisuje sposób kompilowania programu pisanego w języku programowania C.

[Przewodnik: Kompilowanie programu języka C++/interfejsu wiersza polecenia w wierszu polecenia](walkthrough-compiling-a-cpp-cli-program-on-the-command-line.md)<br/>
Opisuje sposób tworzenia i kompilowania programu C++/CLI, który używa .NET Framework.

[Przewodnik: Kompilowanie programu w języku C++/CX w wierszu polecenia](walkthrough-compiling-a-cpp-cx-program-on-the-command-line.md)<br/>
Opisuje sposób tworzenia i kompilowania programu C++/CX, który używa środowisko wykonawcze systemu Windows.

[Ustawianie ścieżki i zmiennych środowiskowych dla kompilacji z wiersza polecenia](setting-the-path-and-environment-variables-for-command-line-builds.md)<br/>
Jak ustawić zmienne środowiskowe, aby używać zestawu narzędzi 32-bitowego lub 64-bitowego do tworzenia docelowych platform x86, x64, ARM i ARM64.

[Odwołanie NMAKE](reference/nmake-reference.md)<br/>
Zawiera łącza do artykułów opisujących narzędzie do konserwacji programów firmy Microsoft (NMAKE.EXE).

[MSBuild w wierszu polecenia — C++](msbuild-visual-cpp.md)<br/>
Zawiera łącza do artykułów, w których omówiono sposób używania msbuild.exe z wiersza polecenia.

## <a name="related-sections"></a>Sekcje pokrewne

[/MD,/MT,/LD (Korzystaj z bibliotek Run-Time)](reference/md-mt-ld-use-run-time-library.md)<br/>
W tym artykule opisano, jak używać tych opcji kompilatora do korzystania z biblioteki wykonawczej Debug lub Release.

[Opcje kompilatora C/C++](reference/compiler-options.md)<br/>
Zawiera łącza do artykułów, które omawiają opcje kompilatora C i C++ oraz CL.exe.

[Opcje konsolidatora MSVC](reference/linker-options.md)<br/>
Zawiera łącza do artykułów, które omawiają Opcje konsolidatora i LINK.exe.

[Dodatkowe narzędzia kompilacji kompilatora MSVC](reference/c-cpp-build-tools.md)<br/>
Oferuje linki do narzędzi do kompilacji C/C++, które są zawarte w programie Visual Studio.

## <a name="see-also"></a>Zobacz też

[Projekty i systemy kompilacji](projects-and-build-systems-cpp.md)
