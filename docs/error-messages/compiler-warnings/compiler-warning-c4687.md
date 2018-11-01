---
title: Ostrzeżenie kompilatora C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 50551faf817f83d8a4af848a75af67ebe7004fe7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635486"
---
# <a name="compiler-warning-c4687"></a>Ostrzeżenie kompilatora C4687

"class": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "interface"

Typu zapieczętowanego "," abstract przydaje się zwykle tylko do przechowywania statyczne funkcje Członkowskie.

Aby uzyskać więcej informacji, zobacz [abstrakcyjne](../../windows/abstract-cpp-component-extensions.md)i [zapieczętowanego](../../windows/sealed-cpp-component-extensions.md).

Domyślnie C4687 jest wystawiana jako błąd. Można pominąć C4687 z [ostrzeżenie](../../preprocessor/warning.md) pragmy. Jeśli chcesz zaimplementować interfejs w typie zapieczętowanym, abstract, można pominąć C4687.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4687.

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```