---
title: Ostrzeżenie kompilatora C4394 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4394
dev_langs:
- C++
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d99200dd01db610aa558e8a9df18b7afacdf3d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099515"
---
# <a name="compiler-warning-c4394"></a>Ostrzeżenie kompilatora C4394

'Funkcja': symbol per-appdomain nie powinien być oznaczony za pomocą __declspec(dllexport)

Funkcja jest oznaczona za pomocą [appdomain](../../cpp/appdomain.md) `__declspec` modyfikator jest skompilowane do MSIL (aby natywna) i tabel eksportu ([wyeksportować](../../windows/export.md) `__declspec` modyfikator) nie są obsługiwane dla funkcji zarządzanej.

Można zadeklarować funkcji zarządzanej, aby mieć dostęp publiczny. Aby uzyskać więcej informacji, zobacz [typ widoczności](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [widoczności składowych](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 zawsze jest wystawiany jako błąd.  Możesz wyłączyć to ostrzeżenie za pomocą `#pragma warning` lub **/wd**; zobacz [ostrzeżenie](../../preprocessor/warning.md) lub [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md)Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4394.

```
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```