---
title: CDynamicParameterAccessor::SetParam | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CDynamicParameterAccessor::SetParam
- ATL::CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor.SetParam
- ATL.CDynamicParameterAccessor.SetParam
- SetParam
- CDynamicParameterAccessor:SetParam
- CDynamicParameterAccessor::SetParam<ctype>
- CDynamicParameterAccessor::SetParam
dev_langs: C++
helpviewer_keywords: SetParam method
ms.assetid: e2349220-545c-46ad-90da-9113ac52551a
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c2d7403dc318a0d5c7a906ec4c7f1e388143b3f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdynamicparameteraccessorsetparam"></a>CDynamicParameterAccessor::SetParam
Ustawia bufor parametru przy użyciu określonych danych (z systemem innym niż ciąg).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      template < class   
      ctype >  
bool SetParam(  
   DBORDINAL nParam,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
template < class ctype >  
bool SetParam(  
   TCHAR* pParamName,  
   const ctype* pData,  
   DBSTATUS status = DBSTATUS_S_OK  
) throw( );  
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
  
 *Stan*  
 [in] `DBSTATUS` Stan kolumny. Aby uzyskać informacje dotyczące `DBSTATUS` wartości, zobacz [stan](https://msdn.microsoft.com/en-us/library/ms722617.aspx) w *OLE DB Podręcznik programisty*, lub Wyszukaj `DBSTATUS` w oledb.h.  
  
## <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** w przypadku powodzenia lub **false** w przypadku awarii.  
  
 Użyj `SetParam` można ustawić danych parametrów typu w buforze. Użyj [SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md) można ustawić dane parametru ciągu w buforze.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cdynamicparameteraccessor — klasa](../../data/oledb/cdynamicparameteraccessor-class.md)