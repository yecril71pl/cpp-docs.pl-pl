---
title: Platform::WrongThreadException, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
ms.openlocfilehash: dde8c9afff6be083580042a958f59e057bc44350
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743955"
---
# <a name="platformwrongthreadexception-class"></a>Platform::WrongThreadException, klasa

Element zgłaszany, gdy wątek wywołuje za pomocą wskaźnika interfejsu dla obiektu serwera proxy, który nie należy do komórka wątku.

## <a name="syntax"></a>Składnia

```cpp
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md).

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz także

[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)
