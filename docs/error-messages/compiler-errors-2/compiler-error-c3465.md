---
title: Błąd kompilatora C3465
ms.date: 11/04/2016
f1_keywords:
- C3465
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
ms.openlocfilehash: 117c9b9918950fd2e95e206c5aea457dee183b0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222322"
---
# <a name="compiler-error-c3465"></a>Błąd kompilatora C3465

Aby użyć typu "type" musi odwoływać się do zestawu 'Zestaw'

Przekazywanie dalej typu będzie działać dla aplikacji klienckiej, dopóki nie zostanie ponownie skompilowany klienta. Gdy zostanie ponownie skompilowana, konieczne będzie odwołanie dla każdego zestawu zawierającego definicję typu używane w aplikacji klienckiej.

Aby uzyskać więcej informacji, zobacz [Type Forwarding (C++sposób niezamierzony)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład tworzy zestaw, który zawiera nową lokalizację typu.

```
// C3465.cpp
// compile with: /clr /LD
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>Przykład

Poniższy przykład tworzy zestawu, który zawierał definicji typu, ale zawiera teraz składni przesyłania dalej dla typu.

```
// C3465_b.cpp
// compile with: /clr /LD
#using "C3465.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3465.

```
// C3465_c.cpp
// compile with: /clr
// C3465 expected
#using "C3465_b.dll"
// Uncomment the following line to resolve.
// #using "C3465.dll"

int main() {
   R^ r = gcnew R();
}
```