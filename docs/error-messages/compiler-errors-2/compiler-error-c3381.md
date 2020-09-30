---
title: Błąd kompilatora C3381
description: Błąd kompilatora Microsoft C++ C3381, jego przyczyny i sposoby ich rozwiązywania.
ms.date: 09/28/2020
f1_keywords:
- C3381
helpviewer_keywords:
- C3381
ms.assetid: d276c89f-8377-4cb6-a8d4-7770885f06c4
ms.openlocfilehash: 48a6c81f9506c532333b5353b8b194d17c91043f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510156"
---
# <a name="compiler-error-c3381"></a>Błąd kompilatora C3381

> "*Identyfikator*": specyfikatory dostępu do zestawu są dostępne tylko w kodzie skompilowanym z opcją/CLR

Typ został zadeklarowany lub zdefiniowany za pomocą specyfikatora dostępu, który jest dozwolony tylko w kodzie skompilowanym za pomocą **`/clr`** .

## <a name="remarks"></a>Uwagi

Ten błąd może wynikać z błędnego miejsca **`public`** lub **`protected`** **`private`** słowa kluczowego lub brakującego dwukropka ( **`:`** ) Po specyfikatorze dostępu w **`class`** lub **`struct`** .

W języku C++/CLI typy natywne mogą być widoczne poza zestawem, ale dostęp do zestawu można określić tylko dla typów natywnych w **`/clr`** kompilacji. Aby uzyskać więcej informacji, zobacz [widoczność typów](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Type_visibility) i [ `/clr` (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Przykład

Poniższy przykład generuje C3381. Aby rozwiązać ten problem, należy najpierw usunąć **`public`** specyfikator z `class A` definicji lub skompilować przy użyciu **`/clr`** opcji. Następnie Dodaj dwukropek po **`private`** określeniu dostępu dla `class B {} b;` . Dzieje się tak, ponieważ Klasa zagnieżdżona nie może mieć specyfikatora dostępu do zestawu jako części swojej deklaracji.

```cpp
// C3381.cpp
// compile with: /c
public class A {   // C3381
    private class B {} b;   // C3381
};
```
