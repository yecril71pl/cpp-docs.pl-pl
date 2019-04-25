---
title: Kompilator ostrzeżenie (poziom 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 1948bdec5367fa7943f5a0de4338fd4ecd6c6581
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62220510"
---
# <a name="compiler-warning-level-4-c4564"></a>Kompilator ostrzeżenie (poziom 4) C4564

Metoda "method" klasy "class" definiuje nieobsługiwany parametr domyślny "parametru"

Kompilator wykrył metody z co najmniej jeden parametr z wartościami domyślnymi. Wartości domyślne dla parametrów zostanie zignorowany, gdy metoda jest wywoływana; jawnie określić wartości dla tych parametrów. Jeśli nie zostanie jawnie wartości tych parametrów, kompilator języka C++, zostanie wygenerowany błąd.

Biorąc pod uwagę następujący plik .dll, utworzony za pomocą Visual Basic, który umożliwia skonfigurowanie parametrów domyślnych argumenty metody:

```
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

I poniższy przykład C++, używającej dll utworzony za pomocą Visual Basic

```
// C4564.cpp
// compile with: /clr /W4 /WX
#using <C4564.dll>

int main() {
   TestClass ^ myx = gcnew TestClass();   // C4564
   myx->MyMethod(9);
   // try the following line instead, to avoid an error
   // myx->MyMethod(9, 1);
}
```