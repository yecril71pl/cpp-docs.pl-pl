---
title: "Kompilatora (poziom 1) ostrzeżenie C4167 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4167
dev_langs: C++
helpviewer_keywords: C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9df836e1d0e3f33feca4884e1c05194f065be545
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4167"></a>Kompilator C4167 ostrzegawcze (poziom 1)
Funkcja: dostępne tylko jako funkcja wewnętrzna  
  
 **Funkcji #pragma** próbuje wymusić kompilatorowi używanie konwencjonalnej wywołanie funkcji, używany w postaci wewnętrznej. Pragma została zignorowana.  
  
 Aby uniknąć tego ostrzeżenia, należy usunąć **funkcji #pragma**.  
  
## <a name="example"></a>Przykład  
  
```  
// C4167.cpp  
// compile with: /W1  
#include <malloc.h>  
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only  
int main(){}  
```