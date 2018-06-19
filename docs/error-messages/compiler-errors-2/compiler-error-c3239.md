---
title: C3239 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3239
dev_langs:
- C++
helpviewer_keywords:
- C3239
ms.assetid: 22a518b7-020f-4f3c-9963-a094667fd1ac
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e0a96d2bf743d0ae2eae75bc4f90b7451f771af6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33247696"
---
# <a name="compiler-error-c3239"></a>C3239 błąd kompilatora
"type": wskaźnik do wskaźnika wnętrza/pin jest niedozwolony przez środowisko uruchomieniowe języka wspólnego  
  
 Kompilator napotkano nieprawidłowy typ danych.  
  
 Poniższy przykład generuje C3229:  
  
```  
// C3239.cpp  
// compile with: /clr  
int main() {  
   interior_ptr<int>* pip0;   // C3239  
  
   // OK  
   int * pip1;  
   interior_ptr<int> pip2;  
   int ** pip;  
}  
```