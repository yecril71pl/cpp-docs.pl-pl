---
title: Ostrzeżenie kompilatora C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 83f5c535f9cf252783110838c181c88c8b0096ee
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631608"
---
# <a name="compiler-warning-c4687"></a>Ostrzeżenie kompilatora C4687

> "*Class*": zapieczętowana Klasa abstrakcyjna nie może implementować interfejsu "*Interface*"

## <a name="remarks"></a>Uwagi

Zapieczętowany, abstrakcyjny typ jest zwykle przydatny tylko do przechowywania statycznych funkcji Członkowskich.

Aby uzyskać więcej informacji, [](../../extensions/abstract-cpp-component-extensions.md) Zobacz abstrakcyjny i [zapieczętowany](../../extensions/sealed-cpp-component-extensions.md).

C4687 jest domyślnie wystawiany jako błąd. Możesz pominąć C4687 z pragmą [ostrzeżenia](../../preprocessor/warning.md) . Jeśli masz pewność, że chcesz zaimplementować interfejs w zapieczętowanym, abstrakcyjnym typie, możesz pominąć C4687.

## <a name="example"></a>Przykład

Poniższy przykład generuje C4687.

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
