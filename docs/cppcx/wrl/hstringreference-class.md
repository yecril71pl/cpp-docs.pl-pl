---
title: HStringReference — Klasa
ms.date: 07/15/2019
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HStringReference
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::CopyTo
- corewrappers/Microsoft::WRL::Wrappers::HStringReference::Get
- corewrappers/Microsoft::WRL::Wrappers::GetRawBuffer
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
ms.openlocfilehash: 591af0d66c9c209ba56310a0bd5cf5cd74e34929
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498353"
---
# <a name="hstringreference-class"></a>HStringReference — Klasa

Reprezentuje element HSTRING, który jest tworzony na podstawie istniejącego ciągu.

## <a name="syntax"></a>Składnia

```cpp
class HStringReference;
```

## <a name="remarks"></a>Uwagi

Okres istnienia buforu zapasowego w nowym HSTRING nie jest zarządzany przez środowisko wykonawcze systemu Windows. Obiekt wywołujący przydziela ciąg źródłowy w ramce stosu, aby uniknąć alokacji sterty i wyeliminować ryzyko przecieku pamięci. Ponadto obiekt wywołujący musi upewnić się, że ciąg źródłowy pozostanie niezmieniony w czasie trwania dołączonego HSTRING. Aby uzyskać więcej informacji, zobacz [Funkcja WindowsCreateStringReference](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference:: HStringReference](#hstringreference) | Inicjuje nowe wystąpienie klasy `HStringReference` klasy.

### <a name="public-methods"></a>Metody publiczne

Element członkowski                              | Opis
----------------------------------- | ------------------------------------------------------------------
[HStringReference:: CopyTo](#copyto) | Kopiuje bieżący `HStringReference` obiekt do obiektu HSTRING.
[HStringReference:: Get](#get)       | Pobiera wartość bazowego uchwytu HSTRING.
[HStringReference:: GetRawBuffer](#getrawbuffer) | Pobiera wskaźnik do danych ciągu bazowego.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference:: operator =](#operator-assign)       | Przenosi wartość innego `HStringReference` obiektu do bieżącego `HStringReference` obiektu.
[HStringReference:: operator = =](#operator-equality)    | Wskazuje, czy dwa parametry są równe.
[HStringReference:: operator! =](#operator-inequality)  | Wskazuje, czy dwa parametry nie są równe.
[HStringReference:: operator&lt;](#operator-less-than) | Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HStringReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers. h

**Obszaru** Microsoft:: WRL:: otoki

## <a name="copyto"></a>HStringReference:: CopyTo

Kopiuje bieżący `HStringReference` obiekt do obiektu HSTRING.

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

## <a name="get"></a>HStringReference:: Get

Pobiera wartość bazowego uchwytu HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość bazowego uchwytu HSTRING.

## <a name="getrawbuffer"></a>HStringReference:: GetRawBuffer

Pobiera wskaźnik do danych ciągu bazowego.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```
### <a name="parameters"></a>Parametry

*Długość* Wskaźnik do zmiennej **int** , która otrzymuje długość danych.

### <a name="return-value"></a>Wartość zwracana

Stały wskaźnik do danych ciągu bazowego.

## <a name="hstringreference"></a>HStringReference:: HStringReference

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
Parametr szablonu, który określa rozmiar buforu docelowego `HStringReference` .

*str*<br/>
Odwołanie do ciągu znaków dwubajtowych.

*Funkcja*<br/>
Maksymalna długość buforu parametrów *str* , która ma być używana w tej operacji. Jeśli parametr *len* nie jest określony, zostanie użyty cały parametr *str* . Jeśli wartość *len* jest większaniż wartość, *len* jest ustawiony na1.

*other*<br/>
Inny `HStringReference` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor inicjuje nowy `HStringReference` obiekt, który ma taki sam rozmiar jak parametr *str*.

Drugi Konstruktor inicjuje nowy `HStringReference` obiekt, którego rozmiar specifeid przez parametr *len*.

Trzeci Konstruktor inicjuje nowy `HStringReference` obiekt do wartości *innego* parametru, a następnie niszczy *inny* parametr.

## <a name="operator-assign"></a>HStringReference:: operator =

Przenosi wartość innego `HStringReference` obiektu do bieżącego `HStringReference` obiektu.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parametry

*other*<br/>
Istniejący `HStringReference` obiekt.

### <a name="remarks"></a>Uwagi

Wartość istniejącego *innego* obiektu jest kopiowana do bieżącego `HStringReference` obiektu, a następnie *drugi* obiekt zostanie zniszczony.

## <a name="operator-equality"></a>HStringReference:: operator = =

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

*LHS*<br/>
Pierwszy parametr do porównania. *LHS* może być `HStringReference` obiektem lub dojściem HSTRING.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być `HStringReference` obiektem lub uchwytem HSTRING.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli parametry *LHS* i *RHS* są równe; w przeciwnym razie **false**.

## <a name="operator-inequality"></a>HStringReference:: operator! =

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

*LHS*<br/>
Pierwszy parametr do porównania. *LHS* może być `HStringReference` obiektem lub dojściem HSTRING.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być `HStringReference` obiektem lub uchwytem HSTRING.

### <a name="return-value"></a>Wartość zwracana

**prawda** , jeśli parametry *LHS* i *RHS* nie są równe; w przeciwnym razie **false**.

## <a name="operator-less-than"></a>HStringReference:: operator&lt;

Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parametry

*LHS*<br/>
Pierwszy parametr do porównania. *LHS* może być odwołaniem do `HStringReference`.

*RHS*<br/>
Drugi parametr do porównania.  *RHS* może być odwołaniem do `HStringReference`.

### <a name="return-value"></a>Wartość zwracana

**ma wartość true** , jeśli parametr *LHS* jest mniejszy niż parametr *RHS* ; w przeciwnym razie **false**.
