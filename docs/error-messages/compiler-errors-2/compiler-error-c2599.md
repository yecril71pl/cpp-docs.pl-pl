---
title: C2599 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2599
dev_langs:
- C++
helpviewer_keywords:
- C2599
ms.assetid: 88515f36-7589-47e2-862e-0de8b18d6668
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce7741e878b8743346bf9a088d973d65c4d7c290
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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