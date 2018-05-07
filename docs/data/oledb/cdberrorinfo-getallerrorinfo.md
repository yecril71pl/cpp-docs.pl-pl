---
title: CDBErrorInfo::GetAllErrorInfo | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDBErrorInfo.GetAllErrorInfo
- CDBErrorInfo::GetAllErrorInfo
- ATL::CDBErrorInfo::GetAllErrorInfo
- GetAllErrorInfo
- CDBErrorInfo.GetAllErrorInfo
dev_langs:
- C++
helpviewer_keywords:
- GetAllErrorInfo method
ms.assetid: 630049fa-d296-497a-bbf6-f5d3d71d271d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 590215ddc5c62e5c717aebe196bc33ce7d514e7a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdberrorinfogetallerrorinfo"></a>CDBErrorInfo::GetAllErrorInfo
Zwraca wszystkie typy w rekordach błędu informacje o błędzie.  
  
## <a name="syntax"></a>Składnia  
  
```
HRESULT GetAllErrorInfo(ULONG ulRecordNum,  
   LCID lcid,  BSTR* pbstrDescription,  
   BSTR* pbstrSource = NULL,  
   GUID* pguid = NULL,  
   DWORD* pdwHelpContext = NULL,  
   BSTR* pbstrHelpFile = NULL) const throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *ulRecordNum*  
 [in] Liczony od zera numer rekordu, dla którego ma zostać zwrócona informacje o błędzie.  
  
 `lcid`  
 [in] Identyfikator ustawień regionalnych informacje o błędzie do zwrócenia.  
  
 `pbstrDescription`  
 [out] Wskaźnik do opis błędu lub wartość NULL, jeśli ustawienia regionalne nie jest obsługiwane. Zobacz uwagi.  
  
 `pbstrSource`  
 [out] Wskaźnik do ciąg zawierający nazwę składnika, który wygenerował błąd.  
  
 `pguid`  
 [out] Wskaźnik do identyfikatora GUID interfejsu, który jest zdefiniowany kod błędu.  
  
 *pdwHelpContext*  
 [out] Wskaźnik do kontekstu pomocy o identyfikatorze błędu.  
  
 *pbstrHelpFile*  
 [out] Wskaźnik do ciąg zawierający ścieżkę do pliku pomocy, który opisuje błąd.  
  
## <a name="return-value"></a>Wartość zwracana  
 `S_OK` w przypadku powodzenia. Zobacz [IErrorRecords::GetErrorInfo](https://msdn.microsoft.com/en-us/library/ms711230.aspx) w *OLE DB Podręcznik programisty* dla innych wartości zwracanych.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="remarks"></a>Uwagi  
 Wartość danych wyjściowych `pbstrDescription` uzyskać wewnętrznie przez wywołanie IErrorInfo::GetDescription, który ustawia wartość null, jeśli ustawienia regionalne nie jest obsługiwana, czy są spełnione oba poniższe warunki:  
  
1.  wartość `lcid` nie jest stany USA Język angielski i  
  
2.  wartość `lcid` jest nie równa się wartości zwróconej przez GetUserDefaultLCID.  
  
## <a name="see-also"></a>Zobacz też  
 [CDBErrorInfo, klasa](../../data/oledb/cdberrorinfo-class.md)