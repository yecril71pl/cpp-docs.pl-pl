---
title: C3219 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3219
dev_langs:
- C++
helpviewer_keywords:
- C3219
ms.assetid: 9c9757b0-1256-4cdf-9d8c-a3a72f300ce5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 16341412ae5028753b2a542b45da4ea2b549c29e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33248648"
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