---
title: __writecr4
ms.date: 11/04/2016
f1_keywords:
- _writecr4
helpviewer_keywords:
- _writecr4 intrinsic
ms.assetid: ab7651d7-b86b-4be7-a0a0-7263099c70fc
ms.openlocfilehash: 37bdde20b6d0fe1079969677250ce59acedf51ec
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328646"
---
# <a name="writecr4"></a>__writecr4

**Microsoft Specific**

Zapisuje wartość `Data` do rejestru CR4.

## <a name="syntax"></a>Składnia

```
void writecr4(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Dane*<br/>
[in] Wartość do zapisu do rejestru CR4.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writecr4`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)