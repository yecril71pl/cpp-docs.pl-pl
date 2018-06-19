---
title: VarArgs | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: aac0c54b-0a2d-4a22-b1de-ee41381a3eb1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7b71cd426bc89570f9d394f3e38dc7a002f6e8
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32380511"
---
# <a name="varargs"></a>Elementy vararg
Jeśli parametry są przekazywane za pośrednictwem VARARG (na przykład wielokropka argumentów), zasadniczo przekazywanie normalne parametru dotyczy tym przechodzeniu piątego i kolejne argumenty. Odpowiada ponownie wywołującej zrzutu argumenty, które mają ich pobrać adresu. Tylko wartości zmiennoprzecinkowych zarówno liczb całkowitych i zmiennoprzecinkowych rejestru będzie zawierać wartości typu float w przypadku, gdy wywoływany oczekuje, że wartość w rejestrach liczby całkowitej.  
  
## <a name="see-also"></a>Zobacz też  
 [Konwencja wywoływania](../build/calling-convention.md)