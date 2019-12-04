---
title: Błąd krytyczny C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 95e13a6914b5e02441f95dd2256532dbd1d718e5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747023"
---
# <a name="fatal-error-c1308"></a>Błąd krytyczny C1308

Łączenie zestawów nie jest obsługiwane

Element. webmodule jest dozwolony jako dane wejściowe dla konsolidatora, ale zestaw nie jest. Ten błąd może zostać wygenerowany, gdy zostanie podjęta próba połączenia zestawu skompilowanego z `/clr:safe`.

Aby uzyskać więcej informacji, zobacz [. moduły plików jako dane wejściowe konsolidatora](../../build/reference/netmodule-files-as-linker-input.md).

Poniższy przykład generuje C1308:

```cpp
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

A następnie

```cpp
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```
