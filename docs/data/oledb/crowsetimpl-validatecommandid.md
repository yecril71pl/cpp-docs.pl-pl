---
title: CRowsetImpl::ValidateCommandID | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CRowsetImpl.ValidateCommandID
- CRowsetImpl::ValidateCommandID
dev_langs: C++
helpviewer_keywords: ValidateCommandID method
ms.assetid: cdde6088-41bc-4b8f-a32b-f36f7d9b5ec0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fa772283a3dc5f5b3a69639aa0828226f3c90760
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="crowsetimplvalidatecommandid"></a>CRowsetImpl::ValidateCommandID
Sprawdza, aby zobaczyć, czy w jednej lub obu **DBID**s zawierają wartości ciągu, a jeśli tak, kopiuje je do jego elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT CRowsetBaseImpl::ValidateCommandID(  
   DBID* pTableID,  
   DBID* pIndexID   
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTableID`  
 [in] Wskaźnik do **DBID** reprezentujący identyfikator tabeli.  
  
 `pIndexID`  
 [in] Wskaźnik do **DBID** reprezentujący identyfikator indeksu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana za pomocą statycznego rozszerzające przez `CRowsetImpl` do wypełnienia jej elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Domyślnie ta metoda sprawdza, aby zobaczyć, czy w jednej lub obu **DBID**s zawierają wartości ciągu, a jeśli tak, kopiuje je do jego elementów członkowskich danych. Przez umieszczenie metodę z tego podpisu w Twojej `CRowsetImpl`-klasy, stosowana metoda zostanie wywołana zamiast implementacji podstawowej.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowsetimpl — klasa](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)