---
title: "C3209 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3209
dev_langs: C++
helpviewer_keywords: C3209
ms.assetid: 1de44e39-69d1-4894-8f89-ff92136e8e5d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 99cffcf55850035bc114c5b158ad3fde304234f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3209"></a>C3209 błąd kompilatora
"class": klasa generyczna musi być zarządzane lub WinRTclass  
  
 Klasa generyczna musi być zarządzanej klasy lub klasy środowiska wykonawczego systemu Windows.  
  
 Poniższy przykład generuje C3209 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C3209.cpp  
// compile with: /clr  
generic <class T>  
class C {};   // C3209  
  
// OK - ref class can be generic  
generic <class T>  
ref class D {};  
```