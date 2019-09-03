---
title: __outdword
ms.date: 09/02/2019
f1_keywords:
- __outdword
helpviewer_keywords:
- out instruction
- outdword instruction
- __outdword intrinsic
ms.assetid: ed1e4994-a84b-4759-8bf9-cd48fb073f4d
ms.openlocfilehash: ce1358e7cef0136ccf7d314038d06d271916e0bc
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221657"
---
# <a name="__outdword"></a>__outdword

**Microsoft Specific**

Generuje instrukcję do wysłania DoubleWord *danych* z portu portu. `out`

## <a name="syntax"></a>Składnia

```C
void __outdword(
   unsigned short Port,
   unsigned long Data
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, do którego mają zostać wysłane dane.

*Data*\
podczas DoubleWord do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__outdword`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
