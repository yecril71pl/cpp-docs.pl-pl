---
title: __outbytestring | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbytestring
dev_langs:
- C++
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7ef1bb6e4804fc71531f694a3dac4c5504941bf0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393766"
---
# <a name="outbytestring"></a>__outbytestring

**Microsoft Specific**

Generuje `rep outsb` instrukcji, która wysyła pierwszy `Count` bajtów danych wskazywanego przez `Buffer` port określony przez `Port`.

## <a name="syntax"></a>Składnia

```
void __outbytestring( 
   unsigned short Port, 
   unsigned char* Buffer, 
   unsigned long Count 
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do wysyłania danych do.

*Bufor*<br/>
[in] Dane, które zostaną wysłane do określonego portu.

*Liczba*<br/>
[in] Liczba bajtów danych do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__outbytestring`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)