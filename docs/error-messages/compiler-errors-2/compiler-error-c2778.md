---
title: Błąd kompilatora C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 56c316ac971d0bdd1a0ca27ef8d4282acbe24779
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227679"
---
# <a name="compiler-error-c2778"></a>Błąd kompilatora C2778

niewłaściwie uformowane GUID w __declspec(uuid())

Podano niepoprawny identyfikator GUID do [uuid](../../cpp/uuid-cpp.md) atrybutów rozszerzonych.

Identyfikator GUID musi być ciągiem liczb szesnastkowych o następującym formacie:

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

`uuid` Atrybutów rozszerzonych akceptuje ciągi rozpoznawane przez [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring), z ogranicznikami lub bez nawiasów.

Poniższy przykład spowoduje wygenerowanie C2778:

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```