---
title: "Cdberrorinfo — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CDBErrorInfo
- ATL::CDBErrorInfo
- ATL.CDBErrorInfo
dev_langs: C++
helpviewer_keywords: CDBErrorInfo class
ms.assetid: 9a5c18a2-ee3e-40f5-ab4c-581288d7f737
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3d1ecd29e32686e8cc91ec9716625beeee2cef25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cdberrorinfo-class"></a>CDBErrorInfo — Klasa
Zapewnia obsługę OLE DB wystąpił błąd podczas przetwarzania przy użyciu OLE DB [IErrorRecords](https://msdn.microsoft.com/en-us/library/ms718112.aspx) interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```  
class CDBErrorInfo  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md)|Zwraca wszystkie informacje o błędzie w rekordach błędu.|  
|[GetBasicErrorInfo](../../data/oledb/cdberrorinfo-getbasicerrorinfo.md)|Wywołania [IErrorRecords::GetBasicErrorInfo](https://msdn.microsoft.com/en-us/library/ms723907.aspx) zwraca podstawowe informacje dotyczące określonego błędu.|  
|[GetCustomErrorObject](../../data/oledb/cdberrorinfo-getcustomerrorobject.md)|Wywołania [IErrorRecords::GetCustomErrorObject](https://msdn.microsoft.com/en-us/library/ms725417.aspx) zwraca wskaźnik do interfejsu na obiekt błędu niestandardowego.|  
|[GetErrorInfo](../../data/oledb/cdberrorinfo-geterrorinfo.md)|Wywołania [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) do zwrócenia **IErrorInfo** wskaźnika interfejsu do określonego rekordu.|  
|[GetErrorParameters](../../data/oledb/cdberrorinfo-geterrorparameters.md)|Wywołania [IErrorRecords::GetErrorParameters](https://msdn.microsoft.com/en-us/library/ms715793.aspx) do zwrócenia parametry błędów.|  
|[GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md)|Pobiera błąd rekordów dla określonego obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 Ten interfejs zwraca błąd rekordów do użytkownika. Wywołanie [CDBErrorInfo::GetErrorRecords](../../data/oledb/cdberrorinfo-geterrorrecords.md) first, aby uzyskać liczbę rekordów błędów. Następnie wywołania funkcji jedną dostępu, takich jak [CDBErrorInfo::GetAllErrorInfo](../../data/oledb/cdberrorinfo-getallerrorinfo.md), aby pobrać informacje o błędzie dla każdego rekordu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [DBViewer](../../visual-cpp-samples.md)   
 [Szablony konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [Dokumentacja szablonów konsumentów OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)