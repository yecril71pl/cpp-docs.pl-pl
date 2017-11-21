---
title: "C2719 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2719
dev_langs: C++
helpviewer_keywords: C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f7e6707dfd5666cb8852e3bbf59cf7a81dd24766
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2719"></a>C2719 błąd kompilatora
"parametr": formalny parametr z __declspec(align('#')) nie zostanie wyrównany  
  
 [Dopasuj](../../cpp/align-cpp.md) `__declspec` modyfikator nie jest dozwolony w parametrów funkcji. Wyrównanie parametru funkcji jest kontrolowana przez Konwencję wywołania używane. Aby uzyskać więcej informacji, zobacz [konwencji wywoływania](../../cpp/calling-conventions.md).  
  
 Poniższy przykład generuje C2719 i pokazuje, jak rozwiązywanie problemu:  
  
```  
// C2719.cpp  
void func(int __declspec(align(32)) i);   // C2719  
// try the following line instead  
// void func(int i);  
```