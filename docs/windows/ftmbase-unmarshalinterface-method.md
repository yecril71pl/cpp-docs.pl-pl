---
title: "FtmBase::UnmarshalInterface — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ce3710e84a9f7680b56f461029f279a659a5c14a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface — Metoda
Inicjuje nowo utworzonego serwera proxy i zwraca wskaźnika interfejsu do tego serwera proxy.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStm`  
 Wskaźnik do strumienia, z którego ma zostać wycofana wskaźnika interfejsu.  
  
 `riid`  
 Odwołanie do identyfikatora interfejsu, który ma zostać wycofana.  
  
 `ppv`  
 Po zakończeniu tej operacji, adres zmienna wskaźnika, która odbiera wskaźnika interfejsu w `riid`. Jeśli ta operacja zakończy się pomyślnie, *`ppv` zawiera wskaźnik żądanego interfejsu interfejsu, który ma zostać wycofana.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_NOINTERFACE lub E_FAIL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)