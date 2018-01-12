---
title: "Kompilatora (poziom 1) ostrzeżenie C4600 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4600
dev_langs: C++
helpviewer_keywords: C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b031f423d2230ffea03c33d35c3d959cafc9bf37
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4600"></a>Kompilator C4600 ostrzegawcze (poziom 1)
\#pragma "Nazwa makra": Oczekiwano prawidłowym ciągiem niepustym  
  
 Nie można określić pustego ciągu podczas wypychania lub Powiększ nazwę makra w trybie [pop_macro](../../preprocessor/pop-macro.md) lub [dyrektywy push_macro](../../preprocessor/push-macro.md).  
  
 Poniższy przykład generuje C4600:  
  
```  
// C4600.cpp  
// compile with: /W1  
int main()  
{  
   #pragma push_macro("")   // C4600 passing an empty string  
}  
```