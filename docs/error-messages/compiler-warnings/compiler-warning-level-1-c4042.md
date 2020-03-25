---
title: Ostrzeżenie kompilatora (poziom 1) C4042
ms.date: 11/04/2016
f1_keywords:
- C4042
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
ms.openlocfilehash: 0ffc4c4aeb7d37ffa45f503a34fd369d36c00ce4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164212"
---
# <a name="compiler-warning-level-1-c4042"></a>Ostrzeżenie kompilatora (poziom 1) C4042

"Identyfikator": ma złą klasę magazynu

Nie można użyć określonej klasy magazynu z tym identyfikatorem w tym kontekście. Kompilator używa domyślnej klasy magazynu:

- `extern`, jeśli *Identyfikator* jest funkcją.

- **auto**Auto, jeśli *Identyfikator* jest parametrem formalnym lub zmienną lokalną.

- Brak klasy magazynu, jeśli *Identyfikator* jest zmienną globalną.

To ostrzeżenie może być spowodowane określeniem klasy magazynu innej niż **register** w deklaracji parametru.

Poniższy przykład generuje C4042

```cpp
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```
