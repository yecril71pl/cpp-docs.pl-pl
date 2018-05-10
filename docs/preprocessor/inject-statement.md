---
title: inject_statement — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- inject_statement
dev_langs:
- C++
helpviewer_keywords:
- inject_statement attribute
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 115f5b3d7012ae3e9073d81e0c1005dcb513e045
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
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
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)