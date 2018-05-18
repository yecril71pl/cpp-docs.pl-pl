---
title: Pojęcia związane z wdrażaniem | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows Installer [C++]
- dependencies [C++], application deployment and
- application deployment [C++], about application deployment
- deploying applications [C++], about deploying applications
- libraries [C++], application deployment issues
ms.assetid: ebd7f246-ab54-40e8-87fa-dac02c0047b3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0960e94acdbe660474efbeeddd0f72fa4f0606f6
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2018
---
# <a name="deployment-concepts"></a>Pojęcia związane z wdrażaniem

W tej sekcji omówiono głównego zagadnienia dotyczące wdrażania aplikacji w języku C++.

## <a name="windows-installer-deployment-in-c"></a>Wdrożenia Instalatora Windows w języku C++

Projekty Visual C++ zwykle użyć tradycyjnych instalacji Instalatora Windows do wdrożenia. Aby przygotować wdrożenia Instalatora Windows, pakietu aplikacji w pliku setup.exe i rozpowszechnianie tego pliku, wraz z pakietu Instalator (msi). Użytkownicy, a następnie uruchomić setup.exe do zainstalowania aplikacji.

Pakiet aplikacji, dodając instalacji projektu do rozwiązania; Podczas tworzenia, tworzy instalacji i Instalator plików pakietu, które musisz przekazać użytkownikom. Aby uzyskać więcej informacji, zobacz [Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md).

## <a name="library-dependencies"></a>Zależności biblioteki

Po utworzeniu aplikacji C/C++ za pomocą funkcji udostępnianych przez usługę bibliotek języka Visual C++ staje się on zależny od obecności tych bibliotek w czasie wykonywania. Aby do uruchomienia aplikacji jego należy połączyć, statycznie lub dynamicznie, niezbędne bibliotek języka Visual C++. Jeśli aplikacja dynamicznie łącza do biblioteki Visual C++, a następnie po uruchomieniu tej biblioteki musi występować, może zostać załadowany. Z drugiej strony Jeśli aplikacja łączy statycznie do biblioteki Visual C++, następnie nie musi znajdować się na komputerze użytkownika odpowiedniej biblioteki dll. Jednak statyczne połączenie ma pewne negatywne skutki takich jak zwiększenie rozmiaru plików aplikacji i utrudnia konserwacji potencjalnie. Aby uzyskać więcej informacji, zobacz [zalety używania bibliotek DLL](../build/dlls-in-visual-cpp.md#advantages-of-using-dlls).

## <a name="packaging-and-redistributing"></a>Tworzenie pakietów i dystrybucja

Pakiecie bibliotek języka Visual C++ w postaci bibliotek DLL, a wszystkie wymagane biblioteki dla aplikacji C/C++ są instalowane przez program Visual Studio na komputerze dewelopera. Jednak w przypadku wdrażania aplikacji dla użytkowników, nie jest możliwe w większości przypadków, aby zainstalować program Visual Studio niezbędne do uruchomienia aplikacji. Jest ważne można było ponownie dystrybuować tylko części Visual C++, które są wymagane przez aplikację do poprawnego działania.

Aby uzyskać więcej informacji dotyczących tworzenia pakietów i redystrybucji zobacz następujące tematy:

- [Określanie, które biblioteki dll do ponownej dystrybucji](../ide/determining-which-dlls-to-redistribute.md).

- [Wybieranie metody wdrażania](../ide/choosing-a-deployment-method.md).

- [Wdrożenie usługi Universal CRT](universal-crt-deployment.md).

Aby uzyskać przykłady wdrożeń i sugestie dotyczące rozwiązywania problemów Zobacz:

- [Przykłady wdrożeń](../ide/deployment-examples.md).

- [Rozwiązywanie problemów z C/C++ izolowany aplikacji i zestawy Side-by-side](../build/troubleshooting-c-cpp-isolated-applications-and-side-by-side-assemblies.md).

## <a name="see-also"></a>Zobacz także

- [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)
- [Objaśnienie zależności aplikacji Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md)
- [Wdrożenia Instalatora Windows](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
