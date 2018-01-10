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
ms.workload: cplusplus
ms.openlocfilehash: c0d6ca616e3685db36d6d24b339a860eab4c6150
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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