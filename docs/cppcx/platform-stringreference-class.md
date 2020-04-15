---
title: Platform::StringReference, klasa
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::StringReference::StringReference
- VCCORLIB/Platform::StringReference::Data
- VCCORLIB/Platform::StringReference::Length
- VCCORLIB/Platform::StringReference::GetHSTRING
- VCCORLIB/Platform::StringReference::GetString
ms.assetid: 2d09c7ec-0f16-458e-83ed-7225a1b9221e
ms.openlocfilehash: 4748eecdf67ae5a60ddf97783a934a05e80b406c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374662"
---
# <a name="platformstringreference-class"></a>Platform::StringReference, klasa

Typ optymalizacji, którego można użyć do `Platform::String^` przekazywania danych ciągu z parametrów wejściowych do innych metod przy użyciu co najmniej operacji kopiowania.

## <a name="syntax"></a>Składnia

```cpp
class StringReference
```

### <a name="remarks"></a>Uwagi

### <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Odwzszłużenie ciągu::StringReference](#ctor)|Dwa konstruktory do `StringReference`tworzenia wystąpień .|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[StringReference::Data](#data)|Zwraca dane ciągu jako tablicę wartości char16.|
|[CiągReference::Długość](#length)|Zwraca liczbę znaków w ciągu.|
|[CiągReferencja::GetHSTRING](#gethstring)|Zwraca dane ciągu jako HSTRING.|
|[CiągReference::GetString](#getstring)|Zwraca dane ciągu `Platform::String^`jako plik .|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[StringReference::operator=](#operator-assign)|Przypisuje a `StringReference` do `StringReference` nowego wystąpienia.|
|[StringReference::operator()](#operator-call)|Konwertuje `StringReference` a `Platform::String^`do .|

### <a name="requirements"></a>Wymagania

**Minimalny obsługiwany klient:** Windows 8

**Minimalny obsługiwany serwer:** System Windows Server 2012

**Obszar nazw:** Platformy

**Nagłówek:** vccorlib.h

## <a name="stringreferencedata-method"></a><a name="data"></a>StringReference:metoda :Data

Zwraca zawartość tego `StringReference` jako tablicę wartości char16.

### <a name="syntax"></a>Składnia

```cpp
const ::default::char16 * Data() const;
```

### <a name="return-value"></a>Wartość zwracana

Tablica znaków tekstowych char16 UNICODE.

## <a name="stringreferencegethstring-method"></a><a name="gethstring"></a>StringReference::Metoda GetHSTRING

Zwraca zawartość ciągu jako `__abi_HSTRING`plik .

### <a name="syntax"></a>Składnia

```cpp
__abi_HSTRING GetHSTRING() const;
```

### <a name="return-value"></a>Wartość zwracana

An, `__abi_HSTRING` który zawiera dane ciągu.

### <a name="remarks"></a>Uwagi

## <a name="stringreferencegetstring-method"></a><a name="getstring"></a>StringReference::Metoda GetString

Zwraca zawartość ciągu jako `Platform::String^`plik .

### <a name="syntax"></a>Składnia

```cpp
__declspec(no_release_return) __declspec(no_refcount)
    ::Platform::String^ GetString() const;
```

### <a name="return-value"></a>Wartość zwracana

A, `Platform::String^` który zawiera dane ciągu.

## <a name="stringreferencelength-method"></a><a name="length"></a>StringReference::Metoda długości

Zwraca liczbę znaków w ciągu.

### <a name="syntax"></a>Składnia

```cpp
unsigned int Length() const;
```

### <a name="return-value"></a>Wartość zwracana

Niepodpisana liczba całkowita określająca liczbę znaków w ciągu.

### <a name="remarks"></a>Uwagi

## <a name="stringreferenceoperator-operator"></a><a name="operator-assign"></a>StringReference::operator= Operator

Przypisuje określony obiekt do `StringReference` bieżącego obiektu.

### <a name="syntax"></a>Składnia

```cpp
StringReference& operator=(const StringReference& __fstrArg);
StringReference& operator=(const ::default::char16* __strArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
Adres `StringReference` obiektu, który jest używany do `StringReference` inicjowania bieżącego obiektu.

*__strArg*<br/>
Wskaźnik do tablicy wartości char16, która jest `StringReference` używana do inicjowania bieżącego obiektu.

### <a name="return-value"></a>Wartość zwracana

Odwołanie do obiektu typu `StringReference`.

### <a name="remarks"></a>Uwagi

Ponieważ `StringReference` jest to standardowa klasa C++, a nie klasa ref, nie jest wyświetlana w **przeglądarce obiektów**.

## <a name="stringreferenceoperator--operator"></a><a name="operator-call"></a>StringReference::operator() Operator

Konwertuje `StringReference` obiekt `Platform::String^` na obiekt.

### <a name="syntax"></a>Składnia

```cpp
__declspec(no_release_return) __declspec(no_refcount)
         operator ::Platform::String^() const;
```

### <a name="return-value"></a>Wartość zwracana

Dojście do obiektu `Platform::String`typu .

## <a name="stringreferencestringreference-constructor"></a><a name="ctor"></a>StringReference::Konstruktor stringreference

Inicjuje nowe wystąpienie klasy `StringReference`.

### <a name="syntax"></a>Składnia

```cpp
StringReference();
StringReference(const StringReference& __fstrArg);
StringReference(const ::default::char16* __strArg);
StringReference(const ::default::char16* __strArg, size_t __lenArg);
```

### <a name="parameters"></a>Parametry

*__fstrArg*<br/>
Którego `StringReference` dane są używane do inicjowania nowego wystąpienia.

*__strArg*<br/>
Wskaźnik do tablicy char16 wartości, który jest używany do inicjowania nowego wystąpienia.

*__lenArg*<br/>
Liczba elementów `__strArg`w programie .

### <a name="remarks"></a>Uwagi

Pierwsza wersja tego konstruktora jest konstruktorem domyślnym. Druga wersja inicjuje `StringReference` nową klasę wystąpienia z obiektu, `__fstrArg` który jest określony przez parametr. Trzeci i czwarty przeciążenia zainicjować nowe `StringReference` wystąpienie z tablicy char16 wartości. char16 reprezentuje 16-bitowy znak tekstowy UNICODE.

## <a name="see-also"></a>Zobacz też

[Platform::StringReference, klasa](../cppcx/platform-stringreference-class.md)
