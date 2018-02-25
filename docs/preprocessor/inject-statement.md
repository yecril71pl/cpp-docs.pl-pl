---
title: "inject_statement — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7dacc2867b767495c608789b9efbe23bf7aa7110
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="injectstatement"></a>inject_statement
**Określonego języka C++**  
  
 Wstawia jej argument jako tekst źródłowy do nagłówka biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
inject_statement("source_text")  
```  
  
#### <a name="parameters"></a>Parametry  
 `source_text`  
 Tekst źródłowy, który ma zostać wstawiony do plik nagłówka biblioteki typów.  
  
## <a name="remarks"></a>Uwagi  
 Tekst jest umieszczona na początku deklaracji przestrzeni nazw, która opakowuje zawartość biblioteki typów w pliku nagłówka.  
  
 KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)