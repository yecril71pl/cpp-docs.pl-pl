---
title: Kompilator ostrzeżenie (poziom 1) C4490 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4490
dev_langs:
- C++
helpviewer_keywords:
- C4490
ms.assetid: f9b03ecf-41a1-4f4d-a74c-2c1e88234ccc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d6bda2aaf729c2d4b8fb29dcbeaff428ed79d78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46090870"
---
# <a name="compiler-warning-level-1-c4490"></a>Kompilator ostrzeżenie (poziom 1) C4490

"override": Niepoprawne użycie specyfikatora override; 'Funkcja' nie odpowiada metodzie bazowej klasy referencyjnej

Specyfikator przesłonięcia zostało niepoprawnie użyte. Na przykład nie zastępuje funkcję interfejsu, możesz wdrożyć.

Aby uzyskać więcej informacji, zobacz [zastąpienie specyfikatorów](../../windows/override-specifiers-cpp-component-extensions.md).

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