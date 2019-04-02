---
title: HStringReference — Klasa
ms.date: 09/25/2018
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator==
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator!=
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::operator<
helpviewer_keywords:
- Microsoft::WRL::Wrappers::HStringReference class
- Microsoft::WRL::Wrappers::HStringReference::CopyTo method
- Microsoft::WRL::Wrappers::HStringReference::Get method
- Microsoft::WRL::Wrappers::HStringReference::HStringReference, constructor
- Microsoft::WRL::Wrappers::HStringReference::operator= operator
- Microsoft::WRL::Wrappers::HStringReference::operator== operator
- Microsoft::WRL::Wrappers::HStringReference::operator!= operator
- Microsoft::WRL::Wrappers::HStringReference::operator< operator
ms.assetid: 9bf823b1-17eb-4ac4-8c5d-27d27c7a4150
ms.openlocfilehash: b9d2e49d0a7e1321e2259c06e1313a90d55dc90e
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2019
ms.locfileid: "58787290"
---
# <a name="hstringreference-class"></a>HStringReference — Klasa

Reprezentuje HSTRING, utworzony na podstawie istniejącego ciągu.

## <a name="syntax"></a>Składnia

```cpp
class HStringReference;
```

## <a name="remarks"></a>Uwagi

Okres istnienia buforu zapasowego w nowym obiekcie HSTRING nie jest zarządzane przez środowisko wykonawcze Windows. Obiekt wywołujący przydziela ciąg źródłowy ramce stosu, aby uniknąć alokacji stosu i wyeliminować ryzyko przecieku pamięci. Ponadto wywołujący musi zapewnić, że ciąg źródłowy pozostaje niezmieniony w czasie użytkowania dołączonego HSTRING. Aby uzyskać więcej informacji, zobacz [funkcja WindowsCreateStringReference](/windows/desktop/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Inicjuje nowe wystąpienie klasy `HStringReference` klasy.

### <a name="public-methods"></a>Metody publiczne

Element członkowski                              | Opis
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Kopiuje bieżący `HStringReference` obiektu do obiektu HSTRING.
[HStringReference::Get](#get)       | Pobiera wartość podstawowego dojścia HSTRING.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator =](#operator-assign)       | Przenosi wartość innego `HStringReference` obiekt do bieżącego `HStringReference` obiektu.
[HStringReference::operator ==](#operator-equality)    | Wskazuje, czy dwa parametry są równe.
[HStringReference::operator! =](#operator-inequality)  | Wskazuje, czy dwa parametry nie są równe.
[HStringReference::operator&lt;](#operator-less-than) | Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HStringReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Namespace:** Microsoft::wrl:: wrappers

## <a name="copyto"></a>HStringReference::CopyTo

Kopiuje bieżący `HStringReference` obiektu do obiektu HSTRING.

```cpp
HRESULT CopyTo(
   _Out_ HSTRING *str
   ) const throw();
```

### <a name="parameters"></a>Parametry

*str*<br/>
HSTRING, który otrzymuje kopię.

### <a name="remarks"></a>Uwagi

Ta metoda wywołuje [WindowsDuplicateString](/windows/desktop/api/winstring/nf-winstring-windowsduplicatestring) funkcji.

## <a name="get"></a>HStringReference::Get

Pobiera wartość podstawowego dojścia HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość podstawowego dojścia HSTRING.

## <a name="hstringreference"></a>HStringReference::HStringReference

Inicjuje nowe wystąpienie klasy `HStringReference` klasy.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parametry

*sizeDest*<br/>
Parametr szablonu, który określa rozmiar docelowy `HStringReference` buforu.

*str*<br/>
Odwołanie do ciągu znaków dwubajtowych.

*len*<br/>
Maksymalna długość *str* bufora parametru w tej operacji. Jeśli *len* parametr nie jest określony, całą *str* parametr jest używany. Jeśli *len* jest większa niż *sizeDest*, *len* ustawiono *sizeDest*-1.

*other*<br/>
Inny `HStringReference` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje nową `HStringReference` obiekt, który jest taki sam rozmiar jak parametr *str*.

Inicjuje nowe wystąpienie drugi Konstruktor `HStringReference` obiekt specifeid rozmiaru za pomocą parametru *len*.

Trzeci Konstruktor inicjuje nowe `HStringReference` obiektu do wartości *innych* parametru, a następnie niszczy *innych* parametru.

## <a name="operator-assign"></a>HStringReference::operator =

Przenosi wartość innego `HStringReference` obiekt do bieżącego `HStringReference` obiektu.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parametry

*other*<br/>
Istniejące `HStringReference` obiektu.

### <a name="remarks"></a>Uwagi

Wartość istniejącego *innych* obiekt jest kopiowany do bieżącego `HStringReference` obiektu, a następnie *innych* niszczony jest obiekt.

## <a name="operator-equality"></a>HStringReference::operator ==

Wskazuje, czy dwa parametry są równe.

```cpp
inline bool operator==(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator==(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być `HStringReference` obiektu lub dojścia HSTRING.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być `HStringReference` obiektu lub dojścia HSTRING.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* i *rhs* parametry są równe; w przeciwnym razie **false**.

## <a name="operator-inequality"></a>HStringReference::operator! =

Wskazuje, czy dwa parametry nie są równe.

```cpp
inline bool operator!=(
               const HStringReference& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HSTRING& lhs,
               const HStringReference& rhs) throw()

inline bool operator!=(
               const HStringReference& lhs,
               const HSTRING& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być `HStringReference` obiektu lub dojścia HSTRING.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być `HStringReference` obiektu lub dojścia HSTRING.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* i *rhs* parametry nie są równe; w przeciwnym razie **false**.

## <a name="operator-less-than"></a>HStringReference::operator&lt;

Wskazuje, czy pierwszy parametr jest mniejszy od drugiego parametru.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lewa strona reguły przepisywania*<br/>
Pierwszy parametr do porównania. *Lewa strona reguły przepisywania* może być odwołaniem do `HStringReference`.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być odwołaniem do `HStringReference`.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli *lhs* parametr jest mniejsza niż *rhs* parametru; w przeciwnym razie **false**.
