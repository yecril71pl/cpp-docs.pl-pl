---
title: WeakRef::WeakRef, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef, constructor
ms.assetid: 589f87e0-8dcc-4e82-aab2-f2f66f1ec47c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e7b7d35fd8cae44c3f374a81cae572e4c9ee4f8
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2018
ms.locfileid: "40011162"
---
# <a name="weakrefweakref-constructor"></a>WeakRef::WeakRef — Konstruktor
Inicjuje nowe wystąpienie klasy **WeakRef** klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
### <a name="parameters"></a>Parametry  
 *ptr*  
 Wskaźnik, odwołanie lub odwołanie rvalue do istniejącego obiektu, który inicjuje bieżące **WeakRef** obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Pierwszy Konstruktor inicjuje pustą **WeakRef** obiektu. Drugi Konstruktor inicjuje **WeakRef** obiektu ze wskaźnika do `IWeakReference` interfejsu. Trzeci Konstruktor inicjuje **WeakRef** obiektu z odwołaniem do `ComPtr<IWeakReference>` obiektu. Czwarty i piąty Konstruktor inicjuje **WeakRef** obiektu z innego **WeakRef** obiektu.  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Zobacz też  
 [WeakRef, klasa](../windows/weakref-class.md)