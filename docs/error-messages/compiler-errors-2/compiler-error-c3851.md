---
title: Błąd kompilatora C3851 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f495a61fd3c157862fe65d82c1ffe5f047d798dd
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895178"
---
# <a name="compiler-error-c3851"></a>Błąd kompilatora C3851

> "*char*": universal-character-name nie może wyznaczyć znaku w podstawowym zestawie znaków

## <a name="remarks"></a>Uwagi

W kodzie skompilowany jako języka C++ nie można użyć nazwę znaki uniwersalne, która reprezentuje znak w zestawie znaków podstawowego źródła poza ciągu lub literału. Aby uzyskać więcej informacji, zobacz [zestawów znaków](../../cpp/character-sets.md). W kodzie skompilowany jako C, nie można użyć znaki uniwersalne nazwy znaków w zakresie 0x20 0x7f, włącznie, z wyjątkiem 0x24 ('$'), 0x40 ("\@"), lub 0x60 ("\`").

## <a name="example"></a>Przykład

Poniższe przykłady Generowanie C3851 i pokazują, jak go naprawić:

```cpp
// C3851.cpp
int main()  
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```