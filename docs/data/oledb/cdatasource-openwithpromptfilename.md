---
title: CDataSource::OpenWithPromptFileName | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDataSource.OpenWithPromptFileName
- OpenWithPromptFileName
- ATL::CDataSource::OpenWithPromptFileName
- ATL.CDataSource.OpenWithPromptFileName
- CDataSource::OpenWithPromptFileName
dev_langs:
- C++
helpviewer_keywords:
- OpenWithPromptFileName method
ms.assetid: 89460504-1aaf-4412-aa7b-fa5a4b39ada3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 318ec8fbba3845fd3e7a15d2efea6ba658712cf0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33094273"
---
# <a name="cdatasourceopenwithpromptfilename"></a>CDataSource::OpenWithPromptFileName
Ta metoda monituje użytkownika o okno dialogowe, a następnie otwiera źródłem danych przy użyciu pliku określonego przez użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT OpenWithPromptFileName(HWND hWnd = GetActiveWindow(   ),   
   DBPROMPTOPTIONS dwPromptOptions = DBPROMPTOPTIONS_NONE,   
   LPCOLESTR szInitialDirectory = NULL) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 `hWnd`  
 [in] Dojście do okna, który ma być nadrzędną okna dialogowego.  
  
 `dwPromptOptions`  
 [in] Określa styl okna dialogowego lokalizatora do wyświetlenia. Możliwe wartości można znaleźć w temacie Msdasc.h.  
  
 *szInitialDirectory*  
 [in] Początkowy katalog do wyświetlenia w oknie dialogowym lokalizatora.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda zostanie otwarty obiekt źródła danych przy użyciu składników usług w oledb32.dll; Ta biblioteka DLL zawiera implementację funkcji składników usług, takich jak pule zasobów, automatycznej rejestracji w transakcji i tak dalej. Aby uzyskać więcej informacji, zobacz "OLE DB Services" w OLE DB Podręcznik programisty na [ http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true ](http://msdn.microsoft.com/library/default.asp?url=/library/oledb/htm/oledbole_db_services.asp?frame=true).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDataSource, klasa](../../data/oledb/cdatasource-class.md)