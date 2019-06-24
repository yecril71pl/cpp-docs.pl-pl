---
title: Wdrożenie środowiska Universal CRT
ms.date: 05/11/2018
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
ms.openlocfilehash: 1f6e685cca65c4b31ac2e6147341c4b5a3fe8228
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344458"
---
# <a name="universal-crt-deployment"></a>Wdrożenie środowiska Universal CRT

Z programu Visual Studio .NET za pomocą programu Visual Studio 2013 każdy głównej wersji narzędzi i kompilatora języka C++ dostępnych nowych, autonomiczną wersję biblioteki Microsoft C Runtime (CRT). Te wersje autonomiczny CRT były niezależne od i do różnych stopni, niezgodne ze sobą. Na przykład biblioteka CRT, używane przez program Visual Studio 2012 został wersji 11, msvcr110.dll nazwanych i CRT, używany przez Visual Studio 2013 został wersja 12, o nazwie msvcr120.dll. Począwszy od programu Visual Studio 2015, nie jest już wymagane. Visual Studio 2015 i nowszych wersjach programu Visual Studio, wszystkie używać jednego Universal CRT.

Universal CRT jest składnikiem systemu operacyjnego Microsoft Windows dołączone jako część systemu operacyjnego w systemie Windows 10. Jest ona dostępna dla starszych systemów operacyjnych Windows Vista do Windows 8.1 za pomocą usługi Windows Update. Obsługiwana jest lokalne wdrożenie Universal CRT, z pewnymi ograniczeniami.

## <a name="central-deployment"></a>Wdrożenie centralne

Preferowaną metodą instalacji centralnie Universal CRT jest korzystanie z systemu Microsoft Windows Update. Universal CRT jest zalecana aktualizacja wszystkie obsługiwane systemy operacyjne Microsoft Windows, więc w programie domyślnie większości komputerów je zainstalować jako część procesu regularnych aktualizacji. Wstępną wersję Universal CRT zostało [KB2999226](https://support.microsoft.com/kb/2999226). Nowsza aktualizacja przy użyciu różnych poprawki została wprowadzona w [KB3118401](https://support.microsoft.com/kb/3118401), i zostały dodatkowe aktualizacje z dalszych poprawki i nowe funkcje. Nowsze aktualizacje Wyszukaj [support.microsoft.com](https://support.microsoft.com) dla uniwersalnego środowiska języka C lub Universal CRT.

Nie wszystkie komputery Windows Microsoft regularne instalowanie aktualizacji przy użyciu programu Windows Update, a niektóre nie mogą instalować wszystkie zalecane aktualizacje. Do obsługi aplikacji skompilowanych przy użyciu programu Visual Studio 2015 lub nowszy C++ zestawy narzędzi na tych komputerach istnieją pliki redystrybucyjne Universal CRT dla dystrybucji w trybie offline. Te pliki redystrybucyjne może zostać pobrana z jednej z powyższych linków KB. Pakiet redystrybucyjny Universal CRT wymaga, że komputer został zaktualizowany do bieżącego dodatku service pack. Tak na przykład pakiet redystrybucyjny systemu Windows 7 zostanie zainstalowana tylko na Windows 7 z dodatkiem SP1, nie Windows 7 RTM.

Ponieważ Universal CRT podstawowych zależą od elementu C++ bibliotek, wizualizacja C++ redistributable (VCRedist) instaluje wstępną wersję Universal CRT (wersja 10.0.10240) na komputerach, które jeszcze nie masz je zainstalowane. Ta wersja jest niewystarczająca do zapewnienia C++ zależności biblioteki. Twoja aplikacja jest zależna od nowszą wersję Universal CRT, musi przenieść swoje aktualne maszyny za pomocą usługi Windows Update lub jawnie instalacji tej wersji. Najlepiej zainstalować uniwersalnego środowiska uruchomieniowego c. za pośrednictwem witryny Windows Update lub MSU przed zainstalowanie programu VCRedist, aby uniknąć potencjalnych wielu wymagane ponowne uruchomienie.

Nie wszystkie systemy operacyjne kwalifikują się do najnowszych uniwersalnego środowiska języka C za pomocą usługi Windows Update. W systemie Windows 10 centralnie wdrożoną wersję zgodny z wersją systemu operacyjnego. Dodatkowo można zaktualizować uniwersalnego środowiska uruchomieniowego c. należy zaktualizować system operacyjny. Windows Vista do Windows 8.1 najnowsza wersja dostępna uniwersalnego środowiska uruchomieniowego c. obecnie opiera się na wersję, uwzględnione w Windows 10 rozliczenia aktualizacji, dodatkowe poprawki (wersja 10.0.14393).

## <a name="local-deployment"></a>Wdrożenie lokalne

Lokalne wdrożenie Universal CRT jest obsługiwane, ale nie jest zalecane dla kwestie bezpieczeństwa i wydajności. Biblioteki dll do lokalnego wdrożenia są dołączane jako część zestawu Windows SDK, w zestawy Windows\\10\\Redist\\ucrt\\podkatalogu bibliotek DLL, według architektury komputera. Biblioteki DLL wymagane obejmują ucrtbase.dll i zestaw APISet usługi przesyłania dalej o nazwie interfejsu api biblioteki DLL-ms-win -\*.dll. Różni się zbiór bibliotek DLL wymagane w każdym systemie operacyjnym. Zdecydowanie zaleca się obejmują wszystkie biblioteki DLL serwera podczas wdrażania lokalnie.

Istnieją dwa ograniczenia dotyczące wdrożenia lokalnego, w których trzeba pamiętać:

- W systemie Windows 10 Universal CRT w katalogu jest zawsze używana, nawet jeśli aplikacja zawiera kopii lokalnej dla aplikacji Universal CRT. Ma ona wartość true, nawet wtedy, gdy lokalna kopia jest nowsza, ponieważ Universal CRT jest podstawowym składnikiem systemu operacyjnego w systemie Windows 10.

- W wersjach systemu Windows przed systemu Windows 8 Universal CRT nie można spakować lokalnie za pomocą wtyczki, jeśli znajduje się w katalogu innym niż katalog główny pliku wykonywalnego aplikacji. Nie można rozpoznać ucrtbase.dll pomyślnie w tym przypadku są usługi przesyłania dalej APISet biblioteki dll. Niektóre zalecane rozwiązania alternatywne obejmują:

  - Statycznie łączy Universal CRT
  - Centralnie wdrażać Universal CRT, lub
  - Umieść pliki Universal CRT w tym samym katalogu co aplikacja.

## <a name="deployment-on-microsoft-windows-xp"></a>Wdrożenia na Microsoft Windows XP

Visual Studio 2015 i Visual Studio 2017 nadal obsługiwać rozwoju oprogramowania do użycia w systemie Microsoft Windows XP. Aby zapewnić obsługę tego podejścia, wersję Universal CRT działa w systemie Microsoft Windows XP. System operacyjny Microsoft Windows XP nie jest już w mainstream lub rozszerzonej pomocy technicznej, więc centralne wdrożenie Universal CRT na systemu Microsoft Windows XP różni się od innych systemów operacyjnych.

Gdy element wizualny C++ pakiet redystrybucyjny jest zainstalowany w systemie Windows XP, go bezpośrednio instaluje Universal CRT i wszystkie jego zależności w katalogu systemu. Go nie zainstalować lub są zależne od dowolnej aktualizacji Windows. Redystrybucyjne moduły scalania, Microsoft_VC*wersji*_CRT_\*pliki .msm, zrób to samo.

Lokalne wdrożenie Universal CRT w systemie Windows XP jest taki sam jak w innych obsługiwanych systemach operacyjnych.

## <a name="see-also"></a>Zobacz także

- [Wdrażanie w Visual C++](deployment-in-visual-cpp.md)
