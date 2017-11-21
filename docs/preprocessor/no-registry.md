---
title: no_registry | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: no_registry
dev_langs: C++
helpviewer_keywords: no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 347cdd89a8d8c3014a02708c91df3292275f4e3a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="noregistry"></a>no_registry
`no_registry`informuje kompilator, aby nie Szukaj rejestrze zaimportowany z biblioteki typów `#import`.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
#import filename no_registry  
```  
  
#### <a name="parameters"></a>Parametry  
 *Nazwa pliku*  
 Biblioteki typów.  
  
## <a name="remarks"></a>Uwagi  
 Biblioteki typu występującego w odwołaniu nie zostanie znaleziony w katalogach include, kompilacja zakończy się niepowodzeniem nawet w przypadku biblioteki typów w rejestrze.  `no_registry`propaguje na inne niejawnie zaimportowany z biblioteki typu `auto_search`.  
  
 Kompilator nigdy nie będzie przeszukiwać rejestru dla biblioteki typów, które są określone przez nazwę pliku i przekazywane bezpośrednio do `#import`.  
  
 Podczas `auto_search` jest określony, dodatkowy `#import`s zostanie wygenerowane z `no_registry` ustawienia wstępnego `#import` (jeśli początkowej `#import` dyrektywy `no_registry`, `auto_search`-generowane `#import`jest również `no_registry`.)  
  
 `no_registry`jest to przydatne, jeśli chcesz zaimportować krzyżowego typu występującego w odwołaniu biblioteki bez ryzyka kompilatora znajdowanie starszej wersji pliku w rejestrze.  `no_registry`jest również przydatne, jeśli biblioteka typów nie jest zarejestrowana.  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)