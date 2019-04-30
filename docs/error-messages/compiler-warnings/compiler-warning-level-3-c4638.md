---
title: Kompilator ostrzeżenie (poziom 3) C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: 1bdd7541e16f5c02756678ae78a777094b5fe588
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401661"
---
# <a name="compiler-warning-level-3-c4638"></a>Kompilator ostrzeżenie (poziom 3) C4638

> Docelowy komentarza dokumentu XML: odwołanie do nieznanego symbolu "*symbol*"

## <a name="remarks"></a>Uwagi

Kompilator nie może rozpoznać symbolu (*symbol*). Symbol muszą być prawidłowe w kompilacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4638:

```cpp
// C4638.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary> Text </summary>
   /// <see cref="aSymbolThatAppearsNowhereInMyProject"/>
   // Try the following line instead:
   // /// <see cref="System::Console::WriteLine"/>
   void MyMethod() {}
};   // C4638
```