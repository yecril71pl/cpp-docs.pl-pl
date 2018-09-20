---
title: HandleT::operator = — Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::operator=
dev_langs:
- C++
helpviewer_keywords:
- operator= operator
ms.assetid: 9e42dcca-30fa-4e8b-8954-802fd64a5595
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4c6aeca188f51f35c739c32f5290aac011781b41
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396899"
---
# <a name="handletoperator-operator"></a>HandleT::operator= Operator

Przenosi wartość określonego **HandleT** obiekt do bieżącego **HandleT** obiektu.

## <a name="syntax"></a>Składnia

```cpp
HandleT& operator=(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*<br/>
Odwołanie rvalue do uchwytu.

## <a name="return-value"></a>Wartość zwracana

Odwołanie do bieżącego **HandleT** obiektu.

## <a name="remarks"></a>Uwagi

Ta operacja powoduje unieważnienie **HandleT** obiekt określony przez parametr *h*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HandleT, klasa](../windows/handlet-class.md)