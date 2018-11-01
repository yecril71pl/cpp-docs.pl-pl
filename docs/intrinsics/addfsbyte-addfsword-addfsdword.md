---
title: __addfsbyte, __addfsword, __addfsdword
ms.date: 11/04/2016
f1_keywords:
- __addfsbyte_cpp
- __addfsdword
- __addfsword_cpp
- __addfsbyte
- __addfsword
- __addfsdword_cpp
helpviewer_keywords:
- __addfsdword intrinsic
- __addfsword intrinsic
- __addfsbyte intrinsic
ms.assetid: 706c70df-6b52-4401-9268-2977ed8ad715
ms.openlocfilehash: ccbf604b13db3d40b8ee62c18db1a71e615c79ea
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505407"
---
# <a name="addfsbyte-addfsword-addfsdword"></a>__addfsbyte, __addfsword, __addfsdword

**Microsoft Specific**

Dodaj wartość do lokalizacji w pamięci określonej przez przesunięcie względem początku `FS` segmentu.

## <a name="syntax"></a>Składnia

```
void __addfsbyte( 
   unsigned long Offset, 
   unsigned char Data 
);
void __addfsword( 
   unsigned long Offset, 
   unsigned short Data 
);
void __addfsdword( 
   unsigned long Offset, 
   unsigned long Data 
);
```

#### <a name="parameters"></a>Parametry

*Przesunięcie*<br/>
[in] Przesunięcie od początku `FS`.

*Dane*<br/>
[in] Wartość do dodania do lokalizacji w pamięci.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__addfsbyte`|x86|
|`__addfsword`|x86|
|`__addfsdword`|x86|

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako funkcje wewnętrzne.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[__incfsbyte, \__incfsword, \__incfsdword](../intrinsics/incfsbyte-incfsword-incfsdword.md)<br/>
[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[__writefsbyte, \__writefsdword, \__writefsqword, \__writefsword](../intrinsics/writefsbyte-writefsdword-writefsqword-writefsword.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)