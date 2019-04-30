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
ms.openlocfilehash: 2bf4297a6c61d16c68d6a9cb893aed78b9d7609d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388166"
---
# <a name="redistributing-visual-c-files"></a>Redystrybuowanie plików programu Visual C++

> [!NOTE]
> Jesteś tutaj, ponieważ potrzebujesz do pobrania jednego z plików środowiska uruchomieniowego Visual C++? Przejdź do [witrynie internetowej firmy Microsoft](http://www.microsoft.com/) i wprowadź **pakiet redystrybucyjny Visual C++** w polu wyszukiwania. Pobierz i zainstaluj pakiet redystrybucyjny dla architektury komputera — na przykład x64 Jeśli korzystasz z 64-bitowych Windows 64 i wersji programu Visual C++ (na przykład 2015), które są potrzebne.

Podczas wdrażania aplikacji należy również wdrożyć pliki, które są wymagane do jej obsługi. Jeśli któryś z tych plików jest dostarczany przez firmę Microsoft, sprawdź, czy masz pozwolenie na jego redystrybucję. Aby przejrzeć postanowienia licencyjne programu Visual Studio, zobacz łącze postanowień licencyjnych w oknie dialogowym Microsoft Visual Studio IDE lub pobrać [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft](https://visualstudio.microsoft.com/license-terms/mlt687465/) pliku. Aby wyświetlić "Listę REDIST", o której mowa w sekcji "Kod dystrybucyjny" postanowień licencyjnych firmy Microsoft dotyczących niektórych wersji programu Visual Studio, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2017 i Microsoft Visual Studio 2017 Zestaw SDK (obejmuje programy narzędziowe i pliki BuildServer)](/visualstudio/productinfo/2017-redistribution-vs), lub dla programu Visual Studio 2015, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2015 i zestawu Microsoft Visual Studio 2015 SDK](/visualstudio/productinfo/2015-redistribution-vs). Aby uzyskać więcej informacji o plikach przeznaczonych do redystrybucji, zobacz [Determining Which DLLs to Redistribute](determining-which-dlls-to-redistribute.md) i [przykłady wdrożeń](deployment-examples.md).

Aby wdrożyć redystrybuowane pliki Visual C++, można użyć pakietów redystrybucyjnych Visual C++ (VCRedist\_x86.exe, VCRedist\_x64.exe lub VCRedist\_arm.exe) które znajdują się w programie Visual Studio. W programie Visual Studio 2017, te pliki znajdują się w folderze Program Files [(x86)]\\programu Microsoft Visual Studio\\2017\\_wersji_\\VC\\Redist\\ MSVC\\_lib-version_ folderu, gdzie _wersji_ wydanie programu Visual Studio zainstalowane, i _lib wersji_ stanowi wersję biblioteki, aby ponownie rozesłać. W programie Visual Studio 2015, te pliki znajdują się w katalogu instalacji programu Visual Studio w Program Files [(x 86)] \Microsoft Visual Studio *wersji*\VC\redist\\*ustawień regionalnych* \\. Innym rozwiązaniem jest użycie redystrybucyjne moduły scalania (pliki .msm), które w programie Visual Studio 2017 można znaleźć w folderze Program Files [(x 86)]\\programu Microsoft Visual Studio\\2017\\_wersji_ \\ VC\\Redist\\MSVC\\_wersji lib_\\MergeModules\\ folderu. W programie Visual Studio 2015 te znajdują się w Program Files [(x 86)] \Common modułów\\. Istnieje również możliwość bezpośrednio zainstalować pakiet redystrybucyjny bibliotek DLL Visual C++ w *lokalnego folderu aplikacji*, czyli do folderu, który zawiera plik wykonywalny aplikacji. Obsługę przyczyny, zaleca się, że używasz tej lokalizacji instalacji.

Pakiety redystrybucyjne Visual C++ instalują i rejestrują wszystkie biblioteki Visual C++. Jeśli używasz któregoś z nich, musisz ustawić jego uruchomienie w systemie docelowym jako warunek wstępny do instalacji aplikacji. Zaleca się używanie tych pakietów dla wdrożeń, ponieważ umożliwiają one automatyczne aktualizowanie bibliotek Visual C++. Na przykład o tym, jak używać tych pakietów, zobacz [instruktażu: Wdrażanie aplikacji Visual C++ przy użyciu pakietu redystrybucyjnego Visual C++](deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).

Każdy pakiet Visual C++ Redistributable sprawdza istnienie nowszą wersję na tym komputerze. Jeśli zostanie znaleziony nowszej wersji, pakiet nie jest zainstalowany. Począwszy od programu Visual Studio 2015, pakiety redystrybucyjne wyświetlania komunikatu o błędzie informujący, że Instalator nie powiodło się. Jeśli pakiet jest uruchamiany za pomocą **/quiet** flagę bez komunikatu o błędzie jest wyświetlany. W obu przypadkach zostanie zarejestrowany błąd przez Instalatora firmy Microsoft, a wynik błędu jest zwracany do obiektu wywołującego. Począwszy od pakietów programu Visual Studio 2015, możesz uniknąć tego błędu, sprawdzając w rejestrze, aby dowiedzieć się, jeśli jest zainstalowana nowsza wersja. Obecnie zainstalowanej wersji jest przechowywany w \Microsoft\VisualStudio HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node]\\_wersji programu vs_\VC\Runtimes\\{x86 | x64 | Klucz ARM}, gdzie _wersji programu vs_ jest numer wersji dla programu Visual Studio (14.0 zarówno dla programu Visual Studio 2015 i Visual Studio 2017, ponieważ 2017 r. zaktualizowany pakiet redystrybucyjny binarnym zgodny z wersji 2015), oraz w których klucz ARM, x 86 lub x64 w zależności od wersji zainstalowanego programu vcredist platformy. (Nie trzeba sprawdzić w podkluczu Wow6432Node, chyba że używasz RegEdit, aby wyświetlić wersję zainstalowanego x86 pakiet na x64 platformy.) Numer wersji jest przechowywany w wartości ciągu REG_SZ **wersji** , a także w zestawie **głównych**, **pomocnicza**, **Bld**i **Rbld** wartości REG_DWORD. Aby uniknąć błąd w czasie instalacji, możesz pominąć instalacji pakietu redystrybucyjnego, jeśli aktualnie zainstalowana wersja jest nowsza.

Jeśli używasz modułu scalania, która zawiera biblioteki DLL Visual C++, należy ją dołączyć w pakietu Instalatora Windows (lub podobnego pakietu instalacyjnego), którego używasz, aby wdrożyć aplikację. Aby uzyskać więcej informacji, zobacz [Redystrybucja za pomocą scalonych modułów](redistributing-components-by-using-merge-modules.md). Aby uzyskać przykład, zobacz [instruktażu: Wdrażanie programu Visual C++ Application By Using projektu Instalatora](walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), który ilustruje również używać programu InstallShield Limited Edition do utworzenia pakietu instalacyjnego.

## <a name="potential-run-time-errors"></a>Potencjalne błędy czasu wykonywania

Jeśli Windows nie można odnaleźć jednego z biblioteki DLL wymaganej dla aplikacji, może zostać wyświetlony komunikat podobny do następującego: "Tej aplikacji nie powiodło się, ponieważ *biblioteki*.dll nie został znaleziony. Ponowne zainstalowanie aplikacji może naprawić ten problem."

Aby rozwiązać tego rodzaju błąd, upewnij się, że Instalatorem aplikacji poprawnie się kompiluje i redystrybucyjnych bibliotek są prawidłowo wdrożone w systemie docelowym. Aby uzyskać więcej informacji, zobacz [poznanie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Redystrybucja za pomocą modułów scalania](redistributing-components-by-using-merge-modules.md)|Opisuje sposób używania wizualizacji C++ redystrybucyjnych modułów scalania do zainstalowania wizualizacji C++ bibliotek środowiska uruchomieniowego jako współdzielone Dlll w folderze %windir%\system32\.|
|[Ponowne dystrybuowanie kontrolek ActiveX programu Visual C++](redistributing-visual-cpp-activex-controls.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z formantów ActiveX.|
|[Ponowne dystrybuowanie biblioteki MFC](redistributing-the-mfc-library.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z MFC.|
|[Ponowne dystrybuowanie aplikacji ATL](redistributing-an-atl-application.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z ATL. Począwszy od programu Visual Studio 2012, nie biblioteki dla biblioteki ATL jest wymagany.|
|[Przykłady wdrożeń](deployment-examples.md)|Zawiera łącza do przykładów, które pokazują sposób wdrażania aplikacji Visual C++.|
|[Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)|Wprowadza koncepcje i technologie wdrażania Visual C++.|