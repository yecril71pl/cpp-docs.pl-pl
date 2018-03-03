---
title: "Wartości | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 24003f89-220f-4f93-be7a-b650c26157d7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ea979083fb00d57e455b97c2f6b94f7ea7c6b596
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="values"></a>Wartości
**ANSI 3.1.2.5** oświadczenia i zestawy wartości różnych typów liczb zmiennoprzecinkowych  
  
 **Float** typ zawiera 32 bitów: 1 znaku, 8 dla wykładnik i 23 w przypadku mantysa. Zakres wynosi od +/-3.4E38 z co najmniej 7 cyfr precyzji.  
  
 **Podwójne** typ zawiera 64 bity: 1 znaku, 11 dla wykładnik i 52 dla mantysa. Zakres wynosi od +/-1.7E308 z co najmniej 15 cyfr.  
  
 **Podwójnej długości** typ zawiera 80 bitów: 1 znaku, 15 dla wykładnik i 64 dla mantysa. Zakres wynosi od +/-1.2E4932 z co najmniej 19 cyfr precyzji. Należy pamiętać, że przez kompilator Microsoft C reprezentacja typu **podwójnej długości** jest taki sam jak typ **podwójne**.  
  
## <a name="see-also"></a>Zobacz też  
 [Obliczenia matematyczne na liczbach zmiennoprzecinkowych](../c-language/floating-point-math.md)