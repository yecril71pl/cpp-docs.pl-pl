---
title: "Kompilatora (poziom 1) ostrzeżenie C4508 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4508
dev_langs:
- C++
helpviewer_keywords:
- C4508
ms.assetid: c05f113b-b789-4df0-a4ef-78bce4767021
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 52139327831be17d6800f30b00f667da7d3b0376
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4508"></a>Kompilator C4508 ostrzegawcze (poziom 1)
"Funkcja": funkcja powinna zwrócić wartość; Założono typ zwracany "void"  
  
 Funkcja nie ma zwracanego typu określony. W takim przypadku C4430 również powinny wyzwalać i kompilator implementuje poprawka zgłoszone przez C4430 (wartość domyślna to int).  
  
 Aby usunąć to ostrzeżenie, jawnie deklarować zwracany typ funkcji.  
  
 Poniższy przykład generuje C4508:  
  
```  
// C4508.cpp  
// compile with: /W1 /c  
#pragma warning (disable : 4430)  
func() {}   // C4508  
void func2() {}   // OK  
```