---
title: Klasa wartości platform::sizet | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78d205956f026fe730848afa4c0d6fe7b52b52c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44102005"
---
# <a name="platformsizet-value-class"></a>Klasa wartości Platform::SizeT

Reprezentuje rozmiar obiektu. SizeT jest typem danych bez znaku.

## <a name="syntax"></a>Składnia

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Elementy członkowskie

|Element członkowski|Opis|
|------------|-----------------|
|[Konstruktor SizeT::SizeT](#ctor)|Inicjuje nowe wystąpienie klasy z określoną wartością.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Metadane:** platform.winmd

## <a name="ctor"></a>  Konstruktor SizeT::SizeT

Inicjuje nowe wystąpienie klasy SizeT z określoną wartością.

### <a name="syntax"></a>Składnia

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parametry

*Wartość1*<br/>
Wartość nieoznaczona 32-bitowych.

*Wartość2*<br/>
Wskaźnik na wartość nieoznaczona 32-bitowych.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)