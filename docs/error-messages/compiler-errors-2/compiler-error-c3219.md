---
title: "C3219 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3219
dev_langs: C++
helpviewer_keywords: C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ea908b51246cf77d8813ce2d80499174564f7787
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3219"></a>C3219 błąd kompilatora
"param": parametr ogólny nie może zostać ograniczony przez wiele elementów niebędących interfejsami: "class"  
  
 Nie jest prawidłową ograniczenia parametru ogólnego przez co najmniej dwie klasy zarządzane.  
  
 Poniższy przykład generuje C3219:  
  
```  
// C3219.cpp  
// compile with: /clr  
ref class A {};  
ref class B {};  
  
generic <class T>  
where T : A, B  
ref class E {};   // C3219  
```  
  
 W poniższym przykładzie pokazano możliwe rozwiązania:  
  
```  
// C3219b.cpp  
// compile with: /clr /c  
ref class A {};  
  
interface struct C {};  
  
generic <class T>  
where T : A  
ref class E {};  
```