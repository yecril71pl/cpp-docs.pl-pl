---
title: Ostrzeżenie kompilatora (poziom 3) C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: 3662116359f906ef6f0a004fada8efd6771d0a0a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174131"
---
# <a name="compiler-warning-level-3-c4638"></a>Ostrzeżenie kompilatora (poziom 3) C4638

> Obiekt docelowy komentarza dokumentu XML: odwołanie do nieznanego symbolu "*symbol*"

## <a name="remarks"></a>Uwagi

Kompilator nie może rozpoznać symbolu (*symbol*). Symbol musi być prawidłowy w kompilacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4638:

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
