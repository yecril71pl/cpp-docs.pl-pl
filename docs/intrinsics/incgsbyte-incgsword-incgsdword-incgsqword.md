---
title: __incgsbyte, __incgsword, __incgsdword, __incgsqword
ms.date: 09/02/2019
f1_keywords:
- __incgsdword
- __incgsqword_cpp
- __incgsword_cpp
- __incgsword
- __incgsbyte
- __incgsbyte_cpp
- __incgsqword
- __incgsdword_cpp
helpviewer_keywords:
- __incgsbyte intrinsic
- __incgsword intrinsic
- __incgsqword intrinsic
- __incgsdword intrinsic
ms.assetid: 06bfdf4f-7643-4fe0-8455-60ce3068073e
ms.openlocfilehash: 8b4e88b4ccd2cf1d2a3130e3a535de1c9a434320
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217792"
---
# <a name="__incgsbyte-__incgsword-__incgsdword-__incgsqword"></a>__incgsbyte, __incgsword, __incgsdword, __incgsqword

**Microsoft Specific**

Dodaj jeden do wartości w lokalizacji pamięci określonej przez przesunięcie względem początku `GS` segmentu.

## <a name="syntax"></a>Składnia

```C
void __incgsbyte(
   unsigned long Offset
);
void __incgsword(
   unsigned long Offset
);
void __incgsdword(
   unsigned long Offset
);
void __incgsqword(
   unsigned long Offset
);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
podczas Przesunięcie od początku `GS`.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__incgsbyte`|X64|
|`__incgsword`|X64|
|`__incgsdword`|X64|
|`__incgsqword`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako wewnętrznie.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[\__addgsbyte, \__addgsword, \__addgsdword, \__addgsqword](../intrinsics/addgsbyte-addgsword-addgsdword-addgsqword.md)\
[\__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[\__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
