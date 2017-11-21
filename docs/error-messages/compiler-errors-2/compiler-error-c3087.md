---
title: "C3087 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3087
dev_langs: C++
helpviewer_keywords: C3087
ms.assetid: 4f5bdd52-a853-4f02-b160-6868e9190b9d
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d786cb3f8c04e5d8ff32aebe30915d4aca3cfb2f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3087"></a>C3087 błąd kompilatora
"named_argument": wywołanie "attribute" już inicjalizuje ten element członkowski  
  
 Nazwany argument została określona w tym samym bloku atrybutu jako argument bez nazwy dla tej samej wartości. Należy określić tylko argument o nazwie lub bez nazwy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3087.  
  
```  
// C3087.cpp  
// compile with: /c  
[idl_quote("quote1", text="quote2")];   // C3087  
[idl_quote(text="quote3")];   // OK  
[idl_quote("quote4")];   // OK  
```