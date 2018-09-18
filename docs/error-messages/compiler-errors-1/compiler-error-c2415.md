---
title: Błąd kompilatora C2415 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2415
dev_langs:
- C++
helpviewer_keywords:
- C2415
ms.assetid: f225c913-2bea-46b1-b096-3d358ac94a15
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd889880997828396521ddba638bb606552e7d92
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46112580"
---
# <a name="compiler-error-c2415"></a>Błąd kompilatora C2415

niewłaściwy typ operandu

Opcode nie używać argumentów operacji tego typu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Aby rozwiązać problem, sprawdzając następujące możliwe przyczyny

1. Opcode nie obsługuje liczby operandów używane. Sprawdź podręcznika język asemblera, aby określić poprawną liczbę argumentów.

1. Procesor nowsza obsługuje instrukcji za pomocą dodatkowych typów. Dostosuj [/arch (minimalna architektura Procesora)](../../build/reference/arch-minimum-cpu-architecture.md) możliwość użycia procesora nowsze.