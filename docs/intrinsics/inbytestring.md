---
title: __inbytestring
ms.date: 09/02/2019
f1_keywords:
- __inbytestring
- __inbytestring_cpp
helpviewer_keywords:
- rep insb instruction
- __inbytestring intrinsic
ms.assetid: fe549556-e7a3-4af3-8ebf-8a7dc3cb233b
ms.openlocfilehash: cb6e811c809c6069c47415e87804641f30a3897b
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2019
ms.locfileid: "70217815"
---
# <a name="__inbytestring"></a>__inbytestring

**Microsoft Specific**

Odczytuje dane z określonego portu przy użyciu `rep insb` instrukcji.

## <a name="syntax"></a>Składnia

```C
void __inbytestring(
   unsigned short Port,
   unsigned char* Buffer,
   unsigned long Count
);
```

### <a name="parameters"></a>Parametry

*Przewożąc*\
podczas Port, z którego ma zostać odczytany.

*Buforu*\
określoną Dane odczytane z portu są zapisywane w tym miejscu.

*Liczbą*\
podczas Liczba bajtów danych do odczytania.

## <a name="requirements"></a>Wymagania

|Wewnętrznej|Architektura|
|---------------|------------------|
|`__inbytestring`|x86, x64|

**Plik nagłówka** \<intrin. h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna tylko jako wewnętrzna.

**ZAKOŃCZENIE określonych przez firmę Microsoft**

## <a name="see-also"></a>Zobacz także

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)
