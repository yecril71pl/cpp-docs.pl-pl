---
title: "C2507 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2507
dev_langs: C++
helpviewer_keywords: C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f520dee6ad9630dc338010311119ae9f41bbf86b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2507"></a>C2507 błąd kompilatora
"identyfikator": zbyt wiele modyfikatorów virtual dla klasy podstawowej  
  
 Klasy lub struktury jest zadeklarowany jako `virtual` więcej niż raz. Tylko jeden `virtual` modyfikator mogą być wyświetlane dla każdej klasy na liście klas podstawowych.  
  
 Poniższy przykład generuje C2507:  
  
```  
// C2507.cpp  
// compile with: /c  
class A {};  
class B : virtual virtual public A {};   // C2507  
class C : virtual public A {};   // OK  
```