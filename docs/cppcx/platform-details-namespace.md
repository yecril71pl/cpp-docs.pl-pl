---
title: Platform::details Namespace
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Details
helpviewer_keywords:
- Platform::Details Namespace
ms.assetid: e13c1f93-c823-4f0f-a3ee-2429bfd184db
ms.openlocfilehash: 05677a08b7c63ddbe2196da946d62c00004d8942
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750562"
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

## <a name="see-also"></a>Zobacz także

[Namespace platformy](platform-namespace-c-cx.md)
