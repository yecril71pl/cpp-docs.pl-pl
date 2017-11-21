---
title: Klasa CSimpleArrayEqualHelper | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs: C++
helpviewer_keywords: CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0d53e09c64aa19b4e843297b64bad132c64a75a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csimplearrayequalhelper-class"></a>Klasa CSimpleArrayEqualHelper
Ta klasa jest pomocnika dla [CSimpleArray](../../atl/reference/csimplearray-class.md) klasy.  
  
## <a name="syntax"></a>Składnia  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Klasy pochodnej.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Statyczny) Sprawdza dwie `CSimpleArray` obiekt elementy pod kątem równości.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa cech jest dodatek do `CSimpleArray` klasy. Zapewnia metodę porównywania dwa elementy przechowywane w `CSimpleArray` obiektu. Domyślnie elementy są porównywane przy użyciu **operator=()**, ale jeśli tablica zawiera złożone typy danych, które nie mają własnych operator równości, należy zastąpić tę klasę.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
 Sprawdza dwie `CSimpleArray` obiekt elementy pod kątem równości.  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>Parametry  
 *T1*  
 Obiekt typu T.  
  
 *T2*  
 Obiekt typu T.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca wartość PRAWDA, jeśli elementy są takie same, wartość false w przeciwnym razie wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CSimpleArray](../../atl/reference/csimplearray-class.md)   
 [Klasa CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
