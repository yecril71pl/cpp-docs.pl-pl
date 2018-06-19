---
title: C2588 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 67eb6362ff55e09b05349d10fcdc2377d8ff2996
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33231673"
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