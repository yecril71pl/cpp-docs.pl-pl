---
title: __writecr0
ms.date: 11/04/2016
f1_keywords:
- _writecr0
helpviewer_keywords:
- _writecr0 intrinsic
ms.assetid: a143d08d-0333-4e1b-91b4-4acb2ae91b5a
ms.openlocfilehash: cdc93f178f033b072cad68180dfee305d9bf62a5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330531"
---
# <a name="writecr0"></a>__writecr0

**Microsoft Specific**

Zapisuje wartość `Data` do rejestru CR0.

## <a name="syntax"></a>Składnia

```
void writecr0(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Dane*<br/>
[in] Wartość do zapisu do rejestru CR0.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writecr0`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)