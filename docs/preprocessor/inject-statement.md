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
ms.openlocfilehash: eb4142b742ae6c2a758c2a2fb5e09c604959433f
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465874"
---
# <a name="injectstatement"></a>inject_statement
**Określonego język C++**  
  
Wstawia jej argument jako tekst źródłowy do nagłówka biblioteki typów.  
  
## <a name="syntax"></a>Składnia  
  
```  
inject_statement("source_text")  
```  
  
### <a name="parameters"></a>Parametry  
*source_text*  
Tekst źródłowy, który ma zostać wstawiony do pliku nagłówka biblioteki typów.  
  
## <a name="remarks"></a>Uwagi  
 
Tekst zostanie umieszczony na początku deklaracji przestrzeni nazw, który otacza zawartość biblioteki typów w pliku nagłówkowym.  
  
**KONIEC określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)