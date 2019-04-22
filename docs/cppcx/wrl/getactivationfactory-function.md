---
title: GetActivationFactory — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Details::GetActivationFactory
- client/ABI::Windows::Foundation::GetActivationFactory
- client/Windows::Foundation::GetActivationFactory
helpviewer_keywords:
- GetActivationFactory function
ms.assetid: 5736d285-6beb-42aa-8788-e261c0010afe
ms.openlocfilehash: 3e138eee9e5bc02971cd1eb34c78f2be4ad5c9a0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59033946"
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

## <a name="see-also"></a>Zobacz także

[Windows::Foundation, przestrzeń nazw](windows-foundation-namespace.md)