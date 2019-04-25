---
title: Ostrzeżenie kompilatora C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: 00c9e139e920473590389c05f076a7cd91a4fb8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311481"
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