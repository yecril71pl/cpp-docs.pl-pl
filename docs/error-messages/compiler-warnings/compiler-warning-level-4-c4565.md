---
title: "Kompilatora (poziom 4) ostrzeżenie C4565 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4565
dev_langs: C++
helpviewer_keywords: C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2cbe5e8aecd8863f0b3ba092b8d199c1032ce157
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4565"></a>Kompilator C4565 ostrzegawcze (poziom 4)
"Funkcja": zmiana definicji; symbol został wcześniej zadeklarowany z __declspec(modifier)  
  
 Symbol został ponownie zdefiniować lub ponownie zadeklarować i deklaracji, w przeciwieństwie do pierwszej deklaracji, lub definicji lub druga definicja nie miał `__declspec` modyfikator (***modyfikator***). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.  
  
 Poniższy przykład generuje C4565:  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```