---
title: no_registry | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_registry
dev_langs:
- C++
helpviewer_keywords:
- no_registry attribute
ms.assetid: d30de4e2-551c-428c-98fd-951330d578d3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 105c2b0ee4d2648a1cc43d0baca9f30146184e78
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/10/2018
ms.locfileid: "42465402"
---
# <a name="noregistry"></a>no_registry
**no_registry** informuje kompilator, który nie należy przeszukiwać rejestru dla biblioteki typów, zaimportowane wraz z `#import`.  
  
## <a name="syntax"></a>Składnia  
  
```  
#import filename no_registry  
```  
  
### <a name="parameters"></a>Parametry  
*Nazwa pliku*  
Biblioteki typów.  
  
## <a name="remarks"></a>Uwagi  
 
Przywoływanej biblioteki typów nie zostanie znaleziony w katalogach include, kompilacja zakończy się niepowodzeniem, nawet jeśli biblioteki typów znajduje się w rejestrze.  **no_registry** propaguje do innych bibliotek typów niejawnie zaimportowane wraz z `auto_search`.  
  
Kompilator wyszuka nigdy nie rejestru dla biblioteki typów, które są określone przez nazwę pliku i przekazywana bezpośrednio do `#import`.  
  
Podczas `auto_search` jest określony, dodatkowy `#import`s zostanie wygenerowany za pomocą **no_registry** ustawienia wstępnego `#import` (jeśli początkowej `#import` dyrektywy **no_registry** , `auto_search`-generowane `#import` jest również **no_registry**.)  
  
**no_registry** jest przydatne, jeśli chcesz zaimportować krzyżowe bibliotek typu odwołania, bez ryzyka stałego skanowania kompilatora znajdowanie starszej wersji pliku w rejestrze. **no_registry** jest również przydatne, jeśli biblioteka typów nie jest zarejestrowany.  
  
## <a name="see-also"></a>Zobacz też  
 
[atrybuty #import](../preprocessor/hash-import-attributes-cpp.md)   
[#import — dyrektywa](../preprocessor/hash-import-directive-cpp.md)