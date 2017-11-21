---
title: "raw_method_prefix — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: raw_method_prefix
dev_langs: C++
helpviewer_keywords: raw_method_prefix attribute
ms.assetid: 71490313-af78-4bb2-b28a-eee67950d30b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3cc417466308480ba6a10c5e0bfe190d172f366f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="rawmethodprefix"></a>raw_method_prefix
**Określonego języka C++**  
  
 Określa różne prefiksu, aby uniknąć konfliktów nazw.  
  
## <a name="syntax"></a>Składnia  
  
```  
raw_method_prefix("Prefix")  
```  
  
#### <a name="parameters"></a>Parametry  
 `Prefix`  
 Prefiks, który ma być używany.  
  
## <a name="remarks"></a>Uwagi  
 Niskiego poziomu właściwości i metody są udostępniane przez funkcje elementu członkowskiego o nazwie z prefiksem domyślne **raw_** w celu uniknięcia konfliktów nazw z wysokiego poziomu funkcji Członkowskich obsługi błędów.  
  
> [!NOTE]
>  Efekty `raw_method_prefix` atrybutu nie zostaną zmienione na obecność [raw_interfaces_only —](#_predir_raw_interfaces_only) atrybutu. `raw_method_prefix` Zawsze mają pierwszeństwo `raw_interfaces_only` określania prefiksu. Jeśli oba atrybuty są używane w tym samym `#import` instrukcji, a następnie prefiksu określonego przez `raw_method_prefix` atrybut jest używany.  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)