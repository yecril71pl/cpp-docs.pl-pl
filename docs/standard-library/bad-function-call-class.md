---
title: bad_function_call — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- functional/std::bad_function_call
dev_langs:
- C++
helpviewer_keywords:
- bad_function_call class
ms.assetid: b70a0268-43ff-4f3b-a283-faf1cb172d4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5e00dd485478a5a6fb7ff029afdad7bf7212fd56
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33839949"
---
# <a name="badfunctioncall-class"></a>bad_function_call — Klasa

Raporty wywołanie funkcji uszkodzone.

## <a name="syntax"></a>Składnia

```cpp
class bad_function_call
 : public std::exception {
 };
```

## <a name="remarks"></a>Uwagi

Klasa opisuje wyjątek, aby wskazać, że wywołanie `operator()` na [funkcji klasy](../standard-library/function-class.md)
