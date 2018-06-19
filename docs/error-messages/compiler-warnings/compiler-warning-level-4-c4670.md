---
title: Kompilatora (poziom 4) ostrzeżenie C4670 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4670
dev_langs:
- C++
helpviewer_keywords:
- C4670
ms.assetid: e172b134-b1fb-4dfe-8e9d-209ea08b73c7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9bec30fff715984073aa3061979fff11923f0bf8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33315363"
---
# <a name="compiler-warning-level-4-c4670"></a>Kompilator C4670 ostrzegawcze (poziom 4)
'Identyfikator': Ta klasa podstawowa jest niedostępna  
  
 Określona klasa podstawowa obiektu zostanie wygenerowany **spróbuj** bloku nie jest dostępny. Nie można utworzyć wystąpienia obiektu, jeśli generowany jest. Sprawdź, czy klasa podstawowa jest dziedziczona ze specyfikatorem dostępu.  
  
 Poniższy przykład generuje C4670:  
  
```  
// C4670.cpp  
// compile with: /EHsc /W4  
class A  
{  
};  
  
class B : /* public */ A  
{  
} b;   // inherits A with private access by default  
  
int main()  
{  
    try  
    {  
       throw b;   // C4670  
    }  
    catch( B )  
    {  
    }  
}  
```