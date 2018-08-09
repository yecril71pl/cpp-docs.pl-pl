---
title: ComPtr::AsIID, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 07/11/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::AsIID
dev_langs:
- C++
helpviewer_keywords:
- AsIID method
ms.assetid: d5a3cdb2-796d-4410-966a-847c0e8fb226
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32f75c838ea178b1313ab0bf9f005ff2a4c5d75b
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652565"
---
# <a name="comptrasiid-method"></a>ComPtr::AsIID — Metoda
Zwraca **ComPtr** obiekt, który reprezentuje interfejs identyfikowane przez identyfikator określonego interfejsu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
WRL_NOTHROW HRESULT AsIID(  
   REFIID riid,  
   _Out_ ComPtr<IUnknown>* p  
) const;  
```  
  
### <a name="parameters"></a>Parametry  
 *Parametr riid*  
 Identyfikator interfejsu.  
  
 *p*  
 Jeśli obiekt ma interfejs, którego identyfikator jest równy *riid*, podwójnie pośredniego wskaźnika do interfejsu, określonego przez *riid* parametru; w przeciwnym razie wskaźnik do `IUnknown`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)