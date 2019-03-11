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
ms.openlocfilehash: 79181702c95f8c666b06bdb26319ccb06e55db0a
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749298"
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

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="see-also"></a>Zobacz także

[Platform::COMException, klasa](../cppcx/platform-comexception-class.md)
