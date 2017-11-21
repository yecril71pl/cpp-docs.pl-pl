---
title: "Kompilatora (poziom 1) ostrzeżenie C4176 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4176
dev_langs: C++
helpviewer_keywords: C4176
ms.assetid: cfffb934-219a-4a63-9df6-ba54405bf766
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 96b6b70eff74bc25fb39cf3a709da5bf17423806
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4176"></a>Kompilator C4176 ostrzegawcze (poziom 1)
'podskładnik': nieznany podskładnik dla składnika przeglądarki #pragma  
  
 **Składnika** pragma zawiera nieprawidłowy podskładnika. Aby wykluczyć odwołania do konkretnej nazwy, należy użyć **odwołania** opcji przed nazwą.  
  
## <a name="example"></a>Przykład  
  
```  
// C4176.cpp  
// compile with: /W1 /LD  
#pragma component(browser, off, i)  // C4176  
#pragma component(browser, off, references, i) // ok  
```