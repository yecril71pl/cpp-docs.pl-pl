---
title: "C3062 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3062
dev_langs:
- C++
helpviewer_keywords:
- C3062
ms.assetid: 78632e6d-255f-42c3-b124-31a9194ff86d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4fa921df80f0740387217ec9b295cfa90e089d54
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3062"></a>C3062 błąd kompilatora
Instrukcja "enum": moduł wyliczający wymaga wartości, ponieważ podstawowy typ to 'type'  
  
 Można określić typu podstawowego dla wyliczenia. Jednak niektóre typy wymagają można przypisać wartości do każdego modułu wyliczającego.  
  
 Aby uzyskać więcej informacji na wyliczenia, zobacz [Wylicz klasy](../../windows/enum-class-cpp-component-extensions.md).  
  
 Poniższy przykład generuje C3062:  
  
```  
// C3062.cpp  
// compile with: /clr  
  
enum class MyEnum : bool { a };   // C3062  
enum class MyEnum2 : bool { a = true};   // OK  
```