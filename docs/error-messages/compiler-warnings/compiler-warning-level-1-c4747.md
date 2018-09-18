---
title: Kompilator ostrzeżenie (poziom 1) C4747 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4747
dev_langs:
- C++
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2d3eb5b83fedc7455cbf1b97119296a6eb6a1ab1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118482"
---
# <a name="compiler-warning-level-1-c4747"></a>Kompilator ostrzeżenie (poziom 1) C4747

Wywołanie zarządzanego "punkt wejścia": kod zarządzany nie mogą być uruchamiane w ramach blokady modułu ładującego, włączając w to punkt wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL

Kompilator znaleziono skompilowane do MSIL (prawdopodobieństwo) punkt wejścia biblioteki DLL.  Ze względu na potencjalne problemy z ładowaniem DLL, w której punkt wejścia został wcześniej skompilowany na język MSIL, zdecydowanie odradza się kompilowanie funkcję punktu wejścia w DLL na język MSIL.

Aby uzyskać więcej informacji, zobacz [inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md) i [błąd narzędzi konsolidatora LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie można skompilować moduł za pomocą **/CLR**.

1. Oznacz funkcję punktu wejścia przy użyciu `#pragma unmanaged`.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4747.

```
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```