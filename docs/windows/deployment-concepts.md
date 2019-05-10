---
title: Pojęcia związane z wdrażaniem
ms.date: 11/04/2016
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
ms.openlocfilehash: ac3565b4ec465ec60672d2238fbe81b71613a6c1
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2019
ms.locfileid: "65449053"
---
# <a name="deployment-concepts"></a>Pojęcia związane z wdrażaniem

W tej sekcji opisano najważniejsze kwestie dotyczące wdrażania aplikacji w języku C++.

## <a name="windows-installer-deployment-in-c"></a>Wdrażanie za pomocą Instalatora Windows w języku C++

Program Visual Studio C++ projekty zazwyczaj korzystają z tradycyjnych instalacji Instalatora Windows dla wdrożenia. W celu przygotowania wdrożenia Instalatora Windows, pakietu aplikacji w pliku setup.exe i dystrybucja tego pliku, wraz z pakiet instalacyjny (.msi). Użytkownicy następnie uruchom setup.exe do zainstalowania aplikacji.

Pakiet aplikacji przez dodanie projektu Instalatora do rozwiązania; podczas kompilowania, tworzy Konfiguracja i Instalator plików pakietu, które są rozpowszechniane do użytkowników. Aby uzyskać więcej informacji, zobacz [Wybieranie metody wdrażania](choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Zależności biblioteki

Podczas kompilowania aplikacji C/C++ za pomocą funkcje udostępniane przez bibliotek języka Visual C++, staje się zależy od obecności tych bibliotek w czasie wykonywania. Aby do uruchomienia aplikacji jego należy połączyć, statycznie lub dynamicznie, wymaganych bibliotek języka Visual C++. Jeśli aplikacja dynamicznie łączy do biblioteki Visual C++, a następnie po uruchomieniu tej biblioteki musi być obecny, może zostać załadowany. Z drugiej strony Jeśli aplikacja statycznie łączy do biblioteki Visual C++, następnie nie potrzebuje odpowiedniej biblioteki dll, znajdować się na komputerze użytkownika. Jednak łączenia statycznego ma pewne negatywne skutki, takie jak zwiększenie rozmiaru plików aplikacji i utrudnia konserwacji potencjalnie. Aby uzyskać więcej informacji, zobacz [zalety używania bibliotek DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Tworzenie pakietów i dystrybucja

Biblioteki języka Visual C++ są spakowane w postaci bibliotek DLL, a wszystkie wymagane biblioteki dla aplikacji C/C++ są instalowane przez program Visual Studio na komputerze dewelopera. Jednak w przypadku wdrażania aplikacji dla użytkowników, nie jest możliwe w większości przypadków do wymagane w przypadku instalowania programu Visual Studio, aby można było uruchomić aplikację. Jest ważne można było ponownie dystrybuować tylko części języka Visual C++, które są wymagane przez aplikację do poprawnego działania.

Aby uzyskać więcej informacji na temat tworzenia pakietów i dystrybucja zobacz następujące tematy:

- [Określanie, które biblioteki dll do ponownej dystrybucji](determining-which-dlls-to-redistribute.md).

- [Wybieranie metody wdrażania](choosing-a-deployment-method.md).

- [Wdrożenie usługi Universal CRT](universal-crt-deployment.md).

Przykłady wdrożeń i sugestie dotyczące rozwiązywania problemów Zobacz:

- [Przykłady wdrożeń](deployment-examples.md).

- [Rozwiązywanie problemów z języka C/C++ izolowanymi oraz aplikacjami wykonywanymi Side-by-side](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)
- [Objaśnienie zależności aplikacji Visual C++](understanding-the-dependencies-of-a-visual-cpp-application.md)
