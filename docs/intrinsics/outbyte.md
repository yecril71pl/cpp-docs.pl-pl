---
title: __outbyte
ms.date: 09/02/2019
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: 18792010c45ffb648e9555ccb73f8614c3e3e6ea
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217198"
---
# <a name="__outbyte"></a>__outbyte

**Microsoft Specific**

Generuje instrukcję, która wysyła 1 bajt określony przez `Data` port we/wy określony przez `Port`. `out`

## <a name="syntax"></a>Składnia

```C
void __outbyte(
   unsigned short Port,
   unsigned char Data
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, do którego mają zostać wysłane dane.

*Data*\
podczas Bajt, który ma zostać wysłany przez określony port.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__outbyte`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
