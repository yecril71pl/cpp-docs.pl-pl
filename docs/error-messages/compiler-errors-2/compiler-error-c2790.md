---
title: C2790 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2790
dev_langs:
- C++
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11f1c90fed93666fad7513e2b4186a5baa2aa406
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2790"></a>C2790 błąd kompilatora
"super": to słowo kluczowe może być użyte tylko w treści funkcji członkowskiej klasy  
  
 Ten komunikat o błędzie jest wyświetlany, jeśli użytkownik spróbuje się kiedykolwiek do używa słowa kluczowego [super](../../cpp/super.md) poza kontekstem funkcją członkowską.  
  
 Poniższy przykład generuje C2790:  
  
```  
// C2790.cpp  
void f() {  
   __super::g();   // C2790  
}  
```