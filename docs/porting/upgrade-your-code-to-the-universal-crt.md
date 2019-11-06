---
title: Uaktualnienie kodu do Universal CRT
ms.date: 03/31/2017
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
ms.openlocfilehash: 0554ff713b499f99e7e7508faf687c1635e6d912
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627173"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Uaktualnienie kodu do Universal CRT

W programie Visual Studio 2015 został Refaktoryzacja Biblioteka środowiska uruchomieniowego języka Microsoft C (CRT). Standardowa biblioteka C, rozszerzenia POSIX i funkcje specyficzne dla firmy Microsoft, makra i zmienne globalne zostały przeniesione do nowej biblioteki, biblioteki środowiska uruchomieniowego uniwersalnego C (Universal CRT lub UCRT). Składniki CRT charakterystyczne dla kompilatora zostały przeniesione do nowej biblioteki vcruntime.

UCRT jest teraz składnikiem systemu Windows i jest dostarczany jako część systemu Windows 10. UCRT obsługuje stabilną ABI na podstawie Konwencji wywoływania C i jest ściśle zgodna ze standardem ISO C99, z tylko kilkoma wyjątkami. Nie jest już powiązany z określoną wersją kompilatora. UCRT można użyć w dowolnej wersji systemu Windows obsługiwanej przez program Visual Studio 2015 lub Visual Studio 2017. Korzyść polega na tym, że nie trzeba już aktualizować kompilacji, aby docelowa była nowa wersja CRT z każdym uaktualnieniem programu Visual Studio.

W przypadku tego refaktoryzacji nazwy lub lokalizacje wielu plików nagłówka CRT, plików bibliotek i redystrybucyjnych oraz metod wdrażania wymaganych dla Twojego kodu zostały zmienione. Ponadto wiele funkcji i makr w UCRT zostały dodane lub zmienione w celu usprawnienia zgodności ze standardami. Aby móc korzystać z tych zmian, należy zaktualizować istniejący kod i system kompilacji projektu.

## <a name="where-to-find-the-universal-crt-files"></a>Gdzie można znaleźć pliki uniwersalne CRT

Jako składnik systemu Windows pliki i nagłówki biblioteki UCRT są teraz częścią zestawu Windows Software Development Kit (SDK). Podczas instalowania programu Visual Studio instalowane są również części Windows SDK wymagane do korzystania z UCRT. Instalator programu Visual Studio dodaje lokalizacje nagłówków UCRT, bibliotek i plików DLL do domyślnych ścieżek używanych przez system kompilacji projektu programu Visual Studio. Gdy aktualizujesz projekty programu Visual C++ Studio, jeśli korzystają z domyślnych ustawień projektu, IDE automatycznie odnajdzie nowe lokalizacje dla plików nagłówkowych, a konsolidator automatycznie używa nowych domyślnych bibliotek UCRT i vcruntime. Podobnie, jeśli używasz wiersza polecenia programisty do wykonywania kompilacji w wierszu polecenia, zmienne środowiskowe, które zawierają ścieżki do nagłówków i bibliotek, są aktualizowane i działają automatycznie.

Pliki nagłówkowe standardowej biblioteki C znajdują się teraz w Windows SDK w folderze include w katalogu specyficznym dla wersji zestawu SDK. Typowa lokalizacja plików nagłówkowych znajduje się w katalogu Program Files lub Program Files (x86) w systemie Windows Kit\\10\\zawiera\\_SDK-version_\\UCRT, w której _wersja zestawu SDK_ odpowiada wersji systemu Windows lub Aktualizacja, na przykład 10.0.14393.0, dla rocznicowej aktualizacji systemu Windows 10.

Biblioteki statyczne UCRT i biblioteki zastępcze łącza dynamicznego są dostępne w katalogu Program Files lub Program Files (x86) w systemie Windows Kit\\10\\lib\\_zestaw SDK-version_\\UCRT\\_Architecture_, gdzie  _Architektura_ to ARM, x86 lub x64. Statyczne biblioteki sieci sprzedaży i debugowania to libucrt. lib i libucrtd. lib, a biblioteki DLL UCRT to UCRT. lib i ucrtd. lib.

Biblioteki DLL UCRT i Debug są dostępne w oddzielnych lokalizacjach. Biblioteki DLL są redystrybucyjne i znajdują się w katalogu Program Files lub Program Files (x86) w systemie Windows Kit\\10\\Redist\\UCRT\\dll\\_architektura_\. Biblioteki UCRT debugowania nie są redystrybucyjne i znajdują się w katalogu Program Files lub Program Files (x86) w systemie Windows Kit\\10\\bin\\_architektura_\\UCRT.

Biblioteka obsługi środowiska C++ uruchomieniowego języka C i specyficznego dla kompilatora, **vcruntime**, zawiera kod wymagany do obsługi uruchamiania programu oraz funkcji, takich jak obsługa wyjątków i wewnętrzne. Biblioteka i jej pliki nagłówkowe nadal znajdują się w folderze Microsoft Visual Studio specyficznym dla wersji w katalogu Program Files lub Program Files (x86). W programie Visual Studio 2017 nagłówki są dostępne w obszarze Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-Version_\\include i biblioteki linków znajdują się w witrynie Microsoft Visual Studio\\2017\\_edition_\\VC\\Tools\\MSVC\\_lib-version_\\lib\\_Architektura_, gdzie _Edition_ jest wydaniem programu Visual Studio zainstalowana, _lib-Version_ jest wersją bibliotek, a _Architektura_ procesora. Biblioteki linków dla OneCore i sklepu znajdują się również w folderze biblioteki. Wersje detaliczne i Debug biblioteki statycznej są libvcruntime. lib i libvcruntimed. lib. Biblioteki zastępcze dołączania dynamicznego i debugowania są odpowiednio vcruntime. lib i vcruntimed. lib.

Gdy aktualizujesz projekty programu Visual C++ Studio, w przypadku ustawienia właściwości **konsolidatora** projektu **Ignoruj wszystkie domyślne biblioteki** na **tak** lub w przypadku używania `/NODEFAULTLIB` konsolidatora w wierszu polecenia należy zaktualizować listę biblioteki mające na celu uwzględnienie nowych, odczynnikowych bibliotek. Zastąp starą bibliotekę CRT, na przykład libcmt. lib, libcmtd. lib, msvcrt. lib lub msvcrtd. lib, przy użyciu równoważnych bibliotek refaktoryzacji. Aby uzyskać informacje na temat określonych bibliotek do użycia, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Wdrażanie i redystrybucja uniwersalnej CRT

Ponieważ UCRT jest teraz składnikiem systemu operacyjnego Microsoft Windows, jest on częścią systemu operacyjnego Windows 10 i jest dostępny w Windows Update w przypadku starszych systemów operacyjnych, Windows Vista do Windows 8.1. Dostępna jest wersja redystrybucyjna systemu Windows XP. Jako składnik systemu operacyjnego UCRT aktualizacje i obsługa są zarządzane przez Windows Update niezależnie od programu Visual Studio i wersji kompilatorów firmy Microsoft C++ . Ponieważ UCRT to składnik systemu Windows, ze względu na bezpieczeństwo i łatwość aktualizacji oraz mniejszy rozmiar obrazu, zdecydowanie zalecamy centralne wdrożenie UCRT dla aplikacji.

UCRT można użyć w dowolnej wersji systemu Windows obsługiwanej przez program Visual Studio 2015 lub Visual Studio 2017. Można ją ponownie rozpowszechniać za pomocą pakietu VCRedist dla obsługiwanych wersji systemu Windows innych niż Windows 10. Pakiety VCRedist obejmują składniki UCRT i automatycznie instalują je w systemach operacyjnych Windows, które nie są instalowane domyślnie. Aby uzyskać więcej informacji, zobacz [Redystrybuowanie plików wizualnych C++ ](../windows/redistributing-visual-cpp-files.md).

Wdrożenie UCRT na poziomie aplikacji jest obsługiwane, ale nie jest zalecane ze względu na wydajność i bezpieczeństwo. Biblioteki DLL dla wdrożenia aplikacji lokalnych są dołączane jako część Windows SDK w podkatalogu **Redist** . Wymagane biblioteki DLL obejmują ucrtbase. dll i zestaw bibliotek DLL **usługi przesyłania dalej APISet** o nazwie API-ms-win-_podzestaw_. dll. Zestaw bibliotek DLL wymaganych w poszczególnych systemach operacyjnych jest różny, dlatego zaleca się dołączenie wszystkich bibliotek DLL w przypadku używania wdrożenia aplikacji lokalnych. Aby uzyskać dodatkowe informacje i zastrzeżenia dotyczące wdrożenia aplikacji lokalnych, zobacz [wdrażanie w programie Visual C++ ](../windows/deployment-in-visual-cpp.md).

## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Zmiany w funkcjach i makrach uniwersalnej CRT

Wiele funkcji zostało dodanych do UCRT w celu usprawnienia zgodności ISO C99 i rozwiązywania problemów z jakością kodu i zabezpieczeniami. W niektórych przypadkach wymagało to zmiany w bibliotece. Jeśli kod został skompilowany w sposób przejrzysty przy użyciu starszej wersji CRT, ale jest dzielony podczas kompilowania przy użyciu UCRT, należy zmienić kod, aby korzystać z tych aktualizacji i funkcji. Aby zapoznać się ze szczegółową listą istotnych zmian i aktualizacji CRT znalezionych w uniwersalnej CRT, zobacz sekcję [Biblioteka środowiska uruchomieniowego języka C (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) w historii zmian wizualizacji C++ . Zawiera listę odpowiednich nagłówków i funkcji, których można użyć do identyfikowania zmian potrzebnych w kodzie.

## <a name="see-also"></a>Zobacz także

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)<br/>
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Uaktualnianie projektów ze starszych wersji wizualizacjiC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)
