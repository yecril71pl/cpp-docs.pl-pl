---
title: "Kompilatora (poziom 1) ostrzeżenie C4305 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 1/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe4b2b420c44584fdd5b4d48b4264bbc7a51bee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4305"></a>Kompilator C4305 ostrzegawcze (poziom 1)

> "*kontekstu*": obcięcie z "*type1*"do"*type2*"  

## <a name="remarks"></a>Uwagi

To ostrzeżenie zostanie wyświetlone, gdy wartość jest konwertowana na mniejszy typ podczas inicjowania lub jako argument konstruktora, co doprowadzi do utraty danych.

## <a name="example"></a>Przykład

Ten przykład przedstawia dwa sposoby, które można napotkać tego ostrzeżenia:

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

Aby rozwiązać ten problem, zainicjować za pomocą wartości prawidłowego typu lub Użyj rzutowania jawnego do poprawnego typu. Na przykład użyć **float** literału, takich jak 2.71828f zamiast **podwójne** (domyślny typ dla literałów liczb zmiennoprzecinkowych) zainicjować **float** zmiennej, lub do przekazania do Konstruktor pobierający **float** argumentu.
