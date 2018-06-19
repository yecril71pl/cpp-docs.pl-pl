---
title: C3896 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3896
dev_langs:
- C++
helpviewer_keywords:
- C3896
ms.assetid: eb8be0f6-5b4e-4d71-8285-8a2a94f8ba29
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bcc60c09d6fd99e56f0261409099e56713604a76
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269741"
---
# <a name="compiler-error-c3896"></a>C3896 błąd kompilatora
"członek": niewłaściwy inicjator: ten literał elementu członkowskiego danych może zostać zainicjowana tylko z "nullptr"  
  
 A [literału](../../windows/literal-cpp-component-extensions.md) niepoprawnie zainicjować elementu członkowskiego danych.  Zobacz [nullptr](../../windows/nullptr-cpp-component-extensions.md) Aby uzyskać więcej informacji.  
  
 Poniższy przykład generuje C3896:  
  
```  
// C3896.cpp  
// compile with: /clr /c  
ref class R{};  
  
value class V {  
   literal R ^ r = "test";   // C3896  
   literal R ^ r2 = nullptr;   // OK  
};  
```