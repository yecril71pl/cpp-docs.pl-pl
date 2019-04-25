---
title: Błąd kompilatora C3399
ms.date: 11/04/2016
f1_keywords:
- C3399
helpviewer_keywords:
- C3399
ms.assetid: 306ad199-d150-4f6c-bcf1-24a7948b93be
ms.openlocfilehash: d05a861a2baedb86482503b6860098f12c41bd78
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62300430"
---
# <a name="compiler-error-c3399"></a>Błąd kompilatora C3399

"type": nie można udostępnić argumentów podczas tworzenia wystąpienia parametru generycznego

Po określeniu `gcnew()` ograniczenia, należy określić że typu ograniczenie konstruktora bez parametrów. Dlatego jest błąd, aby spróbować utworzyć wystąpienia tego typu i przekazywania parametru.

Zobacz [ograniczenia dotyczące parametrów typu ogólnego (C++sposób niezamierzony)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) Aby uzyskać więcej informacji.

## <a name="example"></a>Przykład

Poniższy przykład spowoduje wygenerowanie C3399.

```
// C3399.cpp
// compile with: /clr /c
generic <class T>
where T : gcnew()
void f() {
   T t = gcnew T(1);   // C3399
   T t2 = gcnew T();   // OK
}
```