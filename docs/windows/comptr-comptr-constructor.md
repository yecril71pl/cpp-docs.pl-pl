---
title: "Comptr::comptr — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::ComPtr
dev_langs: C++
helpviewer_keywords: ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
caps.latest.revision: "4"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5b31fdcbad35bc65b2d8ca26ccab69e875c1d3aa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr — Konstruktor
Intializes nowe wystąpienie klasy comptr — klasa. Przeciążenia Podaj konstruktorów domyślnej, copy, przenoszenia i konwersji.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Typ `other` parametru.  
  
 `other`  
 Obiekt typu `U`.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor jest domyślny konstruktor, który implictly tworzy pusty obiekt. Określa drugi Konstruktor [__nullptr](../windows/nullptr-cpp-component-extensions.md), co powoduje jawnie pustego obiektu.  
  
 Trzeci konstruktora tworzy obiekt z obiektu określonego przez wskaźnik.  
  
 Konstruktory czwartym i piątym są konstruktorami kopiowania. Konstruktor piątej kopiuje obiekt, czy jest możliwe do przekonwertowania na typ bieżącego.  
  
 Konstruktory szóstego lub siódmego są konstruktorów przenoszenia. Konstruktor siódmego przenosi obiekt, jeśli do przekonwertowania na typ bieżącego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [Comptr — klasa](../windows/comptr-class.md)