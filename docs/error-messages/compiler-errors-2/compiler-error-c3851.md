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
ms.openlocfilehash: e6d0f6da9c3295aa6a8fad4bf5dfd8e725424739
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032494"
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