---
title: Błąd kompilatora C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: eadc9b45b4cd4f2d9b533f387dadd66be8acc963
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749571"
---
# <a name="compiler-error-c3381"></a>Błąd kompilatora C3381

"Assembly": specyfikatory dostępu do zestawu są dostępne tylko w kodzie skompilowanym z opcją/CLR

Typy natywne mogą być widoczne poza zestawem, ale dostęp do zestawu można określić tylko dla typów natywnych w kompilacji **/CLR** .

Aby uzyskać więcej informacji, zobacz [typu widoczność](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3381.

```cpp
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```
