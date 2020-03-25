---
title: Błąd kompilatora C3505
ms.date: 11/04/2016
f1_keywords:
- C3505
helpviewer_keywords:
- C3505
ms.assetid: ed73c99e-93a1-4f3a-bac7-ba7ed5d836e4
ms.openlocfilehash: 0c67eb46208c35c1b11a74898107ad3c0e6e570d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200854"
---
# <a name="compiler-error-c3505"></a>Błąd kompilatora C3505

> nie można załadować biblioteki typów "*GUID*"

C3505 może być spowodowany tym, że korzystasz z 32-bitowego, obsługiwanego przez procesor x86 kompilatora międzykompilatorowego dla 64-bitowych, elementów docelowych x64 na komputerze 64-bitowym, ponieważ kompilator działa w emulatorze WOW64 i może odczytywać tylko z gałęzi rejestru 32-bitowego.

Można rozwiązać ten problem, tworząc zarówno 32-bitowe, jak i 64-bitowe wersje biblioteki typów, którą próbujesz zaimportować, a następnie zarejestrować oba te błędy.  Można też użyć natywnego kompilatora 64-bitowego, który wymaga zmiany właściwości **katalogów VC + +** w IDE, aby wskazywały kompilator 64-bitowy.

Aby uzyskać więcej informacji, zobacz,

- [Instrukcje: włączanie 64-bitowego zestawu narzędzi języka Visual C++ w wierszu polecenia](../../build/how-to-enable-a-64-bit-visual-cpp-toolset-on-the-command-line.md)

- [Instrukcje: konfigurowanie projektów programu Visual C ++ dla wersji 64-bitowych, platformy docelowe x64](../../build/how-to-configure-visual-cpp-projects-to-target-64-bit-platforms.md)
