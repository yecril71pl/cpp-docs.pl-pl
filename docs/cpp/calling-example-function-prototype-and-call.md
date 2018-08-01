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
ms.openlocfilehash: 9f9ee05b55a0945d18e78dc67df5653c06c8a1bc
ms.sourcegitcommit: 2b9e8af9b7138f502ffcba64e2721f7ef52af23b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2018
ms.locfileid: "39404385"
---
# <a name="calling-example-function-prototype-and-call"></a>Przykład wywołania: prototyp funkcji i wywołanie
## <a name="microsoft-specific"></a>Specyficzne dla firmy Microsoft  
 Poniższy przykład pokazuje wyniki wywołania funkcji, za pomocą różnych konwencji wywoływania.  
  
 Ten przykład jest oparty na następujący szkielet funkcji. Zastąp `calltype` przy użyciu odpowiednich konwencji wywoływania.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [wyniki podczas wywoływania przykład](../cpp/results-of-calling-example.md).  
  
**END specyficzny dla Microsoft**  
  
## <a name="see-also"></a>Zobacz także  
 [Konwencje wywoływania](../cpp/calling-conventions.md)