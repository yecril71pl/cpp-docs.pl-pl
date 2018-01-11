---
title: ActivatableClass makra | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs: C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7043a3a9013f02048b34149dd113d2125dced6a2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="activatableclass-macros"></a>ActivatableClass Makra

Wypełnia wewnętrznej pamięci podręcznej zawiera fabryka, która może utworzyć wystąpienie określonej klasy.

## <a name="syntax"></a>Składnia

```cpp
ActivatableClass(
   className
);

ActivatableClassWithFactory(
   className,
   factory
);

ActivatableClassWithFactoryEx(
   className,
   factory,
   serverName
);
```

### <a name="parameters"></a>Parametry

*className*  
Nazwa klasy w celu utworzenia.  

*Fabryka*  
Fabryka, która spowoduje utworzenie wystąpienia określonej klasy.

*serverName*  
Nazwa, która określa podzestaw fabryki w module.

## <a name="remarks"></a>Uwagi

Nie należy używać tych makr w klasycznym modelu COM, jeśli używasz `#undef` dyrektywy upewnij się, że **&#95; &#95; WRL_WINRT_STRICT &#95; &#95;**  definicji makra jest usuwany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)