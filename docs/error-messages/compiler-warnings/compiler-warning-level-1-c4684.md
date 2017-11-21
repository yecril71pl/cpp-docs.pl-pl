---
title: "Kompilatora (poziom 1) ostrzeżenie C4684 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4684
dev_langs: C++
helpviewer_keywords: C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7a5dd86000a80f9c692989a307a2ce30a77c027f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4684"></a>Kompilator C4684 ostrzegawcze (poziom 1)
'attribute': ostrzeżenie!! atrybut może powodować generowanie nieprawidłowego kodu: Używaj ostrożnie  
  
 Użyto atrybutu, który zwykle nie należy używać.  
  
 Poniższy przykład generuje C4684:  
  
```  
// C4684.cpp  
// compile with: /W1 /LD  
 [module(name="xx")]; // C4684 expected  
[no_injected_text];  
```