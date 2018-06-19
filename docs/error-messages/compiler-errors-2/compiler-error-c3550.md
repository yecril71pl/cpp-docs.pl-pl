---
title: C3550 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3550
dev_langs:
- C++
helpviewer_keywords:
- C3550
ms.assetid: 9f2d5ffc-e429-41a1-89e3-7acc4fd47e14
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91003af2069ba32083caefa8f5a79cbe0e7cd9c9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252897"
---
# <a name="compiler-error-c3550"></a>C3550 błąd kompilatora
w tym kontekście dozwolone jest tylko zwykły element "decltype(auto)"  
  
 Jeśli `decltype(auto)` jest używany jako symbol zastępczy dla zwracanego typu funkcji musi być używany przez samego siebie. Nie można użyć jako część deklaracji wskaźnika (`decltype(auto*)`), deklaracja odwołania (`decltype(auto&)`), lub inne takie kwalifikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [auto](../../cpp/auto-cpp.md)