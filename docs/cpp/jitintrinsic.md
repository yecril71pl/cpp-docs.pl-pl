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
ms.openlocfilehash: 9e726413f0bbfbd9d6affa348777c995c51283a5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245521"
---
# <a name="jitintrinsic"></a>jitintrinsic

Oznacza funkcję jako istotny dla 64-bitowe środowisko uruchomieniowe języka wspólnego. Jest on używany w przypadku pewnych funkcji w bibliotekach udostępnionych przez firmę Microsoft.

## <a name="syntax"></a>Składnia

```
__declspec(jitintrinsic)
```

## <a name="remarks"></a>Uwagi

**jitintrinsic** dodaje MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) do sygnatury funkcji.

Użytkownicy są odradzane ze za pomocą tego **__declspec** modyfikator, jako nieoczekiwane wyniki mogą wystąpić.

## <a name="see-also"></a>Zobacz także

[__declspec](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)