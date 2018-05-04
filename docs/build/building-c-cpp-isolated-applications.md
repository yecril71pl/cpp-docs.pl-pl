---
title: Tworzenie C/C++ izolowanych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69de94159ef792aedff35efe81e8bb663d571105
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="building-cc-isolated-applications"></a>Kompilowanie izolowanych kompilacji C/C++
Izolowanych aplikacji zależy tylko zestawy side-by-side i wiąże z jego zależności za pomocą manifestu. Nie jest wymagane dla aplikacji pełni izolowanym, aby działać poprawnie w systemie Windows. jednak przez inwestowanie w tworzenie aplikacji pełni samodzielnie, możesz zapisać czasu Jeśli potrzebne do obsługi aplikacji w przyszłości. Aby uzyskać więcej informacji o zaletach tworzenie aplikacji pełni samodzielnie, zobacz [aplikacje izolowane](http://msdn.microsoft.com/library/aa375190).  
  
 Podczas tworzenia natywnych aplikacji C/C++ za pomocą języka Visual C++, system projektu domyślnie programu Visual Studio generuje plik manifestu, który opisuje zależności aplikacji na bibliotek języka Visual C++. Jeśli są one tylko zależności aplikacji ma, staje się on izolowanych aplikacji zaraz po odbudowaniu w programie Visual Studio. Jeśli aplikacja używa innych bibliotek w czasie wykonywania, a następnie może być konieczne odbudowanie jako zestawy side-by-side wykonanie kroków opisanych w tych bibliotek [budynku C/C++--wspólny zestawy](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane i zestawy Side-by-side](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Kompilowanie aplikacji izolowanych C/C++ oraz aplikacji wykonywanych równocześnie](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)