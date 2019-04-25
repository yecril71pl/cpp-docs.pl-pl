---
title: Platform::CallbackContext, wyliczenie
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 7f4e020ab0b1e377456c27d3b4666e15b5a4f7a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161683"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::CallbackContext, wyliczenie

Określa kontekst wątku, w którym wykonuje funkcję wywołania zwrotnego (program obsługi zdarzeń).

## <a name="syntax"></a>Składnia

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Elementy członkowskie

|Kod typu|Opis|
|---------------|-----------------|
|Dowolne|Funkcja wywołania zwrotnego można wykonywać w dowolnym kontekście wątku.|
|Ten sam|Funkcja wywołania zwrotnego można wykonać w kontekście wątku, który uruchomił operację asynchroniczną.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd