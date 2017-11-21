---
title: "Kompilatora (poziom 1) ostrzeżenie C4085 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4085
dev_langs: C++
helpviewer_keywords: C4085
ms.assetid: 2bc6eb25-058f-4597-b351-fd69587b5170
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d4af461dbedf1a63c4357562093a3a1d9e2efd04
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4085"></a>Kompilator C4085 ostrzegawcze (poziom 1)
Oczekiwano wartości parametru pragma "on" lub "off"  
  
 Pragma wymaga **na** lub **poza** parametru. Pragma została zignorowana.  
  
 Poniższy przykład generuje C4085:  
  
```  
// C4085.cpp  
// compile with: /W1 /LD  
#pragma optimize( "t", maybe )  // C4085  
```