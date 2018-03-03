---
title: "Kompilatora (poziom 1) ostrzeżenie C4662 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4662
dev_langs:
- C++
helpviewer_keywords:
- C4662
ms.assetid: 7efda273-d04a-47b7-ad65-ff1ff94b5ffc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9510d0bb8f6786662efa0fcb8e2d4c5f384405d7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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