---
title: uuid (C++)
ms.date: 11/04/2016
f1_keywords:
- uuid_cpp
helpviewer_keywords:
- __declspec keyword [C++], uuid
- uuid __declspec keyword
ms.assetid: 9d004621-09bc-4a8d-871b-648f5d5102d7
ms.openlocfilehash: f775820fe7f84c5081a213ca9ecb07d617716a9d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226987"
---
# <a name="uuid-c"></a>uuid (C++)

**Specyficzne dla firmy Microsoft**

Kompilator dołącza identyfikator GUID do klasy lub struktury zadeklarowanej lub zdefiniowanej (tylko pełne definicje obiektów COM) z **`uuid`** atrybutem.

## <a name="syntax"></a>Składnia

```
__declspec( uuid("ComObjectGUID") ) declarator
```

## <a name="remarks"></a>Uwagi

**`uuid`** Atrybut przyjmuje ciąg jako argument. Ten ciąg Określa identyfikator GUID w normalnym formacie rejestru z ogranicznikami **{}** lub bez nich. Na przykład:

```cpp
struct __declspec(uuid("00000000-0000-0000-c000-000000000046")) IUnknown;
struct __declspec(uuid("{00020400-0000-0000-c000-000000000046}")) IDispatch;
```

Ten atrybut może być stosowany w ponownej deklaracji. Dzięki temu nagłówki systemowe mogą podawać definicje interfejsów, takich jak `IUnknown` , oraz ponowną deklarację w innym nagłówku (na przykład \<comdef.h> ) w celu dostarczenia identyfikatora GUID.

Za pomocą słowa kluczowego [__uuidof](../cpp/uuidof-operator.md) można zastosować do pobrania stałego identyfikatora GUID dołączonego do typu zdefiniowanego przez użytkownika.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
