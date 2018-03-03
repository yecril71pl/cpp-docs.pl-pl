---
title: "Kompilatora (poziom 1) ostrzeżenie C4584 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ba427de26d07851c5bf2a2dd3f599c4cbe7afc5c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4584"></a>Kompilatora (poziom 1) ostrzeżenie C4584
"class1": klasy podstawowej "class2" jest już klasą podstawową "class3"  
  
 Klasy, który zdefiniowano dziedziczy dwie klasy, z których jedna dziedziczy od innych. Na przykład:  
  
```  
// C4584.cpp  
// compile with: /W1 /LD  
class A {  
};  
  
class B : public A {  
};  
  
class C : public A, public B { // C4584  
};  
```  
  
 W takim przypadku ostrzeżenie czy wygenerowane klasy C ponieważ dziedziczy ona zarówno z klasy A i B, który również dziedziczy z klasy A. — klasa To ostrzeżenie służy jako przypomnienia muszą pełnej kwalifikacji korzystanie z członków z tych klas podstawowych czy zostanie wygenerowany błąd kompilatora, z powodu niejednoznaczności klienckiemu, który element członkowski klasy można odwołać się.