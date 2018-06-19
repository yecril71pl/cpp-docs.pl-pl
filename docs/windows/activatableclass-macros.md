---
title: ActivatableClass makra | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ActivatableClass
- ActivatableClassWithFactory
- ActivatableClassWithFactoryEx
dev_langs:
- C++
helpviewer_keywords:
- ActivatableClassWithFactory
- ActivatableClass
- ActivatableClassWithFactoryEx
ms.assetid: 9bd64709-ec2c-4678-8c96-ea5982622bdd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: aeb68deddd1cdfa9e1e869a08bfb0a1f3bb8d6ca
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857467"
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

Nie należy używać tych makr w klasycznym modelu COM, jeśli używasz `#undef` dyrektywy upewnij się, że **&#95; &#95;WRL_WINRT_STRICT&#95; &#95;** definicji makra jest usuwany.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::wrl —

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)