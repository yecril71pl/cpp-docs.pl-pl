---
title: FtmBase::UnmarshalInterface, metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: a1991454daa76fcf7878a7487080124b5a34dbeb
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39644037"
---
# <a name="ftmbaseunmarshalinterface-method"></a>FtmBase::UnmarshalInterface — Metoda
Inicjuje nowo utworzony serwer proxy i zwraca wskaźnik interfejsu do tego serwera proxy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHODIMP UnmarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __deref_out void **ppv  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *pStm*  
 Wskaźnik do strumienia, z którego ma zostać wycofana wskaźnika interfejsu.  
  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu Aby zostać wycofana.  
  
 *ppv*  
 Po zakończeniu tej operacji, adres zmiennej wskaźnika, który otrzymuje wskaźnik interfejsu w *riid*. Jeśli operacja zakończy się powodzeniem, **ppv* znajduje się wskaźnik interfejsu żądanego interfejsu Aby zostać wycofana.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie E_NOINTERFACE lub E_FAIL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)