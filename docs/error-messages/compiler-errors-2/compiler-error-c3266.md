---
title: Błąd kompilatora C3266
ms.date: 11/04/2016
f1_keywords:
- C3266
helpviewer_keywords:
- C3266
ms.assetid: 7375c099-acb7-42f6-898d-57cfefa010b8
ms.openlocfilehash: d93056116ebf2f4646dc34f848b073fe6401b9db
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365861"
---
# <a name="compiler-error-c3266"></a>Błąd kompilatora C3266

"class": konstruktor klasy musi mieć listę parametrów "void"

Konstruktory klasy w klasie za pomocą programowania/CLR nie przyjmuje parametrów.

Poniższy przykład spowoduje wygenerowanie C3266:

```
// C3266.cpp
// compile with: /clr

ref class X {
   static X(int i) { // C3266
   // try the following line instead
   // static X() {
   }
};

int main() {
}
```
