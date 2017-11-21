---
title: "is_trivially_copy_constructible — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: type_traits/std::is_trivially_copy_constructible
dev_langs: C++
helpviewer_keywords: is_trivially_copy_constructible
ms.assetid: 4274cef5-afdd-4f2d-bc83-7562e7944ddf
caps.latest.revision: "24"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 465d5a1756a416eac2c01c5191b4f63f986ffcba
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="istriviallycopyconstructible-class"></a>is_trivially_copy_constructible — klasa
Testy, jeśli typ ma konstruktora kopiującego prosta.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>
struct is_trivially_copy_constructible;
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ do zapytania.  
  
## <a name="remarks"></a>Uwagi  
 Wystąpienie typu predykatu posiada wartość true Jeśli typ `T` jest klasa, która ma trivial konstruktora kopiującego, w przeciwnym razie posiada wartość false.  
  
 Konstruktor kopiujący dla klasy `T` jest proste, jeśli jest niejawnie zadeklarowany jako, klasa `T` nie ma funkcje wirtualne ani wirtualnych typów podstawowych, bezpośrednie podstawy klasy `T` mieć konstruktorów trivial kopiowania, klas wszystkich niestatyczna elementy członkowskie danych typu klasy mają trivial kopiowanie konstruktorów i klasy wszystkich członków danych niestatycznych tablicy typu klasy trivial kopiowanie konstruktorów.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<type_traits >  
  
 **Namespace:** Standard  
  
## <a name="see-also"></a>Zobacz też  
 [< type_traits >](../standard-library/type-traits.md)



