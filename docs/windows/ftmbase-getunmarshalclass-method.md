---
title: "FtmBase::GetUnmarshalClass — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase::GetUnmarshalClass
dev_langs:
- C++
helpviewer_keywords:
- GetUnmarshalClass method
ms.assetid: 535fc539-5b97-4967-b158-f7568f13d341
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 978379c64f22026f19dd76afa39af08402cebc65
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ftmbasegetunmarshalclass-method"></a>FtmBase::GetUnmarshalClass — Metoda
Pobiera identyfikator klasy, który COM używa do lokalizowania biblioteki DLL zawierającej kod dla odpowiedniego serwera proxy. COM ładuje tę bibliotekę DLL, można utworzyć niezainicjowanych wystąpienia serwera proxy.  
  
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
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odwołanie do identyfikatora interfejsu, który ma być przekazywane.  
  
 `pv`  
 Wskaźnik do interfejsu, który ma być organizowany; może mieć wartości NULL, jeśli element wywołujący nie ma wskaźnik do żądanego interfejsu.  
  
 `dwDestContext`  
 Docelowy kontekst, w którym ma zostać wycofana określonego interfejsu.  
  
 Określ jedną lub więcej wartości wyliczenia MSHCTX.  
  
 Unmarshaling może wystąpić w innego apartamentu bieżącego procesu (MSHCTX_INPROC) lub w inny proces na tym samym komputerze co bieżący proces (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Zarezerwowane do użytku w przyszłości; musi mieć wartość NULL.  
  
 `mshlflags`  
 Po tej operacji zakończeniu wskaźnik do identyfikatora CLSID ma być używany do utworzenia obiektu pośredniczącego w procesie klienta.  
  
 `pCid`  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartości S_FALSE.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** ftm.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [FtmBase, klasa](../windows/ftmbase-class.md)