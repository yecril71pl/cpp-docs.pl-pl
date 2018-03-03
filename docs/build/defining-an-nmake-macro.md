---
title: Definiowanie makro NMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- macros, NMAKE
- defining NMAKE macros
- NMAKE macros, defining
ms.assetid: 45aae451-9d33-4a3d-8799-2e0cae17070d
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96799bbd10d442c50d66ac4e84169864b9b989ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="defining-an-nmake-macro"></a>Definiowanie makro NMAKE
## <a name="syntax"></a>Składnia  
  
```  
  
macroname=string  
```  
  
## <a name="remarks"></a>Uwagi  
 *Makra* jest kombinacją litery, cyfry i znaki podkreślenia (_), maksymalnie 1024 znaki i jest wielkość liter. *Makra* może zawierać wywołanej makra. Jeśli *makra* składa się wyłącznie z wywołanego makro makro wywoływany nie może być null lub niezdefiniowany.  
  
 `string` Może być dowolną sekwencją zero lub więcej znaków. Pusty ciąg zawiera zero znaków lub tylko spacji ani karty. `string` Może zawierać wywołanie makra.  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcesz dowiedzieć się więcej o?  
 [Znaki specjalne w makrach](../build/special-characters-in-macros.md)  
  
 [Zerowe i niezdefiniowane makra](../build/null-and-undefined-macros.md)  
  
 [Miejsce definiowania makr](../build/where-to-define-macros.md)  
  
 [Pierwszeństwo w definicjach makr](../build/precedence-in-macro-definitions.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Makra i NMAKE](../build/macros-and-nmake.md)