---
title: Błąd kompilatora C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 5730102371d00ebaf3ae05fdefb70184b58d7c18
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481780"
---
# <a name="compiler-error-c3505"></a>Błąd kompilatora C3505

> Nie można załadować biblioteki typów '*guid*"

Może być spowodowany C3505, jeśli używasz 32-bitowe, obsługiwane x86 kompilator krzyżowy dla 64-bitowych, x64 obiekty docelowe w 64-bitowe maszyny, ponieważ kompilator jest uruchomiona w emulatorze WOW64 i można jedynie odczytywać gałęzi rejestru 32-bitowych.

Można rozwiązać ten problem, tworząc zarówno 32-bitowych i 64-bitowe wersje biblioteki typów, którą próbowano zaimportować, a następnie zarejestruj oba te.  Lub możesz użyć natywnych 64-bitowego kompilatora, co wymaga zmienić swoje **katalogi VC ++** właściwości w IDE, aby wskazywał 64-bitowego kompilatora.

Aby uzyskać więcej informacji, zobacz,

- [Instrukcje: włączanie 64-bitowego zestawu narzędzi języka Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Instrukcje: konfigurowanie projektów programu Visual C ++ dla wersji 64-bitowych, platformy docelowe x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)