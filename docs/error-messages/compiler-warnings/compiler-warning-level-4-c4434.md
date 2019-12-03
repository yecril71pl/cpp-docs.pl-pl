---
title: Ostrzeżenie kompilatora (poziom 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 97a010bef151e97914d131b3a1fe2437a244e9c4
ms.sourcegitcommit: d0504e2337bb671e78ec6dd1c7b05d89e7adf6a7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2019
ms.locfileid: "74683216"
---
# <a name="compiler-warning-level-4-c4434"></a>Ostrzeżenie kompilatora (poziom 4) C4434

Konstruktor klasy musi mieć prywatną dostępność; Zmiana dostępu prywatnego

C4434 wskazuje, że kompilator zmienił dostępność konstruktora statycznego. Konstruktory statyczne muszą mieć prywatną dostępność, ponieważ są przeznaczone tylko do wywoływania przez środowisko uruchomieniowe języka wspólnego. Aby uzyskać więcej informacji, zobacz [statyczne konstruktory](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4434.

```cpp
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```