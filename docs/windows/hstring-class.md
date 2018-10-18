---
title: Klasa HString | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/24/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
- corewrappers/Microsoft::WRL::Wrappers::HString::Attach
- corewrappers/Microsoft::WRL::Wrappers::HString::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HString::Detach
- corewrappers/Microsoft::WRL::Wrappers::HString::Get
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a93c36748eb01a1c647a2aa433196c7364f60744
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410814"
---
# <a name="hstring-class"></a>HString — Klasa

Klasa pomocnicza do zarządzania okresem istnienia [HSTRING](/windows/desktop/WinRT/hstring) przy użyciu wzorca RAII.

## <a name="syntax"></a>Składnia

```cpp
class HString;
```

## <a name="remarks"></a>Uwagi

Środowisko wykonawcze Windows zapewnia dostęp do ciągów za pomocą [HSTRING](/windows/desktop/WinRT/hstring) uchwyty. `HString` Klasa oferuje wygodne funkcje i operatory upraszczające korzystanie z dojść HSTRING. Ta klasa może obsługiwać okres istnienia HSTRING, jest ona właścicielem za pośrednictwem wzór RAII.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                | Opis
----------------------------------- | -----------------------------------------------------
[HString::HString](#hstring)        | Inicjuje nowe wystąpienie klasy `HString` klasy.
[HString:: ~ HString](#tilde-hstring) | Likwiduje bieżące wystąpienie `HString` klasy.

### <a name="public-methods"></a>Metody publiczne

Nazwa                                     | Opis
---------------------------------------- | -------------------------------------------------------------------------------------------------------------
[HString::Attach](#attach)               | Kojarzy określonego `HString` obiekt z bieżącego `HString` obiektu.
[HString::CopyTo](#copyto)               | Kopiuje bieżący `HString` obiektu do obiektu HSTRING.
[HString::Detach](#detach)               | Powoduje usunięcie określonego `HString` obiekt z jego podstawową wartość.
[HString::Get](#get)                     | Pobiera wartość podstawowego dojścia HSTRING.
[HString::GetAddressOf](#getaddressof)   | Pobiera wskaźnik do podstawowego dojścia HSTRING.
[HString::IsValid](#isvalid)             | Wskazuje, czy bieżący `HString` obiekt jest prawidłowy.
[HString::MakeReference](#makereference) | Tworzy `HStringReference` obiekt z określonego parametru ciągu.
[HString::Release](#release)             | Usuwa wartość ciągu i aktywuje bieżący `HString` obiektu na wartość pustą.
[HString::Set](#set)                     | Ustawia wartość bieżącego `HString` obiekt określony ciąg znaków dwubajtowych lub `HString` parametru.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                         | Opis
-------------------------------------------- | ----------------------------------------------------------------------------
[HString::operator =](#operator-assign)       | Przenosi wartość innego `HString` obiekt do bieżącego `HString` obiektu.
[HString::operator ==](#operator-equality)    | Wskazuje, czy dwa parametry są równe.
[HString::operator! =](#operator-inequality)  | Wskazuje, czy dwa parametry nie są równe.
[HString::operator&lt;](#operator-less-than) | Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HString`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="tilde-hstring"></a>HString:: ~ HString

Likwiduje bieżące wystąpienie `HString` klasy.

```cpp
~HString() throw()  
```

## <a name="attach"></a>HString::Attach

Kojarzy określonego `HString` obiekt z bieżącego `HString` obiektu.

```cpp
void Attach(
       HSTRING hstr
       ) throw()  
```

### <a name="parameters"></a>Parametry

*HSTR*<br/>
Istniejące `HString` obiektu.

## <a name="copyto"></a>HString::CopyTo

Kopiuje bieżący `HString` obiektu do obiektu HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, który otrzymuje kopię.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [WindowsDuplicateString](https://msdn.microsoft.com/library/br224634.aspx) funkcji.

## <a name="detach"></a>HString::Detach

Powoduje usunięcie określonego `HString` obiekt z jego podstawową wartość.

```cpp
HSTRING Detach() throw()  
```

### <a name="return-value"></a>Wartość zwracana

Podstawowe `HString` wartość przed wykonaniem operacji odłączania pracę.

## <a name="get"></a>HString::Get

Pobiera wartość podstawowego dojścia HSTRING.

```cpp
HSTRING Get() const throw()  
```

### <a name="return-value"></a>Wartość zwracana

Wartość podstawowego dojścia HSTRING

## <a name="getaddressof"></a>HString::GetAddressOf

Pobiera wskaźnik do podstawowego dojścia HSTRING.

```cpp
HSTRING* GetAddressOf() throw()  
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do podstawowego dojścia HSTRING.

### <a name="remarks"></a>Uwagi

Po tej operacji jest niszczony, wartość ciągu podstawowego dojścia HSTRING.

## <a name="hstring"></a>HString::HString

Inicjuje nowe wystąpienie klasy `HString` klasy.

```cpp
HString(HSTRING hstr = nullptr) throw();
HString(HString&& other) throw();
```

### <a name="parameters"></a>Parametry

*HSTR*<br/>
Dojścia HSTRING.

*other*<br/>
Istniejące `HString` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje nową `HString` obiektu, który jest pusty.

Drugi Konstruktor inicjuje nowe `HString` obiektu do wartości istniejących *innych* parametru i następnie niszczy *innych* parametru.

## <a name="isvalid"></a>HString::IsValid

Wskazuje, czy bieżący `HString` obiekt jest pusty lub nie.

```cpp
bool IsValid() const throw()  
```

### <a name="parameters"></a>Parametry

**wartość true,** Jeśli bieżące `HString` obiekt nie jest pusty; w przeciwnym razie **false**.

## <a name="makereference"></a>HString::MakeReference

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

*sizeDest*<br/>
Parametr szablonu, który określa rozmiar docelowy `HStringReference` buforu.

*str*<br/>
Odwołanie do ciągu znaków dwubajtowych.

*Len*<br/>
Maksymalna długość *str* bufora parametru w tej operacji. Jeśli *len* parametr nie jest określony, całą *str* parametr jest używany.

### <a name="return-value"></a>Wartość zwracana

`HStringReference` Obiektu, którego wartość jest taka sama, jak określa *str* parametru.

## <a name="operator-assign"></a>HString::operator = — Operator

Przenosi wartość innego `HString` obiekt do bieżącego `HString` obiektu.

```cpp
HString& operator=(HString&& other) throw()  
```

### <a name="parameters"></a>Parametry

*other*<br/>
Istniejące `HString` obiektu.

### <a name="remarks"></a>Uwagi

Wartość istniejącego *innych* obiekt jest kopiowany do bieżącego `HString` obiektu, a następnie *innych* niszczony jest obiekt.

## <a name="operator-equality"></a>HString::operator == — Operator

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

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być `HString` lub `HStringReference` obiektu lub dojścia HSTRING.

*RHS*<br/>
Drugi parametr do porównania. *rhs* może być `HString` lub `HStringReference` obiektu lub dojścia HSTRING.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* i *rhs* parametry są równe; w przeciwnym razie **false**.

## <a name="operator-inequality"></a>HString::operator! = — Operator

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

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być `HString` lub `HStringReference` obiektu lub dojścia HSTRING.

*RHS*<br/>
Drugi parametr do porównania. *rhs* może być `HString` lub `HStringReference` obiektu lub dojścia HSTRING.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* i *rhs* parametry nie są równe; w przeciwnym razie **false**.

## <a name="operator-less-than"></a>HString::operator&lt; — Operator

Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.

```cpp
inline bool operator<(
    const HString& lhs,
    const HString& rhs) throw()  
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być odwołaniem do `HString`.

*RHS*<br/>
Drugi parametr do porównania. *RHS* może być odwołaniem do `HString`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* parametr jest mniejsza niż *rhs* parametru; w przeciwnym razie **false**.

## <a name="release"></a>HString::Release

Usuwa wartość ciągu i aktywuje bieżący `HString` obiektu na wartość pustą.

```cpp
void Release() throw()  
```

## <a name="set"></a>HString::Set

Ustawia wartość bieżącego `HString` obiekt określony ciąg znaków dwubajtowych lub `HString` parametru.

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

*Len*<br/>
Maksymalna długość *str* parametr, który jest przypisany do bieżącego `HString` obiektu.

*HSTR*<br/>
Istniejące `HString` obiektu.
