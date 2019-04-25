---
title: Błąd kompilatora C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: f53312fa9225270ef79d50d2ad351adce790d6fa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300540"
---
# <a name="compiler-error-c3367"></a>Błąd kompilatora C3367

"static_member_function": nie można użyć statycznej funkcji by utworzyć niezwiązanego delegata

Jeśli chcesz wywołać niezwiązanego delegata, należy przekazać wystąpienia obiektu. Ponieważ funkcja statycznej składowej jest wywoływana za pośrednictwem nazwy klasy, można tylko utworzyć wystąpienie niezwiązanego delegata z funkcję składową wystąpienia.

Aby uzyskać więcej informacji na temat niezwiązane obiekty delegowane zobacz [jak: Definiowanie i używanie delegatów (C++sposób niezamierzony)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3367.

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```