---
title: Błąd kompilatora C3381 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3381
dev_langs:
- C++
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7bd6c1d641f7476d3c372939b948931a306e0f80
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080717"
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