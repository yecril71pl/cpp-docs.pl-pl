---
title: Platform::StringReference, klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
dev_langs:
- C++
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b177cf30b4eee49d144ddf3516a4bbf3da91c85
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105799"
---
# <a name="platformstringreference-class"></a>Platform::StringReference, klasa

Typ optymalizacji, który służy do przekazywania danych ciągu z `Platform::String^` wprowadź parametry do innych metod, co najmniej operacji kopiowania.

## <a name="syntax"></a>Składnia

```cpp
class StringReference
```

### <a name="remarks"></a>Uwagi

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[StringReference::StringReference](#ctor)|Dwa konstruktory do tworzenia wystąpień `StringReference`.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[StringReference::Data](#data)|Zwraca dane ciągu w postaci tablicy wartości char16.|
|[StringReference::Length](#length)|Zwraca liczbę znaków w ciągu.|
|[StringReference::GetHSTRING](#gethstring)|Zwraca dane ciągu w postaci HSTRING.|
|[StringReference::GetString](#getstring)|Zwraca dane ciągu jako `Platform::String^`.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[StringReference::operator =](#operator-assign)|Przypisuje `StringReference` na nową `StringReference` wystąpienia.|
|[StringReference::operator()](#operator-call)|Konwertuje `StringReference` do `Platform::String^`.|

### <a name="requirements"></a>Wymagania

**Minimalna obsługiwana klienta:** systemu Windows 8

**Minimalna obsługiwana serwera:** systemu Windows Server 2012

**Namespace:** platformy

**Nagłówek:** vccorlib.h

## <a name="data"></a>  Metoda StringReference::Data

Zwraca zawartość to `StringReference` jako tablicę wartości char16.

### <a name="syntax"></a>Składnia

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Wartość zwracana

Tablica znaków UNICODE, tekst char16.

## <a name="gethstring"></a>  Metoda StringReference::GetHSTRING

Zwraca zawartość ciągu jako `__abi_HSTRING`.

### <a name="syntax"></a>Składnia

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Wartość zwracana

`__abi_HSTRING` Zawierający dane ciągu.

### <a name="remarks"></a>Uwagi

## <a name="getstring"></a>  Metoda StringReference::GetString

Zwraca zawartość ciągu jako `Platform::String^`.

### <a name="syntax"></a>Składnia

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Wartość zwracana

Element `Platform::String^` zawierający dane ciągu.

## <a name="length"></a>  Metoda StringReference::Length

Zwraca liczbę znaków w ciągu.

### <a name="syntax"></a>Składnia

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Wartość zwracana

Liczba całkowita bez znaku, która określa liczbę znaków w ciągu.

### <a name="remarks"></a>Uwagi

## <a name="operator-assign"></a>  StringReference::operator = — Operator

Przypisuje określony obiekt do bieżącego `StringReference` obiektu.

### <a name="syntax"></a>Składnia

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
Adres `StringReference` obiekt, który służy do inicjowania bieżącego `StringReference` obiektu.

*__strArg*<br/>
Wskaźnik do tablicy wartości char16, który służy do inicjowania bieżącego `StringReference` obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `StringReference`.

### <a name="remarks"></a>Uwagi

Ponieważ `StringReference` standardowa klasy języka C++ i nie klasy referencyjnej, nie ma w **przeglądarki obiektów**.

## <a name="operator-call"></a>  StringReference::operator() Operator

Konwertuje `StringReference` obiekt `Platform::String^` obiektu.

### <a name="syntax"></a>Składnia

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu typu `Platform::String`.

## <a name="ctor"></a>  Konstruktor StringReference::StringReference

Inicjuje nowe wystąpienie klasy `StringReference` klasy.

### <a name="syntax"></a>Składnia

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
`StringReference` Którego dane są używane do inicjowania nowego wystąpienia.

*__strArg*<br/>
Wskaźnik do tablicy wartości char16 służy do inicjowania nowego wystąpienia.

*__lenArg*<br/>
Liczba elementów w `__strArg`.

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego konstruktora jest konstruktor domyślny. Inicjuje nowe wystąpienie druga wersja `StringReference` wystąpienia klasy z obiektu, który jest określony przez `__fstrArg` parametru. Trzecia i czwarta przeciążenia zainicjować nowy `StringReference` wystąpienia z tablicy wartości char16. char16 reprezentuje znak tekst UNICODE 16-bitowych.

## <a name="see-also"></a>Zobacz też

[Platform::StringReference, klasa](../cppcx/platform-stringreference-class.md)