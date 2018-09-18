---
title: Kompilator ostrzeżenie (poziom 4) C4629 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4629
dev_langs:
- C++
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5f728d60a654a672002610d41aa4e387b4479e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081328"
---
# <a name="compiler-warning-level-4-c4629"></a>Kompilator ostrzeżenie (poziom 4) C4629

użyto dwuznaku, sekwencja znaków 'dwuznak' zinterpretowana jako token "char" (Wstaw spację między dwoma znakami, jeśli to nie mają)

W obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md), kompilator wyświetla ostrzeżenie, gdy wykryje dwuznak.

Poniższy przykład spowoduje wygenerowanie C4629:

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```