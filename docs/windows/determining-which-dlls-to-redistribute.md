---
title: Ustalanie, które biblioteki DLL są przeznaczone do ponownej dystrybucji
ms.date: 03/25/2019
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: dd600e2b3e094b1547badd93596a9dbed2438fb3
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787394"
---
# <a name="determining-which-dlls-to-redistribute"></a>Ustalanie, które biblioteki DLL są przeznaczone do ponownej dystrybucji

Podczas kompilowania aplikacji korzystającej z biblioteki dll, dostarczone przez program Visual Studio użytkownicy twojej aplikacji musi mieć również tych bibliotek DLL na swoich komputerach do uruchomienia aplikacji. Ponieważ większość użytkowników prawdopodobnie nie masz zainstalowanego programu Visual Studio, musisz podać te biblioteki DLL dla nich. Program Visual Studio udostępnia te biblioteki DLL jako *pliki redystrybucyjne* zawierających w Instalatorem aplikacji.

Aby ułatwić obejmują redystrybucyjnych bibliotek DLL z Instalatorem są dostępne jako autonomiczny *pakietów redystrybucyjnych*. Są to pliki wykonywalne architektury, które używają centralnego wdrożenia, aby zainstalować pakiet redystrybucyjny pliki na komputerze użytkownika. Vcredist na przykład\_x86.exe instaluje biblioteki 32-bitowych dla x86 komputerów, vcredist\_x64.exe instaluje biblioteki 64-bitowych x64 komputerów i vcredist\_ARM.exe instaluje biblioteki, na komputerach ARM. Zaleca się wdrożenie centralne, ponieważ firma Microsoft mogła używać Windows aktualizacji usługi można niezależnie zaktualizować tych bibliotek. Oprócz kopiowania w instalacji programu Visual Studio bieżące pakiety redystrybucyjne są dostępne do pobrania. Aby uzyskać łącza do najnowszej obsługiwane pakiety redystrybucyjne dla zarówno bieżących jak starsze zestawy narzędzi, zobacz [r obsługiwane pliki do pobrania Visual C++](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads). Określone wcześniejsze wersje pakietów redystrybucyjnych można znaleźć, przeszukując [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431) dla "Visual C++ Redistributable Packages".

Główny numer wersji pakietu redystrybucyjnego wdrażania musi odpowiadać wersji zestawu narzędzi Visual Studio umożliwia tworzenie aplikacji, a podrzędny numer wersji musi być taka sama lub nowszej. Visual Studio 2017 i Visual Studio 2015 mają numery wersji zestawu narzędzi zgodne, co oznacza, że program Visual Studio 2017 do redystrybucji pliki mogą być używane przez aplikacje zbudowane przy użyciu zestawu narzędzi 2015. Może być zgodne, nie jest obsługiwana przy użyciu pliki redystrybucyjne 2015 w aplikacje zbudowane przy użyciu zestawu narzędzi 2017 r. Obsługiwany jest tylko przy użyciu pakietu redystrybucyjnego, jest taka sama jak lub nowszej niż ta wersja zestawu narzędzi.

Innym sposobem, aby uwzględnić redystrybucyjnych bibliotek DLL z Instalatorem jest użycie *modułów scalania,*. Te moduły Installer firmy Microsoft są objęte i instalowany przez Instalatora aplikacji. Modułów scalania dla redystrybucyjnych bibliotek dll znajdują się w katalogu instalacji programu Visual Studio w obszarze \\VC\\Redist\MSVC\\*wersji*\\MergeModules\\ . We wcześniejszych wersjach programu Visual Studio, te pliki znajdują się w Twojej \\Program Files lub \\katalogu Program Files (x86) w wspólne pliki\\podkatalogu scalonych modułów. Aby uzyskać więcej informacji dotyczących używania tych plików, zobacz [Redystrybucja składników za pomocą modułów scalania](redistributing-components-by-using-merge-modules.md).

Poszczególne redystrybucyjnych bibliotek dll znajdują się również w instalacji programu Visual Studio. Domyślnie są zainstalowane w katalogu instalacyjnym programu Visual Studio w \\VC\\Redist\\MSVC\\*wersji* folderu. *Wersji* liczb może reprezentować różne pomocnicza numery kompilacji jednego wspólnego zestawu plików do dystrybucji. Użyj najnowszej wersji pliku DLL biblioteki, pakiet redystrybucyjny lub moduł scalania znalezione w tych katalogach. Przez zainstalowanie ich w tym samym katalogu co aplikacja, może używać tych bibliotek do wdrożenia lokalnego. Nie zaleca się wdrożenie lokalne ponieważ sprawia, że użytkownik odpowiada za dostarczanie aktualizacji do wdrożonej aplikacji. Wdrożenie centralne przy użyciu pakietów redystrybucyjnych jest preferowana.

Aby określić, które biblioteki DLL musisz redystrybuować z aplikacją, Zbierz listę bibliotek DLL, od których zależy aplikacja. Są zwykle wyświetlane na liście importu danych wejściowych biblioteki do konsolidatora. Niektórych bibliotek, takich jak vcruntime i Universal C Runtime Library (UCRT), są domyślnie dołączone. Jeśli Twoja aplikacja lub jednej z jego zależności za pomocą LoadLibrary dynamicznie załadować biblioteki DLL, tej biblioteki DLL nie mogą być wyświetlane w danych wejściowych do konsolidatora. Jednym ze sposobów zbierania listy dynamicznie ładowanych bibliotek DLL jest uruchomienie modułu przeszukiwania zależności (depends.exe) w aplikacji, zgodnie z opisem w [poznanie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md). Niestety to narzędzie jest nieaktualna i może zgłaszać, że nie można odnaleźć niektórych bibliotek DLL.

Jeśli masz listę zależności, porównaj je do listy w pliku Redist.txt znajdują się w katalogu instalacyjnego programu Microsoft Visual Studio połączone lub "Listę REDIST" Pakiet redystrybucyjny bibliotek DLL, o której mowa w sekcji "Pliki kodu dystrybucyjnego" Microsoft postanowień licencyjnych dotyczących oprogramowania dla tej kopii programu Visual Studio. Dla programu Visual Studio 2017, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2017 (obejmuje programy narzędziowe, rozszerzalność i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=823098). Dla programu Visual Studio 2015, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2015 i Microsoft Visual Studio 2015 SDK (obejmuje programy narzędziowe i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=799794). Dla programu Visual Studio 2013, lista jest dostępna online w [Kod dystrybucyjny dla programu Microsoft Visual Studio 2013 i Microsoft Visual Studio 2013 SDK](http://go.microsoft.com/fwlink/p/?LinkId=313603).

W wersjach programu Visual Studio przed Visual Studio 2015, biblioteka środowiska uruchomieniowego C (CRT) został dołączony jako pakiet redystrybucyjny bibliotek DLL w msvc*wersji*.dll. Począwszy od programu Visual Studio 2015, funkcje w CRT zostały zaprojektowane od nowa vcruntime i UCRT. UCRT teraz jest składnikiem systemu w systemie Windows 10, zarządzane przez usługę Windows Update. Jest ona dostępna we wszystkich systemach operacyjnych Windows 10. Aby wdrożyć aplikację do starszych systemów operacyjnych, może być konieczne ponownie rozesłać UCRT, jak również. Wczesnych wersji 140_xp Biblioteka UCRT jest zawarty w programie Visual Studio przeznaczone do redystrybucji pliki, których jest ona instalowana tylko w systemach operacyjnych starszych niż Windows 10, i tylko wtedy, jeśli nie ma wersji 140_xp Biblioteka UCRT jest już zainstalowany. Do zainstalowania wersja UCRT systemów niskiego poziomu, jak pakiet aktualizacji systemu Microsoft dla [systemu Windows 10 uniwersalnego środowiska uruchomieniowego C](https://www.microsoft.com/download/details.aspx?id=48234) w programie Microsoft Download Center.

Nie możesz redystrybuować wszystkich plików, które znajdują się w programie Visual Studio; są dozwolona jest tylko Redystrybucja plików, które są określone w Redist.txt lub online "Listę REDIST"." Wersje do debugowania aplikacji i różnych debugowania języka Visual C++ bibliotek DLL nie są do dystrybucji. Aby uzyskać więcej informacji, zobacz [Wybieranie metody wdrażania](choosing-a-deployment-method.md).

W poniższej tabeli opisano niektóre z bibliotek DLL Visual C++, które aplikacja może zależeć od.

|Visual C++ Library|Opis|Informacje zawarte w tym artykule dotyczą|
|--------------------------|-----------------|----------------|
|vcruntime*version*.dll|Biblioteka środowiska uruchomieniowego dla kodu natywnego.|Aplikacje, które korzystają z normalnym C i C++ language uruchamianie i kończenie działania usług.|
|vccorlib*version*.dll|Biblioteka środowiska uruchomieniowego dla kodu zarządzanego.|Aplikacje, które używają usług języka C++ dla kodu zarządzanego.|
|msvcp*wersji*.dll i msvcp*wersji*_*dotnumber*.dll|Standardowa biblioteka C++ dla kodu natywnego.|Aplikacje, które używają [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*wersji*.dll|Biblioteka środowiska uruchomieniowego współbieżności dla kodu natywnego.|Aplikacje, które używają [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).|
|MFC*wersji*.dll|Microsoft Foundation Classes (MFC) Library.|Aplikacje, które używają [biblioteki MFC](../mfc/mfc-desktop-applications.md).|
|MFC*wersji* *języka*.dll|Microsoft Foundation Classes (MFC) zasobów biblioteki.|Aplikacje, które używają zasobów określonego języka dla MFC.|
|MFC*wersji*u.dll|Biblioteka MFC z obsługą standardu Unicode.|Aplikacje, które używają [biblioteki MFC](../mfc/mfc-desktop-applications.md) i wymagają obsługi standardu Unicode.|
|mfcmifc80.dll|Biblioteka interfejsów zarządzanych MFC.|Aplikacje, które używają [biblioteki MFC](../mfc/mfc-desktop-applications.md) z [kontrolek formularzy Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*.dll|Biblioteka zarządzana MFC.|Aplikacje, które używają [biblioteki MFC](../mfc/mfc-desktop-applications.md) z [kontrolek formularzy Windows Forms](/dotnet/framework/winforms/controls/index).|
|mfcm*version*u.dll|Biblioteka zarządzana MFC z obsługą standardu Unicode.|Aplikacje, które używają [biblioteki MFC](../mfc/mfc-desktop-applications.md) z [kontrolek formularzy Windows Forms](/dotnet/framework/winforms/controls/index) i wymagają obsługi standardu Unicode.|
|vcamp*version*.dll|Biblioteka AMP dla kodu natywnego.|Aplikacje, które używają [biblioteki C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) kodu.|
|vcomp*version*.dll|Biblioteki OpenMP dla kodu natywnego.|Aplikacje, które używają [biblioteki języka C++, OpenMP](../parallel/openmp/openmp-in-visual-cpp.md) kodu.|

> [!NOTE]
> Nie trzeba redystrybuować biblioteki Active Template Library jako osobne biblioteki DLL. Jego funkcja została przeniesiona do nagłówki i biblioteki statycznej.

Aby uzyskać więcej informacji na temat sposobu rozpowszechniania tych bibliotek DLL z aplikacją, zobacz [Redistributing Visual C++ Files](redistributing-visual-cpp-files.md). Aby uzyskać przykłady, zobacz [przykłady wdrożeń](deployment-examples.md).

Zazwyczaj nie trzeba redystrybuować systemowych bibliotek DLL, ponieważ są one częścią systemu operacyjnego. Jednak mogą istnieć wyjątki, na przykład, gdy aplikacja jest uruchamiana w różnych wersjach systemów operacyjnych firmy Microsoft. W takim przypadku należy koniecznie przeczytaj odpowiednie postanowienia licencyjne. Ponadto spróbuj systemową bibliotekę DLL aktualizować za pośrednictwem usługi Windows Update, dodatki service Pack lub przy użyciu pakietów redystrybucyjnych udostępnianych przez firmę Microsoft.

## <a name="see-also"></a>Zobacz także

[Wybieranie metody wdrażania](choosing-a-deployment-method.md)<br/>
[Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)
