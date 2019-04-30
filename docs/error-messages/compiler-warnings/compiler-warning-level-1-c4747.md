---
title: Kompilator ostrzeżenie (poziom 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: ecaabd482049771b1d3915470a2be7a52e36d361
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404029"
---
# <a name="compiler-warning-level-1-c4747"></a>Kompilator ostrzeżenie (poziom 1) C4747

Wywołanie zarządzanego "punkt wejścia": Kod zarządzany nie mogą być uruchamiane w ramach blokady modułu ładującego, włączając w to punkt wejścia biblioteki DLL i wywołania osiągnięte z punktu wejścia biblioteki DLL

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