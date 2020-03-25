---
title: Redystrybuowanie plików programu Visual C++
ms.date: 11/04/2016
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 46192fe7ff5b29c22a5001cc460c74f5ddf6d1bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167930"
---
# <a name="redistributing-visual-c-files"></a>Redystrybuowanie plików programu Visual C++

> [!NOTE]
> Jesteś tutaj, ponieważ szukasz pobrania jednego z plików środowiska uruchomieniowego Visual C++ ? Przejdź do [witryny sieci Web firmy Microsoft](https://www.microsoft.com/) i wprowadź w polu wyszukiwania **element redystrybucyjny Visual C++**  . Pobierz i zainstaluj pakiet redystrybucyjny dla architektury komputera (na przykład x64, jeśli używasz 64-bitowego systemu Windows) i wersji wizualizacji C++ (na przykład 2015), która jest potrzebna.

Podczas wdrażania aplikacji należy również wdrożyć pliki, które są wymagane do jej obsługi. Jeśli któryś z tych plików jest dostarczany przez firmę Microsoft, sprawdź, czy masz pozwolenie na jego redystrybucję. Aby zapoznać się z postanowieniami licencyjnymi programu Visual Studio, zobacz link postanowienia licencyjne w oknie dialogowym Informacje o Microsoft Visual Studio w środowisku IDE lub Pobierz plik [postanowień licencyjnych dotyczących oprogramowania firmy Microsoft](https://visualstudio.microsoft.com/license-terms/mlt687465/) . Aby wyświetlić "listę Redist", o której mowa w punkcie "Kod dystrybucyjny" postanowień licencyjnych dotyczących oprogramowania firmy Microsoft dotyczących niektórych wersji programu Visual Studio, zobacz [Kod dystrybucyjny dla Microsoft Visual Studio 2017 i Microsoft Visual Studio 2017 SDK (zawiera narzędzia i pliki BuildServer)](/visualstudio/productinfo/2017-redistribution-vs)lub dla programu Visual Studio 2015, zobacz [Kod dystrybucyjny dla Microsoft Visual Studio 2015 i Microsoft Visual Studio 2015 SDK](/visualstudio/productinfo/2015-redistribution-vs). Aby uzyskać więcej informacji na temat redystrybucyjnych plików, zobacz [Określanie bibliotek DLL do dystrybucji](determining-which-dlls-to-redistribute.md) i [wdrażania przykładów](deployment-examples.md).

Aby wdrożyć pliki wizualizacji C++ redystrybucyjnej, można użyć pakietów C++ redystrybucyjnych wizualnych (VCRedist\_x86. exe, VCRedist\_x64. exe lub VCRedist\_ARM. exe), które są zawarte w programie Visual Studio. W programie Visual Studio 2017 te pliki znajdują się w plikach programu [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\redist\\MSVC\\_lib-Version_ , gdzie _Edition_ jest zainstalowana wersja programu Visual Studio, a _wersja_ biblioteki do redystrybucji. W programie Visual Studio 2015 te pliki mogą znajdować się w katalogu instalacyjnym programu Visual Studio w plikach programowych [(x86)] \Microsoft Visual Studio *Version*\VC\redist\\*locale*\\. Inną opcją jest użycie redystrybucyjnych modułów scalania (plików. msm), które w programie Visual Studio 2017 można znaleźć w plikach programu [(x86)]\\Microsoft Visual Studio\\2017\\_edition_\\VC\\redist\\MSVC\\_lib-version_\\MergeModules\\ folder. W programie Visual Studio 2015 można je znaleźć w plikach programów [(x86)] \Common Files\Merge modules\\. Możliwe jest również bezpośrednie zainstalowanie redystrybucyjnych C++ bibliotek DLL w *folderze lokalnym aplikacji*, który jest folderem zawierającym plik wykonywalny aplikacji. Ze względów obsługi nie zaleca się używania tej lokalizacji instalacji.

Pakiety redystrybucyjne Visual C++ instalują i rejestrują wszystkie biblioteki Visual C++. Jeśli używasz któregoś z nich, musisz ustawić jego uruchomienie w systemie docelowym jako warunek wstępny do instalacji aplikacji. Zaleca się używanie tych pakietów dla wdrożeń, ponieważ umożliwiają one automatyczne aktualizowanie bibliotek Visual C++. Aby zapoznać się z przykładem dotyczącym korzystania z tych pakietów, zobacz [Przewodnik: C++ wdrażanie aplikacji wizualnej przy C++ użyciu pakietu redystrybucyjnego Visual](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Każdy pakiet C++ redystrybucyjny wizualizacji sprawdza obecność nowszej wersji na komputerze. Jeśli zostanie znaleziona nowsza wersja, pakiet nie jest zainstalowany. Począwszy od programu Visual Studio 2015, pakiety redystrybucyjne wyświetlają komunikat o błędzie z informacją, że instalacja nie powiodła się. Jeśli pakiet jest uruchamiany przy użyciu flagi **/quiet** , nie jest wyświetlany żaden komunikat o błędzie. W obu przypadkach błąd jest rejestrowany przez Instalatora Microsoft i zwracany jest wynik błędu do obiektu wywołującego. Począwszy od pakietów programu Visual Studio 2015, możesz uniknąć tego błędu, sprawdzając rejestr, aby dowiedzieć się, czy jest zainstalowana nowsza wersja. Obecnie zainstalowana wersja jest przechowywana w HKEY_LOCAL_MACHINE \SOFTWARE [\Wow6432Node] \Microsoft\VisualStudio\\_vs-Version_\VC\Runtimes\\{x86 | x64 | ARM}, gdzie _wersja vs_ jest numerem wersji dla programu Visual studio (14,0 dla programu visual Studio 2015 i visual Studio 2017, ponieważ zaktualizowany pakiet redystrybucyjny 2017 jest binarny zgodny z wersją 2015) i gdzie Key to ARM, x86 lub x64, w zależności od zainstalowanych wersji VCRedist dla platformy. (Nie musisz ewidencjonować podklucza Wow6432Node, chyba że używasz programu regedit do wyświetlania wersji zainstalowanego pakietu x86 na platformie x64). Numer wersji jest przechowywany w REG_SZ **wersji** wartości ciągu, a także w zestawie wartości REG_DWORD **głównych**, **pomocniczych**, **BLD**i **Rbld** . Aby uniknąć błędu podczas instalacji, należy pominąć instalację pakietu redystrybucyjnego, jeśli aktualnie zainstalowana wersja jest nowsza.

Jeśli używasz modułu scalania zawierającego wizualizacje C++ dll, musisz go uwzględnić w pakiecie Instalator Windows (lub podobnym pakiecie instalacyjnym) używanym do wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [Redystrybucja przy użyciu modułów scalania](redistributing-components-by-using-merge-modules.md). Aby zapoznać się z przykładem, zobacz [Przewodnik: C++ wdrażanie aplikacji wizualnej przy użyciu projektu Instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), który pokazuje również, jak używać InstallShield Limited Edition do utworzenia pakietu instalacyjnego.

## <a name="potential-run-time-errors"></a>Potencjalne błędy czasu wykonywania

Jeśli system Windows nie może odnaleźć jednej z bibliotek DLL biblioteki redystrybucyjnej wymaganej przez aplikację, może być wyświetlany komunikat podobny do tego: "nie można uruchomić tej aplikacji, ponieważ nie znaleziono *biblioteki*dll. Ponowne zainstalowanie aplikacji może rozwiązać ten problem ".

Aby rozwiązać ten rodzaj błędu, upewnij się, że Instalator aplikacji poprawnie kompiluje i że biblioteki redystrybucyjne są poprawnie wdrożone w systemie docelowym. Aby uzyskać więcej informacji, zobacz [Omówienie zależności aplikacji wizualnej C++ ](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Redystrybucja przy użyciu modułów scalania](redistributing-components-by-using-merge-modules.md)|Opisuje, jak używać Visual C++ redystrybucyjnych modułów scalania do instalowania bibliotek C++ środowiska uruchomieniowego języka Visual jako udostępnionych bibliotek DLL w folderze%windir%\system32\.|
|[Ponowne dystrybuowanie kontrolek ActiveX programu Visual C++](redistributing-visual-cpp-activex-controls.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z formantów ActiveX.|
|[Ponowne dystrybuowanie biblioteki MFC](redistributing-the-mfc-library.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z MFC.|
|[Ponowne dystrybuowanie aplikacji ATL](redistributing-an-atl-application.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z biblioteki ATL. Począwszy od programu Visual Studio 2012, nie jest wymagana biblioteka redystrybucyjna ATL.|
|[Przykłady wdrożeń](deployment-examples.md)|Zawiera łącza do przykładów, które pokazują sposób wdrażania aplikacji Visual C++.|
|[Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)|Wprowadza koncepcje i technologie wdrażania Visual C++.|
