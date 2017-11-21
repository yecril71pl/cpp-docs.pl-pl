---
title: "C2588 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2588
dev_langs: C++
helpviewer_keywords: C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c6d71e5bfe442f2b3f2225cd4dc6cb88fc73d24a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2588"></a>C2588 błąd kompilatora
":: ~ identyfikator": niedozwolony globalny — destruktor  
  
 Destruktor jest zdefiniowany dla elementu innego niż klasy, struktury lub związku. Jest to niedozwolone.  
  
 Przyczyną tego błędu może być Brak klasy, struktury lub Unii nazwy po lewej stronie rozpoznawanie zakresów (`::`) operatora.  
  
 Poniższy przykład generuje C2588:  
  
```  
// C2588.cpp  
~F();   // C2588  
```