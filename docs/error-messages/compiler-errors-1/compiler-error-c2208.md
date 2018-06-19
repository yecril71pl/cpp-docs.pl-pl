---
title: C2208 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2208
dev_langs:
- C++
helpviewer_keywords:
- C2208
ms.assetid: 9ae704bc-bf70-45f1-8e47-0470f21edd4e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 24377d17735fc63e9dc0541dfd9fb432eb0e0cda
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33172112"
---
# <a name="compiler-error-c2208"></a>C2208 błąd kompilatora
'type': Brak członków zdefiniowanych przy użyciu tego typu  
  
 Identyfikator rozpoznawania nazwy typu znajduje się w deklaracji agregacji, ale kompilator nie deklaruje elementu członkowskiego.  
  
 Poniższy przykład generuje C2208:  
  
```  
// C2208.cpp  
class C {  
   C;   // C2208  
   C(){}   // OK  
};  
```