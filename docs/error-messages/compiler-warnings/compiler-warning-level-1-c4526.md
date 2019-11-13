---
title: Ostrzeżenie kompilatora (poziom 1) C4526
ms.date: 11/04/2016
f1_keywords:
- C4526
helpviewer_keywords:
- C4526
ms.assetid: 490f8916-5fdc-4cad-b412-76c3382a5976
ms.openlocfilehash: 60ac01d6a118f37a22b39ab41fa60252866f3360
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966268"
---
# <a name="compiler-warning-level-1-c4526"></a>Ostrzeżenie kompilatora (poziom 1) C4526

"Function": statyczna funkcja członkowska nie może przesłonić funkcji wirtualnej "Virtual function'overrideed", funkcja wirtualna zostanie ukryta

Statyczna funkcja członkowska spełnia kryteria umożliwiające przesłonięcie funkcji wirtualnej, co sprawia, że funkcja członkowska jest wirtualna i statyczna.

Poniższy kod generuje C4526:

```cpp
// C4526.cpp
// compile with: /W1 /c
// C4526 expected
struct myStruct1 {
   virtual void __stdcall func( int ) = 0;
};

struct myStruct2: public myStruct1 {
   static void __stdcall func( int );
};
```

Możliwe są następujące poprawki:

- Jeśli funkcja była przeznaczona do przesłonięcia funkcji wirtualnej klasy bazowej, Usuń specyfikator statyczny.

- Jeśli funkcja była przeznaczona do statycznej funkcji członkowskiej, zmień jej nazwę, aby nie powodowała konfliktu z funkcją wirtualną klasy bazowej.