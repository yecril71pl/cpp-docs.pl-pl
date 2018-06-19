---
title: Kompilatora (poziom 4) ostrzeżenie C4125 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4125
dev_langs:
- C++
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: af7fdd16925f080137be386cb3d2dd0dd3d8b446
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293848"
---
# <a name="compiler-warning-level-4-c4125"></a>Kompilator C4125 ostrzegawcze (poziom 4)
cyfra dziesiętna kończy ósemkową sekwencja ucieczki  
  
 Kompilator oblicza liczbę ósemkową bez cyfra dziesiętna przyjęto założenie, że znaku jest dziesiętną wartością cyfrową.  
  
## <a name="example"></a>Przykład  
  
```  
// C4125a.cpp  
// compile with: /W4  
char array1[] = "\709"; // C4125  
int main()  
{  
}  
```  
  
 Jeśli cyfrę 9 służy jako znak, popraw przykładzie w następujący sposób:  
  
```  
// C4125b.cpp  
// compile with: /W4  
char array[] = "\0709";  // C4125 String containing "89"  
int main()  
{  
}  
```