---
title: CDBErrorInfo::GetErrorRecords | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDBErrorInfo.GetErrorRecords
- ATL.CDBErrorInfo.GetErrorRecords
- ATL::CDBErrorInfo::GetErrorRecords
- GetErrorRecords
- CDBErrorInfo::GetErrorRecords
dev_langs:
- C++
helpviewer_keywords:
- GetErrorRecords method
ms.assetid: 07746774-bcca-4833-8f55-a619e9777c17
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 33e0ab54bc3da570aecba0df347e14a511b0a833
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cdberrorinfogeterrorrecords"></a>CDBErrorInfo::GetErrorRecords
Pobiera błąd rekordów dla określonego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT GetErrorRecords(IUnknown* pUnk,   
   const IID& iid,   
   ULONG* pcRecords) throw();  


HRESULT GetErrorRecords(ULONG* pcRecords) throw();  
```  
  
#### <a name="parameters"></a>Parametry  
 *pUnk*  
 [in] Interfejs do obiektu, dla którego można pobrać rekordów błędów.  
  
 `iid`  
 [in] Uzyskanie identyfikatora IID interfejsu skojarzonego z powodu błędu.  
  
 *pcRecords*  
 [out] Wskaźnik do rekordów błędów liczby (w oparciu o jeden).  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Formularz pierwszej funkcji, jeśli chcesz sprawdzić, które interfejs, aby uzyskać informacje o błędzie z. W przeciwnym razie użyj drugi formularz.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [CDBErrorInfo, klasa](../../data/oledb/cdberrorinfo-class.md)