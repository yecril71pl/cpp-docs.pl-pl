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
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740464"
---
# <a name="uuid-c"></a>uuid (C++)

**Microsoft Specific**

Kompilator dołącza identyfikator GUID do klasy lub struktury zadeklarowanej lub zdefiniowanej (tylko pełne definicje obiektów COM) przy użyciu atrybutu **UUID** .

## <a name="syntax"></a>Składnia

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Uwagi

Atrybut **UUID** przyjmuje ciąg jako argument. Ten ciąg Określa identyfikator GUID w normalnym formacie rejestru z ogranicznikami **{}** lub bez nich. Przykład:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Ten atrybut może być stosowany w ponownej deklaracji. Dzięki temu nagłówki systemowe mogą podawać definicje interfejsów, takich jak `IUnknown`, i ponowna deklaracja w innym nagłówku (na \<przykład comdef. h >), aby podać identyfikator GUID.

Za pomocą słowa kluczowego [__uuidof](../cpp/uuidof-operator.md) można zastosować do pobrania stałego identyfikatora GUID dołączonego do typu zdefiniowanego przez użytkownika.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)