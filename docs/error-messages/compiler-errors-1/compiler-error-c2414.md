---
title: Błąd kompilatora C2414
ms.date: 11/04/2016
f1_keywords:
- C2414
helpviewer_keywords:
- C2414
ms.assetid: bbe94e03-862e-4990-b15e-544ae464727d
ms.openlocfilehash: 84fa715c8bd567770f361552e203a37c44ffdde4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402986"
---
# <a name="compiler-error-c2414"></a>Błąd kompilatora C2414

Niedozwolona liczba operandów

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Opcode nie obsługuje liczby operandów używane. Sprawdź podręcznika język asemblera, aby określić poprawną liczbę argumentów.

1. Procesor nowsza obsługuje instrukcji z różną liczbę argumentów. Dostosuj [/arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md) możliwość użycia procesora nowsze.