---
title: HString — Klasa
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
- corewrappers/Microsoft::WRL::Wrappers::HString::GetRawBuffer
- corewrappers/Microsoft::WRL::Wrappers::HString::GetAddressOf
- corewrappers/Microsoft::WRL::Wrappers::HString::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::IsValid
- corewrappers/Microsoft::WRL::Wrappers::HString::MakeReference
- corewrappers/Microsoft::WRL::Wrappers::HString::operator=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator==
- corewrappers/Microsoft::WRL::Wrappers::HString::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HString::operator<
- corewrappers/Microsoft::WRL::Wrappers::HString::Release
- corewrappers/Microsoft::WRL::Wrappers::HString::Set
- corewrappers/Microsoft::WRL::Wrappers::HString::~HString
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HString class
- Microsoft::WRL::Wrappers::HString::Attach method
- Microsoft::WRL::Wrappers::HString::CopyTo method
- Microsoft::WRL::Wrappers::HString::Detach method
- Microsoft::WRL::Wrappers::HString::Get method
- Microsoft::WRL::Wrappers::HString::GetAddressOf method
- Microsoft::WRL::Wrappers::HString::HString, constructor
- Microsoft::WRL::Wrappers::HString::IsValid method
- Microsoft::WRL::Wrappers::HString::MakeReference method
- Microsoft::WRL::Wrappers::HString::operator= operator
- Microsoft::WRL::Wrappers::HString::operator== operator
- Microsoft::WRL::Wrappers::HString::operator!= operator
- Microsoft::WRL::Wrappers::HString::operator< operator
- Microsoft::WRL::Wrappers::HString::Release method
- Microsoft::WRL::Wrappers::HString::Set method
- Microsoft::WRL::Wrappers::HString::~HString, destructor
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
ms.openlocfilehash: 625d7b7d6fc001a6fb63144807b5f29d3620485b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371429"
---
# <a name="hstring-class"></a>HString — Klasa

Klasa pomocnika do zarządzania okresem istnienia [HSTRING](/windows/win32/WinRT/hstring) przy użyciu wzorca RAII.

## <a name="syntax"></a>Składnia

```cpp
class HString;
```

## <a name="remarks"></a>Uwagi

Środowisko wykonawcze systemu Windows zapewnia dostęp do ciągów za pośrednictwem uchwytów [HSTRING.](/windows/win32/WinRT/hstring) Klasa `HString` zapewnia funkcje wygody i operatorów, aby uprościć korzystanie z uchwytów HSTRING. Ta klasa może obsługiwać okres istnienia HSTRING posiada za pośrednictwem wzorca RAII.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                | Opis
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inicjuje nowe wystąpienie klasy `HString`.
[HString::~HString](#tilde-hstring) | Niszczy bieżące wystąpienie `HString` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                     | Opis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Dołącz](#attach)               | Kojarzy określony `HString` obiekt z `HString` bieżącym obiektem.
[HString::CopyTo](#copyto)               | Kopiuje `HString` bieżący obiekt do obiektu HSTRING.
[HString::Detach](#detach)               | Odłącza określony `HString` obiekt od jego wartości podstawowej.
[HString::Pobierz](#get)                     | Pobiera wartość podstawowej dojścia HSTRING.
[HString::GetAddressOf](#getaddressof)   | Pobiera wskaźnik do podstawowego uchwytu HSTRING.
[HString::GetRawBuffer](#getrawbuffer)   | Pobiera wskaźnik do podstawowych danych ciągu.
[HString::IsValid](#isvalid)             | Wskazuje, czy `HString` bieżący obiekt jest prawidłowy.
[HString::MakeReference](#makereference) | Tworzy `HStringReference` obiekt z określonego parametru ciągu.
[HString::Zwolnij](#release)             | Usuwa wartość ciągu źródłowego i intializes bieżącego `HString` obiektu do pustej wartości.
[HString::Zestaw](#set)                     | Ustawia wartość bieżącego `HString` obiektu na określony ciąg `HString` lub parametr o szerokim znaku.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                         | Opis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator=](#operator-assign)       | Przenosi wartość innego `HString` obiektu do `HString` bieżącego obiektu.
[HString::operator==](#operator-equality)    | Wskazuje, czy dwa parametry są równe.
[HString::operator!=](#operator-inequality)  | Wskazuje, czy dwa parametry nie są równe.
[HString::operator&lt;](#operator-less-than) | Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HString`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="hstringhstring"></a><a name="tilde-hstring"></a>HString::~HString

Niszczy bieżące wystąpienie `HString` klasy.

```cpp
~HString() throw()
```

## <a name="hstringattach"></a><a name="attach"></a>HString::Dołącz

Kojarzy określony `HString` obiekt z `HString` bieżącym obiektem.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametry

*hstr (własówce*<br/>
Istniejący `HString` obiekt.

## <a name="hstringcopyto"></a><a name="copyto"></a>HString::CopyTo

Kopiuje `HString` bieżący obiekt do obiektu HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
HSTRING, który odbiera kopię.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje funkcję [WindowsDuplicateString.](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring)

## <a name="hstringdetach"></a><a name="detach"></a>HString::Detach

Odłącza określony `HString` obiekt od jego wartości podstawowej.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość `HString` bazowa przed rozpoczęciem operacji odłączania.

## <a name="hstringget"></a><a name="get"></a>HString::Pobierz

Pobiera wartość podstawowej dojścia HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość bazowego uchwytu HSTRING

## <a name="hstringgetaddressof"></a><a name="getaddressof"></a>HString::GetAddressOf

Pobiera wskaźnik do podstawowego uchwytu HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowej dojścia HSTRING.

### <a name="remarks"></a>Uwagi

Po tej operacji wartość ciągu podstawowej dojście HSTRING jest niszczony.

## <a name="hstringgetrawbuffer"></a><a name="getrawbuffer"></a>HString::GetRawBuffer

Pobiera wskaźnik do podstawowych danych ciągu.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parametry

*długość* Wskaźnik do zmiennej **int,** która odbiera długość danych.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik **const** do podstawowych danych ciągu.

## <a name="hstringhstring"></a><a name="hstring"></a>HString::HString

Inicjuje nowe wystąpienie klasy `HString`.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametry

*hstr (własówce*<br/>
Uchwyt HSTRING.

*Innych*<br/>
Istniejący `HString` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje nowy `HString` obiekt, który jest pusty.

Drugi konstruktor inicjuje nowy `HString` obiekt do wartości istniejącego *innego* parametru, a następnie niszczy *inny* parametr.

## <a name="hstringisvalid"></a><a name="isvalid"></a>HString::IsValid

Wskazuje, czy `HString` bieżący obiekt jest pusty, czy nie.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametry

**true,** jeśli `HString` bieżący obiekt nie jest pusty; w przeciwnym razie **false**.

## <a name="hstringmakereference"></a><a name="makereference"></a>HString::MakeReference

Tworzy `HStringReference` obiekt z określonego parametru ciągu.

```cpp
template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[ sizeDest]);

    template<unsigned int sizeDest>
    static HStringReference MakeReference(
              wchar_t const (&str)[sizeDest],
              unsigned int len);
```

### <a name="parameters"></a>Parametry

*rozmiarDest*<br/>
Parametr szablonu określający rozmiar buforu docelowego. `HStringReference`

*Str*<br/>
Odwołanie do ciągu znaków o szerokim charakterze.

*len*<br/>
Maksymalna długość buforu parametrów *str* do użycia w tej operacji. Jeśli parametr *len* nie jest określony, używany jest cały parametr *str.*

### <a name="return-value"></a>Wartość zwracana

Obiekt, `HStringReference` którego wartość jest taka sama jak określony *parametr str.*

## <a name="hstringoperator-operator"></a><a name="operator-assign"></a>HString::operator= Operator

Przenosi wartość innego `HString` obiektu do `HString` bieżącego obiektu.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Istniejący `HString` obiekt.

### <a name="remarks"></a>Uwagi

Wartość istniejącego *innego* obiektu jest kopiowana `HString` do bieżącego obiektu, a następnie *drugi* obiekt jest niszczony.

## <a name="hstringoperator-operator"></a><a name="operator-equality"></a>HString::operator== Operator

Wskazuje, czy dwa parametry są równe.

```cpp
inline bool operator==(
               const HString& lhs,
               const HString& rhs) throw()

inline bool operator==(
                const HString& lhs,
                const HStringReference& rhs) throw()

inline bool operator==(
                const HStringReference& lhs,
                const HString& rhs) throw()

inline bool operator==(
                 const HSTRING& lhs,
                 const HString& rhs) throw()

inline bool operator==(
                 const HString& lhs,
                 const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy parametr do porównania. *może* być lub `HString` `HStringReference` obiekt, lub uchwyt HSTRING.

*Rhs*<br/>
Drugi parametr do porównania. *może* być lub `HString` `HStringReference` obiekt, lub uchwyt HSTRING.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli parametry *lhs* i *rhs* są równe; w przeciwnym razie **false**.

## <a name="hstringoperator-operator"></a><a name="operator-inequality"></a>HString::operator!= Operator

Wskazuje, czy dwa parametry nie są równe.

```cpp
inline bool operator!=( const HString& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HStringReference& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HStringReference& rhs) throw()

inline bool operator!=( const HSTRING& lhs,
                        const HString& rhs) throw()

inline bool operator!=( const HString& lhs,
                        const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy parametr do porównania. *może* być lub `HString` `HStringReference` obiekt, lub uchwyt HSTRING.

*Rhs*<br/>
Drugi parametr do porównania. *może* być lub `HString` `HStringReference` obiekt, lub uchwyt HSTRING.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli parametry *lhs* i *rhs* nie są równe; w przeciwnym razie **false**.

## <a name="hstringoperatorlt-operator"></a><a name="operator-less-than"></a>HString::operator&lt; Operator

Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy parametr do porównania. *może* być odniesieniem `HString`do .

*Rhs*<br/>
Drugi parametr do porównania. *może* być odniesieniem `HString`do .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli parametr *lhs* jest mniejszy niż parametr *rhs;* w przeciwnym razie **false**.

## <a name="hstringrelease"></a><a name="release"></a>HString::Zwolnij

Usuwa wartość ciągu źródłowego i intializes bieżącego `HString` obiektu do pustej wartości.

```cpp
void Release() throw()
```

## <a name="hstringset"></a><a name="set"></a>HString::Zestaw

Ustawia wartość bieżącego `HString` obiektu na określony ciąg `HString` lub parametr o szerokim znaku.

```cpp
HRESULT Set(
          const wchar_t* str) throw();
HRESULT Set(
          const wchar_t* str,
          unsigned int len
           ) throw();
HRESULT Set(
          const HSTRING& hstr
           ) throw();
```

### <a name="parameters"></a>Parametry

*Str*<br/>
Ciąg znaków o szerokim charakterze.

*len*<br/>
Maksymalna długość parametru *str* przypisanego do `HString` bieżącego obiektu.

*hstr (własówce*<br/>
Istniejący `HString` obiekt.
