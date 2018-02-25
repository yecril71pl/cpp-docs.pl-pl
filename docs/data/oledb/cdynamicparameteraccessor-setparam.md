---
title: CDynamicParameterAccessor::SetParam | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
dev_langs:
- C++
helpviewer_keywords:
- SetParam method
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 3fcedc0d54e5b25eb4490425253f6c1bfd139a85
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="cdynamicparameteraccessorsetparam"></a>CDynamicParameterAccessor::SetParam
Ustawia bufor parametru przy użyciu określonych danych (z systemem innym niż ciąg).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
template <class ctype>
bool SetParam(DBORDINAL nParam,  
               constctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  

template <class ctype>  
bool SetParam(TCHAR* pParamName,  
               const ctype* pData,  
               DBSTATUS status = DBSTATUS_S_OK) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `ctype`  
 Parametr opartego na szablonie, który jest typem danych.  
  
 `nParam`  
 [in] Liczba parametrów (przesunięcie od 1). Parametr 0 jest zarezerwowana dla wartości zwracanych. Liczba parametrów jest indeks parametru na podstawie jego kolejności w języku SQL lub procedurę składowaną wywołania. Na przykład:  
  
 [!code-cpp[NVC_OLEDB_Consumer#8](../../data/oledb/codesnippet/cpp/cdynamicparameteraccessor-setparam_1.cpp)]  
  
 `pParamName`  
 [in] Nazwa parametru.  
  
 `pData`  
 [in] Wskaźnik do pamięci zawierający dane do zapisania w buforze.  
  
 *status*  
 [in] `DBSTATUS` Stan kolumny. Aby uzyskać informacje dotyczące `DBSTATUS` wartości, zobacz [stan](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty*, lub Wyszukaj `DBSTATUS` w oledb.h.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
 Użyj `SetParam` można ustawić danych parametrów typu w buforze. Użyj [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) można ustawić dane parametru ciągu w buforze.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDynamicParameterAccessor, klasa](../../data/oledb/cdynamicparameteraccessor-class.md)