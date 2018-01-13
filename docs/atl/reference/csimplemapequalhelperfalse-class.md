---
title: Klasa CSimpleMapEqualHelperFalse | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs: C++
helpviewer_keywords: CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1418114233b59112fcffb58ef4ae7c437af5ab3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csimplemapequalhelperfalse-class"></a>Klasa CSimpleMapEqualHelperFalse
Ta klasa jest pomocnika dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statyczny) Testy dwa klucze pod kątem równości.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statyczny) Zwraca wartość false.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa cech jest dodatek do `CSimpleMap` klasy. Zapewnia on metodę porównywania dwóch elementów zawartych w `CSimpleMap` obiektu, w szczególności dwa elementy wartość lub dwa elementy klucza.  
  
 Porównanie wartości zawsze zwróci wartość false, a ponadto wywoła `ATLASSERT` z argumentu o wartości false, jeśli kiedykolwiek jest wywoływany. W sytuacjach, w którym testu równości nie jest wystarczająco zdefiniowany, ta klasa umożliwia mapy zawierający pary klucz wartość, aby działać prawidłowo w przypadku większości metod, ale się nie powieść w sposób wyraźnie określone dla metod, które są zależne od porównań, takich jak [CSimpleMap:: FindVal](../../atl/reference/csimplemap-class.md#findval).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey  
 Testy dwa klucze pod kątem równości.  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>Parametry  
 `k1`  
 Pierwszy klucz.  
  
 `k2`  
 Drugi klucz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli klucze są takie same, wartość false w przeciwnym razie wartość.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).  
  
##  <a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue  
 Zwraca wartość false.  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zawsze zwraca wartość false, a wywoła `ATLASSERT` z argumentu o wartości false, jeśli kiedykolwiek jest wywoływany. Celem `CSimpleMapEqualHelperFalse::IsEqualValue` jest wymuszenie metod, które się nie powieść w sposób wyraźnie określone podczas testów równości nie zostały odpowiednio zdefiniowane za pomocą porównania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
