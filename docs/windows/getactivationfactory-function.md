---
title: Getactivationfactory — funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
dev_langs:
- C++
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5afaa14d926cc7dde86cdbdb6b5ca8162f81d7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402151"
---
# <a name="getactivationfactory-function"></a>GetActivationFactory — Funkcja

Pobiera fabrykę aktywacji dla typu określonego przez parametr szablonu.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
inline HRESULT GetActivationFactory(
   _In_ HSTRING activatableClassId,
   _Out_ Microsoft::WRL::Details::ComPtrRef<T> factory
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Parametr szablonu, który określa typ fabryką aktywacji.

*activatableClassId*<br/>
Nazwa klasy, która może spowodować fabryką aktywacji.

*Fabryka*<br/>
Po zakończeniu tej operacji, odwołanie do aktywacji fabryki dla typu *T*.

## <a name="return-value"></a>Wartość zwracana

S_OK w przypadku powodzenia; w przeciwnym razie błąd HRESULT, która wskazuje, dlaczego ta operacja nie powiodła się.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Windows::Foundation

## <a name="see-also"></a>Zobacz też

[Windows::Foundation, przestrzeń nazw](../windows/windows-foundation-namespace.md)