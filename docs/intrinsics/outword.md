---
title: __outword
ms.date: 11/04/2016
f1_keywords:
- __outword
helpviewer_keywords:
- __outword intrinsic
- out instruction
ms.assetid: 995f8834-0f50-4b4f-a7a2-af0e7c371cda
ms.openlocfilehash: 8a34dfe8bfaedf8f6df5e6f26015eeccd67ed957
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332013"
---
# <a name="outword"></a>__outword

**Microsoft Specific**

Generuje `out` instrukcji, który wysyła słowo `Data` z portu We/Wy, określony przez `Port`.

## <a name="syntax"></a>Składnia

```
void __outword(
   unsigned short Port,
   unsigned short Data
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do wysyłania danych do.

*Dane*<br/>
[in] Dane do wysłania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__outword`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)