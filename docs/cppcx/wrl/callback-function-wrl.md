---
title: Funkcja wywołania zwrotnego (WRL)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
ms.openlocfilehash: 138ad9d5d3bd4cf9e5263845f950dbbe7971fde6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214139"
---
# <a name="callback-function-wrl"></a>Funkcja wywołania zwrotnego (WRL)

Tworzy obiekt, którego funkcja członkowska jest metodą wywołania zwrotnego.

## <a name="syntax"></a>Składnia

```cpp
template<
   typename TDelegateInterface,
   typename TCallback
>
ComPtr<TDelegateInterface> Callback(
   TCallbackcallback
);
template<
   typename TDelegateInterface,
   typename TCallbackObject
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)()
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8)
);
template<
   typename TDelegateInterface,
   typename TCallbackObject,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8,
   typename TArg9
>
ComPtr<TDelegateInterface> Callback(
   _In_ TCallbackObject *object,
   _In_ HRESULT (TCallbackObject::* method)(TArg1,
   TArg2,
   TArg3,
   TArg4,
   TArg5,
   TArg6,
   TArg7,
   TArg8,
   TArg9)
);
```

### <a name="parameters"></a>Parametry

*TDelegateInterface*<br/>
Parametr szablonu, który określa interfejs delegata do wywołania w przypadku wystąpienia zdarzenia.

*TCallback*<br/>
Parametr szablonu, który określa typ obiektu, który reprezentuje obiekt i jego funkcję członkowską wywołania zwrotnego.

*TCallbackObject*<br/>
Parametr szablonu, który określa obiekt, którego funkcja członkowska jest metodą do wywołania w przypadku wystąpienia zdarzenia.

*TArg1*<br/>
Parametr szablonu, który określa typ pierwszego argumentu metody wywołania zwrotnego.

*TArg2*<br/>
Parametr szablonu, który określa typ drugiego argumentu metody wywołania zwrotnego.

*TArg3*<br/>
Parametr szablonu, który określa typ trzeciego argumentu metody wywołania zwrotnego.

*TArg4*<br/>
Parametr szablonu, który określa typ czwartego argumentu metody wywołania zwrotnego.

*TArg5*<br/>
Parametr szablonu, który określa typ piątego argumentu metody wywołania zwrotnego.

*TArg6*<br/>
Parametr szablonu, który określa typ szóstego argumentu metody wywołania zwrotnego.

*TArg7*<br/>
Parametr szablonu, który określa typ siódmego argumentu metody wywołania zwrotnego.

*TArg8*<br/>
Parametr szablonu, który określa typ ósmego argumentu metody wywołania zwrotnego.

*TArg9*<br/>
Parametr szablonu, który określa typ dziewiątego argumentu metody wywołania zwrotnego.

*wywołania zwrotnego*<br/>
Obiekt, który reprezentuje obiekt wywołania zwrotnego i jego funkcję członkowską.

*object*<br/>
Obiekt, którego funkcja członkowska jest wywoływana w przypadku wystąpienia zdarzenia.

*Method*<br/>
Funkcja członkowska do wywołania po wystąpieniu zdarzenia.

## <a name="return-value"></a>Wartość zwracana

Obiekt, którego funkcja członkowska jest określoną metodą wywołania zwrotnego.

## <a name="remarks"></a>Uwagi

Podstawą obiektu delegata musi być `IUnknown`, a nie `IInspectable`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** Event. h

**Przestrzeń nazw:** Microsoft:: WRL

## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)
