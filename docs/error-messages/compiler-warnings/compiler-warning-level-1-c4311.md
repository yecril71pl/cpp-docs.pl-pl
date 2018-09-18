---
title: Kompilator ostrzeżenie (poziom 1) C4311 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4311
dev_langs:
- C++
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e01aef8ffe6314452ad4644f2192583c89a42ea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46114426"
---
# <a name="compiler-warning-level-1-c4311"></a>Kompilator ostrzeżenie (poziom 1) C4311

'zmienna' : obcinanie wskaźnika z 'typ do 'typ'

To ostrzeżenie wykrywa problemy obcięcie wskaźnika 64-bitowego. Na przykład, jeśli kod jest kompilowany dla architektury 64-bitowych, wartość wskaźnika (64-bitowy) zostanie obcięta Jeśli zostanie przypisany do `int` (32-bitowy). Aby uzyskać więcej informacji, zobacz [zasady za pomocą wskaźników](/windows/desktop/WinProg64/rules-for-using-pointers).

Aby uzyskać dodatkowe informacje na temat typowych przyczyn ostrzeżenie C4311, zobacz [typowe błędy kompilatora](/windows/desktop/WinProg64/common-compiler-errors).

Poniższy kod generuje C4311 podczas kompilowania elementu docelowego 64-bitowego i pokazuje, jak go naprawić:

```
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}

```