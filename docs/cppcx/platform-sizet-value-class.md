---
title: Klasa wartości Platform::SizeT
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 5add9212dc2655bc37cd357741073f855b009bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322162"
---
# <a name="platformsizet-value-class"></a>Klasa wartości Platform::SizeT

Reprezentuje rozmiar obiektu. SizeT jest niepodpisanym typem danych.

## <a name="syntax"></a>Składnia

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Elementy członkowskie

|Członek|Opis|
|------------|-----------------|
|[SizeT::Konstruktor SizeT](#ctor)|Inicjuje nowe wystąpienie klasy o określonej wartości.|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Metadane:** platform.winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a>SizeT::Konstruktor SizeT

Inicjuje nowe wystąpienie SizeT o określonej wartości.

### <a name="syntax"></a>Składnia

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parametry

*wartość 1*<br/>
Niepodpisana wartość 32-bitowa.

*wartość2*<br/>
Wskaźnik do niepodpisanej wartości 32-bitowej.

## <a name="see-also"></a>Zobacz też

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
