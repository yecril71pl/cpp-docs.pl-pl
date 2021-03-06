---
title: jitintrinsic
ms.date: 11/04/2016
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
ms.openlocfilehash: cecadcad15ee65a44ad5a8245efdb69903c89459
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233707"
---
# <a name="jitintrinsic"></a>jitintrinsic

Oznacza funkcję jako istotną dla 64-bitowego środowiska uruchomieniowego języka wspólnego. Jest on używany w przypadku niektórych funkcji w bibliotekach dostarczonych przez firmę Microsoft.

## <a name="syntax"></a>Składnia

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Uwagi

**`jitintrinsic`** dodaje MODOPT ( <xref:System.Runtime.CompilerServices.IsJitIntrinsic> ) do sygnatury funkcji.

Użytkownicy nie odradzają korzystania z tego **`__declspec`** modyfikatora, ponieważ mogą wystąpić nieoczekiwane wyniki.

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
