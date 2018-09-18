---
title: Ostrzeżenie kompilatora C4986 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4986
dev_langs:
- C++
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f464f2a6e1f76c7d8b9de8bcc2353766aff0854
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46077064"
---
# <a name="compiler-warning-c4986"></a>Ostrzeżenie kompilatora C4986

'Funkcja': specyfikacja wyjątku jest niezgodna z poprzednią deklaracją

To ostrzeżenie mogą być generowane po specyfikacji wyjątku w jednej deklaracji, a nie drugą.

Domyślnie C4986 jest wyłączona. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżenia, są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C4986.

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