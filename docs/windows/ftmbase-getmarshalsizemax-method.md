---
title: FtmBase::GetMarshalSizeMax, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c39c313f06bb4dd1f4dbc095df159a38625e9db8
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39570217"
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax — Metoda
Uzyskaj górnej granicy liczby bajtów potrzebnych do organizowania określony wskaźnik interfejsu do określonego obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu aby być organizowany.  
  
 *Wa*  
 Wskaźnik interfejsu do przekazywania; może mieć wartości NULL.  
  
 *dwDestContext*  
 Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.  
  
 Określ co najmniej jednej wartości wyliczenia MSHCTX.  
  
 Obecnie unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub w inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Zarezerwowane dla przyszłego użytku; musi mieć wartość NULL.  
  
 *mshlflags*  
 Flaga wskazująca, czy ma być przesyłane z powrotem do procesu klienta dane, które mają być przekazywane — typowy przypadek — lub zapisywane w tabeli globalne, gdzie mogą być pobierane przez wielu klientów. Określ co najmniej jednej wartości wyliczenia MSHLFLAGS.  
  
 *pSize*  
 Gdy ta operacja zostanie ukończone, wskaźnik do górnej granicy ilości danych do zapisania do organizowania strumienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie, lub E_NOINTERFACE E_FAIL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)