---
title: HString::GetAddressOf, metoda | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
dev_langs:
- C++
ms.assetid: 6050decf-5f99-49f0-9497-1c8192c485ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e327e2818903396c154be7406ec325695b6b6982
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42613368"
---
# <a name="hstringgetaddressof-method"></a>HString::GetAddressOf — Metoda

Pobiera wskaźnik do podstawowego dojścia HSTRING.

## <a name="syntax"></a>Składnia

```cpp
HSTRING* GetAddressOf() throw()  
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowego dojścia HSTRING.

## <a name="remarks"></a>Uwagi

Po tej operacji jest niszczony, wartość ciągu podstawowego dojścia HSTRING.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)