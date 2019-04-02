---
title: Uruchamianie aplikacji C++ - clr w poprzedniej wersji środowiska uruchomieniowego
ms.date: 11/04/2016
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
ms.openlocfilehash: 9b26439d389cb4035541cedde8a5b5cf50682098
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787443"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Uruchamianie aplikacji C++/clr w poprzedniej wersji środowiska uruchomieniowego

O ile nie określono inaczej, aplikacji w języku C++ .NET Framework został opracowany pod kątem są uruchamiane w wersji środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego, której kompilator używa do tworzenia aplikacji. Jednak jest możliwe dla aplikacji .exe, który zaprojektowano pod kątem jednej wersji środowiska uruchomieniowego do uruchamiania w innej wersji, który zapewnia wymaganą funkcję.

Aby to osiągnąć, należy podać plik app.config, który zawiera informacje o wersji środowiska uruchomieniowego w `supportedRuntime` tagu.

W czasie wykonywania plik app.config musi mieć nazwę w postaci *nazwa_pliku.ext*.config, gdzie *nazwa_pliku.ext* jest nazwą pliku wykonywalnego, który uruchomił aplikację, a musi być w tym samym katalogu co plik wykonywalny. Na przykład jeśli aplikacja nosi nazwę TestApp.exe, plik app.config będzie nosić TestApp.exe.config.

Jeśli określisz więcej niż jedna wersja środowiska uruchomieniowego i aplikacja zostanie uruchomiona na komputerze, który ma więcej niż jedna wersja zainstalowanego środowiska uruchomieniowego, aplikacja używa pierwszej wersji, została określona w pliku konfiguracji, który jest zainstalowany.

## <a name="see-also"></a>Zobacz także

[Wdrażanie aplikacji komputerowych](deploying-native-desktop-applications-visual-cpp.md)
