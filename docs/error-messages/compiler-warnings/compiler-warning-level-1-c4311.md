---
title: Ostrzeżenie kompilatora (poziom 1) C4311
ms.date: 11/04/2016
f1_keywords:
- C4311
helpviewer_keywords:
- C4311
ms.assetid: ddc579d0-d051-47bc-915d-71ffb32323c9
ms.openlocfilehash: 52f8338423b5e3366b85207477b3b1ee5e9c399f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163105"
---
# <a name="compiler-warning-level-1-c4311"></a>Ostrzeżenie kompilatora (poziom 1) C4311

'zmienna' : obcinanie wskaźnika z 'typ do 'typ'

To ostrzeżenie wykrywa problemy z obcinaniem wskaźnika 64-bitowego. Na przykład jeśli kod jest kompilowany dla architektury 64-bitowej, wartość wskaźnika (64 bitów) zostanie obcięta, jeśli zostanie przypisana do `int` (32 bity). Aby uzyskać więcej informacji, zobacz [reguły dotyczące korzystania ze wskaźników](/windows/win32/WinProg64/rules-for-using-pointers).

Aby uzyskać dodatkowe informacje na temat typowych przyczyn C4311 ostrzeżeń, zobacz [typowe błędy kompilatora](/windows/win32/WinProg64/common-compiler-errors).

Poniższy przykład kodu generuje C4311 podczas kompilowania dla elementu docelowego 64-bitowego, a następnie pokazuje, jak go naprawić:

```cpp
// C4311.cpp
// compile by using: cl /W1 C4311.cpp
int main() {
   void* p = &p;
   unsigned int i = (unsigned int) p;   // C4311 for 64-bit targets
   unsigned long long j = (unsigned long long) p;   // OK
}
```
