---
title: ComPtr::ComPtr, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::ComPtr
dev_langs:
- C++
helpviewer_keywords:
- ComPtr, constructor
ms.assetid: eaf70907-beac-458f-a503-2e5e27b0c196
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d08eb264ff3b4fc2f0170d6aee742ff29611613e
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39465373"
---
# <a name="comptrcomptr-constructor"></a>ComPtr::ComPtr — Konstruktor
Aktywuje nowe wystąpienie klasy **ComPtr** klasy. Przeciążenia zawierają konstruktory domyślne, kopiowanie, przenoszenie i konwersji.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW ComPtr();  
WRL_NOTHROW ComPtr(  
   decltype(__nullptr)  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr(  
   const ComPtr& other  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   const ComPtr<U> &other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr(  
   _Inout_ ComPtr<U>&& other,  
   typename ENABLE_IF<__is_convertible_to(U*,  
   T*),  
   void *>;  
```  
  
#### <a name="parameters"></a>Parametry  
 *U*  
 Typ *innych* parametru.  
  
 *other*  
 Obiekt typu *U*.  
  
## <a name="return-value"></a>Wartość zwracana  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor jest konstruktor domyślny, która niejawnie tworzy pustego obiektu. Drugi Konstruktor Określa [__nullptr](../windows/nullptr-cpp-component-extensions.md), co powoduje jawne utworzenie pustego obiektu.  
  
 Trzeci Konstruktor tworzy obiekt w obiekcie określonym przez wskaźnik.  
  
 Konstruktory czwarty i piąty są konstruktorów kopiujących. Piąty Konstruktor kopiuje obiekt, jeśli jest konwertowany na typ bieżącego.  
  
 Konstruktory szóstego lub siódmego są konstruktorów przenoszenia. Siódmego Konstruktor przenosi obiekt, jeśli jest konwertowany na typ bieżącego.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)