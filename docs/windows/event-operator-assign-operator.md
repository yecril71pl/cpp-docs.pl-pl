---
title: Event::operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Event::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: d8fe9820-8856-4899-9553-56226bdc4945
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2aaea1c1c0a036b7c6ba26a9f5df94a72e9ea582
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641798"
---
# <a name="eventoperator-operator"></a>Event::operator= Operator
Przypisuje określonego **zdarzeń** referencję do bieżącego **zdarzeń** wystąpienia.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
WRL_NOTHROW Event& operator=(  
   _Inout_ Event&& h  
);  
```  
  
### <a name="parameters"></a>Parametry  
 *h*  
 Odwołania rvalue do **zdarzeń** wystąpienia.  
  
## <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do bieżącego **zdarzeń** wystąpienia.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** corewrappers.h  
  
 **Namespace:** Microsoft::wrl:: wrappers  
  
## <a name="see-also"></a>Zobacz też  
 [Event, klasa (Biblioteka szablonów języka C++ środowiska uruchomieniowego systemu Windows)](../windows/event-class-windows-runtime-cpp-template-library.md)