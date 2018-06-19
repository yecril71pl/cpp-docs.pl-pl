---
title: C4986 ostrzeżenia kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4986
dev_langs:
- C++
helpviewer_keywords:
- C4986
ms.assetid: a3a7b008-29dd-4203-85f3-7740ab6790bb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5c5342a65e9f900582246bb007d9dd67338dd8e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275165"
---
# <a name="compiler-warning-c4986"></a>C4986 ostrzeżenia kompilatora
"Funkcja": specyfikacja wyjątku jest niezgodna z poprzednią deklaracją  
  
 To ostrzeżenie mogą być generowane, gdy brak specyfikacji wyjątku w jednej deklaracji i nie innych.  
  
 Domyślnie C4986 jest wyłączone. Aby uzyskać więcej informacji, zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4986.  
  
```cpp  
class X { };  
void f1() throw (X*);  
// ...  
void f1()  
{  
    // ...  
}    
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład eliminuje to ostrzeżenie.  
  
```cpp  
class X { };  
void f1() throw (X*);  
// ...  
void f1() throw (X*)  
{  
    // ...  
}    
```