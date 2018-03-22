---
title: WeakRef::CopyTo — metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::CopyTo
dev_langs:
- C++
helpviewer_keywords:
- CopyTo method
ms.assetid: f83de6da-b3d4-41a6-9845-cd725ecf3b75
caps.latest.revision: ''
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d83ff273d3f6e9748be722b47d08c459564aa911
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/22/2018
---
# <a name="weakrefcopyto-method"></a>WeakRef::CopyTo — Metoda
Przypisuje wskaźnik interfejsu, jeśli jest dostępny do zmiennej wskaźnikowej określony.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Wskaźnik interfejsu IInspectable. Błąd jest emitowany Jeśli `U` nie pochodzi od IInspectable.  
  
 `riid`  
 Identyfikatora interfejsu. Błąd jest emitowany Jeśli `riid` nie pochodzi od **słabego odwołania**.  
  
 `ptr`  
 Podwójnie pośredni wskaźnik do IInspectable lub słabego odwołania.  
  
## <a name="return-value"></a>Wartość zwracana  
 S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT opisujący błąd. Aby uzyskać więcej informacji zobacz uwagi.  
  
## <a name="remarks"></a>Uwagi  
 Zwracana wartość S_OK oznacza, że ta operacja powiodła się, ale nie wskazuje, czy odwołanie słabe została rozpoznana jako silne odwołanie. Jeśli zostanie zwrócona wartość S_OK, przetestuj parametru `p` jest silne odwołanie; oznacza to, że parametr `p` nie jest równa `nullptr`.  
  
 Począwszy od zestawu SDK systemu Windows 10, ta metoda nie ustawiono wystąpienie weakref — `nullptr` , jeśli nie można uzyskać słabe odwołanie, dlatego należy unikać błąd podczas sprawdzania kodu, który sprawdza weakref — dla `nullptr`. Zamiast tego należy sprawdzić `ptr` dla `nullptr`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)