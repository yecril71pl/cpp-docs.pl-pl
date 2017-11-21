---
title: "Kompilatora (poziom 1) ostrzeżenie C4618 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4618
dev_langs: C++
helpviewer_keywords: C4618
ms.assetid: 6ff10d0a-6d5b-4373-8196-1d57bb6b1611
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f1a9319e40dfb2aea29c6163628320aa08896066
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4618"></a>Kompilator C4618 ostrzegawcze (poziom 1)
Parametry dyrektywy pragma zawierają ciąg pusty; dyrektywa pragma została zignorowana  
  
 Pusty ciąg został podany jako argument **#pragma**.  
  
 Pragma została przetworzona bez argumentu.  
  
 Poniższy przykład generuje C4618:  
  
```  
// C4618.cpp  
// compile with: /W1 /LD  
#pragma code_seg("")   // C4618  
```