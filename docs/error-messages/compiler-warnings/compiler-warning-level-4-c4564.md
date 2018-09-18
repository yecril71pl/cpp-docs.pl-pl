---
title: Kompilator ostrzeżenie (poziom 4) C4564 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4564
dev_langs:
- C++
helpviewer_keywords:
- C4564
ms.assetid: 555b301b-313e-4262-9f81-eb878674be60
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ea8d392251c8168490d7841ad590731b5a08e7f5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031837"
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