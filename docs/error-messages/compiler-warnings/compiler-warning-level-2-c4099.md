---
title: Ostrzeżenie kompilatora (poziom 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: 09ea9e2963735c1e011e25b42b04ad6d67d084a5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471724"
---
# <a name="compiler-warning-level-2-c4099"></a>Ostrzeżenie kompilatora (poziom 2) C4099

'Identyfikator': Nazwa typu najpierw widoczna przy użyciu "objecttype1" teraz widoczna przy użyciu "objecttype2"

Obiekt, który został zadeklarowany jako struktura jest zdefiniowana jako klasa lub obiekt, który został zadeklarowany jako klasa jest zdefiniowana jako struktury. Kompilator używa typu podanego w definicji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4099.

```
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```