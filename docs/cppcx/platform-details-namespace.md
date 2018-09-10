---
title: Platform::details Namespace | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Details
dev_langs:
- C++
helpviewer_keywords:
- Platform::Details Namespace
ms.assetid: e13c1f93-c823-4f0f-a3ee-2429bfd184db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20f491d0dde585a6561dc36191e43f1a5d1e9354
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108287"
---
# <a name="platformdetails-namespace"></a>Platform::details Namespace

Ta przestrzeń nazw jest przeznaczona wyłącznie do użytku wewnętrznego i nie jest przeznaczona do użycia na potrzeby programowania.

## <a name="syntax"></a>Składnia

```cpp
namespace Platform {
   namespace Details {
}}
```

### <a name="members"></a>Elementy członkowskie

Chociaż ta przestrzeń nazw jest przeznaczony do użytku wewnętrznego, przeglądarki można wyświetlić następujące elementy członkowskie tej przestrzeni nazw.

|Nazwa|Uwagi|
|----------|------------|
|Konsola|Klasa. Wyświetla dane wyjściowe w testach jednostkowych.|
|_GUID|Struct|
|Sterty|Class|
|HeapAllocationTrackingLevel|Wyliczenie|
|HeapEntryHandler|Delegate|
|IActivationFactory|Interface|
|IAgileObject|Interface|
|IClassFactory|Interface|
|IEquatable|Interface|
|IPrintable|Interface|
|IWeakReference|Interface|
|IWeakReferenceSource|Interface|

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`Platform`

### <a name="requirements"></a>Wymagania

**Metadane:** platform.winmd

**Namespace:** Platform::Details

## <a name="see-also"></a>Zobacz też

[Namespace platformy](platform-namespace-c-cx.md)