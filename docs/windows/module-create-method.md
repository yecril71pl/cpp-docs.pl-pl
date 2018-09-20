---
title: Module::CREATE, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module::Create
dev_langs:
- C++
helpviewer_keywords:
- Create method
ms.assetid: bfa97fd7-5226-4604-92a5-3b9697053e64
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a8b84bcaec7dbadfb7b735264df12f7e958dcd20
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444700"
---
# <a name="modulecreate-method"></a>Module::Create — Metoda

Tworzy wystąpienie modułu.

## <a name="syntax"></a>Składnia

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()  
);
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ modułu.

*Wywołanie zwrotne*<br/>
Wywołuje się, gdy ostatni obiekt wystąpienia modułu jest zwalniany.

*object*<br/>
*Obiektu* i *metoda* parametry są używane w połączeniu. Wskazuje ostatni obiekt wystąpienia po udostępnieniu ostatni obiekt wystąpienia w module.

*— Metoda*<br/>
*Obiektu* i *metoda* parametry są używane w połączeniu. Wskazuje metodę ostatniego wystąpienia obiektu po udostępnieniu ostatni obiekt wystąpienia w module.

## <a name="return-value"></a>Wartość zwracana

Odwołanie do modułu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** module.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[Klasa modułu](../windows/module-class.md)