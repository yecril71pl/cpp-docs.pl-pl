---
title: "Kompilatora (poziom 4) ostrzeżenie C4131 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4131
dev_langs: C++
helpviewer_keywords: C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 48e7ed1c5570e8bfa9d571cde649e618f51bcc2a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4131"></a>Kompilator C4131 ostrzegawcze (poziom 4)
"Funkcja": używa deklaratora w starym stylu  
  
 Deklaracja określona funkcja nie jest w formie prototypu.  
  
 Deklaracje funkcji w starym stylu powinny być konwertowane na formularzu prototypu.  
  
 W poniższym przykładzie przedstawiono deklaracji funkcji w starym stylu:  
  
```  
// C4131.c  
// compile with: /W4 /c  
void addrec( name, id ) // C4131 expected  
char *name;  
int id;  
{ }  
```  
  
 W poniższym przykładzie przedstawiono formularz prototypu:  
  
```  
void addrec( char *name, int id )  
{ }  
```