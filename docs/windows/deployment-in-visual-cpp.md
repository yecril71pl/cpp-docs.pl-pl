---
title: Wdrożenie w Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 5c4b75a65fcfb34a4988b176ffcb5b2afcb7ea13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377377"
---
# <a name="deployment-in-visual-c"></a>Wdrożenie w Visual C++

Instalacja aplikacji na komputerze innym niż komputer dewelopera jest znana jako *wdrożenie*. Podczas wdrażania aplikacji Visual C++ na innym komputerze należy zainstalować zarówno aplikację, jak i wszystkie pliki bibliotek, od których zależy. Program Visual Studio umożliwia trzy sposoby wdrażania bibliotek języka Visual C++ wraz z aplikacją: *wdrażanie centralne,* *wdrażanie lokalne*i *łączenie statyczne.* Wdrożenie centralne umieszcza pliki bibliotek w katalogu systemu Windows, gdzie usługa Windows Update może je automatycznie aktualizować. Wdrożenie lokalne umieszcza pliki biblioteki w tym samym katalogu co aplikacja. Aby je zaktualizować, należy ponownie wdrożyć wszystkie biblioteki wdrożone lokalnie. Statyczne łączenie wiąże kod biblioteki z aplikacją. Należy ponownie skompilować i ponownie wdrożyć aplikację, aby korzystać z wszelkich aktualizacji do bibliotek podczas korzystania z łączenia statycznego.

W programie Visual Studio 2015 biblioteka środowiska wykonawczego Microsoft C została przekształcona w składniki biblioteki lokalnej specyficzne dla wersji, a nowa biblioteka uniwersalnego środowiska wykonawczego C, która jest teraz częścią systemu Windows. Aby uzyskać szczegółowe informacje na temat wdrażania uniwersalnego crt, zobacz [Uniwersalne wdrożenie CRT](universal-crt-deployment.md).

## <a name="central-deployment"></a>Wdrożenie centralne

W przypadku wdrażania centralnego pliki biblioteki DLL są instalowane w katalogu Windows\System32 lub w przypadku 32-bitowych plików biblioteki w systemach x64 — katalogu Windows\SysWow64. Firma Microsoft automatycznie aktualizuje swoje biblioteki, które są wdrożone centralnie. W przypadku bibliotek języka Visual C++, które są lokalnie wdrażane lub statycznie połączone, należy podać aktualizacje.

Aby centralnie wdrożyć biblioteki języka Visual C++, można użyć jednego z tych dwóch źródeł do zainstalowania plików:

- *Redystrybucyjne* pliki pakietów, które są autonomicznymi plikami wykonywalnymi wierszy poleceń, które zawierają wszystkie biblioteki redystrybucyjne Visual C++ w skompresowanej formie, lub

- *Redystrybucyjne moduły scalania* (pliki msm), których można używać do wdrażania określonych bibliotek i które są dołączane do pliku Instalatora Windows (msi) aplikacji.

Redystrybucyjny plik pakietu instaluje wszystkie biblioteki języka Visual C++ dla określonej architektury systemu. Na przykład jeśli aplikacja jest zbudowana dla x64, można użyć vcredist_x64.exe redystrybucyjnego pakietu, aby zainstalować wszystkie biblioteki języka Visual C++ używane przez aplikację. Przed zainstalowaniem aplikacji można zaprogramować instalatora aplikacji do uruchomienia pakietu redystrybucyjnego jako warunek wstępny.

Moduł scalania umożliwia włączenie logiki konfiguracji dla określonej biblioteki Visual C++ w pliku instalacyjnym instalatora systemu Windows. Można dołączyć dowolną liczbę lub kilka modułów scalania, zgodnie z wymaganiami aplikacji. Użyj modułów korespondencji seryjnej, gdy trzeba zminimalizować rozmiar plików binarnych wdrażania.

Because central deployment by using a redistributable package or merge modules enables Windows Update to automatically update the Visual C++ libraries, we recommend that you use the library DLLs in your application instead of static libraries, and use central deployment instead of local deployment.

## <a name="local-deployment"></a>Wdrożenie lokalne

We wdrożeniu lokalnym pliki bibliotek są instalowane w folderze aplikacji wraz z plikiem wykonywalnym. W tym samym folderze można zainstalować różne wersje bibliotek redystrybucyjnych programu Visual C++, ponieważ nazwa pliku każdej wersji zawiera jej numer wersji. Na przykład wersja 12 biblioteki środowiska wykonawczego języka C++ to msvcp120.dll, a wersja 14 to msvcp140.dll.

Biblioteka może być rozłożona na wiele dodatkowych bibliotek DLL, znanych jako *biblioteki z kropkami.* Na przykład niektóre funkcje w standardowej bibliotece wydanej w programie Visual Studio 2017 w wersji 15.6 został dodany do msvcp140_1.dll, aby zachować zgodność ABI msvcp140.dll. Jeśli używasz programu Visual Studio 2017 w wersji 15.6 (zestaw narzędzi 14.13) lub nowszego zestawu narzędzi z programu Visual Studio 2017, może być konieczne lokalne wdrożenie tych bibliotek kropki, a także biblioteki głównej. Te oddzielne biblioteki kropki są następnie przetaczane do następnej głównej wersji biblioteki podstawowej, gdy zmieni się ABI.

Ponieważ firma Microsoft nie może automatycznie aktualizować lokalnie wdrożonych bibliotek programu Visual C++, nie zaleca się lokalnego wdrażania tych bibliotek. Jeśli zdecydujesz się użyć lokalnego wdrożenia redystrybucyjnych bibliotek, zaleca się zaimplementowanie własnej metody automatycznego aktualizowania lokalnie wdrożonych bibliotek.

## <a name="static-linking"></a>Łączenie statyczne

Oprócz dynamicznie połączonych bibliotek program Visual Studio dostarcza większość swoich bibliotek jako bibliotek statycznych. Można statycznie połączyć bibliotekę statyczną z aplikacją, czyli połączyć kod obiektu biblioteki bezpośrednio z aplikacją. Spowoduje to utworzenie pojedynczego pliku binarnego bez zależności DLL, dzięki czemu nie trzeba wdrażać plików biblioteki Visual C++ oddzielnie. Jednak nie zaleca się tego podejścia, ponieważ bibliotek statycznie połączone nie można zaktualizować w miejscu. Jeśli korzystasz z łączenia statycznego i chcesz zaktualizować połączoną bibliotekę, musisz zrekompilować i ponownie wdrożyć aplikację.

## <a name="troubleshooting-deployment-issues"></a>Rozwiązywanie problemów z wdrażaniem

Kolejność ładowania bibliotek visual c++ jest zależna od systemu. Aby zdiagnozować problemy z modułem ładowania, użyj depends.exe lub where.exe. Aby uzyskać więcej informacji, zobacz [Kolejność wyszukiwania biblioteki dynamicznej (Windows)](/windows/win32/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Zobacz też

- [Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)
- [Wdrożenie środowiska Universal CRT](universal-crt-deployment.md)
