---
title: __writecr8
ms.date: 11/04/2016
f1_keywords:
- _writecr8
helpviewer_keywords:
- _writecr8 intrinsic
ms.assetid: 6f8bd632-dddb-4335-971e-1acee24aa2b9
ms.openlocfilehash: 1a7b31ed7e370c4dd3fee9e5a205be6e34ba560b
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51325787"
---
# <a name="writecr8"></a>__writecr8

**Microsoft Specific**

Zapisuje wartość `Data` do rejestru CR8.

## <a name="syntax"></a>Składnia

```
void writecr8(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Dane*<br/>
[in] Wartość do zapisu do rejestru CR8.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writecr8`|X64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)