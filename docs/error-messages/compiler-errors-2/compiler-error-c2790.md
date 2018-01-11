---
title: "C2790 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2790
dev_langs: C++
helpviewer_keywords: C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b10da64605743612a4d5522b5c19d1f2029ced8c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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