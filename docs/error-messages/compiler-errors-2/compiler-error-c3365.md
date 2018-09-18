---
title: Błąd kompilatora C3365 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3365
dev_langs:
- C++
helpviewer_keywords:
- C3365
ms.assetid: 875ec3a4-522c-4e3d-9b67-48808b857f6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b8cb585c2d1142651e5edd01085dd904be60bc86
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044720"
---
# <a name="compiler-error-c3365"></a>Błąd kompilatora C3365

operator 'operator': operandy typu "type1" i "type2"

Próbowano składanie obiektów delegowanych z różnymi typami.  Zobacz [porady: definiowanie i użycie delegatów (C + +/ interfejsu wiersza polecenia)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md) Aby uzyskać więcej informacji na temat obiektów delegowanych.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3365:

```cpp
// C3365.cpp
// compile with: /clr
delegate void D1();
delegate void D2(int);

ref class R {
public:
   void f(){}
   void g(int){}
};

int main() {
   D1^ d1 = gcnew D1(gcnew R, &R::f);
   D2^ d2 = gcnew D2(gcnew R, &R::g);
   D1^ d3 = gcnew D1(gcnew R, &R::f);

   d1 += d2;   // C3365
   d1 += d3;   // OK
   d1();
}
```