---
title: C3505 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3505
dev_langs:
- C++
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9e0ea8edd3237db2085365450f43b4b955d36f33
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33257660"
---
# <a name="compiler-error-c3505"></a>C3505 błąd kompilatora

> Nie można załadować biblioteki typów '*guid*"  
  
Może być spowodowany C3505, jeśli używasz 32-bitowy, hostowana x86 między kompilatora dla 64-bitowej, x64 wskazuje na 64-bitowego komputera, ponieważ kompilator nie działa w emulatorze WOW64 ale można tylko do odczytu z gałęzi rejestru w 32-bitowych.  
  
Można rozwiązać ten problem, tworząc zarówno 32-bitowe i 64-bitowe wersje biblioteki typów, który próbujesz zaimportować, a następnie zarejestruj je.  Lub skorzystać z macierzystego kompilatora 64-bitowego wymaga zmiany z **katalogi VC ++** właściwości w IDE, aby wskazywał kompilator 64-bitowy.  
  
Aby uzyskać więcej informacji, zobacz,  
  
-   [Instrukcje: włączanie 64-bitowego zestawu narzędzi języka Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)  
  
-   [Instrukcje: konfigurowanie projektów programu Visual C ++ dla wersji 64-bitowych, platformy docelowe x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)