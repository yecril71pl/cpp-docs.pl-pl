---
title: VarArgs | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f3d22a5c3f20480d1e904ec8e087114385ba7ee9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="varargs"></a>Elementy vararg
Jeśli parametry są przekazywane za pośrednictwem VARARG (na przykład wielokropka argumentów), zasadniczo przekazywanie normalne parametru dotyczy tym przechodzeniu piątego i kolejne argumenty. Odpowiada ponownie wywołującej zrzutu argumenty, które mają ich pobrać adresu. Tylko wartości zmiennoprzecinkowych zarówno liczb całkowitych i zmiennoprzecinkowych rejestru będzie zawierać wartości typu float w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)