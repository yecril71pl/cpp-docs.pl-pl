---
title: Ostrzeżenie kompilatora C4439
ms.date: 11/04/2016
f1_keywords:
- C4439
helpviewer_keywords:
- C4439
ms.assetid: 9449958f-f407-4824-829b-9e092f2af97d
ms.openlocfilehash: d604c234b9445a7e5304118124620f0057f30975
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311348"
---
# <a name="compiler-warning-c4439"></a>Ostrzeżenie kompilatora C4439

'Funkcja': definicja funkcji z zarządzanym typem w sygnaturze musi mieć konwencję wywołania __clrcall

Kompilator niejawnie zastąpione konwencja wywołania z [__clrcall](../../cpp/clrcall.md). Aby rozwiązać tego ostrzeżenia, należy usunąć `__cdecl` lub `__stdcall` konwencji wywoływania.

C4439 zawsze jest wystawiany jako błąd. Możesz wyłączyć to ostrzeżenie za pomocą `#pragma warning` lub **/wd**; zobacz [ostrzeżenie](../../preprocessor/warning.md) lub [Wn /W0, / W1, / W2, / W3, / W4, / W1, / W2, / W3, / W4, / Wall / wo, WV, /WX (poziom ostrzegawczy)](../../build/reference/compiler-option-warning-level.md)Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4439.

```
// C4439.cpp
// compile with: /clr
void __stdcall f( System::String^ arg ) {}   // C4439
void __clrcall f2( System::String^ arg ) {}   // OK
void f3( System::String^ arg ) {}   // OK
```