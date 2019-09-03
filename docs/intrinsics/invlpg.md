---
title: __invlpg
ms.date: 09/02/2019
f1_keywords:
- __invlpg
- __invlpg_cpp
helpviewer_keywords:
- invlpg instruction
- __invlpg intrinsic
ms.assetid: 3fb3633f-d9b7-4ec0-9e7f-a7f2fa8ed794
ms.openlocfilehash: ba8bd81498f805992336b0dc4163fe18fa157a2c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221899"
---
# <a name="__invlpg"></a>__invlpg

**Microsoft Specific**

Generuje instrukcję x86 `invlpg` , która unieważnia bufor tłumaczenia referencyjna (TLB) dla strony skojarzonej z pamięcią wskazywaną przez *adres*.

## <a name="syntax"></a>Składnia

```C
void __invlpg(
   void* Address
);
```

### <a name="parameters"></a>Parametry

*Ulica*\
podczas Adres 64-bitowy.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__invlpg`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Wewnętrznie `__invlpg` emituje uprzywilejowaną instrukcję i jest dostępna tylko w trybie jądra z poziomem uprawnień (CPL) równym 0.

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
