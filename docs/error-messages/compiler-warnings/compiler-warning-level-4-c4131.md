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
ms.workload: cplusplus
ms.openlocfilehash: ea37a3f210a2c379471b481fb0812b6c0630d32a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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