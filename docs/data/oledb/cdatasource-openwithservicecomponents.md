---
title: CDataSource::OpenWithServiceComponents | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource::OpenWithServiceComponents
- OpenWithServiceComponents
- CDataSource.OpenWithServiceComponents
dev_langs:
- C++
helpviewer_keywords:
- OpenWithServiceComponents method
ms.assetid: 49c1d037-36ae-4fde-8e54-ced623abe1a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 793f1fcb22ac0c57bc1cccb375a0be24b18116ce
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdatasourceopenwithservicecomponents"></a>CDataSource::OpenWithServiceComponents
Otwiera obiekt źródła danych w oledb32.dll przy użyciu składników usługi.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenWithServiceComponents (const CLSID clsid,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  


HRESULT OpenWithServiceComponents (LPCSTR szProgID,  
   DBPROPSET* pPropset = NULL,  
   ULONG ulPropSets = 1);  
```  
  
#### <a name="parameters"></a>Parametry  
 `clsid`  
 [in] **CLSID** dostawcy danych.  
  
 `szProgID`  
 [in] Identyfikator programu dostawcy danych.  
  
 `pPropset`  
 [in] Wskaźnik do tablicy [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) struktury zawierające właściwości i wartości, które można ustawić. Zobacz [zestawy właściwości i grup właściwości](https://msdn.microsoft.com/en-us/library/ms713696.aspx) w *OLE DB Podręcznik programisty* w systemie Windows SDK. Jeśli obiekt źródła danych został zainicjowany, właściwości musi należeć do grupy właściwości źródła danych. Jeśli w tę samą właściwość jest określony więcej niż raz `pPropset`, która wartość jest używana jest specyficznych dla dostawcy. Jeśli `ulPropSets` wynosi zero, ten parametr jest ignorowany.  
  
 `ulPropSets`  
 [in] Liczba [DBPROPSET](https://msdn.microsoft.com/en-us/library/ms714367.aspx) przekazano struktury *pPropSet* argumentu. Jeśli jest to zero, dostawca ignoruje `pPropset`.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zostanie otwarty obiekt źródła danych przy użyciu składników usług w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usług, takich jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB Services" w OLE DB Podręcznik programisty na [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataSource, klasa](../../data/oledb/cdatasource-class.md)