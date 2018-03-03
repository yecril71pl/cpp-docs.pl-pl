---
title: "Weakref::weakref — Konstruktor | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 125fe25179ddbe975530a0c368a4dfc7e4caaf1a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef — Konstruktor
Inicjuje nowe wystąpienie klasy weakref —.  
  
## <a name="syntax"></a>Składnia  
  
```  
WeakRef();  
WeakRef(  
   decltype(__nullptr)  
);  
  
WeakRef(  
   _In_opt_ IWeakReference* ptr  
);  
  
WeakRef(  
   const ComPtr<IWeakReference>& ptr  
);  
  
WeakRef(  
   const WeakRef& ptr  
);  
  
WeakRef(  
   _Inout_ WeakRef&& ptr  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik, odwołanie lub odwołanie r-wartości do istniejącego obiektu, który inicjuje bieżący obiekt weakref —.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje obiekt weakref — pusty. Drugi Konstruktor inicjuje obiekt weakref — wskaźnik do interfejsu słabego odwołania. Trzeci Konstruktor inicjuje obiekt weakref — z odwołaniem do comptr —\< słabego odwołania > obiektu. Konstruktory czwartym i piątym inicjuje obiekt weakref — z innym obiektem weakref —.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::wrl —  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)