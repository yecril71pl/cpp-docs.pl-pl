---
title: Błąd kompilatora C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 98b5bf0a1315236f3ce96fd4b8c140ce1ab70a9f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501034"
---
# <a name="compiler-error-c2778"></a>Błąd kompilatora C2778

nieprawidłowo sformułowany identyfikator GUID w __declspec (UUID ())

Do rozszerzonego atrybutu [UUID](../../cpp/uuid-cpp.md) jest dostarczany nieprawidłowy identyfikator GUID.

Identyfikator GUID musi być ciągiem liczb szesnastkowych o następującym formacie:

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

Rozszerzony atrybut akceptuje ciągi rozpoznawane przez CLSIDFromString, z ogranicznikami lub bez nich. [](/windows/win32/api/combaseapi/nf-combaseapi-clsidfromstring) `uuid`

Poniższy przykład generuje C2778:

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```