---
title: Ocena tokenów | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: baebf5c7b00dc069a1b0f97a9bc5ffb54f856980
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="evaluation-of-tokens"></a>Ocena tokenów
Gdy kompilator interpretowane tokeny, zawiera maksymalną liczbę znaków jak to możliwe w ramach jednego tokenu przed przejściem do następnego tokenu. Ze względu na to zachowanie kompilator nie może zinterpretować tokeny poprawnie, jeśli ich nie są poprawnie rozdzielone biały znak. Należy wziąć pod uwagę następujące wyrażenie:  
  
```  
i+++j  
```  
  
 W tym przykładzie kompilator najpierw sprawia, że najdłuższym możliwe — operator (`++`) z trzech znak plus, następnie przetwarza pozostałych znak plus jako operator dodawania (`+`). W związku z tym wyrażenie jest interpretowana jako `(i++) + (j)`, a nie `(i) + (++j)`. W tym i podobnych przypadków korzystać biały znak i nawiasów Aby uniknąć niejednoznaczności i zapewnienia prawidłowego wyrażenia.  
  
 **Microsoft Specific**  
  
 Kompilator języka C traktuje znaku CTRL + Z jako wskaźnik końca pliku. Ignoruje dowolny tekst po CTRL + Z.  
  
 **KOŃCOWY określonych firmy Microsoft**  
  
## <a name="see-also"></a>Zobacz też  
 [Tokeny języka C](../c-language/c-tokens.md)