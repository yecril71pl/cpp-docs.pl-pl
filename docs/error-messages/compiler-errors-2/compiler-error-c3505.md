---
title: "C3505 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3505
dev_langs: C++
helpviewer_keywords: C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 47ca6c4e8e8c01e97ed0098c84c8ea8c64f387a6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3505"></a>C3505 błąd kompilatora

> Nie można załadować biblioteki typów '*guid*"  
  
Może być spowodowany C3505, jeśli używasz 32-bitowy, hostowana x86 między kompilatora dla 64-bitowej, x64 wskazuje na 64-bitowego komputera, ponieważ kompilator nie działa w emulatorze WOW64 ale można tylko do odczytu z gałęzi rejestru w 32-bitowych.  
  
Można rozwiązać ten problem, tworząc zarówno 32-bitowe i 64-bitowe wersje biblioteki typów, który próbujesz zaimportować, a następnie zarejestruj je.  Lub skorzystać z macierzystego kompilatora 64-bitowego wymaga zmiany z **katalogi VC ++** właściwości w IDE, aby wskazywał kompilator 64-bitowy.  
  
Aby uzyskać więcej informacji, zobacz,  
  
-   [Porady: Włączanie 64-bitowych Visual C++ narzędzi w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Porady: Konfigurowanie projektów Visual C++ pod kątem 64-bitowy, x64 platformy](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)