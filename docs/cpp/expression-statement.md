---
title: Instrukcja wyrażeń | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- statements [C++], expression
- expression statements
ms.assetid: 547d7f7a-58be-4ffc-a4b3-d64c7ae7538c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60879ca8792e3259a69b7a9a3de6cd83dce0d6d7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="expression-statement"></a>Instrukcja wyrażeń
Instrukcje wyrażeń spowodować wyrażenia do obliczenia. Transfer nie formant lub iteracji odbywa się w wyniku wyrażenia instrukcji.  
  
 Składnia instrukcji wyrażenia jest po prostu  
  
## <a name="syntax"></a>Składnia  
  
```  
[expression ] ;  
```  
  
## <a name="remarks"></a>Uwagi  
 Wszystkie wyrażenia w instrukcji wyrażenia są oceniane i wykonywane są wszystkie efekty uboczne, przed wykonaniem następnej instrukcji. Najbardziej typowe instrukcje wyrażenia są zadania i wywołania funkcji.  Ponieważ wyrażenie jest opcjonalne, tylko średnik jest uznawany za instrukcji puste wyrażenie określone jako [null](../cpp/null-statement.md) instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd instrukcji C++](../cpp/overview-of-cpp-statements.md)