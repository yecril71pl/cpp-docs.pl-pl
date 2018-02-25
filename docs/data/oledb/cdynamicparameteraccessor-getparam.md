---
title: CDynamicParameterAccessor::GetParam | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDynamicParameterAccessor::GetParam
- ATL.CDynamicParameterAccessor.GetParam
- CDynamicParameterAccessor::GetParam<ctype>
- CDynamicParameterAccessor.GetParam
- GetParam
- ATL::CDynamicParameterAccessor::GetParam<ctype>
- ATL::CDynamicParameterAccessor::GetParam
dev_langs:
- C++
helpviewer_keywords:
- GetParam method
ms.assetid: 893a6bf8-7b55-4f6d-8a10-a43b13be7f56
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 61d1a15cd148120914e22a566da45f579fdd72ae
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicparameteraccessorgetparam"></a>CDynamicParameterAccessor::GetParam
Pobiera dane typu dla określonego parametru z buforu parametru.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
template <class ctype>bool GetParam(DBORDINAL nParam,   
  ctype* pData) const throw();  

template <class ctype> bool GetParam(TCHAR* pParamName,   
   ctype* pData) const throw();  

void* GetParam(DBORDINAL nParam) const throw();  

void* GetParam(TCHAR* pParamName) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 Parametr opartego na szablonie, który jest typem danych.  
  
 `nParam`  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowana dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego kolejności w języku SQL lub procedurę składowaną wywołania. Zobacz [SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md) przykład.  
  
 `pParamName`  
 [in] Nazwa parametru.  
  
 `pData`  
 [out] Wskaźnik do pamięci zawierający dane pobrane z buforu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Dla wersji nontemplated punktów pamięci zawierający dane pobrane z buforu. W przypadku wersji szablonu, zwraca **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
 Użyj `GetParam` można pobrać danych parametru typu z buforu. Użyj [GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md) można pobrać dane parametru ciągu z buforu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)