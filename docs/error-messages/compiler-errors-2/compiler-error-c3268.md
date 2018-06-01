---
title: C3268 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3268
dev_langs:
- C++
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: eac0c4e7c25df466ecf1e7e28bccf9ee2a2e2953
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705260"
---
# <a name="compiler-error-c3268"></a>C3268 błąd kompilatora

> "*funkcja*": funkcja generyczna lub funkcja członkowska klasy generycznej nie może mieć zmiennej listy parametrów

## <a name="remarks"></a>Uwagi

**/CLR: pure** i **/CLR: Safe** — opcje kompilatora są używane w programie Visual Studio 2015 i nieobsługiwane w programie Visual Studio 2017 r.

Zobacz [ogólne](../../windows/generics-cpp-component-extensions.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład generuje C3268.

```cpp
// C3268.cpp
// compile with: /clr:pure /c
generic <class ItemType>
void Test(ItemType item, ...) {}   // C3268
// try the following line instead
// void Test(ItemType item) {}

generic <class ItemType2>
ref struct MyStruct { void Test(...){} };   // C3268
// try the following line instead
// ref struct MyStruct { void Test2(){} };   // OK
```