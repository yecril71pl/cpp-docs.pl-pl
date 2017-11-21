---
title: Tworzenie C/C++ izolowanych | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: isolated applications [C++]
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5af0dde80a143166d9824d2739632ca7e7ed4382
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="building-cc-isolated-applications"></a>Kompilowanie izolowanych kompilacji C/C++
Izolowanych aplikacji zależy tylko zestawy side-by-side i wiąże z jego zależności za pomocą manifestu. Nie jest wymagane dla aplikacji pełni izolowanym, aby działać poprawnie w systemie Windows. jednak przez inwestowanie w tworzenie aplikacji pełni samodzielnie, możesz zapisać czasu Jeśli potrzebne do obsługi aplikacji w przyszłości. Aby uzyskać więcej informacji o zaletach tworzenie aplikacji pełni samodzielnie, zobacz [aplikacje izolowane](http://msdn.microsoft.com/library/aa375190).  
  
 Podczas tworzenia natywnych aplikacji C/C++ za pomocą języka Visual C++, system projektu domyślnie programu Visual Studio generuje plik manifestu, który opisuje zależności aplikacji na bibliotek języka Visual C++. Jeśli są one tylko zależności aplikacji ma, staje się on izolowanych aplikacji zaraz po odbudowaniu w programie Visual Studio. Jeśli aplikacja używa innych bibliotek w czasie wykonywania, a następnie może być konieczne odbudowanie jako zestawy side-by-side wykonanie kroków opisanych w tych bibliotek [budynku C/C++--wspólny zestawy](../build/building-c-cpp-side-by-side-assemblies.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Aplikacje izolowane i zestawy Side-by-side](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Tworzenie C/C++ izolowane Side-by-side zestawów ani aplikacji](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)