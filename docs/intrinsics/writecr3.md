---
title: __writecr3
ms.date: 11/04/2016
f1_keywords:
- _writecr3
helpviewer_keywords:
- _writecr3 intrinsic
ms.assetid: 959d49fa-69d5-47cf-88d2-7688367fe38f
ms.openlocfilehash: ede5e08d5bbf2807597eec3c7569bc9a6166518d
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51332026"
---
# <a name="writecr3"></a>__writecr3

**Microsoft Specific**

Zapisuje wartość `Data` do rejestru przedsiębiorstw CR3.

## <a name="syntax"></a>Składnia

```
void writecr3(
   unsigned __int64 Data
);
```

#### <a name="parameters"></a>Parametry

*Dane*<br/>
[in] Wartość do zapisu do rejestru przedsiębiorstw CR3.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writecr3`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)