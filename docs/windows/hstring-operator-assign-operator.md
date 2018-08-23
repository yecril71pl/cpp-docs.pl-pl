---
title: HString::Operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
dev_langs:
- C++
ms.assetid: 8e68c1ff-bc57-4526-810e-af3c284b4e30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9294650db7a1b18c2542603988952a80b3f1905d
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598548"
---
# <a name="hstringoperator-operator"></a>HString::Operator= Operator

Przenosi wartość innego **HString** obiekt do bieżącego **HString** obiektu.

## <a name="syntax"></a>Składnia

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Parametry

*other*  
Istniejące **HString** obiektu.

## <a name="remarks"></a>Uwagi

Wartość istniejącego *innych* obiekt jest kopiowany do bieżącego **HString** obiektu, a następnie *innych* niszczony jest obiekt.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)