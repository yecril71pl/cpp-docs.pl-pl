---
title: "C2904 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C2904
dev_langs: C++
helpviewer_keywords: C2904
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e558f9ce4ffc9847ae7e0a549cc719cece5b6cfc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2904"></a>C2904 błąd kompilatora
'Identyfikator': nazwa już została użyta dla szablonu w bieżącym zakresie  
  
 Sprawdź kod dla takich samych nazwach.  
  
 Poniższy przykład generuje C2904:  
  
```  
// C2904.cpp  
// compile with: /c  
void X();  // X is declared as a function  
template<class T> class X{};  // C2904  
```