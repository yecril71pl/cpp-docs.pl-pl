---
title: Kompilatora (poziom 4) ostrzeżenie C4559 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4559
dev_langs:
- C++
helpviewer_keywords:
- C4559
ms.assetid: ed542f60-454d-45cb-85da-987ede61b1ab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c853fa55482604d97c29653fadb06b0afdd44977
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33295353"
---
# <a name="compiler-warning-level-4-c4559"></a>Kompilator C4559 ostrzegawcze (poziom 4)
"Funkcja": zmiana definicji; __declspec(modifier) zyski — funkcja  
  
 Funkcja została ponownie zdefiniować lub ponownie zadeklarować i drugi deklaracji lub definicji dodane __**declspec** modyfikator (***modyfikator***). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.  
  
 Poniższy przykład generuje C4559:  
  
```  
// C4559.cpp  
// compile with: /W4 /LD  
void f();  
__declspec(noalias) void f();   // C4559  
```