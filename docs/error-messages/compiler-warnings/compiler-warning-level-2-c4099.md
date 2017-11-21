---
title: Kompilator ostrzegawcze (poziom 2) C4099 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4099
dev_langs: C++
helpviewer_keywords: C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: af0f7aacb5e4600b48120576135b2052af2a5315
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-2-c4099"></a>Ostrzeżenie kompilatora (poziom 2) C4099
'Identyfikator': Nazwa typu najpierw widoczna przy użyciu "objecttype1" teraz widoczna przy użyciu "objecttype2"  
  
 Obiekt zadeklarowany w strukturze jest zdefiniowany jako klasa lub obiekt, który został zadeklarowany jako klasa jest zdefiniowana jako struktura. Kompilator używa podane w definicji typu.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C4099.  
  
```  
// C4099.cpp  
// compile with: /W2 /c  
struct A;  
class A {};   // C4099, use different identifer or use same object type  
```