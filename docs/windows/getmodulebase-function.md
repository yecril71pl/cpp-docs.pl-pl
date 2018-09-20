---
title: GetModuleBase, funkcja | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::GetModuleBase
dev_langs:
- C++
ms.assetid: 123d3b14-2eaf-4e02-8dcd-b6567917c6a6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4d460b006d2d17df308a62c0433621aac7008f4d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411420"
---
# <a name="getmodulebase-function"></a>GetModuleBase — Funkcja
Pobiera [ModuleBase](../windows/modulebase-class.md) wskaźnika, który umożliwia zwiększanie i zmniejszanie licznik odwołań [RuntimeClass](../windows/runtimeclass-class.md) obiektu.
  
## <a name="syntax"></a>Składnia
  
```cpp
inline Details::ModuleBase* GetModuleBase() throw()  
```
  
## <a name="return-value"></a>Wartość zwracana

Wskaźnik do `ModuleBase` obiektu.
  
## <a name="remarks"></a>Uwagi

Ta funkcja jest używana wewnętrznie w celu AddRef() liczby odwołań obiektu.
  
Ta funkcja umożliwia kontrolowanie odwołań, wywołując [ModuleBase::IncrementObjectCount](../windows/modulebase-incrementobjectcount-method.md) i [ModuleBase::DecrementObjectCount](../windows/modulebase-decrementobjectcount-method.md).
  
## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h
  
**Namespace:** Microsoft::WRL
  
## <a name="see-also"></a>Zobacz też

[Microsoft::WRL, przestrzeń nazw](../windows/microsoft-wrl-namespace.md)