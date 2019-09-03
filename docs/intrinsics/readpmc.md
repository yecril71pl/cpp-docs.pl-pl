---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221036"
---
# <a name="__readpmc"></a>__readpmc

**Microsoft Specific**

Generuje instrukcję, która odczytuje licznik monitorowania wydajności określony przez licznik. `rdpmc`

## <a name="syntax"></a>Składnia

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>Parametry

*przeciw*\
podczas Licznik wydajności, który ma zostać odczytany.

## <a name="return-value"></a>Wartość zwracana

Wartość określonego licznika wydajności.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Element wewnętrzny jest dostępny tylko w trybie jądra, a procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
