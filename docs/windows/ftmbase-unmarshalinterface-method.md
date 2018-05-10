---
title: FtmBase::UnmarshalInterface — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::UnmarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- UnmarshalInterface method
ms.assetid: 6850a621-e9a6-4001-bc1e-bd5d1b121adc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 964ce5cc33b51c54446874522317814279cdd960
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
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