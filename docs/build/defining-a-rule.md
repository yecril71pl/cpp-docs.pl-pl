---
title: Definiowanie zasady | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- NMAKE program, inference rules
- defining inference rules
ms.assetid: 071cd092-3f2e-4065-b0fb-36a9d393cfa8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7e720613dd4d918b2b697a6ff21a8950f0c5adc2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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