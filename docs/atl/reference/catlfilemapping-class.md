---
title: Klasa CAtlFileMapping | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
dev_langs:
- C++
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 973501339d05f75414d076cbd22f5dabeb0bec7c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43208726"
---
# <a name="catlfilemapping-class"></a>Klasa CAtlFileMapping
Ta klasa reprezentuje plik mapowany w pamięci, dodanie operatora rzutowania do metod [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename T = char>  
class CAtlFileMapping : public CAtlFileMappingBase
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Typ danych użyte dla operatora rzutowania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CAtlFileMapping::operator T *](#operator_t_star)|Umożliwia niejawną konwersję `CAtlFileMapping` obiekty do `T*`.|  
  
## <a name="remarks"></a>Uwagi  
 Ta klasa dodaje operatora rzutowania pojedynczej umożliwia niejawną konwersję `CAtlFileMapping` obiekty do `T*`. Inni członkowie są dostarczane przez klasę bazową [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)  
  
 `CAtlFileMapping`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlfile.h  
  
##  <a name="operator_t_star"></a>  CAtlFileMapping::operator T *  
 Umożliwia niejawną konwersję `CAtlFileMapping` obiekty do `T*`.  
  
```  
operator T*() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `T*` wskaźnik do początku plików mapowanych na pamięć.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) i reinterpretuje obiekt zwrócony wskaźnik jako `T*` gdzie *T* jest typ używany jako parametr szablonu tej klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasa CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)   
 [Klasa — Przegląd](../../atl/atl-class-overview.md)
