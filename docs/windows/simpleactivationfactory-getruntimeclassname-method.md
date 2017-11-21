---
title: "SimpleActivationFactory::GetRuntimeClassName — metoda | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
dev_langs: C++
ms.assetid: 3aa07487-9a42-46f8-8893-37ba6315e50b
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 22cb09115938da3d90bbe7feac0aac490971ffd1
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="simpleactivationfactorygetruntimeclassname-method"></a>SimpleActivationFactory::GetRuntimeClassName — Metoda

Pobiera nazwę klasy środowiska uruchomieniowego wystąpienia z klasą określoną przez `Base` parametr szablonu klasy.

## <a name="syntax"></a>Składnia

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

### <a name="parameters"></a>Parametry

*runtimeName*  
Po zakończeniu wykonywania tej operacji, nazwa klasy środowiska uruchomieniowego.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie wartość HRESULT, która wskazuje błąd.

## <a name="remarks"></a>Uwagi

Jeśli &#95; &#95; WRL_STRICT &#95; &#95; jest zdefiniowany, błędu potwierdzenia jest emitowany Jeśli klasa określony przez `Base` parametr szablonu klasy nie jest pochodną [runtimeclass —](../windows/runtimeclass-class.md), lub nie jest skonfigurowana z WinRt lub WinRtClassicComMix [ Runtimeclasstype —](../windows/runtimeclasstype-enumeration.md) wartość wyliczenia.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[Simpleactivationfactory — klasa](../windows/simpleactivationfactory-class.md)