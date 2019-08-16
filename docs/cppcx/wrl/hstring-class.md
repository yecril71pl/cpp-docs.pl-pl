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
ms.openlocfilehash: 71ebc02dc56b45e8790bfac7b7d4bac80d5f7729
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500499"
---
# <a name="hstring-class"></a>HString — Klasa

Klasa pomocnika służąca do zarządzania okresem istnienia [HString](/windows/win32/WinRT/hstring) przy użyciu wzorca RAII.

## <a name="syntax"></a>Składnia

```cpp
class HString;
```

## <a name="remarks"></a>Uwagi

Środowisko wykonawcze systemu Windows zapewnia dostęp do ciągów za pomocą dojścia [HString](/windows/win32/WinRT/hstring) . `HString` Klasa udostępnia wygodną funkcję i operatory upraszczające korzystanie z uchwytów HSTRING. Ta klasa może obsłużyć okres istnienia HSTRING, do którego należy, za pomocą wzorca RAII.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                | Opis
----------------------------------- | -----------------------------------------------------
[HString:: HString](#hstring)        | Inicjuje nowe wystąpienie klasy `HString` klasy.
[HString:: ~ HString](#tilde-hstring) | Niszczy bieżące wystąpienie `HString` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                     | Opis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString:: Attach](#attach)               | Kojarzy określony `HString` obiekt z bieżącym `HString` obiektem.
[HString:: CopyTo](#copyto)               | Kopiuje bieżący `HString` obiekt do obiektu HSTRING.
[HString::Detach](#detach)               | Usuwa określony `HString` obiekt z jego wartości źródłowej.
[HString:: Get](#get)                     | Pobiera wartość bazowego uchwytu HSTRING.
[HString:: GetAddressOf](#getaddressof)   | Pobiera wskaźnik do bazowego uchwytu HSTRING.
[HString:: GetRawBuffer](#getrawbuffer)   | Pobiera wskaźnik do danych ciągu bazowego.
[HString:: IsValid](#isvalid)             | Wskazuje, czy bieżący `HString` obiekt jest prawidłowy.
[HString:: MakeReference](#makereference) | `HStringReference` Tworzy obiekt z określonego parametru ciągu.
[HString:: Release](#release)             | Usuwa wartość ciągu bazowego i aktywuje bieżący `HString` obiekt do wartości pustej.
[HString:: Set](#set)                     | Ustawia wartość bieżącego `HString` obiektu na określony ciąg znaków dwubajtowych lub `HString` parametr.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                         | Opis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString:: operator =](#operator-assign)       | Przenosi wartość innego `HString` obiektu do bieżącego `HString` obiektu.
[HString::operator==](#operator-equality)    | Wskazuje, czy dwa parametry są równe.
[HString:: operator! =](#operator-inequality)  | Wskazuje, czy dwa parametry nie są równe.
[HString:: operator&lt;](#operator-less-than) | Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HString`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Obszaru** Microsoft:: WRL:: otoki

## <a name="tilde-hstring"></a>HString:: ~ HString

Niszczy bieżące wystąpienie `HString` klasy.

```cpp
~HString() throw()
```

## <a name="attach"></a>HString:: Attach

Kojarzy określony `HString` obiekt z bieżącym `HString` obiektem.

```cpp
void Attach(
       HSTRING hstr
       ) throw()
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Istniejący `HString` obiekt.

## <a name="copyto"></a>HString:: CopyTo

Kopiuje bieżący `HString` obiekt do obiektu HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, który otrzymuje kopię.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje funkcję [WindowsDuplicateString](/windows/win32/api/winstring/nf-winstring-windowsduplicatestring) .

## <a name="detach"></a>HString::Detach

Usuwa określony `HString` obiekt z jego wartości źródłowej.

```cpp
HSTRING Detach() throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość bazowa `HString` przed rozpoczęciem operacji odłączenia.

## <a name="get"></a>HString:: Get

Pobiera wartość bazowego uchwytu HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość bazowego uchwytu HSTRING

## <a name="getaddressof"></a>HString:: GetAddressOf

Pobiera wskaźnik do bazowego uchwytu HSTRING.

```cpp
HSTRING* GetAddressOf() throw()
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do bazowego uchwytu HSTRING.

### <a name="remarks"></a>Uwagi

Po tej operacji wartość ciągu bazowego uchwytu HSTRING zostanie zniszczona.

## <a name="getrawbuffer"></a>HString:: GetRawBuffer

Pobiera wskaźnik do danych ciągu bazowego.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parametry

*Długość* Wskaźnik do zmiennej **int** , która otrzymuje długość danych.

### <a name="return-value"></a>Wartość zwracana

Stały wskaźnik do danych ciągu bazowego.


## <a name="hstring"></a>HString:: HString

Inicjuje nowe wystąpienie klasy `HString` klasy.

```cpp
HString() throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametry

*hstr*<br/>
Uchwyt HSTRING.

*other*<br/>
Istniejący `HString` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje nowy `HString` obiekt, który jest pusty.

Drugi Konstruktor inicjuje nowy `HString` obiekt do wartości istniejącego *innego* parametru, a następnie niszczy *inny* parametr.

## <a name="isvalid"></a>HString:: IsValid

Wskazuje, czy bieżący `HString` obiekt jest pusty.

```cpp
bool IsValid() const throw()
```

### <a name="parameters"></a>Parametry

**true** , jeśli bieżący `HString` obiekt nie jest pusty; w przeciwnym razie, **Fałsz**.

## <a name="makereference"></a>HString:: MakeReference

`HStringReference` Tworzy obiekt z określonego parametru ciągu.

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

*sizeDest*<br/>
Parametr szablonu, który określa rozmiar buforu docelowego `HStringReference` .

*str*<br/>
Odwołanie do ciągu znaków dwubajtowych.

*Funkcja*<br/>
Maksymalna długość buforu parametrów *str* , która ma być używana w tej operacji. Jeśli parametr *len* nie jest określony, zostanie użyty cały parametr *str* .

### <a name="return-value"></a>Wartość zwracana

Obiekt, którego wartość jest taka sama jak określony parametr *str.* `HStringReference`

## <a name="operator-assign"></a>HString:: operator = — operator

Przenosi wartość innego `HString` obiektu do bieżącego `HString` obiektu.

```cpp
HString& operator=(HString&& other) throw()
```

### <a name="parameters"></a>Parametry

*other*<br/>
Istniejący `HString` obiekt.

### <a name="remarks"></a>Uwagi

Wartość istniejącego *innego* obiektu jest kopiowana do bieżącego `HString` obiektu, a następnie *drugi* obiekt zostanie zniszczony.

## <a name="operator-equality"></a>HString:: operator = = — operator

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

*LHS*<br/>
Pierwszy parametr do porównania. *LHS* może być `HString` obiektem `HStringReference` lub dojściem HSTRING.

*RHS*<br/>
Drugi parametr do porównania. *RHS* może być `HString` obiektem `HStringReference` lub uchwytem HSTRING.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli parametry *LHS* i *RHS* są równe; w przeciwnym razie **false**.

## <a name="operator-inequality"></a>Operator HString:: operator! =

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

*LHS*<br/>
Pierwszy parametr do porównania. *LHS* może być `HString` obiektem `HStringReference` lub dojściem HSTRING.

*RHS*<br/>
Drugi parametr do porównania. *RHS* może być `HString` obiektem `HStringReference` lub uchwytem HSTRING.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli parametry *LHS* i *RHS* nie są równe; w przeciwnym razie **false**.

## <a name="operator-less-than"></a>Operator HString::&lt; operator

Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
Pierwszy parametr do porównania. *LHS* może być odwołaniem do `HString`.

*RHS*<br/>
Drugi parametr do porównania. *RHS* może być odwołaniem do `HString`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli parametr *LHS* jest mniejszy niż parametr *RHS* ; w przeciwnym razie **false**.

## <a name="release"></a>HString:: Release

Usuwa wartość ciągu bazowego i aktywuje bieżący `HString` obiekt do wartości pustej.

```cpp
void Release() throw()
```

## <a name="set"></a>HString:: Set

Ustawia wartość bieżącego `HString` obiektu na określony ciąg znaków dwubajtowych lub `HString` parametr.

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

*str*<br/>
Ciąg znaków dwubajtowych.

*Funkcja*<br/>
Maksymalna długość parametru *str* , który jest przypisany do bieżącego `HString` obiektu.

*hstr*<br/>
Istniejący `HString` obiekt.
