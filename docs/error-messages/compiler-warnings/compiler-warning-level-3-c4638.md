---
title: Kompilator ostrzeżenie (poziom 3) C4638 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4638
dev_langs:
- C++
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29febc17f041fee27064fc085896c892eecd5c56
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43198235"
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