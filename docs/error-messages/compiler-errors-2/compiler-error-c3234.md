---
title: "C3234 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3234
dev_langs: C++
helpviewer_keywords: C3234
ms.assetid: ebefc15a-e40d-424b-a3dd-d7e185d0ed7b
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 96291111e8814eb1500ab0dab42c0c6ab90ccda1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3234"></a>C3234 błąd kompilatora
Klasa generyczna nie może pochodzić z parametru typu ogólnego  
  
 Klasa generyczna nie może dziedziczyć z parametru typu ogólnego.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład generuje C3234.  
  
```  
// C3234.cpp  
// compile with: /clr /c  
generic <class T>  
public ref class C : T {};   // C3234  
// try the following line instead  
// public ref class C {};  
```