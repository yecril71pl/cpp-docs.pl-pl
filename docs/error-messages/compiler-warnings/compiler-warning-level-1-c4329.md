---
title: "Kompilatora (poziom 1) ostrzeżenie C4329 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4329
dev_langs: C++
helpviewer_keywords: C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d227329cf402bdbaaeaa33d72e12b51e91ed961
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4329"></a>Kompilator C4329 ostrzegawcze (poziom 1)
__declspec(align()) jest ignorowany w wyliczeniu  
  
 Użycie [Dopasuj](../../cpp/align-cpp.md) — słowo kluczowe z [__declspec](../../cpp/declspec.md) modyfikator nie jest dozwolony na `enum`. Poniższy przykład generuje C4329:  
  
```  
// C4329.cpp  
// compile with: /W1 /LD  
enum __declspec(align(256)) TestEnum {   // C4329  
   TESTVAL1,  
   TESTVAL2,  
   TESTVAL3  
};  
__declspec(align(256)) enum TestEnum1;  
```