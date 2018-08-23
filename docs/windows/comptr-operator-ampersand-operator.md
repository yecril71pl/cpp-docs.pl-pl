---
title: ComPtr::operator&amp; Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr::operator&
dev_langs:
- C++
helpviewer_keywords:
- operator& operator
ms.assetid: 2d77fda6-f4b2-45c1-8a0e-fbc355013531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f513ac83e0ee83109f42cf87b80b4fcc4960db1f
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598606"
---
# <a name="comptroperatoramp-operator"></a>ComPtr::operator&amp; — Operator

Zwalnia interfejs skojarzony z tym **ComPtr** obiektu, a następnie pobiera adres **ComPtr** obiektu.

## <a name="syntax"></a>Składnia

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

## <a name="return-value"></a>Wartość zwracana

Słabe odwołanie do bieżącego **ComPtr**.

## <a name="remarks"></a>Uwagi

Ta metoda różni się od [ComPtr::GetAddressOf](../windows/comptr-getaddressof-method.md) w tym, że ta metoda wydaje odniesienie do wskaźnika interfejsu. Użyj `ComPtr::GetAddressOf` po adresu wskaźnik interfejsu, ale nie chcesz zwolnić interfejsu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** client.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz też

[ComPtr, klasa](../windows/comptr-class.md)