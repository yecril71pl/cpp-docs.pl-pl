---
title: 'Przykład wywołania: Prototyp funkcji i wywołanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fcfda308ed3a5723b32729e7986a7063e9928fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409374"
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