---
title: Definiowanie zasady | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7a8ff7c58033ac5f7e42764d185c45c206bf406f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32367124"
---
# <a name="defining-a-rule"></a>Definiowanie zasady
*Fromext* reprezentuje rozszerzenie nazwy pliku zależnego i *toext* reprezentuje rozszerzenie nazwy pliku docelowego.  
  
```  
.fromext.toext:  
   commands  
```  
  
## <a name="remarks"></a>Uwagi  
 Rozszerzenia nie jest uwzględniana wielkość liter. Makra może być wywoływany do reprezentowania *fromext* i *toext*; makra są rozwinięte podczas przetwarzania wstępnego. Kropki (.) poprzedniego *fromext* musi znajdować się na początku wiersza. Dwukropka (:) jest poprzedzony zero lub więcej spacji ani karty. Może wystąpić tylko z spacji lub kart, średnika (;), aby określić polecenie, znaku numeru (#) do określenia komentarz lub znak nowego wiersza. Nie inne spacje są dozwolone. Polecenia są określane jak bloki opisów.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Ścieżki wyszukiwania w regułach](../build/search-paths-in-rules.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Zasady wnioskowania](../build/inference-rules.md)