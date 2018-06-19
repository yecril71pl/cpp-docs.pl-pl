---
title: CRowsetImpl::GetCommandFromID | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CRowsetImpl::GetCommandFromID
- GetCommandFromID
- CRowsetImpl.GetCommandFromID
dev_langs:
- C++
helpviewer_keywords:
- GetCommandFromID method
ms.assetid: 9f39cb07-1c40-486f-ba5b-cb4a65fab8a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: f79e9287bf8d546ba5007257899a6b6ddc27ad40
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33091297"
---
# <a name="crowsetimplgetcommandfromid"></a>CRowsetImpl::GetCommandFromID
Sprawdza, jeśli jeden lub oba parametry nie zawierają wartości ciągu, a jeśli tak, kopiuje wartości ciągu do elementów członkowskich danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md).  
  
## <a name="syntax"></a>Składnia  
  
```cpp
HRESULT CRowsetBaseImpl::GetCommandFromID(DBID* pTableID,  
   DBID* pIndexID);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pTableID`  
 [in] Wskaźnik do **DBID** reprezentujący nazwę tabeli.  
  
 `pIndexID`  
 [in] Wskaźnik do **DBID** reprezentujący nazwę indeksu.  
  
## <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT`.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda jest wywoływana za pomocą statycznego rozszerzające przez `CRowsetImpl` do wypełnienia elementy członkowskie danych [m_strCommandText](../../data/oledb/crowsetimpl-m-strcommandtext.md) i [m_strIndexText](../../data/oledb/crowsetimpl-m-strindextext.md). Domyślnie ta metoda sprawdza, jeśli jeden lub oba parametry zawierają wartości ciągu. Jeśli zawierają wartości ciągu, ta metoda kopiuje wartości ciągu do elementów członkowskich danych. Przez umieszczenie metodę z tego podpisu w Twojej `CRowsetImpl`-klasy, stosowana metoda zostanie wywołana zamiast implementacji podstawowej.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldb.h  
  
## <a name="see-also"></a>Zobacz też  
 [Crowsetimpl — klasa](../../data/oledb/crowsetimpl-class.md)   
 [CRowsetImpl::SetCommandText](../../data/oledb/crowsetimpl-setcommandtext.md)