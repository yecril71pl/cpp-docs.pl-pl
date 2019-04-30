---
title: Błąd kompilatora C3141
ms.date: 11/04/2016
f1_keywords:
- C3141
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
ms.openlocfilehash: e19de95b5b2c967d71a4b06aca431df8ffe9dc14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374940"
---
# <a name="compiler-error-c3141"></a>Błąd kompilatora C3141

"nazwa_interfejsu": interfejsy obsługują tylko publiczne dziedziczenie

Zdefiniowane za pomocą interfejsów [interfejsu (lub __interface)](../../cpp/interface.md) — słowo kluczowe obsługują tylko publiczne dziedziczenie.

Poniższy przykład spowoduje wygenerowanie C3141:

```
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```