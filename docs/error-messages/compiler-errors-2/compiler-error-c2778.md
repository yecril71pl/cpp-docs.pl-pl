---
title: Błąd kompilatora C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 247aba1b4dfe6b6d6db1e2b8f46f2aa08abf1a79
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739990"
---
# <a name="compiler-error-c2778"></a>Błąd kompilatora C2778

nieprawidłowo sformułowany identyfikator GUID w __declspec (UUID ())

Do rozszerzonego atrybutu [UUID](../../cpp/uuid-cpp.md) jest dostarczany nieprawidłowy identyfikator GUID.

Identyfikator GUID musi być ciągiem liczb szesnastkowych o następującym formacie:

```cpp
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

Rozszerzony atrybut `uuid` akceptuje ciągi rozpoznawane przez [CLSIDFromString](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring), z ogranicznikami lub bez nich.

Poniższy przykład generuje C2778:

```cpp
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```
