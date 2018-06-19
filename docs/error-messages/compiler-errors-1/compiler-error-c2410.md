---
title: C2410 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9c2a2df0941130c4f2416806a05ce0378373eb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226451"
---
# <a name="compiler-error-c2410"></a>C2410 błąd kompilatora
"identyfikator": niejednoznaczna nazwa elementu członkowskiego w "context"  
  
 Identyfikator jest członkiem więcej niż jeden struktury lub związku w tym kontekście.  
  
 Specyfikator struktury lub związku w systemie argument, który spowodował błąd. Specyfikator struktury lub Unii jest identyfikatorem typu `struct` lub `union` ( `typedef` nazwy lub tego samego typu co struktura lub Unia jest odwołanie do zmiennej). Specyfikator musi być lewy operand pierwszy operatora wyboru elementu członkowskiego (.) do użycia argument.