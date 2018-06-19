---
title: Kompilatora (poziom 4) ostrzeżenie C4565 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4565
dev_langs:
- C++
helpviewer_keywords:
- C4565
ms.assetid: a71f1341-a4a1-4060-ad1e-9322531883ed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d3c4249783686c1fabb44395d3c092eca0d9230a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33293367"
---
# <a name="compiler-warning-level-4-c4565"></a>Kompilator C4565 ostrzegawcze (poziom 4)
"Funkcja": zmiana definicji; symbol został wcześniej zadeklarowany z __declspec(modifier)  
  
 Symbol został ponownie zdefiniować lub ponownie zadeklarować i deklaracji, w przeciwieństwie do pierwszej deklaracji, lub definicji lub druga definicja nie miał `__declspec` modyfikator (***modyfikator***). To ostrzeżenie ma charakter informacyjny. Aby usunąć to ostrzeżenie, usuń jedną z definicji.  
  
 Poniższy przykład generuje C4565:  
  
```  
// C4565.cpp  
// compile with: /W4 /LD  
__declspec(noalias) void f();  
void f();   // C4565  
```