---
title: InterfaceTraits::CastToUnknown, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::InterfaceTraits::CastToUnknown
dev_langs:
- C++
helpviewer_keywords:
- CastToUnknown method
ms.assetid: aca47fa0-3c60-47f2-a73c-258f7160adff
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: df27ec7ca4cccb278fee524aab9d0d2dc5a25134
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42589762"
---
# <a name="interfacetraitscasttounknown-method"></a>InterfaceTraits::CastToUnknown — Metoda

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
template<typename T>
static __forceinline IUnknown* CastToUnknown(
   _In_ T* ptr
);
```

### <a name="parameters"></a>Parametry

*T*  
Typ parametru *ptr*.

*ptr*  
Wskaźnik do typu *T*.

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do IUnknown, z którego `Base` pochodzi.

## <a name="remarks"></a>Uwagi

Rzutuje określony wskaźnik do wskaźnika do `IUnknown`.

Aby uzyskać więcej informacji na temat `Base`, zobacz sekcję publiczne definicje typów w [interfacetraits — struktura](../windows/interfacetraits-structure.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[InterfaceTraits, struktura](../windows/interfacetraits-structure.md)  
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)