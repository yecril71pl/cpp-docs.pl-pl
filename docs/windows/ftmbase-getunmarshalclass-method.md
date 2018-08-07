---
title: FtmBase::GetUnmarshalClass, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 329d43227aa131728db72086f99cb86797a5e1e3
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571155"
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass — Metoda
Pobiera identyfikator klasy, który używa modelu COM, aby zlokalizować bibliotekę DLL zawierającego kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, aby utworzyć wystąpienie niezainicjowanej serwera proxy.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDMETHODIMP GetUnmarshalClass(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out CLSID *pCid  
) override;  
```  
  
### <a name="parameters"></a>Parametry  
 *Parametr riid*  
 Odwołanie do identyfikatora interfejsu aby być organizowany.  
  
 *Wa*  
 Wskaźnik do interfejsu, aby zorganizować; może mieć wartości NULL, jeśli obiekt wywołujący nie ma wskaźnik do żądanego interfejsu.  
  
 *dwDestContext*  
 Miejsce docelowe kontekst, w którym ma zostać wycofana określonego interfejsu.  
  
 Określ co najmniej jednej wartości wyliczenia MSHCTX.  
  
 Unmarshaling może wystąpić w innym apartamentu bieżącego procesu (MSHCTX_INPROC) lub w inny proces na tym samym komputerze, co bieżący proces (MSHCTX_LOCAL).  
  
 *pvDestContext*  
 Zarezerwowane dla przyszłego użytku; musi mieć wartość NULL.  
  
 *mshlflags*  
 Gdy ta operacja zostanie ukończone, wskaźnik do CLSID, który ma być używany do tworzenia serwera proxy w procesie klienta.  
  
 *pCid*  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość S_FALSE.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)