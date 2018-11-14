---
title: __writefsbyte __writefsdword, __writefsqword, __writefsword
ms.date: 11/04/2016
f1_keywords:
- __writefsword
- __writefsbyte
- __writefsqword
- __writefsdword
helpviewer_keywords:
- writefsbyte intrinsic
- __writefsword intrinsic
- writefsqword intrinsic
- writefsdword intrinsic
- __writefsdword intrinsic
- __writefsqword intrinsic
- __writefsbyte intrinsic
- writefsword intrinsic
ms.assetid: 23ac6e8e-bc91-4e90-a4c6-da02993637ad
ms.openlocfilehash: 26322b210105f694be764418d9e0b77a0d419844
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328490"
---
# <a name="writefsbyte-writefsdword-writefsqword-writefsword"></a>__writefsbyte __writefsdword, __writefsqword, __writefsword

**Microsoft Specific**

Napisz pamięci w lokalizacji określonej przez przesunięcie względem początku segmentu FS.

## <a name="syntax"></a>Składnia

```
void __writefsbyte(
   unsigned long Offset,
   unsigned char Data
);
void __writefsword(
   unsigned long Offset,
   unsigned short Data
);
void __writefsdword(
   unsigned long Offset,
   unsigned long Data
);
void __writefsqword(
   unsigned long Offset,
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Przesunięcie*<br/>
[in] Przesunięcie od początku FS do zapisu.

*Dane*<br/>
[in] Wartość do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writefsbyte`|x86|
|`__writefsword`|x86|
|`__writefsdword`|x86|
|`__writefsqword`|x86|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Te procedury są dostępne tylko jako funkcje wewnętrzne.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[__readfsbyte, \__readfsdword, \__readfsqword, \__readfsword](../intrinsics/readfsbyte-readfsdword-readfsqword-readfsword.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)