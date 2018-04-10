---
title: C2599 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2599
dev_langs:
- C++
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca22554fbff05e5067ac01044785ef6b4cf6cffb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2599"></a>C2599 błąd kompilatora
Instrukcja "enum": deklaracja przekazująca dalej typ wyliczenia jest niedozwolone.  
  
 Kompilator nie obsługuje już deklaracja przekazująca dalej wyliczenie zarządzanych.  
  
 Deklaracja przekazująca dalej typ wyliczeniowy nie jest dozwolona w obszarze [/Za](../../build/reference/za-ze-disable-language-extensions.md).  
  
 Poniższy przykład generuje C2599:  
  
```  
// C2599.cpp  
// compile with: /clr /c  
enum class Status;   // C2599  
  
enum class Status2 { stop2, hold2, go2};   
  
ref struct MyStruct {  
   // Delete the following line to resolve.  
   Status m_status;  
  
   Status2 m_status2;   // OK  
};  
  
enum class Status { stop, hold, go };  
```