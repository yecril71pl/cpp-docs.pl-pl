---
title: Kompilatora (poziom 1) ostrzeżenie C4662 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4662
dev_langs:
- C++
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60739959a6c26e0a1674b287ebf0a4605966e09b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33283429"
---
# <a name="compiler-warning-level-1-c4662"></a>Kompilator C4662 ostrzegawcze (poziom 1)
jawne utworzenie wystąpienia; szablonu klasy "identifier1" nie ma definicji, z której można wyspecjalizować "identifier2"  
  
 Określony szablon klasy została zadeklarowana ale niezdefiniowana.  
  
## <a name="example"></a>Przykład  
  
```  
// C4662.cpp  
// compile with: /W1 /LD  
template<class T, int i> class MyClass; // no definition  
template MyClass< int, 1>;              // C4662  
```