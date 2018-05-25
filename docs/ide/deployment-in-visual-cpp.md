---
title: Wdrożenia w programie Visual C++ | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 5b9dfdcdce618df3f2bfec64892f62aec20b6db9
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="deployment-in-visual-c"></a>Wdrożenie w Visual C++

Instalacja aplikacji na komputerze innym niż komputer deweloperski nosi nazwę *wdrożenia*. Podczas wdrażania aplikacji Visual C++ na inny komputer, należy zainstalować zarówno aplikację i wszystkie pliki bibliotek, od których zależy. Program Visual Studio pozwala wdrożyć bibliotek języka Visual C++ oraz aplikacji na trzy sposoby: *centralny*, *lokalnego wdrożenia*, i *statycznego łączenia*. Centralne wdrażanie umieszcza pliki bibliotek w katalogu systemu Windows, gdy usługa Windows Update można zaktualizować je automatycznie. Wdrożenia lokalnego umieszcza pliki biblioteki w tym samym katalogu co aplikacja. Należy ponownie wdrożyć żadnych bibliotek lokalnie wdrożonych samodzielnie ich aktualizacji. Statyczne połączenie wiąże kod biblioteki do aplikacji. Należy ponowne skompilowanie i wdrożenie aplikacji mógł korzystać z żadnych aktualizacji do bibliotek, korzystając z statycznego łączenia.

W programie Visual Studio 2015 biblioteki Microsoft C Runtime został zrefaktoryzowany do określonej wersji biblioteki lokalnego składniki i nowej biblioteki uniwersalnego C środowiska uruchomieniowego, która jest teraz częścią systemu Windows. Aby uzyskać szczegółowe informacje dotyczące wdrażania Universal CRT, zobacz [wdrożenia Universal CRT](universal-crt-deployment.md).

## <a name="central-deployment"></a>Wdrożenie centralne

W przypadku wdrożenia centralnej plików biblioteki DLL są zainstalowane w katalogu Windows\System32 lub plików 32-bitowych bibliotek na x64 systemy, w katalogu Windows\SysWow64. Firma Microsoft automatycznie aktualizuje swoje biblioteki, które są wdrożone centralnie. Dla bibliotek języka Visual C++, które są wdrożone lokalnie lub statycznie połączone musisz podać aktualizacji.

Aby centralnie wdrożyć bibliotek języka Visual C++, umożliwia jednego z tych dwóch źródeł dla plików instalacji:

- *Pakiet redystrybucyjny* pliki, które są autonomiczne wiersza polecenia plików wykonywalnych, które zawierają wszystkie bibliotek języka Visual C++ redistributable w postaci skompresowanej, lub

- *Moduły scalania pakietu redystrybucyjnego* (pliki .msm), co umożliwia wdrażanie określone biblioteki i obejmujące w pliku Instalatora Windows (msi) aplikacji.

Plik pakietu redystrybucyjnego powoduje zainstalowanie wszystkich bibliotek języka Visual C++ dla architektury określonym systemie. Na przykład jeśli aplikacja jest skompilowany dla x64, można pakietu redystrybucyjnego vcredist_x64.exe zainstalować wszystkie bibliotek języka Visual C++, który korzysta z aplikacji. Można programu Instalatorem aplikacji, aby uruchomić pakiet redystrybucyjny jako warunek wstępny, przed zainstalowaniem aplikacji.

Moduł scalania umożliwia włączenie logiki Instalatora dla określonej biblioteki Visual C++ w pliku instalacyjnym aplikacji Instalatora Windows. Mogą one obejmować jako liczbę modułów scalania, o wymaganych przez aplikację. Aby zminimalizować rozmiar plików binarnych programu deployment używać modułów scalania.

Ponieważ centralne wdrażanie przy użyciu pakietu redystrybucyjnego lub modułów scalania umożliwia Windows Update można automatycznie zaktualizować bibliotek języka Visual C++, zalecamy korzystania z biblioteki dll w aplikacji zamiast biblioteki statyczne i używać centralnej Wdrażanie zamiast lokalnego wdrożenia.

## <a name="local-deployment"></a>Wdrożenie lokalne

W przypadku wdrożenia lokalnego biblioteki pliki są instalowane w folderze aplikacji wraz z pliku wykonywalnego. Różne wersje programu Visual C++ redistributable biblioteki można zainstalować w tym samym folderze, ponieważ nazwa pliku dla każdej wersji zawiera numeru wersji. Na przykład biblioteka środowiska uruchomieniowego języka C++ w wersji 12 jest msvcp120.dll i wersji 14 jest msvcp140.dll.

Biblioteki mogą rozprzestrzeniać się przez wiele dodatkowych bibliotek DLL, znany jako *kropka bibliotek*. Na przykład niektóre funkcje biblioteki standardowej wydane w Visual Studio 2017 wersji 15,6 dodano do msvcp140_1.dll, preverve zgodność ABI msvcp140.dll. Jeśli używasz wersji programu Visual Studio 2017 15,6 (zestawu narzędzi 14.13) lub nowszym zestaw narzędzi z programu Visual Studio 2017, może być konieczne lokalnie wdrożyć te biblioteki kropką, a także głównym biblioteki. Te biblioteki oddzielne kropka są przesyłane do następnej wersji głównej Podstawowa biblioteka po zmianie ABI.

Ponieważ Microsoft nie może automatycznie aktualizacja lokalnie wdrożona bibliotek języka Visual C++, nie zaleca się z lokalnego wdrożenia tych bibliotek. Jeśli zdecydujesz się użyć lokalnego wdrożenia redystrybucyjnych bibliotek, zaleca się zaimplementowanie własnej metody automatycznego aktualizowania lokalnie wdrożonych bibliotek.

## <a name="static-linking"></a>Łączenie statyczne

Oprócz połączone dynamicznie biblioteki programu Visual Studio udostępnia większość bibliotek jako bibliotek statycznych. Można statycznie Połącz biblioteki statycznej aplikacji, to znaczy, Połącz kod obiektu biblioteki bezpośrednio do aplikacji. Spowoduje to utworzenie jedną wartość binarną bez zależności biblioteki DLL, dzięki czemu nie trzeba wdrożyć osobno pliki bibliotek języka Visual C++. Jednak zaleca się tą metodą, ponieważ nie można zaktualizować statycznie połączone biblioteki w miejscu. Jeśli korzystasz z łączenia statycznego i chcesz zaktualizować połączoną bibliotekę, musisz zrekompilować i ponownie wdrożyć aplikację.

## <a name="troubleshooting-deployment-issues"></a>Rozwiązywanie problemów dotyczących wdrożenia

Kolejność ładowania bibliotek języka Visual C++ jest zależny od systemu. Aby zdiagnozować problemy z modułem ładowania, użyj depends.exe lub where.exe. Aby uzyskać więcej informacji, zobacz [kolejność wyszukiwania biblioteki dll (system Windows)](http://msdn.microsoft.com/library/windows/desktop/ms682586.aspx).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Wdrożenie środowiska Universal CRT](universal-crt-deployment.md)
