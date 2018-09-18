---
title: Błąd kompilatora C3465 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3465
dev_langs:
- C++
helpviewer_keywords:
- C3465
ms.assetid: aeb815e5-b3fc-4525-afe2-d738e9321df1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6aa388d95904aecc8e1ba558b374249bb280e02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048984"
---
# <a name="compiler-error-c3465"></a>Błąd kompilatora C3465

Aby użyć typu "type" musi odwoływać się do zestawu 'Zestaw'

Przekazywanie dalej typu będzie działać dla aplikacji klienckiej, dopóki nie zostanie ponownie skompilowany klienta. Gdy zostanie ponownie skompilowana, konieczne będzie odwołanie dla każdego zestawu zawierającego definicję typu używane w aplikacji klienckiej.

Aby uzyskać więcej informacji, zobacz [przekazywania dalej typów (C + +/ CLI)](../../windows/type-forwarding-cpp-cli.md).

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