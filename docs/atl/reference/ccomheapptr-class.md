---
title: Klasa CComHeapPtr | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs: C++
helpviewer_keywords: CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d851e2c6fb4892bd65cf26ea747a6b99a8006cee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomheapptr-class"></a>Klasa CComHeapPtr
Klasa wskaźnika inteligentnego wskaźniki stosu zarządzania.  
  
## <a name="syntax"></a>Składnia  
  
```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ obiektu do zapisania na stosie.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|Konstruktor.|  
  
## <a name="remarks"></a>Uwagi  
 `CComHeapPtr`pochodną `CHeapPtr`, ale używa [CComAllocator](../../atl/reference/ccomallocator-class.md) można przydzielić pamięci przy użyciu procedury COM. Zobacz [CHeapPtr](../../atl/reference/cheapptr-class.md) i [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) dla dostępnych metod.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr  
 Konstruktor.  
  
```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pData`  
 Istniejące `CComHeapPtr` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wskaźnik stosu można opcjonalnie utworzyć przy użyciu istniejącego `CComHeapPtr` obiektu. Jeśli tak, nowe `CComHeapPtr` obiektu przyjmuje na siebie odpowiedzialność zarządzania nowy wskaźnik i zasobów.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Klasa CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)   
 [Klasa CComAllocator](../../atl/reference/ccomallocator-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
