---
title: "no_namespace — | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3e6528ce33689dc05fa037bdd6bc110e5e6a0de9
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="nonamespace"></a>no_namespace
**Określonego języka C++**  
  
 Określa, że nazwa przestrzeni nazw nie jest generowana przez kompilator.  
  
## <a name="syntax"></a>Składnia  
  
```  
no_namespace  
```  
  
## <a name="remarks"></a>Uwagi  
 Biblioteka typów zawartości w `#import` pliku nagłówka zwykle są zdefiniowane w przestrzeni nazw. Nazwa przestrzeni nazw jest określony w **biblioteki** instrukcji oryginalnego pliku IDL. Jeśli `no_namespace` jest określony atrybut, a następnie tej przestrzeni nazw nie jest generowana przez kompilator.  
  
 Jeśli chcesz użyć nazwy inną przestrzeń nazw, należy użyć [rename_namespace —](../preprocessor/rename-namespace.md) zamiast tego atrybutu.  
  
 KOŃCOWY określonego języka C++  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)