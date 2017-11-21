---
title: "Funkcja wywołania zwrotnego (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::Callback
dev_langs: C++
ms.assetid: afb15d25-3230-44f7-b321-e17c54872943
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 49d97371b351abdac85767853c034ada9b1fa116
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="callback-function-windows-runtime-c-template-library"></a>Callback — Funkcja (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)
Tworzy obiekt, którego funkcja członkowska jest metoda wywołania zwrotnego.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
  
#### <a name="parameters"></a>Parametry  
 `TDelegateInterface`  
 Parametr szablonu, który określa interfejs delegata do wywołania po wystąpieniu zdarzenia.  
  
 `TCallback`  
 Parametr szablonu, który określa typ obiektu, który reprezentuje obiekt i jego funkcji członkowskiej wywołania zwrotnego.  
  
 `TCallbackObject`  
 Parametr szablonu, który określa obiekt, którego funkcja członkowska jest metodę do wywołania po wystąpieniu zdarzenia.  
  
 `TArg1`  
 Parametr szablonu, który określa typ pierwszego argumentu metody wywołania zwrotnego.  
  
 `TArg2`  
 Parametr szablonu, który określa typ drugiego argumentu metody wywołania zwrotnego.  
  
 `TArg3`  
 Parametr szablonu, który określa typ trzeciego argumentu metody wywołania zwrotnego.  
  
 `TArg4`  
 Parametr szablonu, który określa typ czwarty argument metody wywołania zwrotnego.  
  
 `TArg5`  
 Parametr szablonu, który określa typ piątego argument metody wywołania zwrotnego.  
  
 `TArg6`  
 Parametr szablonu, który określa typ szóstego argument metody wywołania zwrotnego.  
  
 `TArg7`  
 Parametr szablonu, który określa typ siódmego argument metody wywołania zwrotnego.  
  
 `TArg8`  
 Parametr szablonu, który określa typ argumentu metody wywołania zwrotnego osiem.  
  
 `TArg9`  
 Parametr szablonu, który określa typ dziewiąty argument metody wywołania zwrotnego.  
  
 `callback`  
 Obiekt, który reprezentuje obiektu wywołania zwrotnego i jej funkcji Członkowskich.  
  
 `object`  
 Obiekt, którego funkcja członkowska jest wywoływana, gdy wystąpi zdarzenie.  
  
 `method`  
 Funkcja członkowska do wywołania po wystąpieniu zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt, którego funkcja członkowska jest metoda określonego wywołania zwrotnego.  
  
## <a name="remarks"></a>Uwagi  
 Podstawa obiektu delegowanego musi być IUnknown, nie IInspectable.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** event.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Microsoft::wrl — Namespace](../windows/microsoft-wrl-namespace.md)