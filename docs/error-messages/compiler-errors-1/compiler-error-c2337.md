---
title: "C2337 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2337
dev_langs: C++
helpviewer_keywords: C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4ca2d5a7108d181ee6e93e94119b945ed7b9da9f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2337"></a>C2337 błąd kompilatora
"Nazwa atrybutu": nie znaleziono atrybutu  
  
 Użyto atrybutu, który nie jest obsługiwana w tej wersji programu Visual C++.  
  
 Poniższy przykład generuje C2337:  
  
```  
// C2337.cpp  
// compile with: /c  
[emitidl];  
[module(name="x")];  
[grasshopper]   // C2337, not a supported attribute  
class a{};  
```