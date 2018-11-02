---
title: Błąd kompilatora C3808
ms.date: 11/04/2016
f1_keywords:
- C3808
helpviewer_keywords:
- C3808
ms.assetid: 2ee8ac97-3ea4-417a-8710-be73a7f98cf4
ms.openlocfilehash: 0a1b0b82241c6e48d2c1941ff8122697d11492eb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587736"
---
# <a name="compiler-error-c3808"></a>Błąd kompilatora C3808

> "*typu*": klasa z atrybutem ComImport nie może definiować składowej "*elementu członkowskiego*", tylko abstrakcyjne lub dllimport funkcje są dozwolone

## <a name="remarks"></a>Uwagi

Typ, który pochodzi od <xref:System.Runtime.InteropServices.ComImportAttribute> nie można zdefiniować *elementu członkowskiego*.

**/CLR: pure** i **/CLR: Safe** opcje kompilatora są przestarzałe w programie Visual Studio 2015 i obsługiwane w programie Visual Studio 2017.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3808.

```cpp
// C3808.cpp
// compile with: /c /clr:pure user32.lib
using namespace System::Runtime::InteropServices;

[System::Runtime::InteropServices::ComImportAttribute()]
ref struct S1 {
   int f() {}   // C3808
   virtual int g() abstract;   // OK

   [DllImport("msvcrt.dll")]
   int printf(System::String ^, int i);   // OK
};
```