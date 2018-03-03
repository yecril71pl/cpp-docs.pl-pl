---
title: "_fmode — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- fmode
- _fmode
dev_langs:
- C++
helpviewer_keywords:
- file translation [C++], default mode
- fmode function
- _fmode function
ms.assetid: ac6df9eb-e5cc-4c54-aff3-373c21983118
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d4fdaeb0e67832f4f9e0c657e48fe74a88b86292
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="fmode"></a>_fmode
`_fmode` Zmiennej ustawia domyślny tryb tłumaczenia pliku translacji tekst lub binarny. Tę zmienną globalną jest przestarzała bezpieczniejsze funkcjonalne wersje [_get_fmode —](../c-runtime-library/reference/get-fmode.md) i [_set_fmode —](../c-runtime-library/reference/set-fmode.md), którego należy użyć zamiast zmiennej globalnej. Jest zadeklarowana w następujący sposób w Stdlib.h.  
  
## <a name="syntax"></a>Składnia  
  
```  
extern int _fmode;  
```  
  
## <a name="remarks"></a>Uwagi  
 Domyślne ustawienie `_fmode` jest `_O_TEXT` do tłumaczenia tekstowej. `_O_BINARY`jest to ustawienie dla trybu binarnego.  
  
 Można zmienić wartości `_fmode` na trzy sposoby:  
  
-   Połącz z Binmode.obj. Spowoduje to zmianę ustawienia początkowej `_fmode` do `_O_BINARY`, powodując wszystkich plików z wyjątkiem `stdin`, `stdout`, i `stderr` ma zostać otwarty w trybie binarnym.  
  
-   Wywoływania `_get_fmode` lub `_set_fmode` można pobrać lub ustawić `_fmode` zmiennej globalnej odpowiednio.  
  
-   Zmień wartość `_fmode` ustawiając go bezpośrednio w programie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne globalne](../c-runtime-library/global-variables.md)   
 [_get_fmode —](../c-runtime-library/reference/get-fmode.md)   
 [_set_fmode](../c-runtime-library/reference/set-fmode.md)