---
title: Ostrzeżenie LNK4248 narzędzi konsolidatora
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 81f3c2abc41673e6e4c9e3f59ff1dd515e1cf365
ms.sourcegitcommit: c1fd917a8c06c6504f66f66315ff352d0c046700
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/16/2020
ms.locfileid: "90685428"
---
# <a name="linker-tools-warning-lnk4248"></a>Ostrzeżenie LNK4248 narzędzi konsolidatora

nierozpoznany token TypeRef (token) dla elementu "Type"; nie można uruchomić obrazu

Typ nie ma definicji w metadanych MSIL.

LNK4248 narzędzi KONSOLIDATORA może wystąpić, gdy istnieje tylko Deklaracja do przodu dla typu w module MSIL (skompilowane z **/CLR**), gdzie w module MSIL jest przywoływany typ, a moduł MSIL jest połączony z modułem macierzystym, który ma definicję dla tego typu.

W takiej sytuacji konsolidator udostępni definicję typu natywnego w metadanych MSIL i może zapewnić poprawne zachowanie.

Jednakże jeśli deklaracja typu do przodu jest typem CLR, definicja typu natywnego konsolidatora może być niepoprawna

Aby uzyskać więcej informacji, zobacz [/CLR (Kompilacja środowiska uruchomieniowego języka wspólnego)](../../build/reference/clr-common-language-runtime-compilation.md).

### <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Podaj definicję typu w module MSIL.

## <a name="examples"></a>Przykłady

Poniższy przykład generuje LNK4248 narzędzi KONSOLIDATORA. Zdefiniuj strukturę A, aby rozwiązać ten problem.

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

Poniższy przykład zawiera definicję typu.

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

Poniższy przykład generuje LNK4248 narzędzi KONSOLIDATORA.

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
