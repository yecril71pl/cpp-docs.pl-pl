---
title: __outbytestring
ms.date: 09/02/2019
f1_keywords:
- __outbytestring
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
ms.openlocfilehash: 31caf17db5d56efccd6b30200994b1080356b4c1
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217173"
---
# <a name="__outbytestring"></a>__outbytestring

**Microsoft Specific**

Generuje instrukcję, która wysyła pierwsze `Count` bajty danych wskazywane przez `Buffer` port określony przez `Port`. `rep outsb`

## <a name="syntax"></a>Składnia

```C
void __outbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, do którego mają zostać wysłane dane.

*Buforu*\
podczas Dane, które mają zostać wysłane przez określony port.

*Liczbą*\
podczas Liczba bajtów danych do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
