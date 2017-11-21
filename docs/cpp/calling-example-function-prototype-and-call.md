---
title: "Przykład wywołania: Prototyp funkcji i wywołanie | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 6076869ac21f5d934e06e6338215da7ed3e7f6dc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="calling-example-function-prototype-and-call"></a>Przykład wywołania: prototyp funkcji i wywołanie
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 W poniższym przykładzie przedstawiono wyniki wywołania funkcji przy użyciu różnych konwencji wywoływania.  
  
 Ten przykład jest oparty na następującą szkieletową funkcji. Zastąp `calltype` z odpowiednią konwencji wywoływania.  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 Aby uzyskać więcej informacji, zobacz [wyniki wywoływania przykład](../cpp/results-of-calling-example.md).  
  
**KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencje wywoływania](../cpp/calling-conventions.md)