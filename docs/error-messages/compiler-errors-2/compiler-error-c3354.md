---
title: "C3354 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3354
dev_langs:
- C++
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd5552afb4981a3ff5303f0f992dbea78cb3a36e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3354"></a>C3354 błąd kompilatora
"Funkcja": funkcja używana do utworzenia delegata nie może mieć zwracanego typu "type"  
  
 Następujące typy są nieprawidłowe jako zwracanych typów `delegate`:  
  
-   Wskaźnik do funkcji  
  
-   Wskaźnik do elementu członkowskiego  
  
-   Wskaźnik do funkcji członkowskiej  
  
-   Odwołanie do funkcji  
  
-   Odwołanie do funkcji członkowskiej  
  
 Poniższy przykład generuje C3354:  
  
```  
// C3354_2.cpp  
// compile with: /clr /c  
using namespace System;  
typedef void ( *VoidPfn )();  
  
delegate VoidPfn func(); // C3354  
// try the following line instead  
// delegate  void func();  
```  
