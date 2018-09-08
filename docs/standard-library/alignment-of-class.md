---
title: alignment_of — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::alignment_of
dev_langs:
- C++
helpviewer_keywords:
- alignment_of class
- alignment_of
ms.assetid: 4141c59a-f94e-41c4-93fd-9ea578b27387
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0089d190b28489d2274df2209890bc3a391b6f66
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103856"
---
# <a name="alignmentof-class"></a>alignment_of — Klasa

Pobiera wyrównanie określonego typu. Ta struktura jest zaimplementowana w [alignof](../cpp/alignof-and-alignas-cpp.md). Użyj `alignof` bezpośrednio po prostu konieczność wartość wyrównania zapytania. Alignment_of — należy używać wtedy, gdy konieczne stałą całkowitą, na przykład podczas wysyłania tagu.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct alignment_of;
```

### <a name="parameters"></a>Parametry

*Ty*<br/>
Typ do zapytania.

## <a name="remarks"></a>Uwagi

Zapytanie typu przechowuje wartość wyrównanie typu *Ty*.

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** standardowe

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
[aligned_storage, klasa](../standard-library/aligned-storage-class.md)<br/>
