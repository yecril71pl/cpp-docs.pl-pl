---
title: Ostrzeżenie kompilatora (poziom 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: d685f1f40826b975623dbedc2ba8115c6b3edc45
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052177"
---
# <a name="compiler-warning-level-2-c4099"></a>Ostrzeżenie kompilatora (poziom 2) C4099

"Identyfikator": nazwa typu najpierw widoczna przy użyciu "objecttype1" jest teraz widoczna przy użyciu "objecttype2"

Obiekt zadeklarowany jako struktura jest zdefiniowany jako Klasa lub obiekt zadeklarowany jako klasa jest zdefiniowany jako struktura. Kompilator używa typu podanego w definicji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4099.

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```