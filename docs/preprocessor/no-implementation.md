---
title: "no_implementation — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- no_implementation
dev_langs:
- C++
helpviewer_keywords:
- no_implementation attribute
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 46d8aec1b04bca446dfacdabec272630cb20f0a6
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
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
  
 KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)