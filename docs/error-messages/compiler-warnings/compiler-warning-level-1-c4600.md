---
title: Kompilatora (poziom 1) ostrzeżenie C4600 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4600
dev_langs:
- C++
helpviewer_keywords:
- C4600
ms.assetid: f023a2a1-7fc4-463f-a434-dc93fcd3f4e9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7866268cffce31467e5306a969e981f310e91ace
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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