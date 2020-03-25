---
title: Ostrzeżenie kompilatora C4986
ms.date: 11/04/2016
f1_keywords:
- C4986
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
ms.openlocfilehash: df6fc88ffe98dd2b4a3129800c7881f26d4f625b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164823"
---
# <a name="compiler-warning-c4986"></a>Ostrzeżenie kompilatora C4986

"Function": Specyfikacja wyjątku nie jest zgodna z poprzednią deklaracją

To ostrzeżenie można wygenerować, gdy istnieje Specyfikacja wyjątku w jednej deklaracji, a nie druga.

Domyślnie C4986 jest wyłączona. Aby uzyskać więcej informacji, zobacz [ostrzeżenia kompilatora, które są domyślnie wyłączone](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C4986.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1()
{
    // ...
}
```

## <a name="example"></a>Przykład

Poniższy przykład eliminuje to ostrzeżenie.

```cpp
class X { };
void f1() throw (X*);
// ...
void f1() throw (X*)
{
    // ...
}
```
