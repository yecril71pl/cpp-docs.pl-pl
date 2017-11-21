---
title: "C3384 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3384
dev_langs: C++
helpviewer_keywords: C3384
ms.assetid: c9f92c6a-62a9-4333-b2b1-bc55c7f288b6
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ce70a37639288bce3244f48635ae4b756bb98cad
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3384"></a>C3384 błąd kompilatora
"type_parameter": wartość ograniczenia i ograniczenie ref wzajemnie się wykluczają  
  
 Nie można ograniczyć typu ogólnego zarówno `value class` i `ref class`.  
  
 Zobacz [ograniczenia dotyczące parametrów typu ogólnego (C + +/ CLI)](../../windows/constraints-on-generic-type-parameters-cpp-cli.md) Aby uzyskać więcej informacji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3384.  
  
```  
// C3384.cpp  
// compile with: /c /clr  
generic <typename T>  
where T : ref class  
where T : value class   // C3384  
ref class List {};  
```