---
title: "C2466 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2466
dev_langs: C++
helpviewer_keywords: C2466
ms.assetid: 75b251d1-7d0b-4a86-afca-26adedf74486
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c3ad19ce37aa51bd6b670da6e857d7eccce04ca
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2466"></a>C2466 błąd kompilatora
Nie można przydzielić tablicy stałego rozmiaru 0  
  
 Tablica jest przydzielona lub zadeklarowana z rozmiarem zero. Wyrażenie stałe dla rozmiaru tablicy musi być liczbą całkowitą większą niż zero. Deklaracja tablicy z zerowego indeks dolny jest dozwolony, tylko w przypadku klasy, struktury lub elementu członkowskiego typu union i tylko z rozszerzeniami firmy Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).  
  
 Poniższy przykład generuje C2466:  
  
```  
// C2466.cpp  
// compile with: /c  
int i[0];   // C2466  
int j[1];   // OK  
char *p;  
```