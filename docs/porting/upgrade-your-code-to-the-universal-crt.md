---
title: Uaktualnienie kodu do Universal CRT
ms.date: 03/31/2017
ms.assetid: eaf34c1b-da98-4058-a059-a10db693a5ce
ms.openlocfilehash: bdf1615d47361654e9690977520d01c332098438
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58898768"
---
# <a name="upgrade-your-code-to-the-universal-crt"></a>Uaktualnienie kodu do Universal CRT

W programie Visual Studio 2015 został wycofany biblioteki Microsoft C Runtime (CRT). Standardowej biblioteki C, rozszerzenia POSIX i specyficzne dla firmy Microsoft funkcje, makra i zmienne globalne zostały przeniesione do nowej biblioteki Universal biblioteki środowiska uruchomieniowego języka C (Universal CRT lub UCRT). Składniki specyficznych dla kompilatora CRT zostało przeniesione do nowej biblioteki vcruntime.

UCRT jest teraz składnika Windows i jest dostarczany jako część systemu Windows 10. UCRT obsługuje stabilnej ABI, oparte na konwencji wywoływania języka C, a jest zbliżony do ISO C99 w warstwie standardowa przy użyciu tylko kilka wyjątków. Nie jest już powiązany do określonej wersji kompilatora. UCRT można użyć w dowolnej wersji systemu Windows, obsługiwane przez program Visual Studio 2015 lub Visual Studio 2017. Korzyścią jest to, że już nie musisz zaktualizować swoich kompilacjach, aby odwoływać się do nowej wersji CRT przy każdym uaktualnieniu programu Visual Studio.

Za pomocą tej refaktoryzacji zostały zmienione nazwy lub lokalizacje, wiele plików nagłówkowych CRT, pliki bibliotek i pakietów redystrybucyjnych i metody wdrażania wymaganych dla kodu. Ponadto wiele funkcji i makr w UCRT zostały dodane lub zmienione w celu zwiększenia zgodność ze standardami. Aby móc korzystać z tych zmian, należy zaktualizować istniejący kod i systemów kompilacji projektu.

## <a name="where-to-find-the-universal-crt-files"></a>Gdzie można znaleźć plików Universal CRT

Jako Windows składnika, UCRT pliki biblioteki i nagłówki są teraz częścią zestaw Windows software development kit (SDK). Podczas instalowania programu Visual Studio instalowane są również elementy wymagane do użycia UCRT SDK Windows. Instalator programu Visual Studio dodaje system kompilacji lokalizacje UCRT nagłówki, biblioteki i pliki DLL do ścieżek domyślnych używanych przez projekt programu Visual Studio. Po zaktualizowaniu projektów Visual C++, jeśli korzystają z domyślnego ustawienia projektu, IDE automatycznie znajdzie nowe lokalizacje dla plików nagłówkowych i konsolidator automatycznie używa nowe rozwiązanie domyślne UCRT i bibliotek vcruntime. Podobnie jeśli używasz wiersz polecenia dla deweloperów w celu kompilacje w wierszu polecenia, środowisko, zmiennych, które zawierają ścieżki nagłówki i biblioteki są aktualizowane i pracy oraz automatycznie.

Pliki nagłówkowe standardowej biblioteki C znajdują się teraz w zestawie Windows SDK w folderze dołączenia w katalogu specyficzny dla wersji zestawu SDK. Typowej lokalizacji plików nagłówka znajduje się w katalogu Program Files (x86) zestawy Windows lub Program Files\\10\\Include\\_wersja zestawu sdk_\\ucrt, gdzie _wersja zestawu sdk_ odnosi się do wersji Windows lub aktualizacja, na przykład 10.0.14393.0 10 Rocznicowej aktualizacji systemu Windows.

UCRT bibliotek statycznych i biblioteki klasy zastępczej znajdują się w katalogu Program Files (x86) zestawy Windows lub Program Files\\10\\Lib\\_wersja zestawu sdk_\\ucrt \\ _architektury_, gdzie _architektury_ jest ARM, x 86 lub X64. Handel detaliczny i debugowania bibliotek statycznych są libucrt.lib i libucrtd.lib i biblioteki dla biblioteki DLL UCRT są ucrt.lib i ucrtd.lib.

Handel detaliczny i debugowania bibliotek DLL UCRT znajdują się w różnych lokalizacjach. Handel detaliczny biblioteki DLL są plikami redystrybucyjnymi i znajduje się w katalogu Program Files (x86) zestawy Windows lub Program Files\\10\\Redist\\ucrt\\biblioteki dll\\_architektury_\. Debugowanie UCRT nie są pakiet redystrybucyjny bibliotek i znajdują się w katalogu Program Files (x86) zestawy Windows lub Program Files\\10\\bin\\_architektury_\\ucrt folder.

C i C++ specyficzne dla kompilatora Biblioteka środowiska uruchomieniowego pomocy technicznej, **vcruntime**, zawiera kod wymagany do uruchamiania programu obsługi i funkcje, takie jak obsługa wyjątków i funkcje wewnętrzne. Biblioteki i jej plików nagłówkowych, nadal znajdują się w folderze specyficzny dla wersji programu Microsoft Visual Studio w katalogu Program files (x86) lub Program Files. W programie Visual Studio 2017, nagłówki znajdują się w ramach programu Microsoft Visual Studio\\2017\\_wersji_\\VC\\narzędzia\\MSVC\\  _lib-version_\\obejmują i biblioteki łączone znajdują się w ramach programu Microsoft Visual Studio\\2017\\_wersji_\\VC\\narzędzia \\MSVC\\_wersji lib_\\lib\\_architektury_, gdzie _wersji_ wersja programu Visual Studio _wersji lib_ stanowi wersję biblioteki, i _architektury_ jest architektury procesora. Biblioteki DLL OneCore i Store również znajdują się w folderze bibliotek. Handel detaliczny i debugowania wersji biblioteki statycznej to libvcruntime.lib i libvcruntimed.lib. Biblioteki łączone dynamicznie handel detaliczny i debugowania wycinka są vcruntime.lib i vcruntimed.lib, odpowiednio.

Gdy aktualizacja projektów Visual C++, jeśli ustawisz projekt **konsolidatora** właściwość **Ignoruj wszystkie domyślne biblioteki** do **tak** lub jeśli używasz `/NODEFAULTLIB` — Opcja konsolidatora w wierszu polecenia, następnie należy zaktualizować listy biblioteki do uwzględnienia nowej, wycofanej bibliotek. Zastąp stare biblioteki CRT, na przykład biblioteki libcmt.lib, libcmtd.lib, msvcrt.lib lub biblioteki msvcrtd.lib, równoważne wycofanej bibliotek. Aby uzyskać informacji na temat określonej biblioteki do użycia, zobacz [funkcje biblioteki CRT](../c-runtime-library/crt-library-features.md).

## <a name="deployment-and-redistribution-of-the-universal-crt"></a>Wdrażanie i rozpowszechniania Universal CRT

Ponieważ UCRT jest obecnie składnikiem systemu operacyjnego Microsoft Windows, jest dołączony jako część systemu operacyjnego w systemie Windows 10 i jest dostępna za pośrednictwem usługi Windows Update dla starszych systemów operacyjnych Windows Vista do Windows 8.1. W wersji redystrybucyjnej jest dostępna dla Windows XP. Jako składnik systemu operacyjnego UCRT aktualizacje i obsługa są zarządzane przez usługę Windows Update niezależnie od wersji kompilatora Visual Studio i Microsoft C++. Ponieważ UCRT to składnik Windows, bezpieczeństwo i łatwość aktualizacji i mniejszy rozmiar obrazu, zdecydowanie zalecamy centralne wdrożenie UCRT dla aplikacji.

UCRT można użyć w dowolnej wersji systemu Windows, obsługiwane przez program Visual Studio 2015 lub Visual Studio 2017. Można redystrybuować go za pomocą pakietu vcredist dla obsługiwanych wersji systemu Windows innych niż Windows 10. Pakiety programu vcredist zawiera składniki UCRT i automatycznie instalowane w systemach operacyjnych Windows, które nie masz je zainstalowane domyślnie. Aby uzyskać więcej informacji, zobacz [Redistributing Visual C++ Files](../windows/redistributing-visual-cpp-files.md).

Wdrożenia lokalnego dla aplikacji UCRT jest obsługiwane, ale niezalecane ze względów wydajności i zabezpieczeń. Biblioteki DLL dla wdrożenia lokalnego dla aplikacji zostały dołączone jako część zestawu Windows SDK, w obszarze **redist** podkatalogu. Biblioteki DLL wymagane obejmują ucrtbase.dll oraz zestaw **APISet usługi przesyłania dalej** biblioteki dll o nazwie interfejsu api-ms-win -_podzbioru_.dll. Różni się zbiór bibliotek DLL wymagane w każdym systemie operacyjnym, dlatego zaleca się obejmują wszystkie biblioteki DLL korzystając z wdrożenia lokalnego dla aplikacji. Dodatkowe szczegóły i ostrzeżenia dotyczące wdrożenia lokalnego dla aplikacji, zobacz [wdrożenia w programie Visual C++](../windows/deployment-in-visual-cpp.md).

## <a name="changes-to-the-universal-crt-functions-and-macros"></a>Zmiany w funkcji Universal CRT i makra

Wiele funkcji dodane lub zaktualizowane w UCRT w celu zwiększenia zgodności ISO C99 i adresem kod jakości i zagadnienia dotyczące zabezpieczeń. W niektórych przypadkach to wymagane, istotne zmiany w bibliotece. Jeśli kod jest kompilowany nie pozostawia żadnych śladów podczas przy użyciu starszej wersji CRT, ale przerwy podczas kompilowania przy użyciu UCRT, należy zmienić swój kod, aby korzystać z zalet te aktualizacje i funkcje. Aby uzyskać szczegółową listę przełomowe zmiany i aktualizacje CRT w Universal CRT, zobacz [biblioteki środowiska uruchomieniowego C (CRT)](visual-cpp-change-history-2003-2015.md#BK_CRT) historię zmian w sekcji Visual C++. Zawiera listę dotyczy nagłówków i funkcje, które służą do identyfikowania zmian w kodzie.

## <a name="see-also"></a>Zobacz także

[Przewodnik po przenoszeniu i uaktualnianiu pakietu Visual C++](visual-cpp-porting-and-upgrading-guide.md)<br/>
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Visual C++ — historia zmian w latach 2003–2015](visual-cpp-change-history-2003-2015.md)<br/>
[Ulepszenia zgodności języka C++ w programie Visual Studio](../overview/cpp-conformance-improvements.md)
