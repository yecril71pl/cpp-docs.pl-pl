---
title: __svm_stgi
ms.date: 09/02/2019
f1_keywords:
- __svm_stgi
helpviewer_keywords:
- __svm_stgi intrinsic
- STGI instruction
ms.assetid: 96488da4-5587-4e99-8674-627a9e51be84
ms.openlocfilehash: 6bd731951b440d3d2597d54c9a52d9f8640a5c5f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219836"
---
# <a name="__svm_stgi"></a>__svm_stgi

**Microsoft Specific**

Ustawia flagę globalnego przerwania.

## <a name="syntax"></a>Składnia

```C
void __svm_stgi(void);
```

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `STGI` z instrukcją maszyny. `__svm_stgi` Flaga globalnego przerwania określa, czy mikroprocesor ignoruje, opóźnia lub obsługuje przerwania, ze względu na zdarzenia, takie jak ukończenie operacji we/wy, alert dotyczący temperatury sprzętu lub wyjątek debugowania.

Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, wyszukaj frazę "Volume Architecture — ręczny wolumin 2". Programowanie systemu "w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_stgi`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__svm_clgi](../intrinsics/svm-clgi.md)
