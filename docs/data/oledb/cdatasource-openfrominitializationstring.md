---
title: CDataSource::OpenFromInitializationString | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDataSource.OpenFromInitializationString
- OpenFromInitializationString
- CDataSource::OpenFromInitializationString
- ATL::CDataSource::OpenFromInitializationString
- ATL.CDataSource.OpenFromInitializationString
dev_langs: C++
helpviewer_keywords: OpenFromInitializationString method
ms.assetid: 5ef1f1fd-92a9-4e1c-ad80-d3601b094b8c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 294c5cd893b04dd477a002adb6dc03fa33c60a29
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cdatasourceopenfrominitializationstring"></a>CDataSource::OpenFromInitializationString
Otwiera źródło danych określona przez ciąg inicjowania dostarczone przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT OpenFromInitializationString(   
   LPCOLESTR szInitializationString,   
   bool fPromptForInfo = false    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 *szInitializationString*  
 [in] Ciąg inicjowania.  
  
 *fPromptForInfo*  
 [in] Jeśli ten argument ma wartość **true**, następnie `OpenFromInitializationString` ustawi **DBPROP_INIT_PROMPT** właściwości **DBPROMPT_COMPLETEREQUIRED**, który określa, że użytkownik zostanie wyświetlony monit, tylko wtedy, gdy potrzeba więcej informacji. Jest to przydatne w sytuacjach, w których ciąg inicjalizacji określa bazę danych, która wymaga hasła, ale ciąg nie zawiera hasła. Monit o hasło (lub wszystkie brakujące informacje) podczas próby nawiązania połączenia z bazą danych.  
  
 Wartość domyślna to **false**, który określa, że użytkownik nigdy nie zostać poproszony (ustawia **DBPROP_INIT_PROMPT** do **DBPROMPT_NOPROMPT**).  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zostanie otwarty obiekt źródła danych przy użyciu składników usług w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usług, takich jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataSource, klasa](../../data/oledb/cdatasource-class.md)