---
title: "Określanie, które biblioteki dll do ponownej dystrybucji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
caps.latest.revision: "31"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3cc7b80e16abeecc756e7fa480c7bfe71682382
ms.sourcegitcommit: 54035dce0992ba5dce0323d67f86301f994ff3db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="determining-which-dlls-to-redistribute"></a>Ustalanie, które biblioteki DLL są przeznaczone do ponownej dystrybucji

Podczas kompilowania aplikacji korzystającej z biblioteki DLL dostarczane przez program Visual Studio użytkownicy aplikacji musi mieć również te biblioteki dll na swoich komputerach do uruchomienia aplikacji. Ponieważ większość użytkowników prawdopodobnie nie ma zainstalowanego programu Visual Studio, musisz podać te biblioteki DLL dla nich. Visual Studio udostępnia te biblioteki DLL jako *pliki redystrybucyjne* obejmujących w Instalatorem aplikacji.

Aby ułatwić obejmują pakietu redystrybucyjnego bibliotek DLL z Instalatorem, są dostępne jako autonomiczny *pakiety redystrybucyjne*. Są to pliki wykonywalne architektury, które zainstaluj pakiet redystrybucyjny pliki na komputerze użytkownika przy użyciu centralnej wdrażania. Na przykład program vcredist\_x86.exe instaluje biblioteki 32-bitowego dla x86 komputery, program vcredist\_x64.exe instaluje 32-bitowe i 64-bitowych bibliotek x64 komputerów i program vcredist\_ARM.exe instaluje biblioteki dla ARM komputery. Zalecamy wdrożenie centralnej, ponieważ firma Microsoft mogłaby użyć usługi Windows Update, można zaktualizować niezależnie te biblioteki. Oprócz kopiowania w instalacji programu Visual Studio, są dostępne do pobrania na bieżącym pakiety redystrybucyjne [VisualStudio.com/Downloads](https://www.visualstudio.com/downloads/) w sekcji platformy i inne narzędzia.

Główny numer wersji pakietu redystrybucyjnego, którą można wdrożyć musi odpowiadać wersji zestawu narzędzi programu Visual Studio, używany do tworzenia aplikacji. Visual Studio 2017 i programu Visual Studio 2015 mają numery wersji narzędzi zgodne, co oznacza, że Visual 2017 Studio wstępnie pliki mogą być używane przez aplikacje przy użyciu zestawu narzędzi 2015. Może być zgodne, nie jest obsługiwana przy użyciu plików pakietu redystrybucyjnego 2015 w aplikacji skompilowanych za pomocą zestawu narzędzi 2017 r. Obsługiwany jest tylko przy użyciu pakietu redystrybucyjnego pakietu, która jest taka sama jak lub nowszej wersji zestawu narzędzi. Łącza do najnowszych obsługiwanych pakietu redystrybucyjnego pakiety dla starszych procesami, zobacz [najnowszej obsługiwane pliki do pobrania Visual C++](https://support.microsoft.com/en-us/help/2977003/the-latest-supported-visual-c-downloads). Określone wcześniejszych wersji do dystrybucji pakietów można znaleźć przeszukując [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=158431) dla "Visual C++ Redistributable Packages".

Innym sposobem obejmują pakietu redystrybucyjnego bibliotek DLL z Instalatorem jest użycie *scalania modułów*. Te moduły Installer firmy Microsoft są uwzględnione w i instalowane przez Instalatorem aplikacji. Moduły scalania dla pakietu redystrybucyjnego bibliotek dll znajdują się w katalogu instalacji programu Visual Studio w obszarze \\VC\\Redist\MSVC\\*wersji*\\MergeModules\\ . We wcześniejszych wersjach programu Visual Studio, te pliki znajdują się w sieci \\Program Files lub \\katalog Program Files (x86) w wspólne pliki\\podkatalogu modułów scalania. Aby uzyskać więcej informacji dotyczących użycia tych plików, zobacz [Redystrybucja składników za pomocą modułów scalania](../ide/redistributing-components-by-using-merge-modules.md).

Pakiet redystrybucyjny poszczególnych bibliotek dll znajdują się również w instalacji programu Visual Studio. Domyślnie są zainstalowane w katalogu instalacyjnym programu Visual Studio w \\VC\\Redist\\MSVC\\*wersji* folderu. *Wersji* numery może reprezentować liczby różnych kompilacji pomocniczej pojedynczego wspólnego zestawu plików pakietu redystrybucyjnego. Użyj najnowszej wersji pliku biblioteki DLL, pakiet redystrybucyjny lub moduł scalania znaleziono w tych katalogach. Te biblioteki można użyć dla wdrożenia lokalnego, instalując je w tym samym katalogu co aplikacja. Nie zaleca się wdrożenie lokalnego ponieważ sprawia, że użytkownik odpowiada za dostarczanie aktualizacji do wdrożonej aplikacji. Centralna wdrożenia przy użyciu pakietu redystrybucyjnego pakietów jest preferowana.

Aby ustalić, które biblioteki DLL trzeba przeprowadzać ponownej dystrybucji z aplikacją, zebrać listę bibliotek DLL, które zależy od aplikacji. Są zwykle wyświetlane na liście importu danych wejściowych biblioteki do konsolidatora. Niektóre biblioteki, takich jak vcruntime i Universal C Runtime Library (Biblioteka UCRT), są domyślnie dołączone. Jeśli aplikacji lub jednej z jego zależności za pomocą metody LoadLibrary dynamicznie załadować biblioteki DLL, że biblioteki DLL nie mogą być wyświetlane w danych wejściowych do konsolidatora. Jednym ze sposobów zebrać listę dynamicznie ładowanych bibliotek DLL jest uruchomienie Walkera zależności (depends.exe) w aplikacji, zgodnie z opisem w [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Niestety to narzędzie jest przestarzałe i może zgłosić, że nie można odnaleźć niektórych bibliotek DLL.

Jeśli na liście zależności, porównaj je do listy połączone w pliku Redist.txt znajdują się w katalogu instalacyjnym programu Microsoft Visual Studio, lub "Lista REDYSTRYBUCYJNA" dll pakietu redystrybucyjnego do którego odwołuje się w sekcji "Pliki kodu dystrybucyjnego" Microsoft postanowień licencyjnych dotyczących oprogramowania dla tej kopii programu Visual Studio. Dla programu Visual Studio 2017 r, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2017 r (zawiera narzędzia rozszerzalności i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=823098). Dla programu Visual Studio 2015, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2015 i Microsoft Visual Studio 2015 SDK (obejmuje narzędzia i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?linkid=799794). Dla programu Visual Studio 2013, lista jest dostępna online w [Kod dystrybucyjny dla programu Microsoft Visual Studio 2013 i zestawu SDK programu Microsoft Visual Studio 2013](http://go.microsoft.com/fwlink/p/?LinkId=313603).

W wersjach programu Visual Studio przed Visual Studio 2015, C Runtime Library (CRT) został uwzględniony jako pakiet redystrybucyjny biblioteki DLL w msvc*wersji*dll. Począwszy od programu Visual Studio 2015, funkcje w CRT zostały zrefaktoryzowany do vcruntime i Biblioteka UCRT. Biblioteka UCRT teraz jest składnikiem systemu w systemie Windows 10, zarządzane przez usługę Windows Update. Jest ona dostępna we wszystkich systemach operacyjnych Windows 10. Aby wdrożyć aplikację na starsze systemy operacyjne, może być konieczne ponownie rozesłać również Biblioteka UCRT. Wcześniejszą wersję programu Biblioteka UCRT jest uwzględniane w plikach pakietu redystrybucyjnego programu Visual Studio, które jest instalowany tylko w systemach operacyjnych starszych niż Windows 10, jeśli nie ma wersji Biblioteka UCRT jest już zainstalowana. Wersja instalowalnych Biblioteka UCRT systemów niskiego poziomu, jak pakiet aktualizacji systemu Microsoft dla [Windows 10 Universal C Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=48234) w programie Microsoft Download Center.

Nie można ponownie rozesłać wszystkie pliki, które znajdują się w programie Visual Studio; są dozwolone tylko aby ponownie rozesłać pliki, które są określone w Redist.txt lub w trybie online "Lista REDYSTRYBUCYJNA." Wersje debugowania aplikacji i różnych debugowania Visual C++ biblioteki DLL nie są do dystrybucji. Aby uzyskać więcej informacji, zobacz [Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md).

W poniższej tabeli opisano niektóre z bibliotek DLL programu Visual C++, aplikacja może być zależna od.

|Biblioteka języka Visual C++|Opis|Informacje zawarte w tym artykule dotyczą|
|--------------------------|-----------------|----------------|
|vcruntime*wersji*.dll|Biblioteka środowiska uruchomieniowego dla kodu natywnego.|Aplikacje korzystające z normalnym C i C++ języka uruchamianie i kończenie działania usług.|
|vccorlib*wersji*.dll|Biblioteka środowiska uruchomieniowego dla kodu zarządzanego.|Aplikacje korzystające z usług języka C++ dla kodu zarządzanego.|
|msvcp*wersji*.dll|Standardowa biblioteka C++ dla natywnego kodu.|Aplikacje używające [standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md).|
|concrt*wersji*.dll|Współbieżność środowiska wykonawczego biblioteki dla kodu natywnego.|Aplikacje używające [współbieżność środowiska wykonawczego](../parallel/concrt/concurrency-runtime.md).|
|MFC*wersji*.dll|Microsoft Foundation Classes (MFC) biblioteki.|Aplikacje używające [biblioteki MFC](../mfc/mfc-desktop-applications.md).|
|MFC*wersji* *języka*.dll|Microsoft Foundation Classes (MFC) zasobów biblioteki.|Aplikacje korzystające z zasobów w określonym języku dla MFC.|
|MFC*wersji*u.dll|Biblioteki MFC z obsługą Unicode.|Aplikacje używające [biblioteki MFC](../mfc/mfc-desktop-applications.md) i wymaga obsługi formatu Unicode.|
|mfcmifc80.dll|Biblioteki zarządzane interfejsy MFC.|Aplikacje używające [biblioteki MFC](../mfc/mfc-desktop-applications.md) z [formantów formularzy systemu Windows](/dotnet/framework/winforms/controls/index).|
|mfcm*wersji*.dll|Zarządzanej biblioteki MFC.|Aplikacje używające [biblioteki MFC](../mfc/mfc-desktop-applications.md) z [formantów formularzy systemu Windows](/dotnet/framework/winforms/controls/index).|
|mfcm*wersji*u.dll|Biblioteki zarządzane MFC z obsługą Unicode.|Aplikacje używające [biblioteki MFC](../mfc/mfc-desktop-applications.md) z [formantów formularzy systemu Windows](/dotnet/framework/winforms/controls/index) i wymaga obsługi formatu Unicode.|
|vcamp*wersji*.dll|Biblioteka AMP dla kodu natywnego.|Aplikacje używające [biblioteki C++ AMP](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) kodu.|
|vcomp*wersji*.dll|Biblioteki OpenMP dla kodu natywnego.|Aplikacje używające [biblioteki C++ OpenMP](../parallel/openmp/openmp-in-visual-cpp.md) kodu.|

> [!NOTE]
> Nie trzeba ponownie rozesłać biblioteki Active Template Library jako oddzielnych bibliotekach DLL. Jego funkcja została przeniesiona do nagłówki i biblioteki statycznej.

Aby uzyskać więcej informacji o sposobie Ponowna dystrybucja te biblioteki dll z aplikacji, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md). Aby uzyskać przykłady, zobacz [przykłady wdrożeń](../ide/deployment-examples.md).

Zazwyczaj nie trzeba ponownie rozesłać systemowej biblioteki dll, ponieważ są one częścią systemu operacyjnego. Jednak może istnieć wyjątki, na przykład, gdy aplikacja jest uruchamiana na różne wersje systemów operacyjnych firmy Microsoft. W takim przypadku należy przeczytać odpowiednie postanowienia licencyjne. Ponadto spróbuj pobrać systemowej biblioteki DLL uaktualniony za pośrednictwem usługi Windows Update, dodatki service Pack lub przy użyciu pakietu redystrybucyjnego pakiety udostępnione przez firmę Microsoft.

## <a name="see-also"></a>Zobacz też

[Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md)

[Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)
