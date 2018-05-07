---
title: C2800 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2800
dev_langs:
- C++
helpviewer_keywords:
- C2800
ms.assetid: a2f1a590-9fe6-44cb-ad09-b4505ef47c6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9dd9723513042ae7ef6d63914f5abecd63192e37
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2800"></a>C2800 błąd kompilatora
"operator operator" nie może być przeciążony.  
  
 Nie może zostać przeciążony następujące operatory: dostęp do elementu członkowskiego klasy (`.`), wskaźnika do elementu członkowskiego (`.*`), zakres rozpoznawania (`::`), wyrażenia warunkowego (`? :`), i `sizeof`.  
  
 Poniższy przykład generuje C2800:  
  
```  
// C2800.cpp  
// compile with: /c  
class C {  
   operator:: ();   // C2800  
};  
```