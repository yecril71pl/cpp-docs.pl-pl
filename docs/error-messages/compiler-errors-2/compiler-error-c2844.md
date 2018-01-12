---
title: "C2844 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2844
dev_langs: C++
helpviewer_keywords: C2844
ms.assetid: dcaf4cd2-21b0-4280-ae42-0a706c524d83
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3353a6dbacaca2779bb4feffe55958baf0c944e8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2844"></a>C2844 błąd kompilatora
"członek": nie może być elementem członkowskim interfejsu "interface"  
  
 [Interfejsu klasy](../../windows/interface-class-cpp-component-extensions.md) nie może zawierać elementu członkowskiego danych, chyba że jest także właściwością.  
  
 Innym niż właściwość lub członek funkcji jest niedozwolone w interfejsie. Ponadto konstruktorów, destruktory i operatory są niedozwolone.  
  
 Poniższy przykład generuje C2844:  
  
```  
// C2844a.cpp  
// compile with: /clr /c  
public interface class IFace {  
   int i;   // C2844  
   // try the following line instead  
   // property int Size;  
};  
```  
