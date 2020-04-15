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
ms.openlocfilehash: fd064f97081fad1a9df9de0865bb7c46ad5b4484
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371425"
---
# <a name="hstringreference-class"></a>HStringReference — Klasa

Reprezentuje HSTRING, który jest tworzony na podstawie istniejącego ciągu.

## <a name="syntax"></a>Składnia

```cpp
class HStringReference;
```

## <a name="remarks"></a>Uwagi

Okres istnienia buforu zapasowego w nowym HSTRING nie jest zarządzany przez środowisko wykonawcze systemu Windows. Wywołujący przydziela ciąg źródłowy w ramce stosu, aby uniknąć alokacji sterty i wyeliminować ryzyko wycieku pamięci. Ponadto obiektu wywołującego musi upewnić się, że ciąg źródłowy pozostaje niezmieniony w okresie istnienia dołączonego HSTRING. Aby uzyskać więcej informacji, zobacz [WindowsCreateStringReference funkcja](/windows/win32/api/winstring/nf-winstring-windowscreatestringreference).

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

Nazwa                                                    | Opis
------------------------------------------------------- | -----------------------------------------------------------
[HStringReference::HStringReference](#hstringreference) | Inicjuje nowe wystąpienie klasy `HStringReference`.

### <a name="public-methods"></a>Metody publiczne

Członek                              | Opis
----------------------------------- | ------------------------------------------------------------------
[HStringReference::CopyTo](#copyto) | Kopiuje `HStringReference` bieżący obiekt do obiektu HSTRING.
[HStringReference::Pobierz](#get)       | Pobiera wartość podstawowej dojścia HSTRING.
[HStringReference::GetRawBuffer](#getrawbuffer) | Pobiera wskaźnik do podstawowych danych ciągu.

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                                  | Opis
----------------------------------------------------- | ----------------------------------------------------------------------------------------------
[HStringReference::operator=](#operator-assign)       | Przenosi wartość innego `HStringReference` obiektu do `HStringReference` bieżącego obiektu.
[HStringReference::operator==](#operator-equality)    | Wskazuje, czy dwa parametry są równe.
[HStringReference::operator!=](#operator-inequality)  | Wskazuje, czy dwa parametry nie są równe.
[HStringReference::operator&lt;](#operator-less-than) | Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`HStringReference`

## <a name="requirements"></a>Wymagania

**Nagłówek:** corewrappers.h

**Obszar nazw:** Microsoft::WRL::Otoki

## <a name="hstringreferencecopyto"></a><a name="copyto"></a>HStringReference::CopyTo

Kopiuje `HStringReference` bieżący obiekt do obiektu HSTRING.

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

## <a name="hstringreferenceget"></a><a name="get"></a>HStringReference::Pobierz

Pobiera wartość podstawowej dojścia HSTRING.

```cpp
HSTRING Get() const throw()
```

### <a name="return-value"></a>Wartość zwracana

Wartość podstawowej dojścia HSTRING.

## <a name="hstringreferencegetrawbuffer"></a><a name="getrawbuffer"></a>HStringReference::GetRawBuffer

Pobiera wskaźnik do podstawowych danych ciągu.

```cpp
const wchar_t* GetRawBuffer(unsigned int* length) const;
```

### <a name="parameters"></a>Parametry

*długość* Wskaźnik do zmiennej **int,** która odbiera długość danych.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik **const** do podstawowych danych ciągu.

## <a name="hstringreferencehstringreference"></a><a name="hstringreference"></a>HStringReference::HStringReference

Inicjuje nowe wystąpienie klasy `HStringReference`.

```cpp
template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest]) throw();

template<unsigned int sizeDest>
HStringReference(wchar_t const (&str)[ sizeDest],
                 unsigned int len) throw();

HStringReference(HStringReference&& other) throw();
```

### <a name="parameters"></a>Parametry

*rozmiarDest*<br/>
Parametr szablonu określający rozmiar buforu docelowego. `HStringReference`

*Str*<br/>
Odwołanie do ciągu znaków o szerokim charakterze.

*len*<br/>
Maksymalna długość buforu parametrów *str* do użycia w tej operacji. Jeśli parametr *len* nie jest określony, używany jest cały parametr *str.* Jeśli *len* jest większy niż *rozmiarDest*, *len* jest ustawiony na *rozmiarDest*-1.

*Innych*<br/>
Inny `HStringReference` obiekt.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor inicjuje nowy `HStringReference` obiekt o tym samym rozmiarze co parametr *str*.

Drugi konstruktor inicjuje nowy `HStringReference` obiekt, który rozmiar specifeid przez parametr *len*.

Trzeci konstruktor inicjuje nowy `HStringReference` obiekt do wartości *innego* parametru, a następnie niszczy *inny* parametr.

## <a name="hstringreferenceoperator"></a><a name="operator-assign"></a>HStringReference::operator=

Przenosi wartość innego `HStringReference` obiektu do `HStringReference` bieżącego obiektu.

```cpp
HStringReference& operator=(HStringReference&& other) throw()
```

### <a name="parameters"></a>Parametry

*Innych*<br/>
Istniejący `HStringReference` obiekt.

### <a name="remarks"></a>Uwagi

Wartość istniejącego *innego* obiektu jest kopiowana `HStringReference` do bieżącego obiektu, a następnie *drugi* obiekt jest niszczony.

## <a name="hstringreferenceoperator"></a><a name="operator-equality"></a>HStringReference::operator==

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

*Lhs*<br/>
Pierwszy parametr do porównania. *może* być obiektem `HStringReference` lub uchwytem HSTRING.

*Rhs*<br/>
Drugi parametr do porównania.  *może* być obiektem `HStringReference` lub uchwytem HSTRING.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli parametry *lhs* i *rhs* są równe; w przeciwnym razie **false**.

## <a name="hstringreferenceoperator"></a><a name="operator-inequality"></a>HStringReference::operator!=

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

*Lhs*<br/>
Pierwszy parametr do porównania. *może* być obiektem `HStringReference` lub uchwytem HSTRING.

*Rhs*<br/>
Drugi parametr do porównania.  *może* być obiektem `HStringReference` lub uchwytem HSTRING.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli parametry *lhs* i *rhs* nie są równe; w przeciwnym razie **false**.

## <a name="hstringreferenceoperatorlt"></a><a name="operator-less-than"></a>HStringReference::operator&lt;

Wskazuje, czy pierwszy parametr jest mniejszy niż drugi parametr.

```cpp
inline bool operator<(
    const HStringReference& lhs,
    const HStringReference& rhs) throw()
```

### <a name="parameters"></a>Parametry

*Lhs*<br/>
Pierwszy parametr do porównania. *może* być odniesieniem `HStringReference`do .

*Rhs*<br/>
Drugi parametr do porównania.  *może* być odniesieniem `HStringReference`do .

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli parametr *lhs* jest mniejszy niż parametr *rhs;* w przeciwnym razie **false**.
