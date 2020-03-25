---
title: Błąd kompilatora C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 97d9ef1eeeffa0e5a63d2c8ae2428a3fad0ff238
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165589"
---
# <a name="compiler-error-c3851"></a>Błąd kompilatora C3851

> "*char*": Universal-Character-Name nie może wyznaczyć znaku w podstawowym zestawie znaków

## <a name="remarks"></a>Uwagi

W kodzie skompilowanym C++jako, nie można użyć uniwersalnej nazwy znaku, która reprezentuje znak w podstawowym zestawie znaków źródłowych poza ciągiem lub literałem znaku. Aby uzyskać więcej informacji, zobacz [zestawy znaków](../../cpp/character-sets.md). W kodzie skompilowanym jako C nie można użyć uniwersalnej nazwy znaków w zakresie 0x20-0x7F, włącznie, z wyjątkiem 0x24 ("$"), 0x40 ("\@") lub 0x60 ("\`").

## <a name="example"></a>Przykład

Poniższe przykłady generują C3851 i pokazują, jak rozwiązać ten problem:

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```
