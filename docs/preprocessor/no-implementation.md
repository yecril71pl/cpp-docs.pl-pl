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
ms.openlocfilehash: 5d4c378d1d64eefe5ae641d259aa502b7e4bcf32
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
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