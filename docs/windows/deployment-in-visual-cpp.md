---
title: Wdrożenie w Visual C++
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
ms.openlocfilehash: 67d5c7b0772eda55d1b653bd73f95ac93e31e644
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514810"
---
# <a name="deployment-in-visual-c"></a>Wdrożenie w Visual C++

Instalacja aplikacji na komputerze innym niż komputer deweloperski jest znana jako *wdrażanie*. Podczas wdrażania aplikacji wizualnej C++ na innym komputerze należy zainstalować zarówno aplikację, jak i wszystkie pliki bibliotek, od których zależy. Program Visual C++ Studio umożliwia trzy sposoby wdrażania bibliotek wizualnych wraz z aplikacją: *wdrażanie centralne*, *lokalne wdrożenie*i konsolidacja *statyczna*. Wdrożenie centralne umieszcza pliki biblioteki w katalogu systemu Windows, w którym usługa Windows Update może je automatycznie aktualizować. Lokalne wdrożenie umieszcza pliki biblioteki w tym samym katalogu, w którym znajduje się aplikacja. Należy ponownie wdrożyć lokalnie wdrożone biblioteki samodzielnie, aby je zaktualizować. Łączenie statyczne wiąże kod biblioteki z Twoją aplikacją. Należy ponownie skompilować i wdrożyć aplikację, aby skorzystać z aktualizacji do bibliotek w przypadku używania konsolidacji statycznej.

W programie Visual Studio 2015 Biblioteka środowiska uruchomieniowego Microsoft C została ponownie wdrożona w ramach specyficznych dla wersji składników biblioteki lokalnej i nowej biblioteki środowiska uruchomieniowego uniwersalnego języka C, która jest teraz częścią systemu Windows. Aby uzyskać szczegółowe informacje na temat wdrażania uniwersalnej CRT, zobacz [uniwersalne CRT Deployment](universal-crt-deployment.md).

## <a name="central-deployment"></a>Wdrożenie centralne

W przypadku wdrażania centralnego pliki bibliotek DLL są instalowane w katalogu Windows\System32 lub dla plików bibliotek 32-bitowych w systemach x64, katalog Windows\SysWow64. Firma Microsoft automatycznie aktualizuje swoje biblioteki, które są wdrożone centralnie. W przypadku C++ bibliotek wizualnych, które są wdrażane lokalnie lub połączone statycznie, należy udostępnić aktualizacje.

Aby wdrożyć centralne biblioteki wizualne C++ , można użyć jednego z tych dwóch źródeł dla plików do zainstalowania:

- Pliki *pakietu* redystrybucyjnego, które są autonomicznymi plikami wykonywalnymi wiersza polecenia, które zawierają wszystkie biblioteki C++ redystrybucyjne wizualizacji w postaci skompresowanej lub

- *Redystrybucyjne moduły scalania* (pliki. msm), których można użyć do wdrożenia określonych bibliotek i dołączenia ich do pliku Instalator Windows (msi) aplikacji.

Plik pakietu redystrybucyjnego instaluje wszystkie biblioteki wizualne C++ dla określonej architektury systemu. Na przykład jeśli aplikacja została skompilowana dla wersji x64, można użyć pakietu redystrybucyjnego VCRedist_x64. exe, aby zainstalować wszystkie biblioteki wizualne C++ używane przez aplikację. Przed zainstalowaniem aplikacji można programować Instalatora aplikacji, aby uruchamiał pakiet redystrybucyjny jako warunek wstępny.

Moduł scalania umożliwia włączenie logiki konfiguracji dla określonej biblioteki wizualnej C++ w pliku konfiguracji aplikacji Instalator Windows. Można dołączyć dowolną liczbę lub kilka modułów scalania wymaganych przez aplikację. Używaj modułów scalania, gdy zachodzi potrzeba zminimalizowania rozmiaru plików binarnych wdrożenia.

Ze względu na to, że centralne wdrożenie przy użyciu pakietu redystrybucyjnego lub modułów scalania pozwala C++ Windows Update automatycznie aktualizować biblioteki wizualne, zalecamy używanie bibliotek DLL w aplikacji zamiast bibliotek statycznych i używanie wdrożenie centralne zamiast wdrożenia lokalnego.

## <a name="local-deployment"></a>Wdrożenie lokalne

W przypadku wdrożenia lokalnego pliki bibliotek są instalowane w folderze aplikacji wraz z plikiem wykonywalnym. Różne wersje bibliotek redystrybucyjnych Visual C++ można zainstalować w tym samym folderze, ponieważ nazwa pliku każdej wersji zawiera numer wersji. Na przykład wersja 12 biblioteki C++ wykonawczej to msvcp120. dll, a wersja 14 to msvcp140. dll.

Biblioteka może być rozłożona na wiele dodatkowych bibliotek DLL, nazywanych także *bibliotekami kropek*. Na przykład niektóre funkcje biblioteki standardowej wydanej w programie Visual Studio 2017 w wersji 15,6 zostały dodane do msvcp140_1. dll, aby zachować zgodność ABI msvcp140. dll. Jeśli używasz programu Visual Studio 2017 w wersji 15,6 (zestawu narzędzi 14,13) lub nowszego zestawu narzędzi z programu Visual Studio 2017, może być konieczne lokalne wdrożenie tych bibliotek z kropką oraz biblioteki głównej. Te oddzielne biblioteki kropek są następnie rzutowane do następnej wersji głównej biblioteki podstawowej, gdy ABI ulegnie zmianie.

Ponieważ firma Microsoft nie może automatycznie aktualizować lokalnie C++ wdrożonych bibliotek wizualnych, nie zalecamy lokalnego wdrożenia tych bibliotek. Jeśli zdecydujesz się użyć lokalnego wdrożenia redystrybucyjnych bibliotek, zaleca się zaimplementowanie własnej metody automatycznego aktualizowania lokalnie wdrożonych bibliotek.

## <a name="static-linking"></a>Łączenie statyczne

Oprócz bibliotek połączonych dynamicznie program Visual Studio dostarcza większość jej bibliotek jako bibliotek statycznych. Można statycznie połączyć bibliotekę statyczną z aplikacją, czyli połączyć kod obiektu biblioteki bezpośrednio z aplikacją. Spowoduje to utworzenie pojedynczego pliku binarnego bez zależności biblioteki DLL, aby nie trzeba było oddzielnie wdrażać C++ plików biblioteki wizualnej. Jednak nie zalecamy tego podejścia, ponieważ nie można zaktualizować bibliotek połączonych statycznie. Jeśli korzystasz z łączenia statycznego i chcesz zaktualizować połączoną bibliotekę, musisz zrekompilować i ponownie wdrożyć aplikację.

## <a name="troubleshooting-deployment-issues"></a>Rozwiązywanie problemów z wdrażaniem

Kolejność ładowania bibliotek wizualnych C++ jest zależna od systemu. Aby zdiagnozować problemy z modułem ładowania, użyj depends.exe lub where.exe. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania biblioteki dołączanej dynamicznie (Windows)](/windows/win32/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji klasycznych](deploying-native-desktop-applications-visual-cpp.md)
- [Wdrożenie środowiska Universal CRT](universal-crt-deployment.md)
