---
title: Kompilatora (poziom 1) ostrzeżenie C4329 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4329
dev_langs:
- C++
helpviewer_keywords:
- C4329
ms.assetid: 4316f51a-2c56-4b3f-831e-65d24b83b65c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f7eca757f361acaa0aeaf90332d33400f5a0ba6d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278008"
---
# <a name="compiler-warning-level-1-c4329"></a>Kompilator C4329 ostrzegawcze (poziom 1)
__declspec(align()) jest ignorowany w wyliczeniu  
  
 Użycie [Dopasuj](../../cpp/align-cpp.md) — słowo kluczowe z [__declspec](../../cpp/declspec.md) modyfikator nie jest dozwolony na `enum`. Poniższy przykład generuje C4329:  
  
```  
// C4329.cpp  
// compile with: /W1 /LD  
enum __declspec(align(256)) TestEnum {   // C4329  
   TESTVAL1,  
   TESTVAL2,  
   TESTVAL3  
};  
__declspec(align(256)) enum TestEnum1;  
```