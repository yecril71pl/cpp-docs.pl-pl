---
title: "Kompilatora (poziom 1) ostrzeżenie C4083 | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4083
dev_langs: C++
helpviewer_keywords: C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 66a614d71e27b6a90500bd6e3b24f6894a9d5820
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4083"></a>Kompilator C4083 ostrzegawcze (poziom 1)
Oczekiwano 'token'; Znaleziono identyfikator 'Identyfikator'  
  
 Identyfikator występuje w niewłaściwym miejscu w **#pragma** instrukcji.  
  
## <a name="example"></a>Przykład  
  
```  
// C4083.cpp  
// compile with: /W1 /LD  
#pragma warning disable:4083    // C4083  
#pragma warning(disable:4083)   //correct  
```  
  
 Sprawdź składnię [#pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md) dyrektywy.