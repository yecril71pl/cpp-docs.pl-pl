---
title: Uruchamianie aplikacji C++ - clr w poprzedniej wersji środowiska uruchomieniowego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20a20002397e285680927fe519e4eac7b68cc343
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216565"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Uruchamianie aplikacji C++/clr w poprzedniej wersji środowiska uruchomieniowego
O ile nie określono inaczej, aplikacji w języku C++ .NET Framework został opracowany pod kątem są uruchamiane w wersji środowiska uruchomieniowego (języka wspólnego CLR) języka wspólnego, której kompilator używa do tworzenia aplikacji. Jednak jest możliwe dla aplikacji .exe, który zaprojektowano pod kątem jednej wersji środowiska uruchomieniowego do uruchamiania w innej wersji, który zapewnia wymaganą funkcję.  
  
 Aby to osiągnąć, należy podać plik app.config, który zawiera informacje o wersji środowiska uruchomieniowego w `supportedRuntime` tagu.  
  
 W czasie wykonywania plik app.config musi mieć nazwę w postaci *nazwa_pliku.ext*.config, gdzie *nazwa_pliku.ext* jest nazwą pliku wykonywalnego, który uruchomił aplikację, a musi być w tym samym katalogu co plik wykonywalny. Na przykład jeśli aplikacja nosi nazwę TestApp.exe, plik app.config będzie nosić TestApp.exe.config.  
  
 Jeśli określisz więcej niż jedna wersja środowiska uruchomieniowego i aplikacja zostanie uruchomiona na komputerze, który ma więcej niż jedna wersja zainstalowanego środowiska uruchomieniowego, aplikacja używa pierwszej wersji, została określona w pliku konfiguracji, który jest zainstalowany.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie aplikacji pod kątem określonej wersji oprogramowania .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Do uruchomienia w wersji 1.0 lub 1.1 wersję środowiska CLR, aplikacji, który jest kompilowany przez Visual C++ kompilator muszą być skompilowane przy użyciu [/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)