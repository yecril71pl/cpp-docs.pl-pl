---
title: WeakRef::CopyTo, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88a092255655aaea0e06e8f69b520789f441d379
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40016291"
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo — Metoda
Przypisuje wskaźnik interfejsu, jeśli to możliwe, do zmiennej wskaźnika określonej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT CopyTo(  
   REFIID riid,  
   _Deref_out_ IInspectable** ptr  
);  
  
template<typename U>  
HRESULT CopyTo(  
   _Deref_out_ U** ptr  
);  
  
HRESULT CopyTo(  
   _Deref_out_ IWeakReference** ptr  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *U*  
 Wskaźnik `IInspectable` interfejsu. Błąd jest emitowane, jeśli *U* nie pochodzi od `IInspectable`.  
  
 *Parametr riid*  
 Identyfikator interfejsu. Błąd jest emitowane, jeśli *riid* nie pochodzi od `IWeakReference`.  
  
 *ptr*  
 Podwójnie pośredniego wskaźnika do `IInspectable` lub `IWeakReference`.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, który opisuje błąd. Aby uzyskać więcej informacji, zobacz **uwagi**.  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość S_OK oznacza, że ta operacja zakończyło się pomyślnie, ale nie wskazuje, czy słabe odwołanie została rozpoznana jako silne odwołanie. Jeśli zwracana jest S_OK, przetestować ten parametr *p* jest silne odwołanie, czyli parametr *p* nie jest równa **nullptr**.  
  
 Począwszy od zestawu Windows 10 SDK, ta metoda nie ustawia **WeakRef** wystąpienia do **nullptr** Jeśli nie można uzyskać słabe odwołanie, więc należy unikać błąd podczas sprawdzania kodu, który sprawdza WeakRef dla **nullptr**. Zamiast tego należy sprawdzić *ptr* dla **nullptr**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)