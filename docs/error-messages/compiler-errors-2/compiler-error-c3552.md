---
title: C3552 błąd kompilatora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5f1453a6175019ad7c90471330d11c77da26134
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3552"></a>C3552 błąd kompilatora
Typ "typename": późne określony typ zwracany nie może zawierać "auto"  
  
 Jeśli używasz `auto` słowa kluczowego jako symbol zastępczy dla zwracanego typu funkcji, należy podać późne określony typ zwracany. Jednak nie można użyć innej `auto` — słowo kluczowe, aby określić późne określonym przez typ zwracany. Na przykład poniższy fragment kodu zwraca błąd C3552.  
  
 `auto myFunction->auto; // C3552`