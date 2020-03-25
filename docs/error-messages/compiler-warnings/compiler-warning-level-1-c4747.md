---
title: Ostrzeżenie kompilatora (poziom 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 2fd7f0960966a981d82d19e7b2533b1ffcd3bc00
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80175197"
---
# <a name="compiler-warning-level-1-c4747"></a>Ostrzeżenie kompilatora (poziom 1) C4747

Wywoływanie funkcji "EntryPoint": kod zarządzany nie może być uruchamiany w ramach blokady modułu ładującego, w tym punktu wejścia biblioteki DLL i wywołań uzyskanych z punktu wejścia biblioteki DLL

Kompilator znalazł (prawdopodobnie) punkt wejścia biblioteki DLL skompilowany do MSIL.  Ze względu na potencjalne problemy z ładowaniem biblioteki DLL, której punkt wejścia został skompilowany do MSIL, stanowczo odradza się Kompilowanie funkcji punktu wejścia biblioteki DLL do MSIL.

Aby uzyskać więcej informacji, zobacz [Inicjowanie zestawów mieszanych](../../dotnet/initialization-of-mixed-assemblies.md) i [narzędzi konsolidatora LNK1306 błąd](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Nie Kompiluj modułu z **/CLR**.

1. Oznacz funkcję punktu wejścia przy użyciu `#pragma unmanaged`.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4747.

```cpp
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
