---
title: Metoda platform::RecreateException
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 9e167efc54352d125e849956a2da8d8e8cad4ed6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330326"
---
# <a name="platformrecreateexception-method"></a>Metoda platform::ReCreateException

Ta metoda jest tylko do użytku wewnętrznego i nie jest przeznaczony dla kodu użytkownika. Zamiast tego użyj metody Exception::CreateException.

## <a name="syntax"></a>Składnia

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Parametry

*godz.*

### <a name="property-valuereturn-value"></a>Wartość właściwości/Zwracana wartość

Zwraca nowy Platform::Exception ^ zgodnie z określonym HRESULT.
