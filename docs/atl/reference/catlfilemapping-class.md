---
title: Klasa CAtlFileMapping | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2dce8e219c2a64ecc6e9b307533ecc0ea11d2792
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="catlfilemapping-class"></a>Klasa CAtlFileMapping
Ta klasa reprezentuje plików mapowanych na pamięć, Dodawanie operatora rzutowania do metody [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
> [!IMPORTANT]
>  Nie można użyć tej klasy i jej elementów członkowskich w aplikacjach, które są wykonywane w środowisku wykonawczym systemu Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Typ danych użyte dla operatora rzutowania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|Umożliwia niejawnej konwersji wartości `CAtlFileMapping` obiekty do `T`  **\*** .|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dodaje operator rzutowania pojedynczego umożliwiają niejawnej konwersji wartości `CAtlFileMapping` obiekty do `T`  **\*** . Inne elementy członkowskie są dostarczane przez klasę podstawową [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlfile.h  
  
##  <a name="operator_t_star"></a>CAtlFileMapping::operator T *  
 Umożliwia niejawnej konwersji wartości `CAtlFileMapping` obiekty do `T`  **\*** .  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `T`  **\***  wskaźnik do początku plików mapowanych na pamięć.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) i reinterprets zwrócony wskaźnik jako `T`  **\***  gdzie *T* jest typ używany jako szablon Parametr tej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)   
 [Przegląd klas](../../atl/atl-class-overview.md)
