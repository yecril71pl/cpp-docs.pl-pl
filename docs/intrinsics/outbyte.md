---
title: __outbyte
ms.date: 11/04/2016
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: fa17e4859e861a9be46b4ad32b7ad090f6c3dbc6
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326553"
---
# <a name="outbyte"></a>__outbyte

**Microsoft Specific**

Generuje `out` instrukcji, która wysyła 1 bajt określony przez `Data` z portu We/Wy, określony przez `Port`.

## <a name="syntax"></a>Składnia

```
void __outbyte(
   unsigned short Port,
   unsigned char Data
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port do wysyłania danych do.

*Dane*<br/>
[in] Bajtów, które zostaną wysłane do określonego portu.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__outbyte`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta procedura jest dostępna wyłącznie jako wewnętrzna.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)