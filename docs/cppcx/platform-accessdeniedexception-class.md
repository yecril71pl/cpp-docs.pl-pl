---
title: Platform::AccessDeniedException, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::AccessDeniedException
- VCCORLIB/Platform::AccessDeniedException::AccessDeniedException
helpviewer_keywords:
- Platform::AccessDeniedException
ms.assetid: 6ae2155b-7b16-4587-8d2d-da05eab4c7e9
ms.openlocfilehash: 4865492e3b5d8e4acc35e58081a226c9e66ed99f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588152"
---
# <a name="platformaccessdeniedexception-class"></a>Platform::AccessDeniedException, klasa

Zgłoszone podczas dostępu do zasobu lub funkcji jest zabroniony.

## <a name="syntax"></a>Składnia

```cpp
public ref class AccessDeniedException : COMException,    IException,    IPrintable,   IEquatable
```

### <a name="remarks"></a>Uwagi

Jeśli napotkasz ten wyjątek, upewnij się, że żądana odpowiednia możliwość i wprowadzone wymagane deklaracji w manifeście pakietu aplikacji. Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz też

[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)