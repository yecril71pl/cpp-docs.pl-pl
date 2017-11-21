---
title: CManualAccessor::CreateAccessor | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::CManualAccessor::CreateAccessor
- CreateAccessor
- ATL.CManualAccessor.CreateAccessor
- CManualAccessor.CreateAccessor
- CManualAccessor::CreateAccessor
dev_langs: C++
helpviewer_keywords: CreateAccessor method
ms.assetid: 594c8d6d-b49a-4818-a9a5-81c8115d4e42
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9bbd82a7ab2720d63ffa7860c26fc447b58e4f24
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="cmanualaccessorcreateaccessor"></a>CManualAccessor::CreateAccessor
Przydziela pamięć dla kolumny struktury powiązania i inicjuje elementów członkowskich danych kolumny.  
  
## <a name="syntax"></a>Składnia  
  
```  
  
      HRESULT CreateAccessor(   
   int nBindEntries,   
   void* pBuffer,   
   DBLENGTH nBufferSize    
) throw( );  
```  
  
#### <a name="parameters"></a>Parametry  
 `nBindEntries`  
 [in] Liczba kolumn. Liczba ta powinna być zgodna liczba wywołań [CManualAccessor::AddBindEntry](../../data/oledb/cmanualaccessor-addbindentry.md) funkcji.  
  
 `pBuffer`  
 [in] Wskaźnik do buforu, gdzie są przechowywane w kolumnach wyjściowych.  
  
 `nBufferSize`  
 [in] Rozmiar buforu w bajtach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Jeden standardowy `HRESULT` wartości.  
  
## <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, przed wywołaniem `CManualAccessor::AddBindEntry` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atldbcli.h  
  
## <a name="see-also"></a>Zobacz też  
 [Cmanualaccessor — klasa](../../data/oledb/cmanualaccessor-class.md)   
 [Przykładowe DBViewer](../../visual-cpp-samples.md)