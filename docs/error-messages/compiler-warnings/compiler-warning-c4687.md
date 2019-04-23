---
title: Ostrzeżenie kompilatora C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 1978e1a35ba5b5d59b5961a21378d8af6921d145
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59776317"
---
# <a name="compiler-warning-c4687"></a>Ostrzeżenie kompilatora C4687

"class": zapieczętowana klasa abstrakcyjna nie może implementować interfejsu "interface"

Typu zapieczętowanego "," abstract przydaje się zwykle tylko do przechowywania statyczne funkcje Członkowskie.

Aby uzyskać więcej informacji, zobacz [abstrakcyjne](../../extensions/abstract-cpp-component-extensions.md)i [zapieczętowanego](../../extensions/sealed-cpp-component-extensions.md).

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