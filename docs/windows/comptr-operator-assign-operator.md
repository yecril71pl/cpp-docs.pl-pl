---
title: "ComPtr::operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::ComPtr::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 30f04bdfe7b508bf83e34992fefdcb10c58b4655
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="comptroperator-operator"></a>ComPtr::operator= Operator
Przypisuje wartość do bieżącego comptr —.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <  
   typename U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<  
   class U  
>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `U`  
 Klasa.  
  
 `other`  
 Wskaźnik, typu odwołania lub r-wartości odwołanie do typu lub innego comptr —.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego comptr —.  
  
## <a name="remarks"></a>Uwagi  
 Bieżący comptr — pierwszej wersji tego operatora przypisuje pustą wartość.  
  
 W drugiej wersji Jeśli przypisanie wskaźnika interfejsu nie jest taka sama jak bieżący wskaźnik interfejsu comptr — drugi wskaźnika interfejsu jest przypisany do bieżącego comptr —.  
  
 W trzeciej wersji przypisanie wskaźnika interfejsu jest przypisany do bieżącego comptr —.  
  
 W czwartym wersji Jeśli wskaźnik interfejsu przypisywanie wartości nie jest taka sama jak bieżący wskaźnik interfejsu comptr — drugi wskaźnika interfejsu jest przypisany do bieżącego comptr —.  
  
 Wersja piątej jest operatora kopii; Odwołanie do comptr — jest przypisany do bieżącego comptr —.  
  
 Wersja szóstego jest operatora kopii, która używa Przenieś semantyki; odwołania do r-wartości do comptr — Jeśli dowolny typ jest statyczny, rzutowania i następnie przypisane do bieżącej comptr —.  
  
 Wersja siódmego jest operatora kopii, która używa Przenieś semantyki; odwołania do r-wartości do comptr — typu `U` jest statyczna rzutowanie następnie i przypisane do bieżącej comptr —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)