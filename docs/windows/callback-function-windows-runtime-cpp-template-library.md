---
title: Callback — funkcja (Biblioteka szablonów języka C++ środowiska wykonawczego Windows) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Callback
dev_langs:
- C++
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 799d0631ce29fcebd739f29232236e7cf87b74ac
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39652578"
---
# <a name="callback-function-windows-runtime-c-template-library"></a>Callback — Funkcja (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)
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
 *TDelegateInterface*  
 Parametr szablonu, który określa interfejs pełnomocnika do wywołania po wystąpieniu zdarzenia.  
  
 *TCallback*  
 Parametr szablonu, który określa typ obiektu, który reprezentuje obiekt i jego funkcję członkowską wywołania zwrotnego.  
  
 *TCallbackObject*  
 Parametr szablonu, który określa obiekt, którego funkcja członkowska jest metodą do wywołania po wystąpieniu zdarzenia.  
  
 *TArg1*  
 Parametr szablonu, który określa typ pierwszego argumentu metody wywołania zwrotnego.  
  
 *TArg2*  
 Parametr szablonu, który określa typ drugiego argumentu metody wywołania zwrotnego.  
  
 *TArg3*  
 Parametr szablonu, który określa typ trzeciego argumentu metody wywołania zwrotnego.  
  
 *TArg4*  
 Parametr szablonu, który określa typ czwartego argumentu metody wywołania zwrotnego.  
  
 *TArg5*  
 Parametr szablonu, który określa typ piątego argumentu metody wywołania zwrotnego.  
  
 *TArg6*  
 Parametr szablonu, który określa typ szóstego argumentu metody wywołania zwrotnego.  
  
 *TArg7*  
 Parametr szablonu, który określa typ siódmego argumentu metody wywołania zwrotnego.  
  
 *TArg8*  
 Parametr szablonu, który określa typ ósmego argumentu metody wywołania zwrotnego.  
  
 *TArg9*  
 Parametr szablonu, który określa typ dziewiątego argumentu metody wywołania zwrotnego.  
  
 *Wywołanie zwrotne*  
 Obiekt, który reprezentuje obiekt wywołania zwrotnego i jej funkcji członkowskiej.  
  
 *object*  
 Obiekt, którego funkcja członkowska jest wywoływana, gdy wystąpi zdarzenie.  
  
 *— Metoda*  
 Funkcja elementu członkowskiego do wywołania po wystąpieniu zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt, którego funkcja członkowska jest metodą określonego wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 Podstawą obiektu delegowanego musi być `IUnknown`, a nie `IInspectable`.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)