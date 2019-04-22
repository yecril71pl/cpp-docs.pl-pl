---
title: GetModuleBase — Funkcja
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
ms.openlocfilehash: 4d8c8467b7aeb9c21bf5f4ee19c60e6e60880688
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787127"
---
# <a name="getmodulebase-function"></a>Getmodulebase — funkcja

Pobiera [ModuleBase](modulebase-class.md) wskaźnika, który umożliwia zwiększanie i zmniejszanie licznik odwołań [RuntimeClass](runtimeclass-class.md) obiektu.

## <a name="syntax"></a>Składnia

```cpp
inline Details::ModuleBase* GetModuleBase() throw()
```

## <a name="return-value"></a>Wartość zwracana

Wskaźnik do `ModuleBase` obiektu.

## <a name="remarks"></a>Uwagi

Ta funkcja jest używana wewnętrznie w celu AddRef() liczby odwołań obiektu.

Ta funkcja umożliwia kontrolowanie odwołań, wywołując [ModuleBase::IncrementObjectCount](modulebase-class.md#incrementobjectcount) i [ModuleBase::DecrementObjectCount](modulebase-class.md#decrementobjectcount).

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Zobacz także

[Microsoft::WRL, przestrzeń nazw](microsoft-wrl-namespace.md)