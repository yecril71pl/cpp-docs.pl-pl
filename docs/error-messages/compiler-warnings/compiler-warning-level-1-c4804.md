---
title: Ostrzeżenie kompilatora (poziom 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051573"
---
# <a name="compiler-warning-level-1-c4804"></a>Ostrzeżenie kompilatora (poziom 1) C4804

"Operation": niebezpieczne użycie typu "bool" w operacji

To ostrzeżenie dotyczy, gdy użyto zmiennej `bool` lub wartości w nieoczekiwany sposób. Na przykład C4804 jest generowany, jeśli używasz operatorów, takich jak ujemny operator jednoargumentowy ( **-** ) lub operator uzupełniania (`~`). Kompilator szacuje wyrażenie.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4804:

```cpp
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```