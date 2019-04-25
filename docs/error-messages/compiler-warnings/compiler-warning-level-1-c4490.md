---
title: Kompilator ostrzeżenie (poziom 1) C4490
ms.date: 11/04/2016
f1_keywords:
- C4490
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
ms.openlocfilehash: bf51994c210bd751e0d29bec169dfc4366784486
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161098"
---
# <a name="compiler-warning-level-1-c4490"></a>Kompilator ostrzeżenie (poziom 1) C4490

"override": Niepoprawne użycie specyfikatora override; 'Funkcja' nie odpowiada metodzie bazowej klasy referencyjnej

Specyfikator przesłonięcia zostało niepoprawnie użyte. Na przykład nie zastępuje funkcję interfejsu, możesz wdrożyć.

Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów](../../extensions/override-specifiers-cpp-component-extensions.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4490.

```
// C4490.cpp
// compile with: /clr /c /W1

interface struct IFace {
   void Test();
};

ref struct Class1 : public IFace {
   virtual void Test() override {}   // C4490
   // try the following line instead
   // virtual void Test() {}
};
```