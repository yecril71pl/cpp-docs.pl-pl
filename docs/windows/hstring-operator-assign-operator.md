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
ms.openlocfilehash: 8e528bed14f3f6f3b35270975833bdd17fd777db
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422652"
---
# <a name="hstringoperator-operator"></a>HString::Operator= Operator

Przenosi wartość innego **HString** obiekt do bieżącego **HString** obiektu.

## <a name="syntax"></a>Składnia

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Parametry

*other*<br/>
Istniejące **HString** obiektu.

## <a name="remarks"></a>Uwagi

Wartość istniejącego *innych* obiekt jest kopiowany do bieżącego **HString** obiektu, a następnie *innych* niszczony jest obiekt.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HString, klasa](../windows/hstring-class.md)