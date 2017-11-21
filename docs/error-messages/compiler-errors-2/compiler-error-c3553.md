---
title: "C3553 błąd kompilatora | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3553
dev_langs: C++
helpviewer_keywords: C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 9ad1e4d6f59d0cad99935eda97b8a7d7ac358666
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3553"></a>C3553 błąd kompilatora
decltype oczekuje wyrażenia nie jest typem  
  
 `decltype()` — Słowo kluczowe wymaga wyrażenia jako argument, a nie nazwy typu. Na przykład ostatnią instrukcją w poniższy fragment kodu zwraca błąd C3553.  
  
 `int x = 0;`  
  
 `decltype(x+1);`  
  
 `decltype(int); // C3553`