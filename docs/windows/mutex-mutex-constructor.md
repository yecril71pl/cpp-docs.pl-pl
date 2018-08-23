---
title: Mutex::mutex, Konstruktor | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::Mutex::Mutex
dev_langs:
- C++
helpviewer_keywords:
- Mutex, constructor
ms.assetid: 504afcdc-775a-4c98-a06f-4fb4663eba3f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 62a1fc796188c38dfbd3aff004eba15b7e30ea89
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42600508"
---
# <a name="mutexmutex-constructor"></a>Mutex::Mutex — Konstruktor

Inicjuje nowe wystąpienie klasy **Mutex** klasy.

## <a name="syntax"></a>Składnia

```cpp
explicit Mutex(
   HANDLE h
);

Mutex(
   _Inout_ Mutex&& h
);
```

### <a name="parameters"></a>Parametry

*h*  
Dojście lub odwołanie rvalue do uchwytu, aby **Mutex** obiektu.

## <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje **Mutex** obiekt z określonego dojścia. Drugi Konstruktor inicjuje **Mutex** obiektu z określonego dojścia, a następnie przenosi własności obiektu mutex do bieżącego **Mutex** obiektu.

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="see-also"></a>Zobacz też
[Mutex — klasa](../windows/mutex-class1.md)