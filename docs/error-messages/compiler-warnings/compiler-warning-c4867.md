---
title: Ostrzeżenie kompilatora C4867
ms.date: 11/04/2016
f1_keywords:
- C4867
helpviewer_keywords:
- C4867
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
ms.openlocfilehash: 9fa9b382b42a2fb8ba72fd9744c612af5dd598d2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311075"
---
# <a name="compiler-warning-c4867"></a>Ostrzeżenie kompilatora C4867

'Funkcja': wywołanie funkcji brakuje listy argumentów; Użyj "wywołać", aby utworzyć wskaźnik do składowej

Wskaźnik do funkcji składowej został niepoprawnie zainicjowany.

To ostrzeżenie można wygenerować w wyniku pracy zgodności kompilatora, która została wykonana dla programu Visual C++ 2005: rozszerzoną zgodność wskaźników do elementów członkowskich.  Kod, który jest skompilowany przed Visual C++ 2005 teraz wygeneruje C4867.

To jest zawsze ostrzeżenie jako błąd. Użyj [ostrzeżenie](../../preprocessor/warning.md) pragma może wyłączyć to ostrzeżenie. Aby uzyskać więcej informacji na temat C4867 i MFC i ATL, zobacz [_ATL_ENABLE_PTM_WARNING](../../atl/reference/compiler-options-macros.md#_atl_enable_ptm_warning).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4867.

```
// C4867.cpp
// compile with: /c
class A {
public:
   void f(int) {}

   typedef void (A::*TAmtd)(int);

   struct B {
      TAmtd p;
   };

   void g() {
      B b = {f};   // C4867
      B b2 = {&A::f};   // OK
   }
};
```