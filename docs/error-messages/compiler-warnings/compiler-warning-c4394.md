---
title: Ostrzeżenie kompilatora C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: fc4d66444b4ddc5c855e88d466ccc2f42c60e0ca
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510064"
---
# <a name="compiler-warning-c4394"></a>Ostrzeżenie kompilatora C4394

"Function": symbol dla domeny AppDomain nie powinien być oznaczony za pomocą __declspec (dllexport)

Funkcja oznaczona [appdomain](../../cpp/appdomain.md) **`__declspec`** modyfikatorem AppDomain jest skompilowana do MSIL (nie do natywnego), a tabele eksportu (modyfikator[eksportu](../../windows/attributes/export.md) **`__declspec`** ) nie są obsługiwane dla funkcji zarządzanych.

Można zadeklarować funkcję zarządzaną, aby mieć dostęp publiczny. Aby uzyskać więcej informacji, zobacz [widoczność typów](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [widoczność elementów członkowskich](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Member_visibility).

C4394 jest zawsze wystawiony jako błąd.  Możesz wyłączyć to ostrzeżenie przy użyciu `#pragma warning` lub **/WD**; zobacz [Ostrzeżenie](../../preprocessor/warning.md) , [/W,/W0,/W1,/W2,/W3,/W4,/W1,/W2,/W3,/W4,/Wall,/WD,/we,/wo,/WV,/WX (poziom ostrzeżenia)](../../build/reference/compiler-option-warning-level.md) , aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4394.

```cpp
// C4394.cpp
// compile with: /clr /c
__declspec(dllexport) __declspec(appdomain) int g1 = 0;   // C4394
__declspec(dllexport) int g2 = 0;   // OK
```
