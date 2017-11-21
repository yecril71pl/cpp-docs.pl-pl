---
title: "Kompilatora (poziom 1) ostrzeżenie C4628 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4628
dev_langs: C++
helpviewer_keywords: C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 49726b888f18588486b0b58ce771de2e48dfd4e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4628"></a>Kompilator C4628 ostrzegawcze (poziom 1)
dwuznaki nieobsługiwane z -Ze. Sekwencja znaków 'dwuznak' nie jest interpretowana jako alternatywny token dla 'char'  
  
 Digraphs nie są obsługiwane w ramach [/Ze](../../build/reference/za-ze-disable-language-extensions.md). To ostrzeżenie będzie występować z powodu błędu.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4628:  
  
```  
// C4628.cpp  
// compile with: /WX  
#pragma warning(default : 4628)  
int main()  
<%   // C4628 <% digraph for {  
}  
```