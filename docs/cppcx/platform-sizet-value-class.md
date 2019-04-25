---
title: Klasa wartości Platform::SizeT
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 7f81cb9e1fc2ef7a74cb3878c369e4d7d14e3d90
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330144"
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

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="ctor"></a>  Konstruktor SizeT::SizeT

Inicjuje nowe wystąpienie klasy SizeT z określoną wartością.

### <a name="syntax"></a>Składnia

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parametry

*value1*<br/>
Wartość nieoznaczona 32-bitowych.

*value2*<br/>
Wskaźnik na wartość nieoznaczona 32-bitowych.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
