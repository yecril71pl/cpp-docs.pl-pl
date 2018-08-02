---
title: ComPtr::operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 1a0c2752-f7d8-4819-9443-07b88b69ef02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: fac3a845ea7c512f5a7ccffdabdf67ce26029ff8
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2018
ms.locfileid: "39466166"
---
# <a name="comptroperator-operator"></a>ComPtr::operator= Operator
Przypisuje wartość do bieżącego **ComPtr**.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW ComPtr& operator=(  
   decltype(__nullptr)  
);  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ T *other  
);  
template <typename U>  
WRL_NOTHROW ComPtr& operator=(  
   _In_opt_ U *other  
);  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr &other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   const ComPtr<U>& other  
);  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr &&other  
);  
template<class U>  
WRL_NOTHROW ComPtr& operator=(  
   _Inout_ ComPtr<U>&& other  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 *U*  
 Klasa.  
  
 *other*  
 Wskaźnik, odwołanie lub odwołanie rvalue typu lub innej **ComPtr**.  
  
## <a name="return-value"></a>Wartość zwracana  
 Odwołanie do bieżącego **ComPtr**.  
  
## <a name="remarks"></a>Uwagi  
 Pierwsza wersja tego operatora przypisuje wartość pustą do bieżącego **ComPtr**.  
  
 W drugiej wersji, jeśli przypisanie wskaźnika interfejsu nie jest taka sama jak bieżący **ComPtr** wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego **ComPtr**.  
  
 W trzeciej wersji przypisywanie wskaźnika interfejsu jest przypisany do bieżącego **ComPtr**.  
  
 W czwartym wersji, jeśli wskaźnik interfejsu, przypisywanie wartości nie jest taka sama jak bieżący **ComPtr** wskaźnik interfejsu, drugi wskaźnik interfejsu jest przypisany do bieżącego **ComPtr**.  
  
 Piąta wersja jest operator kopiowania; Odwołanie do **ComPtr** jest przypisany do bieżącego **ComPtr**.  
  
 Szósty wersji jest operator kopii, który używa semantyki; przenoszenia odwołania rvalue do **ComPtr** Jeśli dowolnego typu jest statycznego, cast i przypisywany do bieżącego **ComPtr**.  
  
 Wersja siódmego jest operator kopii, który używa semantyki; przenoszenia odwołania rvalue do **ComPtr** typu *U* statyczne następnie rzutowania i ma przypisaną do bieżącego **ComPtr**.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [ComPtr, klasa](../windows/comptr-class.md)