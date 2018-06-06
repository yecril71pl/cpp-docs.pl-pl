---
title: Wdrażanie natywnych aplikacji komputerowych (Visual C++) | Dokumentacja firmy Microsoft
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
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4f4aa355c132b4c94f085cbdf7aa73785357d0f0
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34259247"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Wdrażanie natywnych aplikacji komputerowych (Visual C++)

Wdrażanie to proces, za pomocą którego można dystrybuować Zakończono aplikację lub składnik można zainstalować na innych komputerach. Planowanie wdrożenia zostanie uruchomiony po utworzeniu aplikacji na komputerze dewelopera. Wdrożenie kończy się, gdy aplikacja jest zainstalowana i gotowa do uruchomienia na komputerze użytkownika.

Program Visual Studio oferuje różne technologie wdrażania aplikacji systemu Windows. Obejmują one wdrażania ClickOnce i wdrożenia Instalatora Windows.

- ClickOnce może służyć do wdrażania aplikacji C++, których miejscem docelowym jest środowisko uruchomieniowe języka wspólnego (CLR) — zestawów mieszanych, czystych i weryfikowalnych. Mimo że Instalatora Windows można użyć do wdrożenia aplikacji zarządzanej, zaleca się użycie technologii ClickOnce, ponieważ korzysta z funkcji zabezpieczeń .NET Framework, takich jak podpisywanie manifestu. ClickOnce nie obsługuje wdrażanie natywnych aplikacji C++. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md).

- Technologii Instalatora systemu Windows może służyć do wdrożenia natywnych aplikacji C++ lub aplikacje w języku C++ kierowanych środowiska CLR.

Artykuły w tej sekcji dokumentacji omówiono sposób upewnić się, że natywnych aplikacji Visual C++ działa na dowolnym komputerze, który zawiera pliki, które należy uwzględnić w pakietu instalacyjnego i zalecane sposoby platformy docelowej, Ponowna dystrybucja składników, które zależy od aplikacji.

## <a name="in-this-section"></a>W tej sekcji

- [Wdrażanie w Visual C++](../ide/deployment-in-visual-cpp.md)

- [Pojęcia związane z wdrażaniem](../ide/deployment-concepts.md)

- [Objaśnienie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Ustalanie, które biblioteki DLL są przeznaczone do ponownej dystrybucji](../ide/determining-which-dlls-to-redistribute.md)

- [Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md)

- [Wdrożenie usługi Universal CRT](universal-crt-deployment.md).

- [Ponowne dystrybuowanie plików programu Visual C++](../ide/redistributing-visual-cpp-files.md)

- [Przykłady wdrożeń](../ide/deployment-examples.md)

- [Ponowne dystrybuowanie aplikacji klienta sieci Web](../ide/redistributing-web-client-applications.md)

- [Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](../ide/clickonce-deployment-for-visual-cpp-applications.md)

- [Uruchomiona C++/CLR aplikacji na poprzedniej wersji środowiska uruchomieniowego](../ide/running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Sekcje pokrewne

- [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Wdrażanie](/dotnet/framework/deployment/index)

- [Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)