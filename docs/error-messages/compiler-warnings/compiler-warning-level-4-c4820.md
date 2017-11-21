---
title: "Kompilatora (poziom 4) ostrzeżenie C4820 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4820
dev_langs: C++
helpviewer_keywords: C4820
ms.assetid: 17aa29f4-c287-49b8-bc43-8ed82ffed5ea
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5af422ff96778435c56ff3497d50fb7e923b2297
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4820"></a>Kompilator C4820 ostrzegawcze (poziom 4)
'bajty' dopełnienie bajtami dodane po konstrukcji 'member_name'  
  
 Typ i kolejność elementów spowodował kompilator, aby dodać dopełnienie koniec struktury. Zobacz [Dopasuj](../../cpp/align-cpp.md) uzyskać więcej informacji o dopełnienie struktury.  
  
 To ostrzeżenie jest domyślnie wyłączone. Zobacz [kompilatora ostrzeżeń czy są wyłączone domyślnie](../../preprocessor/compiler-warnings-that-are-off-by-default.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C4820:  
  
```  
// C4820.cpp  
// compile with: /W4 /c  
#pragma warning(default : 4820)   
  
// Delete the following 4 lines to resolve.  
__declspec(align(2)) struct MyStruct {  
   char a;  
   int i;   // C4820  
};  
  
// OK  
#pragma pack(1)  
__declspec(align(1)) struct MyStruct2 {  
   char a;  
   int i;  
};  
```