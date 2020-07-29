---
title: allocate
ms.date: 11/04/2016
f1_keywords:
- allocate_cpp
helpviewer_keywords:
- __declspec keyword [C++], allocate
- allocate __declspec keyword
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
ms.openlocfilehash: 0bf31423cd76c838cbeffa7458bbccb89592bf43
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227624"
---
# <a name="allocate"></a>allocate

**Specyficzne dla firmy Microsoft**

**`allocate`** Specyfikator deklaracji nazywa segment danych, w którym zostanie przydzielony element danych.

## <a name="syntax"></a>Składnia

> **`__declspec(allocate("`***segname* **`))`** *deklarator*

## <a name="remarks"></a>Uwagi

Nazwa *segname* musi być zadeklarowana przy użyciu jednej z następujących pragm:

- [code_seg](../preprocessor/code-seg.md)

- [const_seg](../preprocessor/const-seg.md)

- [data_seg](../preprocessor/data-seg.md)

- [init_seg](../preprocessor/init-seg.md)

- [Paragraf](../preprocessor/section.md)

## <a name="example"></a>Przykład

```cpp
// allocate.cpp
#pragma section("mycode", read)
__declspec(allocate("mycode"))  int i = 0;

int main() {
}
```

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[`__declspec`](../cpp/declspec.md)<br/>
[Słowa kluczowe](../cpp/keywords-cpp.md)
