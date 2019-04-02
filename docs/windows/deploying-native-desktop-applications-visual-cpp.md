---
title: Wdrażanie natywnych aplikacji komputerowych (Visual C++)
ms.date: 05/11/2018
helpviewer_keywords:
- deploying applications [C++]
- application deployment [C++]
- Visual C++, application deployment
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- distributing applications [C++]
ms.assetid: 37f1691e-d67c-41e4-926e-528a237a9bac
ms.openlocfilehash: 46ced4ac5f7952a9b7f66418ea037e053b16e9be
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786813"
---
# <a name="deploying-native-desktop-applications-visual-c"></a>Wdrażanie natywnych aplikacji komputerowych (Visual C++)

Wdrażanie to proces, za pomocą którego można dystrybuować ukończonej aplikacji lub składnika można zainstalować na innych komputerach. Planowanie wdrożenia zostanie uruchomiony po utworzeniu aplikacji na komputerze dewelopera. Wdrożenie kończy się, gdy aplikacja jest zainstalowana i gotowa do uruchomienia na komputerze użytkownika.

Visual Studio zawiera różne technologie wdrażania aplikacji Windows. Obejmują one wdrażania ClickOnce i wdrażanie za pomocą Instalatora Windows.

- ClickOnce może służyć do wdrażania aplikacji w języku C++, których platformą docelową środowisko uruchomieniowe języka wspólnego (CLR) — zestawów mieszanych, czystych i weryfikowalnych. Mimo, że Instalator Windows umożliwia wdrażanie aplikacji zarządzanej, zaleca się użycie technologii ClickOnce, ponieważ wykorzystuje platformę .NET Framework funkcje zabezpieczeń, takie jak podpisywanie manifestu. ClickOnce nie obsługuje wdrażanie natywnych aplikacji w języku C++. Aby uzyskać więcej informacji, zobacz [wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](clickonce-deployment-for-visual-cpp-applications.md).

- Technologia Instalatora Windows może służyć do wdrożenia natywnych aplikacji w języku C++ lub aplikacji w języku C++, których celem jest CLR.

Artykuły w tej sekcji dokumentacji omówiono sposób zapewnienia, że natywnych aplikacji Visual C++ jest uruchamiana na dowolnym komputerze, który zawiera pliki, które należy uwzględnić w pakiecie instalacyjnym i zalecane sposoby za pomocą platformy docelowej Ponowna dystrybucja składników, od których zależy aplikacja.

## <a name="in-this-section"></a>W tej sekcji

- [Wdrażanie w Visual C++](deployment-in-visual-cpp.md)

- [Pojęcia związane z wdrażaniem](deployment-concepts.md)

- [Objaśnienie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)

- [Ustalanie, które biblioteki DLL są przeznaczone do ponownej dystrybucji](determining-which-dlls-to-redistribute.md)

- [Wybieranie metody wdrażania](choosing-a-deployment-method.md)

- [Wdrożenie usługi Universal CRT](universal-crt-deployment.md).

- [Ponowne dystrybuowanie plików programu Visual C++](redistributing-visual-cpp-files.md)

- [Przykłady wdrożeń](deployment-examples.md)

- [Ponowne dystrybuowanie aplikacji klienta sieci Web](redistributing-web-client-applications.md)

- [Wdrożenie rozwiązania ClickOnce dla aplikacji Visual C++](clickonce-deployment-for-visual-cpp-applications.md)

- [Uruchomione c + +/ CLR aplikacji na poprzedniej wersji środowiska uruchomieniowego](running-a-cpp-clr-application-on-a-previous-runtime-version.md)

## <a name="related-sections"></a>Sekcje pokrewne

- [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)

- [Wdrażanie](/dotnet/framework/deployment/index)

- [Rozwiązywanie problemów związanych z aplikacjami izolowanymi C/C++ oraz aplikacjami wykonywanymi równocześnie](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md)