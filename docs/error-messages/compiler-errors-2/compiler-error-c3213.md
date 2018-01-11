---
title: "C3213 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3213
dev_langs: C++
helpviewer_keywords: C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 593e967d944f4a29371469c69d80605e3e2579ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3213"></a>C3213 błąd kompilatora
Klasa podstawowa "base_type" jest mniej dostępny niż "derived_type"  
  
 Typ, który będzie widoczny z zestawu, należy użyć widocznego publicznie klas podstawowych.  
  
 Poniższy przykład generuje C3213:  
  
```  
// C3213.cpp  
// compile with: /clr  
private ref struct privateG {  
public:  
   int i;  
};  
  
public ref struct publicG {  
public:  
   int i;  
};  
  
public ref struct V : public privateG {   // C3213  
public:  
   int j;  
};  
  
public ref struct W: public publicG {   // OK  
public:  
   int j;  
};  
```