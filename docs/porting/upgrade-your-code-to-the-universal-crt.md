---
title: Uaktualnienie kodu do Universal CRT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/31/2017
ms.topic: conceptual
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2057f3dc8abc3f661010300671b67ad5c37a87d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Uaktualnienie kodu do Universal CRT

W programie Visual Studio 2015 został zrefaktoryzowany biblioteki Microsoft C Runtime (CRT). Standardowa biblioteka języka C, POSIX rozszerzeń i specyficzne dla firmy Microsoft funkcje, makra i zmienne globalne zostały przeniesione do nowej biblioteki uniwersalnego biblioteki środowiska uruchomieniowego C (Universal CRT lub biblioteka UCRT). Składniki specyficzne dla kompilatora CRT zostało przeniesione do nowej biblioteki vcruntime.  
  
Biblioteka UCRT jest teraz składnik systemu Windows i jest dostarczana jako część systemu Windows 10. Biblioteka UCRT obsługuje ABI stabilny, oparte na konwencji wywoływania C i odpowiada ściśle C99 ISO standardowe tylko kilka wyjątków. Nie jest już powiązany z określoną wersją kompilatora. Biblioteka UCRT można użyć w dowolnej wersji systemu Windows obsługiwane przez Visual Studio 2015 lub Visual Studio 2017 r. Korzyścią jest to, że nie należy zaktualizować kompilacji do nowej wersji CRT przy każdym uaktualnieniu programu Visual Studio.  
  
Z tym refaktoryzacji zostały zmienione nazwy lub lokalizacji, w których wiele plików nagłówka CRT, pliki bibliotek i pakietów redystrybucyjnych oraz metody wdrażania wymaganych dla tego kodu. Ponadto wiele funkcjami i makrami w Biblioteka UCRT zostały dodane lub zmienione w celu zwiększenia standardów zgodności. Aby móc korzystać z tych zmian, należy zaktualizować istniejący kod i systemów kompilacji projektu.  
  
## <a name="where-to-find-the-universal-crt-files"></a>Gdzie można znaleźć plików Universal CRT

Jako systemu Windows składnik, biblioteka UCRT pliki bibliotek i nagłówki są teraz częścią zestaw Windows software development kit (SDK). Po zainstalowaniu programu Visual Studio instalowane są również części musieli używać Biblioteka UCRT zestaw Windows SDK. Instalator programu Visual Studio dodaje systemu kompilacji lokalizacje Biblioteka UCRT nagłówków, biblioteki i pliki DLL do domyślnych ścieżek używane przez projekt programu Visual Studio. Po zaktualizowaniu projektów Visual C++, jeśli korzystają z domyślnych ustawień projektu, IDE automatycznie znajdzie nowe lokalizacje dla pliki nagłówkowe, a konsolidator automatycznie używa nowego domyślnego Biblioteka UCRT i bibliotek vcruntime. Podobnie jeśli czy przy użyciu wiersza polecenia dewelopera kompilacje w wierszu polecenia, środowisko, zmiennych, które zawierają ścieżki nagłówków i bibliotek są aktualizowane i automatycznie oraz pracy.  
  
Pliki nagłówka biblioteki standardowe C znajdują się teraz w zestawie SDK systemu Windows w folderze include w katalogu wersji zestawu SDK. Typowy lokalizację plików nagłówka znajduje się w Program Files lub zestawy Windows do katalogu Program Files (x86)\\10\\Include\\_wersja zestawu sdk_\\Biblioteka ucrt, gdzie _wersja zestawu sdk_ odpowiada wersji systemu Windows lub aktualizacji, na przykład 10.0.14393.0 10 Anniversary aktualizacji systemu Windows.   
  
Biblioteka UCRT biblioteki statyczne i biblioteki stub znajdują się w Program Files lub zestawy Windows do katalogu Program Files (x86)\\10\\Lib\\_wersja zestawu sdk_\\Biblioteka ucrt \\ _architektura_, gdzie _architektura_ jest ARM, x 86 lub X64. Biblioteki statyczne handlowych i debugowania są libucrt.lib i libucrtd.lib, i z bibliotekami DLL Biblioteka UCRT są ucrt.lib i ucrtd.lib.  
  
Handlowych i debugowania Biblioteka UCRT biblioteki DLL są dostępne w różnych lokalizacjach. Detalicznej biblioteki DLL są plikami redystrybucyjnymi i znajdują się w Program Files lub zestawy Windows do katalogu Program Files (x86)\\10\\Redist\\Biblioteka ucrt\\biblioteki dll\\_architektury_\. Debugowanie Biblioteka UCRT nie są pakietu redystrybucyjnego bibliotek i znajdują się w Program Files lub zestawy Windows do katalogu Program Files (x86)\\10\\bin\\_architektura_\\Biblioteka ucrt folder.   

C i C++ środowiska wykonawczego specyficzne dla kompilatora pomocy technicznej biblioteki, **vcruntime**, zawiera kod wymagany do uruchomienia programu obsługi i funkcje, takie jak obsługa wyjątków i funkcje wewnętrzne. Biblioteki i jej pliki nagłówkowe, nadal znajdują się w folderze określonej wersji programu Microsoft Visual Studio w sieci Program Files lub Program pliki (x86) katalogu. W programie Visual Studio 2017 r, nagłówki znajdują się w programie Microsoft Visual Studio\\2017\\_wersji_\\VC\\narzędzia\\MSVC\\  _lib-version_\\obejmują i biblioteki DLL są dostępne w programie Microsoft Visual Studio\\2017\\_wersji_\\VC\\narzędzia \\MSVC\\_wersji lib_\\lib\\_architektura_, gdzie _wersji_ jest w wersji programu Visual Studio _wersji lib_ jest wersja biblioteki, i _architektura_ jest architektury procesora. Biblioteki DLL systemem OneCore, a także przechowywać również znajdują się w folderze biblioteki. Wersje detaliczne i debugowania biblioteki statycznej są libvcruntime.lib i libvcruntimed.lib. Biblioteki dołączanej dynamicznie handlowych i debugowania stub są odpowiednio vcruntime.lib i vcruntimed.lib.  
  
Kiedy aktualizować projektów Visual C++, jeśli ustawiono projektu **konsolidatora** właściwości **Ignoruj wszystkie domyślne biblioteki** do **tak** lub jeśli używasz konsolidatora/nodefaultlib opcji w wierszu polecenia, a następnie możesz zaktualizować listę bibliotek, aby uwzględnić nowe, refaktoryzowane biblioteki. Zamień stary biblioteki CRT, na przykład libcmt.lib, libcmtd.lib, msvcrt.lib lub msvcrtd.lib, odpowiednik refactored biblioteki. Aby uzyskać informacje na określone biblioteki do użycia, zobacz [Biblioteka CRT — funkcje](../c-runtime-library/crt-library-features.md).  
  
## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Wdrażanie i rozpowszechnianie Universal CRT
  
Ponieważ biblioteka UCRT teraz jest składnikiem systemu operacyjnego Microsoft Windows, jest dołączane jako część systemu operacyjnego do systemu Windows 10 i jest dostępna za pośrednictwem usługi Windows Update dla starszych systemów operacyjnych Windows Vista za pośrednictwem Windows 8.1. Pakiet redystrybucyjny wersja jest dostępna dla systemu Windows XP. Jako składnik systemu operacyjnego Biblioteka UCRT aktualizacje i obsługa są zarządzane przez usługę Windows Update niezależnie od programu Visual Studio i Microsoft C++ wersja kompilatora. Ponieważ biblioteka UCRT to składnik systemu Windows, zwiększając bezpieczeństwo i ułatwiając, aktualizacji i mniejszy rozmiar obrazu, zdecydowanie zaleca się wdrożenie centralnej Biblioteka UCRT dla aplikacji.  
  
Biblioteka UCRT można użyć w dowolnej wersji systemu Windows obsługiwane przez Visual Studio 2015 lub Visual Studio 2017 r. Można rozpowszechniać za pomocą pakietu programu vcredist obsługiwane wersje systemu Windows, innym niż Windows 10. Pakiety programu vcredist zawiera składniki Biblioteka UCRT i zainstalować je automatycznie w systemach operacyjnych Windows, które nie mają ich instalowane domyślnie. Aby uzyskać więcej informacji, zobacz [redystrybuowanie pliki Visual C++](../ide/redistributing-visual-cpp-files.md).  
  
Wdrażanie lokalnej dla aplikacji Biblioteka UCRT jest obsługiwana, chociaż nie jest zalecana ze względów wydajności i zabezpieczeń. Biblioteki DLL dla wdrożenia lokalnej dla aplikacji są objęte jako część zestawu Windows SDK **redist** podkatalogu. Wymaganych bibliotek DLL obejmują ucrtbase.dll i zestaw **APISet usługi przesyłania dalej** o nazwie interfejsu api biblioteki DLL-ms-win -_podzestawu_dll. Zestaw plików DLL wymaganych w każdym systemie operacyjnym różni się więc zaleca się obejmują wszystkie biblioteki DLL używania wdrożenia lokalnej dla aplikacji. Dodatkowe szczegółowe informacje i ostrzeżenia dotyczące wdrażania lokalnej dla aplikacji, zobacz [wdrożenia w programie Visual C++](../ide/deployment-in-visual-cpp.md).  
  
## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Zmiany Universal CRT funkcjami i makrami  

Wiele funkcji zostały dodane lub zaktualizowane w Biblioteka UCRT, aby zwiększyć zgodność ISO C99, a także do rozwiązywania problemów jakość i bezpieczeństwo kodu. W niektórych przypadkach to wymagane, fundamentalne zmiany w bibliotece. Jeśli kod skompilowany prawidłowo po przy użyciu starszej wersji, ale podziały skompilowany Biblioteka UCRT CRT, należy zmienić swój kod, aby wykorzystać te aktualizacje i funkcje. Lista szczegółowych istotne zmiany i aktualizacje CRT w Universal CRT znajduje się [C Runtime Library (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) historii zmian sekcji Visual C++. Zawiera listę odpowiednich nagłówki i funkcje, które służą do identyfikowania zmian w kodzie.  
  
## <a name="see-also"></a>Zobacz też  

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)  
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)  
[Ulepszenia zgodności języka C++ w programie Visual Studio 2017](../cpp-conformance-improvements-2017.md)  
