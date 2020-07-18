---
title: Redystrybuowanie plików programu Visual C++
description: Program Visual Studio zawiera biblioteki i składniki redystrybucyjne, które można wdrożyć za pomocą aplikacji.
ms.date: 07/16/2020
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
ms.openlocfilehash: 7a639f7ad7deb76cade47b0162012dcb70cb0d69
ms.sourcegitcommit: e15b46ea7888dbdd7e0bb47da76aeed680c3c1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86446756"
---
# <a name="redistributing-visual-c-files"></a>Redystrybuowanie plików programu Visual C++

> [!NOTE]
> Jesteś tutaj, ponieważ szukasz pobrania jednego z plików środowiska uruchomieniowego Visual C++? Przejdź do [witryny sieci Web firmy Microsoft](https://www.microsoft.com/) i wprowadź **Visual C++ redystrybucyjny** w polu wyszukiwania. Pobierz i zainstaluj pakiet redystrybucyjny dla architektury komputera (na przykład x64, jeśli używasz 64-bitowego systemu Windows) i wersji Visual C++ (na przykład 2015).

## <a name="redistributable-files-and-licensing"></a>Pliki redystrybucyjne i Licencjonowanie

Podczas wdrażania aplikacji należy również wdrożyć pliki, które są wymagane do jej obsługi. Jeśli którykolwiek z tych plików jest dostarczany przez firmę Microsoft, sprawdź, czy masz uprawnienia do ich rozpowszechniania. Znajdziesz link do postanowień licencyjnych programu Visual Studio w środowisku IDE. Użyj linku postanowienia licencyjne w oknie dialogowym informacje Microsoft Visual Studio. Lub Pobierz odpowiednie umowy licencyjne i licencje z [katalogu licencji](https://visualstudio.microsoft.com/license-terms/)programu Visual Studio.

::: moniker range="vs-2019"

Aby wyświetlić "listę Redist", o której mowa w sekcji "Kod dystrybucyjny" postanowień licencyjnych dotyczących oprogramowania w programie Visual Studio 2019, zobacz [pliki kodu dystrybucyjnego dla Microsoft Visual Studio 2019](/visualstudio/releases/2019/redistribution#-distributable-code-files-for-visual-studio-2019)

::: moniker-end

::: moniker range="vs-2017"

Aby wyświetlić "listę Redist", o której mowa w punkcie "Kod dystrybucyjny" postanowień licencyjnych dotyczących oprogramowania w programie Visual Studio 2017, zobacz [pliki kodu dystrybucyjnego dla Microsoft Visual Studio 2017](/visualstudio/productinfo/2017-redistribution-vs#-distributable-code-files-for-visual-studio-2017).

::: moniker-end

::: moniker range="vs-2015"

Aby wyświetlić "listę Redist", o której mowa w punkcie "Kod dystrybucyjny" postanowień licencyjnych dotyczących oprogramowania w programie Visual Studio 2015, zobacz [pliki kodu dystrybucyjnego dla Microsoft Visual Studio 2015](/visualstudio/productinfo/2015-redistribution-vs#-distributable-code-files-for-visual-studio-2015).

::: moniker-end

Aby uzyskać więcej informacji na temat redystrybucyjnych plików, zobacz [Określanie bibliotek DLL do dystrybucji](determining-which-dlls-to-redistribute.md) i [wdrażania przykładów](deployment-examples.md).

## <a name="locate-the-redistributable-files"></a>Lokalizowanie plików redystrybucyjnych

Aby wdrożyć pliki redystrybucyjne, można użyć pakietów redystrybucyjnych zainstalowanych przez program Visual Studio. W wersjach programu Visual Studio od 2017 te pliki mają nazwy *`vc_redist.arm64.exe`* , *`vc_redist.x64.exe`* i *`vc_redist.x86.exe`* . W programie Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019 są one również dostępne pod nazwami *`vcredist_x86.exe`* , *`vcredist_x64.exe`* i *`vcredist_arm.exe`* (tylko 2015).

Najprostszym sposobem lokalizowania plików redystrybucyjnych jest użycie zmiennych środowiskowych ustawionych w wierszu polecenia dewelopera. W najnowszej wersji programu Visual Studio 2019 znajdują się pliki redystrybucyjne znajdujące się w *`%VCINSTALLDIR%Redist\MSVC\v142`* folderze. Zarówno w programie Visual Studio 2017, jak i w programie Visual Studio 2019 znajdują się one również w temacie *`%VCToolsRedistDir%`* . W programie Visual Studio 2015 te pliki znajdują się w *`%VCINSTALLDIR%redist\<locale>`* lokalizacji, gdzie *`<locale>`* jest ustawieniami regionalnymi pakietów redystrybucyjnych.

Inną opcją wdrożenia jest użycie redystrybucyjnych modułów scalania ( *`.msm`* plików). W programie Visual Studio 2019 te pliki są częścią opcjonalnego składnika instalowalnego o nazwie **C++ 2019 redystrybucyjny MSMs** w Instalator programu Visual Studio. Moduły scalania są instalowane domyślnie w ramach instalacji C++ w programie Visual Studio 2017 i Visual Studio 2015. Po zainstalowaniu w najnowszej wersji programu Visual Studio 2019 w programie znajdują się moduły scalania redystrybucyjne *`%VCINSTALLDIR%Redist\MSVC\v142\MergeModules`* . Zarówno w programie Visual Studio 2019, jak i w programie Visual Studio 2017 znajdują się one również w temacie *`%VCToolsRedistDir%MergeModules`* . W programie Visual Studio 2015 znajdują się one w temacie *`Program Files [(x86)]\Common Files\Merge Modules`* .

## <a name="install-the-redistributable-packages"></a>Instalowanie pakietów redystrybucyjnych

Pakiety redystrybucyjne Visual C++ instalują i rejestrują wszystkie biblioteki Visual C++. Jeśli używasz jednego z nich, uruchom go jako warunek wstępny w systemie docelowym przed zainstalowaniem aplikacji. Zaleca się używanie tych pakietów dla wdrożeń, ponieważ umożliwiają one automatyczne aktualizowanie bibliotek Visual C++. Aby zapoznać się z przykładem dotyczącym korzystania z tych pakietów, zobacz [Przewodnik: wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Każdy Visual C++ pakiet redystrybucyjny sprawdza obecność nowszej wersji na komputerze. Jeśli zostanie znaleziona nowsza wersja, pakiet nie zostanie zainstalowany. Począwszy od programu Visual Studio 2015, pakiety redystrybucyjne wyświetlają komunikat o błędzie z informacją, że instalacja nie powiodła się. Jeśli pakiet jest uruchamiany przy użyciu **`/quiet`** flagi, żaden komunikat o błędzie nie jest wyświetlany. W obu przypadkach błąd jest rejestrowany przez Instalatora Microsoft i zwracany jest wynik błędu do obiektu wywołującego. Począwszy od pakietów programu Visual Studio 2015, możesz uniknąć tego błędu, sprawdzając rejestr, aby dowiedzieć się, czy jest zainstalowana nowsza wersja. Bieżący zainstalowany numer wersji jest przechowywany w `HKEY_LOCAL_MACHINE\SOFTWARE[\Wow6432Node]\Microsoft\VisualStudio\14.0\VC\Runtimes\{x86|x64|ARM}` kluczu. Numer wersji to 14,0 dla programu Visual Studio 2015, Visual Studio 2017 i Visual Studio 2019, ponieważ najnowszy pakiet redystrybucyjny jest zgodny z wersją 2015. Klucz to `ARM` , `x86` lub `x64` w zależności od zainstalowanych wersji VCRedist dla platformy. (Należy zaznaczyć ten podklucz tylko wtedy, gdy używasz programu `Wow6432Node` regedit do wyświetlania wersji zainstalowanego pakietu x86 na platformie x64). Numer wersji jest przechowywany w wartości ciągu REG_SZ, **`Version`** a także w zestawie **`Major`** **`Minor`** wartości,, **`Bld`** i **`Rbld`** `REG_DWORD` . Aby uniknąć błędu podczas instalacji, należy pominąć instalację pakietu redystrybucyjnego, jeśli aktualnie zainstalowana wersja jest nowsza.

## <a name="install-the-redistributable-merge-modules"></a>Zainstaluj Redystrybucyjne moduły scalania

Moduły scalania redystrybucyjne muszą być zawarte w pakiecie Instalator Windows (lub podobnym pakiecie instalacyjnym) używanym do wdrażania aplikacji. Aby uzyskać więcej informacji, zobacz [Redystrybucja przy użyciu modułów scalania](redistributing-components-by-using-merge-modules.md). Aby zapoznać się z przykładem, zobacz [Przewodnik: wdrażanie aplikacji Visual C++ przy użyciu projektu Instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md).

## <a name="install-individual-redistributable-files"></a>Instalowanie pojedynczych plików redystrybucyjnych

Możliwe jest również bezpośrednie zainstalowanie bibliotek DLL redystrybucyjnych w *folderze lokalnym aplikacji*. To jest folder, który zawiera plik wykonywalny aplikacji. Ze względów związanych z obsługą nie zalecamy korzystania z tej lokalizacji instalacji.

## <a name="potential-run-time-errors"></a>Potencjalne błędy czasu wykonywania

Jeśli system Windows nie może odnaleźć jednej z bibliotek DLL biblioteki redystrybucyjnej wymaganej przez aplikację, może zostać wyświetlony komunikat podobny do: "nie można uruchomić tej aplikacji, ponieważ nie znaleziono *biblioteki*dll. Ponowne zainstalowanie aplikacji może rozwiązać ten problem ".

Aby rozwiązać ten rodzaj błędu, upewnij się, że Instalator aplikacji poprawnie kompiluje. Sprawdź, czy biblioteki redystrybucyjne zostały poprawnie wdrożone w systemie docelowym. Aby uzyskać więcej informacji, zobacz [Omówienie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-articles"></a>Pokrewne artykuły:

[Redystrybucja przy użyciu modułów scalania](redistributing-components-by-using-merge-modules.md)\
Opisuje sposób użycia Visual C++ redystrybucyjnych modułów scalania do instalowania bibliotek środowiska uruchomieniowego Visual C++ jako udostępnionych bibliotek DLL w *`%windir%\system32\`* folderze.

[Redystrybucja Visual C++ kontrolek ActiveX](redistributing-visual-cpp-activex-controls.md)\
Opisuje sposób rozpowszechniania aplikacji korzystającej z formantów ActiveX.

[Redystrybuowanie biblioteki MFC](redistributing-the-mfc-library.md)\
Opisuje sposób rozpowszechniania aplikacji korzystającej z MFC.

[Redystrybuowanie aplikacji ATL](redistributing-an-atl-application.md)\
Opisuje sposób rozpowszechniania aplikacji korzystającej z biblioteki ATL. Począwszy od programu Visual Studio 2012, nie jest wymagana biblioteka redystrybucyjna ATL.

[Przykłady wdrożeń](deployment-examples.md)\
Zawiera łącza do przykładów, które pokazują sposób wdrażania aplikacji Visual C++.

[Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)\
Wprowadza koncepcje i technologie wdrażania Visual C++.
