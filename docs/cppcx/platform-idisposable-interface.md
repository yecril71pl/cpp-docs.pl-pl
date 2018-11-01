---
title: Platform::IDisposable, interfejs
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637440"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable, interfejs

Używane, aby zwolnić niezarządzane zasoby.

## <a name="syntax"></a>Składnia

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Atrybuty

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Elementy członkowskie

Interfejs IDisposable dziedziczy po interfejsie IUnknown. Interfejs IDisposable ma również następujące rodzaje składowych:

**Metody**

Interfejs IDisposable, ma następujące metody.

|Metoda|Opis|
|------------|-----------------|
|Metody Dispose|Używane, aby zwolnić niezarządzane zasoby.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy