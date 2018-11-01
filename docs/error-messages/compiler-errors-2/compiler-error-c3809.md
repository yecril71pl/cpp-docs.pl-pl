---
title: Błąd kompilatora C3809
ms.date: 11/04/2016
f1_keywords:
- C3809
helpviewer_keywords:
- C3809
ms.assetid: 37eca584-c20c-464e-8e45-a987214b7ce4
ms.openlocfilehash: 5ff57050980ddb770ea2fcfa4d0be4f42f5ee834
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50458802"
---
# <a name="compiler-error-c3809"></a>Błąd kompilatora C3809

"class": zarządzanej lub typu WinRT nie może mieć żadnych friend funkcji/klas/interfejsów

Typy zarządzane i typów środowiska wykonawczego Windows nie zezwalaj na znajomych. Aby naprawić ten błąd nie deklaruj znajomych w zarządzanych lub typów środowiska wykonawczego Windows.

Poniższy przykład spowoduje wygenerowanie C3809:

```
// C3809a.cpp
// compile with: /clr
ref class A {};

ref class B
{
public:
   friend ref class A;   // C3809
};

int main()
{
}
```