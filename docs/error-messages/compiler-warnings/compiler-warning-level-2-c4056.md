---
title: "Kompilatora (poziom 2) ostrzeżenie C4056 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4056
dev_langs: C++
helpviewer_keywords: C4056
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7457e1d6e9eeeb2bc4c0f957383e51f258a44120
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4056"></a>Kompilator C4056 ostrzegawcze (poziom 2)
przepełnienie zmiennoprzecinkowe punktu stałej arytmetycznej  
  
 Zmiennoprzecinkowej stałej arytmetycznej wygeneruje wyniku, który przekracza maksymalną dozwoloną wartość.  
  
 To ostrzeżenie może być spowodowane optymalizacje kompilatora wykonywane podczas stałej arytmetycznej. Można bezpiecznie zignorować to ostrzeżenie, jeśli jego zniknie po wyłączeniu optymalizacji ([/Od](../../build/reference/od-disable-debug.md)).  
  
 Poniższy przykład generuje C4056:  
  
```  
// C4056.cpp  
// compile with: /W2 /LD  
#pragma warning (default : 4056)  
float fp_val = 1.0e300 * 1.0e300;   // C4056  
```