---
title: __readgsbyte, __readgsdword, __readgsqword, __readgsword
ms.date: 11/04/2016
f1_keywords:
- __readgsbyte
- __readgsdword
- __readgsqword
- __readgsword
helpviewer_keywords:
- __readgsword intrinsic
- __readgsdword intrinsic
- __readgsqword intrinsic
- __readgsbyte intrinsic
ms.assetid: f822632d-854c-4558-a71b-cdfc3eea2236
ms.openlocfilehash: 1bc6a3b2ef2d78e5b30ea36149ea691468c9b0ec
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327515"
---
# <a name="readgsbyte-readgsdword-readgsqword-readgsword"></a>__readgsbyte, __readgsdword, __readgsqword, __readgsword

**Microsoft Specific**

Odczyt pamięci z lokalizacji określonej przez przesunięcie względem początku segmentu GS.

## <a name="syntax"></a>Składnia

```
unsigned char __readgsbyte(
   unsigned long Offset
);
unsigned short __readgsword(
   unsigned long Offset
);
unsigned long __readgsdword(
   unsigned long Offset
);
unsigned __int64 __readgsqword(
   unsigned long Offset
);
```

#### <a name="parameters"></a>Parametry

*Przesunięcie*<br/>
[in] Przesunięcie od początku `GS` do odczytu.

## <a name="return-value"></a>Wartość zwracana

Zawartość pamięci bajt, wyraz, podwójne słowo lub quadword (co zostało wskazane przez nazwę funkcji o nazwie) w lokalizacji `GS:[Offset]`.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__readgsbyte`|X64|
|`__readgsdword`|X64|
|`__readgsqword`|X64|
|`__readgsword`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Te funkcje wewnętrzne są dostępne tylko w trybie jądra i procedury są dostępne tylko jako funkcje wewnętrzne.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[__writegsbyte, \__writegsdword, \__writegsqword, \__writegsword](../intrinsics/writegsbyte-writegsdword-writegsqword-writegsword.md)<br/>
[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)