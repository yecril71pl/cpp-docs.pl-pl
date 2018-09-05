---
title: Wdrożenie w Visual C++ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/11/2018
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
ms.assetid: d4b4ffc0-d2bd-4e4a-84a6-62f1c26f6a09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 468ce7d65e31a70192e1a48bf21126dd96a1936e
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43678915"
---
# <a name="deployment-in-visual-c"></a>Wdrożenie w Visual C++

Instalacja aplikacji na komputerze innym niż komputer deweloperski jest znany jako *wdrożenia*. Podczas wdrażania aplikacji Visual C++ do innego komputera, należy zainstalować zarówno aplikację, jak i wszystkie pliki bibliotek, od których zależy. Program Visual Studio umożliwia trzy sposoby wdrożenia bibliotek języka Visual C++, wraz z aplikacją: *wdrożenie centralne*, *lokalne wdrożenie*, i *łączenia statycznego*. Wdrożenie centralne umieszcza pliki biblioteki w katalogu Windows, w której usługa aktualizacji Windows można je będzie automatycznie aktualizować. Lokalne wdrożenie umieszcza pliki biblioteki, w tym samym katalogu co aplikacja. Należy ponownie wdrożyć żadnych lokalnie wdrożonych bibliotek sobie, aby je zaktualizować. Łączenie statyczne wiąże kod biblioteki w aplikacji. Należy ponownie skompilować i ponownego wdrażania aplikacji w taki sposób, aby móc korzystać z żadnych aktualizacji do bibliotek, korzystając z łączenia statycznego.

W programie Visual Studio 2015 biblioteki wykonawczej C firmy Microsoft został zrefaktoryzowany do określonej wersji biblioteki lokalne składniki i nową bibliotekę uniwersalnego środowiska języka C, która jest teraz częścią programu Windows. Aby uzyskać szczegółowe informacje dotyczące wdrażania Universal CRT, zobacz [wdrożenia Universal CRT](universal-crt-deployment.md).

## <a name="central-deployment"></a>Wdrożenie centralne

We wdrożeniu centralnym, pliki DLL biblioteki są instalowane w katalogu Windows\System32 lub dla plików 32-bitowy library na x64 systemy, w katalogu Windows\SysWow64. Firma Microsoft automatycznie aktualizuje swoje biblioteki, które są wdrożone centralnie. Dla bibliotek języka Visual C++, które są wdrożone lokalnie lub łączone statycznie aktualizacje musi zapewnić.

Aby wdrożyć centralnie biblioteki Visual C++, można Użyj jednego z tych dwóch źródeł dla plików do zainstalowania:

- *Pakiet redystrybucyjny* pliki, które są autonomiczne pliki wykonywalne wiersza polecenia zawierające wszystkie biblioteki Visual C++ redistributable w postaci skompresowany, lub

- *Redystrybucyjne moduły scalania* (pliki .msm), którego można użyć do wdrożenia określonych bibliotek i które dołącza się do pliku Instalatora Windows (msi) Twojej aplikacji.

Plik pakietu redystrybucyjnego instaluje wszystkie biblioteki Visual C++ dla określonej architektury systemu. Na przykład jeśli aplikacja jest wbudowana x64, umożliwia pakiet redystrybucyjny vcredist_x64.exe zainstalować wszystkie biblioteki Visual C++, używanych przez aplikację. Można programować Instalatorem aplikacji do uruchamiania pakietu redystrybucyjnego jako warunek wstępny, przed zainstalowaniem aplikacji.

Moduł scalania umożliwia włączenie logiki Instalatora dla określonej biblioteki Visual C++ w pliku instalacyjnym aplikacji Instalatora Windows. Może zawierać jako liczbę modułów scalania, ponieważ wymaganych przez aplikację. Korzystania z modułów scalania, gdy należy zminimalizować rozmiar wdrożenia plików binarnych.

Ponieważ wdrożenie centralne przy użyciu pakietu redystrybucyjnego lub moduły scalania umożliwia Windows aktualizacji do automatycznego aktualizowania bibliotek języka Visual C++, firma Microsoft zaleca korzystanie z biblioteki dll w aplikacji, zamiast bibliotek statycznych i użyć central Wdrażanie zamiast wdrożenia lokalnego.

## <a name="local-deployment"></a>Wdrożenie lokalne

W przypadku wdrożenia lokalnego pliki bibliotek są instalowane w folderze aplikacji wraz z pliku wykonywalnego. Różne wersje bibliotek pakiet redystrybucyjny Visual C++ można zainstalować w tym samym folderze, ponieważ nazwa pliku każdej wersji obejmuje jego numer wersji. Na przykład wersja 12 biblioteki wykonawczej języka C++ jest msvcp120.dll i w wersji 14 jest msvcp140.dll.

Biblioteki mogą być rozkładane na wiele dodatkowych bibliotek DLL, znane jako *dot bibliotek*. Na przykład niektóre funkcje w standardowej bibliotece ogólnie dostępnych w programie Visual Studio 2017 w wersji 15.6 został dodany do msvcp140_1.dll, aby zachować zgodność ABI msvcp140.dll. Jeśli używasz programu Visual Studio 2017 w wersji 15.6 (zestaw narzędzi 14.13) lub nowszej wersji zestawu narzędzi w programie Visual Studio 2017, może być konieczne lokalnego wdrażania tych bibliotek kropka, a także głównym biblioteki. Tych bibliotek oddzielne kropki są mogą być przesyłane do następnej wersji głównej podstawowej biblioteki po zmianie interfejsu ABI.

Ponieważ Microsoft nie może automatycznie aktualizacji lokalnie wdrożonych bibliotek języka Visual C++, nie zaleca się lokalnego wdrażania tych bibliotek. Jeśli zdecydujesz się użyć lokalnego wdrożenia redystrybucyjnych bibliotek, zaleca się zaimplementowanie własnej metody automatycznego aktualizowania lokalnie wdrożonych bibliotek.

## <a name="static-linking"></a>Łączenie statyczne

Oprócz dynamicznie łączonych bibliotek programu Visual Studio dostarcza większość bibliotek jako bibliotek statycznych. Możesz statycznie połączyć bibliotekę statyczną aplikację, to znaczy, Połącz kod obiektu biblioteki bezpośrednio do aplikacji. Spowoduje to utworzenie jedną wartość binarną bez zależności biblioteki DLL, dzięki czemu nie trzeba wdrażać oddzielnie plików bibliotek Visual C++. Jednak nie zalecamy tego podejścia, ponieważ statycznie łączonych bibliotek nie można zaktualizować w miejscu. Jeśli korzystasz z łączenia statycznego i chcesz zaktualizować połączoną bibliotekę, musisz zrekompilować i ponownie wdrożyć aplikację.

## <a name="troubleshooting-deployment-issues"></a>Rozwiązywanie problemów dotyczących wdrożenia

Kolejność ładowania bibliotek języka Visual C++ jest zależna od systemu. Aby zdiagnozować problemy z modułem ładowania, użyj depends.exe lub where.exe. Aby uzyskać więcej informacji, zobacz [kolejności przeszukiwania bibliotek dołączanych dynamicznie (Windows)](/windows/desktop/Dlls/dynamic-link-library-search-order).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Wdrożenie środowiska Universal CRT](universal-crt-deployment.md)
