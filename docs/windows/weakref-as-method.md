---
title: WeakRef::As, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::As
dev_langs:
- C++
helpviewer_keywords:
- As method
ms.assetid: 7173da62-b3fe-44d6-aea4-1aa97e69b221
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c2a56904fb3709137c167513d0eba426bda7ad14
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589372"
---
# <a name="weakrefas-method"></a>WeakRef::As — Metoda

Ustawia określony `ComPtr` parametru wskaźnika do reprezentowania określonego interfejsu.

## <a name="syntax"></a>Składnia

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Parametry

*U*  
Identyfikator interfejsu.

*ptr*  
Po zakończeniu tej operacji, obiekt, który reprezentuje parametr *U*.

## <a name="return-value"></a>Wartość zwracana

- S_OK, jeśli operacja się powiedzie; w przeciwnym razie wartość HRESULT, która wskazuje przyczynę operacja nie powiodła się, a *ptr* ustawiono **nullptr**.

- S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący **WeakRef** obiekt został zwolniony. Parametr *ptr* ustawiono **nullptr**.

- S_OK, jeśli operacja zakończy się powodzeniem, ale bieżący **WeakRef** obiektu nie jest tworzony na podstawie parametru *U*. Parametr *ptr* ustawiono **nullptr**.

## <a name="remarks"></a>Uwagi

Błąd jest emitowane, jeśli parametr *U* jest `IWeakReference`, lub nie jest tworzony na podstawie `IInspectable`.

Pierwszy szablon jest formularz, który należy używać w kodzie. Drugi szablon jest wewnętrznych specjalizacji pomocnika, która obsługuje funkcje języka C++, takie jak [automatycznie](../cpp/auto-cpp.md) słowem kluczowym dedukcji typu.

Począwszy od zestawu Windows 10 SDK, ta metoda nie ustawia **WeakRef** wystąpienia do **nullptr** Jeśli nie można uzyskać słabe odwołanie, więc należy unikać sprawdzanie błędów kodu, która sprawdza WeakRef dla **nullptr**. Zamiast tego należy sprawdzić *ptr* dla **nullptr**.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[WeakRef, klasa](../windows/weakref-class.md)