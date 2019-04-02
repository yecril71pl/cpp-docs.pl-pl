---
title: Błąd kompilatora C3625
ms.date: 11/04/2016
f1_keywords:
- C3625
helpviewer_keywords:
- C3625
ms.assetid: fdf49f21-d6b1-42f4-9eec-23b04ae8b4aa
ms.openlocfilehash: a3c69b05e22c2d267ad07f19a0d0ab60f3eebb94
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58779017"
---
# <a name="compiler-error-c3625"></a>Błąd kompilatora C3625

'native_type': typ natywny nie może pochodzić od zarządzanych lub WinRT wpisz "type"

Natywne klasy nie może dziedziczyć z zarządzanych lub WinRT klasy. Aby uzyskać więcej informacji, zobacz [klas i struktur](../../extensions/classes-and-structs-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3625:

```
// C3625.cpp
// compile with: /clr /c
ref class B {};
class D : public B {};   // C3625 cannot inherit from a managed class
```
