---
title: HandleT::HandleT, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HandleT::HandleT
dev_langs:
- C++
helpviewer_keywords:
- HandleT, constructor
ms.assetid: 4def6891-7e53-46f1-a197-a80e10744dd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4a932428b274f8ef8fcda88cd48a4d24464e818c
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42597219"
---
# <a name="handlethandlet-constructor"></a>HandleT::HandleT — Konstruktor

Inicjuje nowe wystąpienie klasy **HandleT** klasy.

## <a name="syntax"></a>Składnia

```cpp
explicit HandleT(
   typename HandleTraits::Type h =
      HandleTraits::GetInvalidValue()  
);

HandleT(
   _Inout_ HandleT&& h
);
```

### <a name="parameters"></a>Parametry

*h*  
Dojście.

## <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje **HandleT** obiekt, który nie jest prawidłowy uchwyt do obiektu. Drugi Konstruktor tworzy nową **HandleT** obiektu z parametru *h*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też

[HandleT, klasa](../windows/handlet-class.md)