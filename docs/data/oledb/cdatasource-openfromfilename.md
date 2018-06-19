---
title: CDataSource::OpenFromFileName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource::OpenFromFileName
- ATL::CDataSource::OpenFromFileName
- OpenFromFileName
- CDataSource.OpenFromFileName
- ATL.CDataSource.OpenFromFileName
dev_langs:
- C++
helpviewer_keywords:
- OpenFromFileName method
ms.assetid: c4226de6-59da-4368-9c15-c5afab86f68b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6dfa5411373ab4a5c80c493ad876926620c4f9a5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33090773"
---
# <a name="cdatasourceopenfromfilename"></a>CDataSource::OpenFromFileName
Otwiera źródło danych z pliku określonego przez nazwę pliku dostarczone przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenFromFileName(LPCOLESTR szFileName) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `szFileName`  
 [in] Nazwa pliku, zwykle połączenie ze źródłem danych (. Plik UDL).  
  
 Aby uzyskać więcej informacji o plikach łącze dane (pliki udl), zobacz [omówienie interfejsu API łącza danych](https://msdn.microsoft.com/en-us/library/ms718102.aspx) w zestawie Windows SDK.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zostanie otwarty obiekt źródła danych przy użyciu składników usług w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usług, takich jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB Services" w OLE DB Podręcznik programisty na [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataSource, klasa](../../data/oledb/cdatasource-class.md)