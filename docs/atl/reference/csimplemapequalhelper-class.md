---
title: Klasa CSimpleMapEqualHelper | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs: C++
helpviewer_keywords: CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ecc32dc8e6e9b249b0b8b334ec3d08bf26cbd1ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="csimplemapequalhelper-class"></a>Klasa CSimpleMapEqualHelper
Ta klasa jest pomocnika dla [CSimpleMap](../../atl/reference/csimplemap-class.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```  
  
#### <a name="parameters"></a>Parametry  
 `TKey`  
 Element klucza.  
  
 `TVal`  
 Wartość elementu.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Statyczny) Testy dwa klucze pod kątem równości.|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Statyczny) Sprawdza dwie wartości pod kątem równości.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa cech jest dodatek do `CSimpleMap` klasy. Zapewnia metody do porównywania dwóch `CSimpleMap` obiekt elementów (w szczególności składników kluczy i wartości) pod kątem równości. Domyślnie klucze i wartości są porównywane za pomocą `operator==()`, ale jeśli mapy zawiera złożone typy danych, które nie mają własnych operator równości, tej klasy może zostać zastąpiona w celu zapewnienie bardzo wymaganej funkcjonalności.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey  
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
  
##  <a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue  
 Sprawdza dwie wartości pod kątem równości.  
  
```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```  
  
### <a name="parameters"></a>Parametry  
 *V1*  
 Pierwsza wartość.  
  
 *w wersji 2*  
 Druga wartość.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli wartości są równe, wartość false w przeciwnym razie wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
