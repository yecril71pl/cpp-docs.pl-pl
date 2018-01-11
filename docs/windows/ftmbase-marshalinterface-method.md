---
title: "FtmBase::MarshalInterface — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs: C++
helpviewer_keywords: MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9df1e5d7559b434c1af0f1feff3b73b8141a8865
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface — Metoda
Zapisuje do strumienia dane wymagane do zainicjowania obiektu serwera proxy, w niektórych procesu klienta.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStm`  
 Wskaźnik do strumienia do użycia podczas przekazywania międzyprocesowego.  
  
 `riid`  
 Odwołanie do identyfikatora interfejsu, który ma być przekazywane. Ten interfejs musi pochodzić z interfejsu IUnknown.  
  
 `pv`  
 Wskaźnik do wskaźnika interfejsu, aby zorganizować; może mieć wartości NULL, jeśli element wywołujący nie ma wskaźnik do żądanego interfejsu.  
  
 `dwDestContext`  
 Docelowy kontekst, w którym ma zostać wycofana określonego interfejsu.  
  
 Określ jedną lub więcej wartości wyliczenia MSHCTX.  
  
 Unmarshaling może wystąpić w innego apartamentu bieżącego procesu (MSHCTX_INPROC) lub inny proces na tym samym komputerze co bieżący proces (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Zarezerwowane do użytku w przyszłości; musi być równy zero.  
  
 `mshlflags`  
 Określa, czy można zorganizować dane mają być przekazywane do procesu klienta — typową sytuacją — lub zapisywane w tabeli globalnej, skąd mogą zostać pobrane przez wielu klientów.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK  
 Wskaźnik interfejsu zorganizować został pomyślnie.  
  
 E_NOINTERFACE  
 Określony interfejs nie jest obsługiwany.  
  
 STG_E_MEDIUMFULL  
 Strumień jest pełna.  
  
 E_FAIL  
 Operacja nie powiodła się.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)