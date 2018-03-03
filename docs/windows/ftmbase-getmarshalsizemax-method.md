---
title: "FtmBase::GetMarshalSizeMax — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs:
- C++
helpviewer_keywords:
- GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0d68889531c270db190f861eb20a34783b88987f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax — Metoda
Pobierz górnej granicy liczby bajtów potrzebne do organizowania wskaźników określonego interfejsu w określonym obiekcie.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odwołanie do identyfikatora interfejsu, który ma być przekazywane.  
  
 `pv`  
 Wskaźnik interfejsu zorganizowanie; może mieć wartości NULL.  
  
 `dwDestContext`  
 Docelowy kontekst, w którym ma zostać wycofana określonego interfejsu.  
  
 Określ jedną lub więcej wartości wyliczenia MSHCTX.  
  
 Obecnie unmarshaling może wystąpić innego apartamentu bieżącego procesu (MSHCTX_INPROC) lub inny proces na tym samym komputerze co bieżący proces (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Zarezerwowane do użytku w przyszłości; musi mieć wartość NULL.  
  
 `mshlflags`  
 Flaga wskazująca, czy można zorganizować dane mają być przekazywane do procesu klienta — typową sytuacją — lub zapisywane w tabeli globalnej, skąd mogą zostać pobrane przez wielu klientów. Określ jedną lub więcej wartości wyliczenia MSHLFLAGS.  
  
 `pSize`  
 Po tej operacji zakończeniu wskaźnik do górnej granicy ilości danych do zapisania w strumieniu kierowania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie lub E_NOINTERFACE E_FAIL.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)