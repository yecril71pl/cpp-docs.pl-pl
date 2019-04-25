---
title: Błąd kompilatora C3381
ms.date: 11/04/2016
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: ae416d68831d1964c89d938dfcddd364e521195c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328867"
---
# <a name="compiler-error-c3381"></a>Błąd kompilatora C3381

"assembly": specyfikatory dostępu do zestawu są dostępne tylko w kodzie skompilowanym z opcją/CLR

Typy natywne mogą być widoczna spoza zestawu, ale można określić tylko dostęp do zestawu dla natywnych typów w **/CLR** kompilacji.

Aby uzyskać więcej informacji, zobacz [typ widoczności](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [/CLR (kompilacja języka wspólnego środowiska uruchomieniowego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3381.

```
// C3381.cpp
// compile with: /c
public class A {};   // C3381
```