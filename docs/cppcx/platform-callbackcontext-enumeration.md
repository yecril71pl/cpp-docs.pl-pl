---
title: 'Platform:: CallbackContext, Wyliczenie'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 1daa3988fcb985dab9d3083233a3703a20cc2fdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214282"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform:: CallbackContext, Wyliczenie

Określa kontekst wątku, w którym jest wykonywana funkcja wywołania zwrotnego (procedura obsługi zdarzeń).

## <a name="syntax"></a>Składnia

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Members

|Kod typu|Opis|
|---------------|-----------------|
|Dowolne|Funkcja wywołania zwrotnego można wykonać w dowolnym kontekście wątku.|
|Ten|Funkcja wywołania zwrotnego można wykonać tylko w kontekście wątku, w którym uruchomiono operację asynchroniczną.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** System Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Przestrzeń nazw:** Platformach

**Metadane:** obiekt platform. winmd
