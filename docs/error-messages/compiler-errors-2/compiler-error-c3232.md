---
title: "C3232 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3232
dev_langs: C++
helpviewer_keywords: C3232
ms.assetid: 3119b3a9-0eff-4a3f-b805-e4d160af9e39
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0df7833f7919c5addfe7bcef9dfe818d78271e3e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3232"></a>C3232 błąd kompilatora
"param": nie można użyć parametru typu ogólnego w kwalifikowanej nazwie  
  
 Parametr typu ogólnego zostało niepoprawnie użyte.  
  
 Poniższy przykład generuje C3232:  
  
```  
// C3232.cpp  
// compile with: /clr  
generic <class T>  
ref class C {  
   typename T::TYPE t;   // C3232  
};  
```