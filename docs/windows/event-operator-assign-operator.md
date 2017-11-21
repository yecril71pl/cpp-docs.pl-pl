---
title: "Event::operator = — Operator | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs: C++
helpviewer_keywords: operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: b6001462a5618251acc838d1d8fad3bd93968c81
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="eventoperator-operator"></a>Event::operator= Operator
Przypisuje określonego zdarzenia odwołanie do bieżącego wystąpienia zdarzenia.  
  
## <a name="syntax"></a>Składnia  
  
```  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `h`  
 R-wartości — odwołanie do wystąpienia zdarzenia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego wystąpienia zdarzenia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers —  
  
## <a name="see-also"></a>Zobacz też  
 [Event — klasa (Biblioteka szablonów języka C++ środowiska wykonawczego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)