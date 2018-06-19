---
title: Klasa CSimpleArrayEqualHelperFalse | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7e22d67634f29b60bdc983c892c5fe266df61d08
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358208"
---
# <a name="csimplearrayequalhelperfalse-class"></a>Klasa CSimpleArrayEqualHelperFalse
Ta klasa jest pomocnika dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodnej.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Statyczny) Zwraca wartość false.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa cech jest uzupełnienie `CSimpleArray` klasy. IT zawsze zwraca wartość false, a ponadto wywoła `ATLASSERT` z argumentu o wartości false, jeśli kiedykolwiek jest wywoływany. W sytuacjach, w którym testu równości nie jest wystarczająco zdefiniowany, ta klasa umożliwia tablicę zawierającą elementy, aby działać poprawnie w przypadku większości metod, ale się nie powieść w sposób wyraźnie określone dla metod, które są zależne od porównań, takich jak [CSimpleArray:: Znajdź](../../atl/reference/csimplearray-class.md#find).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpcoll.h  
  
##  <a name="isequal"></a>  CSimpleArrayEqualHelperFalse::IsEqual  
 Zwraca wartość false.  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zawsze zwraca wartość false, a wywoła `ATLASSERT` z nieprawidłowym argumentem wartość false, jeśli odwołuje się do. Celem `CSimpleArrayEqualHelperFalse::IsEqual` jest wymuszenie metod, które się nie powieść w sposób wyraźnie określone podczas testów równości nie zostały odpowiednio zdefiniowane za pomocą porównania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
