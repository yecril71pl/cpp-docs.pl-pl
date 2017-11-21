---
title: "C2165 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2165
dev_langs: C++
helpviewer_keywords: C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d8d319826edac5ccdb83ab69b89abc11d5e54b68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2165"></a>C2165 błąd kompilatora
"— słowo kluczowe": nie można modyfikować wskaźników do danych  
  
 `__stdcall`, `__cdecl`, Lub `__fastcall` — słowo kluczowe próbuje zmodyfikować wskaźnik do danych.  
  
 Poniższy przykład generuje C2165:  
  
```  
// C2165.cpp  
// compile with: /c  
char __cdecl *p;   // C2165  
char *p;   // OK  
```