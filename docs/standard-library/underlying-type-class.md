---
title: Klasa underlying_type | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::underlying_type
dev_langs: C++
helpviewer_keywords: underlying_type
ms.assetid: 691ddce3-2677-4480-bd35-d933fab85d3e
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: b539f62e1e9c6b9bf11b176bd50f7dca63508ddd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="underlyingtype-class"></a>underlying_type — klasa
Tworzy integralną typ podstawowy dla typu wyliczenia.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
struct underlying_type;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do modyfikacji.  
  
## <a name="remarks"></a>Uwagi  
 `type` Typedef elementu członkowskiego szablonu klasy nazwy źródłowego typu całkowitego `T`, gdy `T` jest typ wyliczeniowy, w przeciwnym razie nie jest elementem typedef nie elementu członkowskiego `type`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



