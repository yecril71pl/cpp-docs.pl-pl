---
title: "C2833 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2833
dev_langs: C++
helpviewer_keywords: C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d3adf42ddb4df4365a45fd3ef24bccd682ac3c9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2833"></a>C2833 błąd kompilatora
"operator operator" nie jest rozpoznany jako operator lub typ  
  
 Wyraz `operator` musi występować operator, który chcesz zmienić lub typu, który chcesz przekonwertować.  
  
 Aby uzyskać listę operatory, które można zdefiniować typu zarządzanego, zobacz [operatory zdefiniowane przez użytkownika](../../dotnet/user-defined-operators-cpp-cli.md).  
  
 Poniższy przykład generuje C2833:  
  
```  
// C2833.cpp  
// compile with: /c  
class A {};  
  
void operator ::* ();   // C2833  
void operator :: ();   // OK  
```