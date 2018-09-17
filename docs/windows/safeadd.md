---
title: SafeAdd | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- SafeAdd
dev_langs:
- C++
helpviewer_keywords:
- SafeAdd function
ms.assetid: 3f82b91d-59fe-4ee1-873b-d056182fa8be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ada0997a03cefbec4bcc4faa26ad4eaf8c176ff2
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45704890"
---
# <a name="safeadd"></a>SafeAdd

Dodaje dwie liczby, w sposób zapewniający ochronę przed przepełnienia.

## <a name="syntax"></a>Składnia

```cpp
template<typename T, typename U>
inline bool SafeAdd (
   T t,
   U u,
   T& result
) throw ();
```

### <a name="parameters"></a>Parametry

*t*<br/>
[in] Pierwsza liczba do dodania. To musi być typu T.

*u*<br/>
[in] Druga liczba do dodania. Musi mieć typ U.

*wynik*<br/>
[out] Parametr gdzie **SafeAdd** zapisuje wynik.

## <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli żaden błąd nie wystąpi; **false** w przypadku wystąpienia błędu.

## <a name="remarks"></a>Uwagi

Ta metoda jest częścią [Biblioteka SafeInt](../windows/safeint-library.md) i jest przeznaczony dla operacji dodawania jednego bez tworzenia wystąpienia obiektu [safeint — klasa](../windows/safeint-class.md).

> [!NOTE]
> Ta metoda ją stosować tylko po jednej operacji matematycznych muszą być chronione. Jeśli istnieje wiele operacji, należy użyć `SafeInt` klasy zamiast wywoływania poszczególnych funkcjami autonomicznymi.

Aby uzyskać więcej informacji na temat typów szablonu T i U zobacz [safeint — funkcje](../windows/safeint-functions.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** safeint.h

**Namespace:** Microsoft::Utilities

## <a name="see-also"></a>Zobacz też

[SafeInt, funkcje](../windows/safeint-functions.md)  
[Biblioteka SafeInt](../windows/safeint-library.md)  
[SafeInt, klasa](../windows/safeint-class.md)  
[SafeSubtract](../windows/safesubtract.md)