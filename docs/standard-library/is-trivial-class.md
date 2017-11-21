---
title: Klasa is_trivial | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: type_traits/std::is_trivial
dev_langs: C++
helpviewer_keywords: is_trivial
ms.assetid: 6beb11d4-2f38-4c7e-9959-ca5d26250df7
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7837237d88833fdfdc3a82df0590a990480847d5
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="istrivial-class"></a>is_trivial — klasa
Sprawdza, czy typ jest typem prosta.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
struct is_trivial;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest prosta typem, w przeciwnym razie posiada wartość false. Prosta typy są typy skalarne, typy klas trivially copyable, tablice tych typów i kwalifikowana cv wersje tych typów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



