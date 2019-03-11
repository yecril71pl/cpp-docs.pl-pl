---
title: Klasa wartości Platform::IntPtr
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformIntPtr::IntPtr
- VCCORLIB/PlatformIntPtr::op_explicit Operator
- VCCORLIB/PlatformIntPtr::ToInt32
helpviewer_keywords:
- Platform::IntPtr Struct
ms.assetid: 6c0326e8-edfd-4e53-a963-240b845dcde8
ms.openlocfilehash: 8101fa2c82a0ac3e3b573384d14d9a7eff6ecf61
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747115"
---
# <a name="platformintptr-value-class"></a>Klasa wartości Platform::IntPtr

Reprezentuje podpisem wskaźnik lub uchwyt i których rozmiar jest specyficzne dla platformy (32-bitowy lub 64-bitowych).

## <a name="syntax"></a>Składnia

```cpp
public value struct IntPtr
```

### <a name="members"></a>Elementy członkowskie

Pola IntPtr ma następujące składowe:

|Element członkowski|Opis|
|------------|-----------------|
|[IntPtr::IntPtr](#ctor)|Inicjuje nowe wystąpienie elementu IntPtr.|
|[IntPtr::op_explicit — Operator](#op-explicit)|Konwertuje określony parametr pola IntPtr lub wskaźnik do wartości pola IntPtr.|
|[IntPtr::ToInt32](#toint32)|Konwertuje bieżącego pola IntPtr 32-bitową liczbę całkowitą.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** Windows 8

**Minimalna obsługiwana serwera:** Windows Server 2012

**Namespace:** Platforma

**Metadane:** platform.winmd

## <a name="ctor"> </a> Konstruktor IntPtr::IntPtr

Inicjuje nowe wystąpienie elementu IntPtr z określoną wartością.

### <a name="syntax"></a>Składnia

```cpp
IntPtr( __int64 handle-or-pointer );   IntPtr( void* value );   IntPtr( int 32-bit_value );
```

### <a name="parameters"></a>Parametry

*value*<br/>
Dojście do 64-bitowych lub wskaźnik lub wskaźnika do wartości 64-bitowy lub 32-bitową wartość, które można przekonwertować na wartość 64-bitowych.

## <a name="op-explicit"> </a> IntPtr::op_explicit — Operator

Konwertuje określony parametr pola IntPtr lub wskaźnik do wartości pola IntPtr.

### <a name="syntax"></a>Składnia

```cpp
static IntPtr::operator IntPtr( void* value1);   static IntPtr::operator IntPtr( int value2);   static IntPtr::operator void*( IntPtr value3 );
```

### <a name="parameters"></a>Parametry

*value1*<br/>
Wskaźnik do dojścia lub pola IntPtr.

*value2*<br/>
32-bitowa liczba całkowita, która może zostać przekonwertowany na element IntPtr.

*value3*<br/>
An IntPtr.

### <a name="return-value"></a>Wartość zwracana

Operatory pierwsza i druga zwraca pola IntPtr. Trzeci operator zwraca wskaźnik do wartością reprezentowaną przez bieżące IntPtr.

## <a name="toint32"> </a> Metoda IntPtr::ToInt32

Konwertuje bieżącej wartości pola IntPtr 32-bitową liczbę całkowitą.

### <a name="syntax"></a>Składnia

```cpp
int32 IntPtr::ToInt32();
```

### <a name="return-value"></a>Wartość zwracana

32-bitową liczbę całkowitą.

## <a name="see-also"></a>Zobacz także

[Przestrzeń nazw platformy](../cppcx/platform-namespace-c-cx.md)
