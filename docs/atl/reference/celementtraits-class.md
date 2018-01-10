---
title: Klasa CElementTraits | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CElementTraits
- atlcoll/ATL::CElementTraits
dev_langs: C++
helpviewer_keywords: CElementTraits class
ms.assetid: 496528e5-7f80-4b45-be0c-6f646feb43c5
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ebe629a08170ce011b22595c8b821b278e16faa7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="celementtraits-class"></a>Klasa CElementTraits
Ta klasa jest używana przez klasy kolekcji do zapewnienia metod i funkcje przenoszenie, kopiowanie porównania i operacji wyznaczania wartości skrótu.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CElementTraits : public CDefaultElementTraits<T>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych ma być przechowywany w kolekcji.  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa udostępnia domyślny statyczne funkcje i metody przenoszenia, kopiowania, porównanie i wyznaczania wartości skrótu elementy przechowywane w obiekcie klasy kolekcji. `CElementTraits`określono jako domyślny dostawca tych operacji za pomocą klasy kolekcji [CAtlArray](../../atl/reference/catlarray-class.md), [CAtlList](../../atl/reference/catllist-class.md), [CRBMap](../../atl/reference/crbmap-class.md), [CRBMultiMap](../../atl/reference/crbmultimap-class.md), i [CRBTree](../../atl/reference/crbtree-class.md).  
  
 Wystarczy domyślnej implementacji dla proste typy danych, ale jeśli klasy kolekcji są używane do przechowywania obiektów bardziej złożonych, funkcje i metody musi zostać zastąpiona przez implementacje dostarczone przez użytkownika.  
  
 Aby uzyskać więcej informacji, zobacz [klasy kolekcji ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcoll.h  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
