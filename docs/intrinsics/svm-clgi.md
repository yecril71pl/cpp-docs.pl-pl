---
title: __svm_clgi
ms.date: 09/02/2019
f1_keywords:
- __svm_clgi
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
ms.openlocfilehash: 740c76e5dcc8f94b9257272624a6ad3c1f9726c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219972"
---
# <a name="__svm_clgi"></a>__svm_clgi

**Microsoft Specific**

Czyści flagę globalnego przerwania.

## <a name="syntax"></a>Składnia

```C
void __svm_clgi( void );
```

## <a name="remarks"></a>Uwagi

Funkcja jest równoważna `CLGI` z instrukcją maszyny. `__svm_clgi` Flaga globalnego przerwania określa, czy mikroprocesor ignoruje, opóźnia lub obsługuje przerwania, ze względu na zdarzenia, takie jak ukończenie operacji we/wy, alert dotyczący temperatury sprzętu lub wyjątek debugowania.

Ta funkcja obsługuje interakcję z monitorem maszyny wirtualnej hosta z systemem operacyjnym gościa i jego aplikacjami. Aby uzyskać więcej informacji, wyszukaj frazę "Volume Architecture — ręczny wolumin 2". Programowanie systemu "w witrynie [AMD Corporation](https://developer.amd.com/resources/developer-guides-manuals/) .

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__svm_clgi`|x86, x64|

**Plik nagłówka** \<intrin. h >

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)\
[__svm_stgi](../intrinsics/svm-stgi.md)
