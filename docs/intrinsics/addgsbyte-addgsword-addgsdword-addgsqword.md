---
title: __addgsbyte, __addgsword, __addgsdword, __addgsqword
ms.date: 09/02/2019
f1_keywords:
- __addgsdword
- __addgsqword
- __addgsword_cpp
- __addgsword
- __addgsbyte_cpp
- __addgsqword_cpp
- __addgsbyte
- __addgsdword_cpp
helpviewer_keywords:
- __addgsword intrinsic
- __addgsqword intrinsic
- __addgsdword intrinsic
- __addgsbyte intrinsic
ms.assetid: 4fa03e69-d849-49ed-ba37-1d3aa23c2a21
ms.openlocfilehash: 5dddd8b4a887dc0e01107f8c1036a399b4e52d2e
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221082"
---
# <a name="__addgsbyte-__addgsword-__addgsdword-__addgsqword"></a>__addgsbyte, __addgsword, __addgsdword, __addgsqword

**Microsoft Specific**

Dodaj wartość do lokalizacji pamięci określonej przez przesunięcie względem początku `GS` segmentu.

## <a name="syntax"></a>Składnia

```C
void __addgsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __addgsword(
   unsigned long Offset,
   unsigned short Data
);
void __addgsdword(
   unsigned long Offset,
   unsigned long Data
);
void __addgsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

### <a name="parameters"></a>Parametry

*Przesunięcie*\
podczas Przesunięcie od początku `GS`.

*Data*\
podczas Wartość, która ma zostać dodana do lokalizacji pamięci.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__addgsbyte`|X64|
|`__addgsword`|X64|
|`__addgsdword`|X64|
|`__addgsqword`|X64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako wewnętrznie.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[__incgsbyte, \__incgsword, \__incgsdword, \__incgsqword](../intrinsics/incgsbyte-incgsword-incgsdword-incgsqword.md)\
[__readgsbyte, \__readgsdword, \__readgsqword, \__readgsword](../intrinsics/readgsbyte-readgsdword-readgsqword-readgsword.md)\
[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)\
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
