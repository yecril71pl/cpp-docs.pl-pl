---
title: "C3247 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3247
dev_langs: C++
helpviewer_keywords: C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c3b694129e28351db1aff1367187ceab052eb52
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3247"></a>C3247 błąd kompilatora
"class1": klasa coclass nie może dziedziczyć po innej klasie coclass "class2"  
  
 Klasy oznaczonej [coclass](../../windows/coclass.md) atrybutu nie może dziedziczyć po innej klasie oznaczonej przez `coclass` atrybutu.  
  
 Poniższy przykład generuje C3247:  
  
```  
// C3247.cpp  
[module(name="MyLib")];  
[coclass]  
class a {  
};  
  
[coclass]  
class b : public a {   // C3247  
};  
int main() {  
}  
```