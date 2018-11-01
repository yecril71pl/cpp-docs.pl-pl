---
title: Platform::ChangedStateException, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: 749e242db37944f0c4dcbfb785028b01a0604f14
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50581682"
---
# <a name="platformchangedstateexception-class"></a>Platform::ChangedStateException, klasa

Element zgłaszany, gdy wewnętrzny stan obiektu zmienił, a tym samym unieważniając wyniki metody.

## <a name="syntax"></a>Składnia

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Uwagi

Przykładem, w którym ten wyjątek jest generowany jest, gdy metody iteratora kolekcji lub tego widoku kolekcji są wywoływane po zmianie kolekcji nadrzędnej, powodując unieważnienie wyniki metody.

Aby uzyskać więcej informacji, zobacz [COMException](../cppcx/platform-comexception-class.md) klasy.

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz też

[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)