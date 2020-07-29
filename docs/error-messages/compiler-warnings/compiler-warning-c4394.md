---
title: Ostrzeżenie kompilatora C4394
ms.date: 11/04/2016
f1_keywords:
- C4394
helpviewer_keywords:
- C4394
ms.assetid: 5de94de0-17e3-4e7c-92f4-5c3c1b825120
ms.openlocfilehash: ad6b9624a1bf510465843167d104d1bec189bc70
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87197361"
---
# <a name="compiler-warning-c4394"></a>Ostrzeżenie kompilatora C4394

"Function": symbol dla domeny AppDomain nie powinien być oznaczony za pomocą __declspec (dllexport)

Funkcja oznaczona [appdomain](../../cpp/appdomain.md) **`__declspec`** modyfikatorem AppDomain jest skompilowana do MSIL (nie do natywnego), a tabele eksportu (modyfikator[eksportu](../../windows/export.md) **`__declspec`** ) nie są obsługiwane dla funkcji zarządzanych.

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
