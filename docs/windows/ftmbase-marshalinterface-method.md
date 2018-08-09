---
title: FtmBase::MarshalInterface, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs:
- C++
helpviewer_keywords:
- MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 23779cbe0b27680122c6aa3a8f8748c39f28078e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39647410"
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface — Metoda
Zapisuje w strumieniu danych wymagane do zainicjowania obiektu serwera proxy, w niektórych procesu klienta.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *pStm*  
 Wskaźnik do strumienia, który ma być używany podczas kierowania.  
  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu aby być organizowany. Ten interfejs musi pochodzić od `IUnknown` interfejsu.  
  
 *Wa*  
 Wskaźnik do wskaźnika interfejsu, aby zorganizować; może mieć wartości NULL, jeśli obiekt wywołujący nie ma wskaźnik do żądanego interfejsu.  
  
 *dwDestContext*  
 Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.  
  
 Określ co najmniej jednej wartości wyliczenia MSHCTX.  
  
 Unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Zarezerwowane dla przyszłego użytku; musi mieć wartość zero.  
  
 *mshlflags*  
 Określa, czy dane, które mają być przekazywane do być przesyłane z powrotem do procesu klienta — typowy przypadek — lub zapisywane w tabeli globalne, gdzie mogą być pobierane przez wielu klientów.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Wskaźnik interfejsu zorganizować został pomyślnie.  
  
 E_NOINTERFACE  
 Wybrany interfejs nie jest obsługiwana.  
  
 STG_E_MEDIUMFULL  
 Strumień jest pełny.  
  
 E_FAIL  
 Operacja nie powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)