---
title: no_namespace — | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_namespace
dev_langs:
- C++
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3d4558b0fd6a4014bc9601d5260882af444f87e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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
  
 **KOŃCOWY określonego języka C++**  
  
## <a name="see-also"></a>Zobacz też  
 [atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
 [#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)