---
title: "Aplikacją na poprzedniej wersji środowiska uruchomieniowego - clr C++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b8e0a9860c3c6d4fef87a76aad037f70c1ea787f
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Uruchamianie aplikacji C++/clr w poprzedniej wersji środowiska uruchomieniowego
Jeżeli nie określono inaczej, aplikacji C++ .NET Framework korzysta z wbudowanej działa w typowych wersji języka wspólnego (CLR) kompilator używa do skompilowania aplikacji. Jednak jest możliwe w dla aplikacji .exe, która jest skompilowany dla jednej wersji środowiska uruchomieniowego do uruchamiania w dowolnej wersji, który udostępnia funkcjonalność wymagane.  
  
 W tym celu należy dostarczyć plik app.config, który zawiera informacje o wersji środowiska uruchomieniowego w `supportedRuntime` tagu.  
  
 W czasie wykonywania pliku app.config musi mieć nazwę w postaci *nazwa_pliku.ext*.config, gdzie *nazwa_pliku.ext* to nazwa pliku wykonywalnego, który uruchomił aplikację, a musi być w tym samym katalogu co plik wykonywalny. Na przykład jeśli aplikacja nosi nazwę TestApp.exe, pliku app.config będzie nosić TestApp.exe.config.  
  
 Jeśli aplikacja zostanie uruchomiona na komputerze, który ma więcej niż jedną wersję zainstalowanego środowiska uruchomieniowego można określić więcej niż jedną wersję środowiska uruchomieniowego, aplikacja używa pierwszej wersji, została określona w pliku konfiguracji, który jest zainstalowany.  
  
 Aby uzyskać więcej informacji, zobacz [porady: Konfigurowanie aplikacji pod kątem wersji programu .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Do uruchomienia na wersji 1.0 lub 1.1 CLR, aplikacji, która jest konstruowany przez Visual C++ kompilatora muszą być skompilowane przy użyciu [/clr:initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażanie natywnych aplikacji komputerowych](../ide/deploying-native-desktop-applications-visual-cpp.md)