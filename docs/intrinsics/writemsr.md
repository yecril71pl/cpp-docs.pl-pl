---
title: __writemsr
ms.date: 11/04/2016
f1_keywords:
- __writemsr
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
ms.openlocfilehash: f4af272ccafec9789497d0321c0769c2906f76b7
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330297"
---
# <a name="writemsr"></a>__writemsr

**Microsoft Specific**

Generuje zapisu, można zarejestrować określonego modelu (`wrmsr`) instrukcji.

## <a name="syntax"></a>Składnia

```
void __writemsr(
   unsigned long Register,
   unsigned __int64 Value
);
```

#### <a name="parameters"></a>Parametry

*Zarejestruj się*<br/>
[in] Rejestr określonego modelu.

*Wartość*<br/>
[in] Wartość do zapisania.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__writemsr`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Ta funkcja może być używana tylko w trybie jądra, a ta procedura jest dostępna jako funkcja wewnętrzna wyłącznie.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)