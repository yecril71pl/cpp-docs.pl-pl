---
title: Ostrzeżenie kompilatora (poziom 4) C4564
ms.date: 11/04/2016
f1_keywords:
- C4564
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
ms.openlocfilehash: 042eab1c125f2b98fd36257dfd8971262015ab92
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990679"
---
# <a name="compiler-warning-level-4-c4564"></a>Ostrzeżenie kompilatora (poziom 4) C4564

Metoda "Method" klasy "Class" definiuje nieobsługiwany parametr domyślny "parameter"

Kompilator wykrył metodę z co najmniej jednym parametrem z wartościami domyślnymi. Wartości domyślne parametrów zostaną zignorowane, gdy wywoływana jest metoda; jawnie określ wartości tych parametrów. Jeśli nie określisz jawnie wartości dla tych parametrów, C++ kompilator wygeneruje błąd.

Nadana została następująca Biblioteka. dll utworzona przy użyciu Visual Basic, która umożliwia używanie parametrów domyślnych dla argumentów metody:

```vb
' C4564.vb
' compile with: vbc /t:library C4564.vb
Public class TestClass
   Public Sub MyMethod (a as Integer, _
                        Optional c as Integer=1)
   End Sub
End class
```

I Poniższy C++ przykład, który używa biblioteki. dll utworzonej przy użyciu Visual Basic,

```cpp
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
