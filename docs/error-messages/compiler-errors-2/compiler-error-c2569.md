---
title: "C2569 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2569
dev_langs: C++
helpviewer_keywords: C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: cf7df87144b664463f577360dac13af2d3006c8b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2569"></a>C2569 błąd kompilatora
"EnumOrUnion": enum/union nie można użyć jako klasa podstawowa  
  
 Jeśli typ musi pochodzić od określonego Unii lub wyliczenia, zmień Unii lub wyliczenia klasy lub struktury.  
  
 Poniższy przykład generuje C2569:  
  
```  
// C2569.cpp  
// compile with: /c  
union ubase {};  
class cHasPubUBase : public ubase {};   // C2569  
// OK  
struct sbase {};  
class cHasPubUBase : public sbase {};  
```