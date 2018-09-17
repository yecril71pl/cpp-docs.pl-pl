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
ms.openlocfilehash: 4b6a450d26480a0e89a115efc5731725f8f8b913
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714197"
---
# <a name="badfunctioncall-class"></a>bad_function_call — Klasa

Raporty wywołania funkcji zła.

## <a name="syntax"></a>Składnia

```cpp
class bad_function_call : public std::exception {};
```

## <a name="remarks"></a>Uwagi

Klasa opisuje wyjątek generowany w celu wskazania, że wywołanie `operator()` na [funkcji klasy](../standard-library/function-class.md)
