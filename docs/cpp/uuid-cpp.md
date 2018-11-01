---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: c121ad99dfbe0021a263f324ccdb9a95441bba33
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50511660"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft Specific**

Kompilator dołącza identyfikator GUID do klasy lub struktury zadeklarowane lub zdefiniowane (pełna COM definicje obiektów tylko) za pomocą **uuid** atrybutu.

## <a name="syntax"></a>Składnia

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Uwagi

**Uuid** atrybut przyjmuje ciąg jako argumentem. Ten ciąg nazwy identyfikatora GUID w formacie normalne rejestru z lub bez **{}** ograniczników. Na przykład:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Ten atrybut można stosować w ponowna deklaracja. Dzięki temu nagłówki systemu, aby dostarczyć definicje interfejsów, takich jak `IUnknown`i ponowna deklaracja niektórych innych nagłówka (takie jak \<comdef.h >) umożliwiają określanie wartości identyfikatora GUID.

Słowo kluczowe [__uuidof](../cpp/uuidof-operator.md) mogą być stosowane do pobrania — stała identyfikator GUID jest dołączony do typu zdefiniowanego przez użytkownika.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)