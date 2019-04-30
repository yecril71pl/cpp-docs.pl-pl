---
title: Błąd kompilatora C2415
ms.date: 11/04/2016
f1_keywords:
- C2415
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
ms.openlocfilehash: 81e2da31b39b323919132ae86cd365d9c119be32
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402960"
---
# <a name="compiler-error-c2415"></a>Błąd kompilatora C2415

niewłaściwy typ operandu

Opcode nie używać argumentów operacji tego typu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Opcode nie obsługuje liczby operandów używane. Sprawdź podręcznika język asemblera, aby określić poprawną liczbę argumentów.

1. Procesor nowsza obsługuje instrukcji za pomocą dodatkowych typów. Dostosuj [/arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md) możliwość użycia procesora nowsze.