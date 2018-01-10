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
ms.workload: cplusplus
ms.openlocfilehash: 4e8029abe737aad771edf588e31b4a91d22fa092
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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
 [<type_traits>](../standard-library/type-traits.md)



