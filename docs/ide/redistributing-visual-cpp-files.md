---
title: "Redystrybuowanie plików programu Visual C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- application deployment [C++], file redistributing
- redistributing applications [C++]
- deploying applications [C++], file redistributing
- file redistribution [C++]
- redistributing applications [C++], about redistributing applications
ms.assetid: d201b2ce-36f1-44e5-a96c-0db81a1ba652
caps.latest.revision: "50"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 106123557c4efab5ccddf9f1292570d36b0f8313
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="redistributing-visual-c-files"></a>Redystrybuowanie plików programu Visual C++
Podczas wdrażania aplikacji należy również wdrożyć pliki, które są wymagane do jej obsługi. Jeśli któryś z tych plików jest dostarczany przez firmę Microsoft, sprawdź, czy masz pozwolenie na jego redystrybucję. Aby przejrzeć postanowienia licencyjne programu Visual Studio, zobacz łącze postanowień licencyjnych w oknie dialogowym Microsoft Visual Studio IDE lub pobrać [postanowienia licencyjne dotyczące oprogramowania firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=831114) pliku. Aby wyświetlić "Lista REDYSTRYBUCYJNA", o której mowa w sekcji "Kod dystrybucyjny" postanowień licencyjnych oprogramowania firmy Microsoft do niektórych wydań programu Visual Studio, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2017 i 2017 r Microsoft Visual Studio Zestaw SDK (obejmuje narzędzia i pliki BuildServer)](http://go.microsoft.com/fwlink/p/?LinkId=823098), lub dla programu Visual Studio 2015, zobacz [Kod dystrybucyjny dla programu Microsoft Visual Studio 2015 i Microsoft Visual Studio 2015 SDK](http://go.microsoft.com/fwlink/p/?LinkId=523763). Aby uzyskać więcej informacji na temat plików pakietu redystrybucyjnego zobacz [określania które biblioteki dll do ponownej dystrybucji](../ide/determining-which-dlls-to-redistribute.md) i [przykłady wdrożeń](../ide/deployment-examples.md).  
  
 Aby wdrożyć pakiet redystrybucyjny Visual C++ pliki, można użyć pakiety Visual C++ Redistributable (program VCRedist\_x86.exe, program VCRedist\_x64.exe lub program VCRedist\_arm.exe) dostępnych w programie Visual Studio. W programie Visual Studio 2017 r, te pliki znajdują się w folderze Program Files [(x86)]\\programu Microsoft Visual Studio\\2017\\_wersji_\\VC\\Redist\\ MSVC\\_wersji lib_ folder, gdzie _wersji_ jest w wersji Visual Studio zainstalowany, i _wersji lib_ jest wersja biblioteki, aby ponownie rozesłać. W programie Visual Studio 2015, te pliki znajdują się w katalogu instalacyjnym programu Visual Studio w Program Files [(x 86)] \Microsoft Visual Studio *wersji*\VC\redist\\*ustawień regionalnych* \\. Inną opcją jest użycie modułów scalania redistributable (pliki .msm), które w Visual Studio 2017 znajduje się w folderze Program Files [(x 86)]\\programu Microsoft Visual Studio\\2017\\_wersji_ \\ VC\\Redist\\MSVC\\_wersji lib_\\MergeModules\\ folderu. W programie Visual Studio 2015 te można znaleźć w \Common Files\Merge Program Files [(x 86)] modułów\\. Istnieje również możliwość bezpośrednio zainstaluj pakiet redystrybucyjny Visual dll języka C++ w *aplikacji w lokalnym folderze*, która jest folder zawierający plik wykonywalny aplikacji. Do obsługi przyczyn, nie zaleca się używanie tej lokalizacji instalacji.  
  
 Pakiety redystrybucyjne Visual C++ instalują i rejestrują wszystkie biblioteki Visual C++. Jeśli używasz któregoś z nich, musisz ustawić jego uruchomienie w systemie docelowym jako warunek wstępny do instalacji aplikacji. Zaleca się używanie tych pakietów dla wdrożeń, ponieważ umożliwiają one automatyczne aktualizowanie bibliotek Visual C++. Na przykład o tym, jak używać tych pakietów, zobacz [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą pakietu redystrybucyjnego Visual C++](../ide/deploying-visual-cpp-application-by-using-the-vcpp-redistributable-package.md).  
  
 Pakiet redystrybucyjny każdego Visual C++ sprawdza istnienie nowszą wersję na tym komputerze. Jeśli zostanie znaleziony nowszej wersji, pakiet nie jest zainstalowany. Począwszy od programu Visual Studio 2015, wyświetlania pakiety redystrybucyjne komunikat o błędzie informujący o tym Instalatora nie powiodło się. Jeśli pakiet jest uruchamiany za pomocą **/quiet** flagi, żaden komunikat o błędzie jest wyświetlany. W obu przypadkach przez Instalatora Microsoft jest rejestrowany błąd, a wynik jest zwracany do obiektu wywołującego. Począwszy od programu Visual Studio 2015 pakietów, możesz uniknąć tego błędu, sprawdzania rejestru, aby dowiedzieć się, jeśli jest zainstalowana nowsza wersja. Aktualnie zainstalowana wersja jest przechowywana w kluczu HKEY_LOCAL_MACHINE\SOFTWARE [\Wow6432Node] \Microsoft\VisualStudio\\_wersji programu vs_\VC\Runtimes\\{x86 | x64 | Klucz ARM}, gdzie _wersji programu vs_ jest numer wersji dla programu Visual Studio (14.0 zarówno dla programu Visual Studio 2015 i Visual Studio 2017 r, ponieważ zaktualizowany pakiet redystrybucyjny 2017 r może binarnej wersji 2015), i gdy jest klucz ARM x 86 lub x64 w zależności od wersji zainstalowanego programu vcredist platformy. (Nie trzeba sprawdzać podkluczu Wow6432Node, chyba że używasz RegEdit, aby wyświetlić wersję zainstalowanego x86 pakiet na x64 platformy.) Numer wersji jest przechowywany w wartości ciągu REG_SZ **wersji** , a także w zestawie **głównych**, **pomocnicza**, **Bld**i **Rbld** wartości REG_DWORD. Aby uniknąć błędów w czasie instalacji, możesz pominąć instalacja pakietu redystrybucyjnego, jeśli aktualnie zainstalowana wersja jest nowsza.  
  
 Jeśli używasz moduł scalania, który zawiera bibliotekę DLL programu Visual C++, należy go dołączyć w pakiet Instalatora Windows (lub podobny pakiet instalacyjny), używanej do wdrożenia aplikacji. Aby uzyskać więcej informacji, zobacz [redystrybuowanie przez za pomocą scalania modułów](../ide/redistributing-components-by-using-merge-modules.md). Na przykład zobacz [wskazówki: Wdrażanie Visual C++ aplikacji za pomocą instalacji projektu](../ide/walkthrough-deploying-a-visual-cpp-application-by-using-a-setup-project.md), która również przedstawia sposób użycia InstallShield Limited Edition można utworzyć pakietu instalacyjnego.  
  
## <a name="potential-run-time-errors"></a>Potencjalne błędy czasu wykonywania  
 Biblioteka DLL Visual C++ nie jest dostępny i systemu Windows nie może załadować aplikacji, ten komunikat może być wyświetlany: **tej aplikacji nie powiodło się, ponieważ MSVCR\<numer wersji > nie znaleziono biblioteki dll. Ponowne zainstalowanie aplikacji może naprawić ten problem.**  
  
 Aby rozwiązać tego rodzaju błąd, upewnij się, że aplikacja poprawnie się kompiluje i że biblioteki Visual C++ są prawidłowo wdrożone w systemie docelowym. Aby uzyskać więcej informacji, zobacz [poznanie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md).  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Redystrybucja za pomocą modułów scalania](../ide/redistributing-components-by-using-merge-modules.md)|Informacje dotyczące używania modułów scalania pakietu redystrybucyjnego Visual C++ do zainstalowania bibliotek środowiska uruchomieniowego Visual C++ jako udostępnionej biblioteki dll w folderze %windir%\system32\.|  
|[Ponowne dystrybuowanie kontrolek ActiveX programu Visual C++](../ide/redistributing-visual-cpp-activex-controls.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z formantów ActiveX.|  
|[Ponowne dystrybuowanie plików obsługi baz danych](../ide/redistributing-database-support-files.md)|Omawia, w jaki sposób przeprowadzać redystrybucję plików obsługi dla obiektów Data Access (DAO) oraz technologie bazy danych w programie Microsoft Data Access SDK.|  
|[Ponowne dystrybuowanie biblioteki MFC](../ide/redistributing-the-mfc-library.md)|Opisuje sposób rozpowszechniania aplikacji korzystającej z MFC.|  
|[Ponowne dystrybuowanie aplikacji ATL](../ide/redistributing-an-atl-application.md)|Zawiera opis sposobu ponownej dystrybucji aplikacji, która używa ATL. Począwszy od programu Visual Studio 2012 nie pakietu redystrybucyjnego biblioteki ATL jest wymagany.|  
|[Przykłady wdrożeń](../ide/deployment-examples.md)|Zawiera łącza do przykładów, które pokazują sposób wdrażania aplikacji Visual C++.|  
|[Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)|Wprowadza koncepcje i technologie wdrażania Visual C++.|