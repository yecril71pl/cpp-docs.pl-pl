---
title: Kompilatora (poziom 4) ostrzeżenie C4564 | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1f0cf68eb75d420a0d23c04687d4f9492910b53f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4564"></a>Kompilator C4564 ostrzegawcze (poziom 4)
Metoda "method" klasy "class" definiuje nieobsługiwany parametr domyślny "parameter"  
  
 Kompilator wykryto metodę z co najmniej jeden parametr z wartościami domyślnymi. Wartości domyślne dla parametrów zostanie zignorowany, gdy wywoływana jest metoda; jawnie określić wartości dla tych parametrów. Jeśli nie zostanie jawnie wartości tych parametrów, kompilator języka C++, zostanie wygenerowany błąd.  
  
 Biorąc pod uwagę następujące biblioteki dll, utworzone za pomocą języka Visual Basic, który umożliwia skonfigurowanie parametrów domyślnych argumenty metody:  
  
```  
' C4564.vb  
' compile with: vbc /t:library C4564.vb  
Public class TestClass  
   Public Sub MyMethod (a as Integer, _  
                        Optional c as Integer=1)  
   End Sub  
End class  
```  
  
 I następujące próbka C++, która korzysta z biblioteki DLL utworzone za pomocą języka Visual Basic  
  
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