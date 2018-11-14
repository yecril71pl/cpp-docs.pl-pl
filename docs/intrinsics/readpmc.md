---
title: __readpmc
ms.date: 11/04/2016
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: 059d9344fa329e69666abaca4d73122ab29f8d2a
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326436"
---
# <a name="readpmc"></a>__readpmc

**Microsoft Specific**

Generuje `rdpmc` instrukcji, które odczytuje monitorowania określony przez licznik wydajności `counter`.

## <a name="syntax"></a>Składnia

```
unsigned __int64 __readpmc(
   unsigned long counter
);
```

#### <a name="parameters"></a>Parametry

*Licznik*<br/>
[in] Licznik wydajności do odczytu.

## <a name="return-value"></a>Wartość zwracana

Wartość licznika wydajności określony.

## <a name="requirements"></a>Wymagania

|Wewnętrzne|Architektura|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Plik nagłówkowy** \<intrin.h >

## <a name="remarks"></a>Uwagi

Tym wewnętrzna jest dostępna tylko w trybie jądra, a procedura jest dostępna jako funkcja wewnętrzna tylko.

**END specyficzny dla Microsoft**

## <a name="see-also"></a>Zobacz też

[Funkcje wewnętrzne kompilatora](../intrinsics/compiler-intrinsics.md)