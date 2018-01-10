---
title: "no_implementation — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_implementation
dev_langs: C++
helpviewer_keywords: no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: "4"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: aa0a8337de519b2b0d43e8d5035e3845e1aefbe4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="noimplementation"></a>no_implementation
**Określonego języka C++**  
  
 Pomija generację nagłówka .tli, który zawiera implementacje funkcji Członkowskich otoki.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_implementation  
```  
  
## <a name="remarks"></a>Uwagi  
 Jeśli ten atrybut jest określony, zostanie wygenerowany nagłówek .tlh — z deklaracjami do udostępnienia elementów biblioteki typów bez `#include` instrukcji, aby uwzględnić plik nagłówka .tli.  
  
 Ten atrybut jest używany w połączeniu z [implementation_only —](../preprocessor/implementation-only.md).  
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)