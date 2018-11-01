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
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441357"
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
|Wszystkie|Funkcja wywołania zwrotnego można wykonywać w dowolnym kontekście wątku.|
|Ten sam|Funkcja wywołania zwrotnego można wykonać w kontekście wątku, który uruchomił operację asynchroniczną.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Metadane:** platform.winmd