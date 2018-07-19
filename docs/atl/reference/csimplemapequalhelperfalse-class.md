---
title: Klasa CSimpleMapEqualHelperFalse | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70cea341e7f78032cdaca260e3c891f4c762e0b6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882627"
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
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Statyczny) Testuje dwa klucze pod kątem równości.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Statyczny) Zwraca wartość false.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa cech jest uzupełnieniem `CSimpleMap` klasy. Zapewnia metodę porównywania dwóch elementów zawartych w słowniku `CSimpleMap` obiektu, w szczególności dwa elementy wartości lub dwa kluczowe elementy.  
  
 Porównanie wartości zawsze zwróci wartość false, a ponadto wywoła `ATLASSERT` z nieprawidłowym argumentem wartość false, jeśli nigdy nie jest wywoływany. W sytuacjach, w którym testu równości nie jest wystarczająco zdefiniowana ta klasa umożliwia mapę zawierający pary klucz/wartość, aby działać prawidłowo w przypadku większości metod, ale nie działać w sposób dobrze zdefiniowanych dla metod, które są zależne od porównań, takich jak [CSimpleMap:: FindVal](../../atl/reference/csimplemap-class.md#findval).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey  
 Testuje dwa klucze pod kątem równości.  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>Parametry  
 *K1*  
 Pierwszy klucz.  
  
 *K2*  
 Drugi klucz.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli klucze są takie same, wartość false w przeciwnym razie.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda wywołuje [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).  
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue  
 Zwraca wartość false.  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość false.  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zawsze zwraca wartość false i wywoła `ATLASSERT` z nieprawidłowym argumentem wartość false, jeśli nigdy nie jest wywoływany. Celem `CSimpleMapEqualHelperFalse::IsEqualValue` jest wymuszenie metod, które się nie powieść w dobrze zdefiniowany sposób w przypadku równości testy nie zostały odpowiednio zdefiniowane za pomocą porównania.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
