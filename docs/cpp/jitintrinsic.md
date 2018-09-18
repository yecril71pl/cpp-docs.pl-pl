---
title: jitintrinsic | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 888ec19eaedf881fed97a14a7f3f8b5ee673ce7a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46056290"
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