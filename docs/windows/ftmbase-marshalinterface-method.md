---
title: FtmBase::MarshalInterface — metoda | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: fc22b83aee62b03ec5e664d08440b00718325272
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33874619"
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