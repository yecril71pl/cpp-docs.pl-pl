---
title: Wdrożenie usługi Universal CRT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying the CRT [C++]
- application CRT deployment [C++]
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20006118d4bf27c379b78b84dc8807a4fd6c5e6c
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34256322"
---
# <a name="universal-crt-deployment"></a>Wdrożenie usługi Universal CRT

Z programu Visual Studio .NET, za pomocą programu Visual Studio 2013 każdej głównej wersji narzędzi i kompilatora C++ dołączył nowe, autonomiczna wersja biblioteki Microsoft C Runtime (CRT). Te wersje autonomiczny CRT były niezależne od i do różnych stopni, niezgodne ze sobą. Na przykład biblioteka CRT używane przez program Visual Studio 2012 został msvcr110.dll nazwanego 11, wersji i CRT używany przez Visual Studio 2013 był w wersji 12, msvcr120.dll o nazwie. Począwszy od programu Visual Studio 2015, to nie jest już wymagane. Visual Studio 2015 i nowszych wersjach programu Visual Studio wszystkich Użyj jednego uniwersalne środowisko CRT.

Uniwersalne środowisko CRT jest składnikiem systemu operacyjnego Microsoft Windows. Jest częścią systemu operacyjnego w systemie Windows 10 i jest dostępna dla starszych systemów operacyjnych Windows Vista za pośrednictwem Windows 8.1 za pomocą usługi Windows Update. Ponadto lokalnego wdrożenia Universal CRT jest obsługiwana, z pewnymi ograniczeniami.

## <a name="central-deployment"></a>Wdrożenie centralnej

Preferowaną metodą centralnie zainstalować Universal CRT jest korzystanie z programu Microsoft Windows Update. Uniwersalne środowisko CRT jest zalecana aktualizacja dla wszystkich obsługiwanych systemów operacyjnych Microsoft Windows, domyślnie najczęściej go zainstalować w ramach procesu regularnych aktualizacji. Początkowa wersja Universal CRT zostało [KB2999226](https://support.microsoft.com/en-us/kb/2999226); kolejnej aktualizacji z różnych poprawki została wprowadzona w [KB3118401](https://support.microsoft.com/en-us/kb/3118401), i zostały dodatkowe aktualizacje z dalsze poprawki i nowe funkcje. Nowsze aktualizacje wyszukiwania [support.microsoft.com](https://support.microsoft.com) Universal C Runtime lub Universal CRT.

Nie wszystkie komputery Microsoft Windows regularne instalowanie aktualizacji za pomocą usługi Windows Update, a niektóre nie może zainstalować wszystkie zalecane aktualizacje. Do zapewnienia obsługi aplikacji utworzonych za pomocą programu Visual Studio 2015 i nowszym procesami C++ na tych komputerach, Brak dostępnych pakietów redystrybucyjnych Universal CRT dla dystrybucji w trybie offline. Te pakiety redystrybucyjne może zostać pobrana z jednej z powyższych łączy KB. Należy pamiętać, że pakietów redystrybucyjnych Universal CRT wymagają, że komputer został zaktualizowany do bieżącego dodatku service pack. Tak na przykład pakiet redystrybucyjny systemu Windows 7 zostanie zainstalowana tylko na systemie Windows 7 z dodatkiem SP1, nie systemu Windows 7 RTM.

Ponieważ Universal CRT podstawowych zależność biblioteki języka C++, Visual C++ redistributable (VCRedist) instaluje podstawowej wersji Universal CRT na maszynach, które nie mają wersja już zainstalowana, niewystarczająca do zapewnienia biblioteka języka C++ zależności. Jeśli aplikacja jest zależna od nowszą wersję Universal CRT, należy zainstalować jawnie tego nowszą wersję. Zaleca się zainstalować ten program przed zainstalowanie programu VCRedist, aby uniknąć potencjalnych wielu wymagane ponowne uruchomienie.

## <a name="local-deployment"></a>Wdrożenia lokalnego

Lokalne wdrożenie Universal CRT jest obsługiwane, ale niezalecane wydajności i ze względów bezpieczeństwa.  Biblioteki DLL dla wdrożenia lokalnego są dołączane jako część zestawu Windows SDK, w zestawy Windows\\10\\Redist\\Biblioteka ucrt\\podkatalogu bibliotek DLL, do architektury komputera. Wymaganych bibliotek DLL obejmują ucrtbase.dll i zestaw APISet usługi przesyłania dalej o nazwie interfejsu api biblioteki DLL-ms-Windows -\*dll. Zestaw plików DLL wymaganych w każdym systemie operacyjnym różni się więc zaleca się obejmują wszystkie biblioteki dll podczas wdrażania lokalnie.

Istnieją dwa ograniczenia dotyczące lokalnego wdrożenia pod uwagę:

- W systemie Windows 10 uniwersalne środowisko CRT w katalogu systemowym jest zawsze używana, nawet jeśli aplikacja zawiera kopię Universal CRT lokalnego aplikacji. Dotyczy to nawet jeśli lokalną kopię Universal CRT jest nowsza. Jest to spowodowane Universal CRT jest podstawowym składnikiem systemu operacyjnego w systemie Windows 10.

- W wersjach systemu Windows przed systemu Windows 8 uniwersalne środowisko CRT nie można spakować lokalnie z wtyczkę, która znajduje się w katalogu innym niż katalog, który zawiera główny plik wykonywalny dla aplikacji. Nie można rozpoznać ucrtbase.dll pomyślnie w tym przypadku są usługi przesyłania dalej APISet biblioteki dll. Niektóre zalecanych rozwiązań alternatywnych, obejmują:

  - Statycznie Połącz uniwersalne środowisko CRT
  - Centralne wdrażanie uniwersalne środowisko CRT lub
  - Umieścić pliki Universal CRT w tym samym katalogu co aplikacja.

## <a name="deployment-on-microsoft-windows-xp"></a>Wdrożenia w systemie Microsoft Windows XP

Visual Studio 2015 i Visual Studio 2017 nadal obsługuje rozwoju oprogramowania do użycia w systemie Microsoft Windows XP. W tym wersja Universal CRT działa w systemie Microsoft Windows XP. System operacyjny Microsoft Windows XP nie jest już w typowych lub rozszerzonej pomocy technicznej, dlatego centralna wdrożenie Universal CRT na systemu Microsoft Windows XP różni się od innych systemów operacyjnych.

Po zainstalowaniu pakietu redystrybucyjnego Visual C++ w systemie Windows XP go bezpośrednio instaluje uniwersalne środowisko CRT i wszystkie jego zależności w katalogu systemu bez instalowania lub w zależności od dowolnej usługi Windows Update. Moduły scalania do dystrybucji, Microsoft_VC*wersji*_CRT_\*.msm pliki, wykonaj te same.

Lokalne wdrożenie Universal CRT w systemie Windows XP jest taki sam jak w innych obsługiwanych systemach operacyjnych.

## <a name="see-also"></a>Zobacz także

- [Wdrażanie w Visual C++](deployment-in-visual-cpp.md)
