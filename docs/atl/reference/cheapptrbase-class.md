---
title: Klasa CHeapPtrBase
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase
- ATLCORE/ATL::CHeapPtrBase::AllocateBytes
- ATLCORE/ATL::CHeapPtrBase::Attach
- ATLCORE/ATL::CHeapPtrBase::Detach
- ATLCORE/ATL::CHeapPtrBase::Free
- ATLCORE/ATL::CHeapPtrBase::ReallocateBytes
- ATLCORE/ATL::CHeapPtrBase::m_pData
helpviewer_keywords:
- CHeapPtrBase class
ms.assetid: 501ac1b2-fb34-4c72-b7e6-a4f1fc8fda21
ms.openlocfilehash: 62cabf281473cdf21fe260fa23082bc55f339849
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326903"
---
# <a name="cheapptrbase-class"></a>Klasa CHeapPtrBase

Ta klasa stanowi podstawę dla kilku klas wskaźnika sterty inteligentnej.

> [!IMPORTANT]
> Tej klasy i jej elementów członkowskich nie można używać w aplikacjach, które są wykonywane w czasie wykonywania systemu Windows.

## <a name="syntax"></a>Składnia

```
template <class T, class Allocator = CCRTAllocator>
class CHeapPtrBase
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ obiektu, który ma być przechowywany na stercie.

*Programu przydzielania*<br/>
Klasa alokacji pamięci do użycia. Domyślnie procedury CRT są używane do przydzielania i zwalniania pamięci.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Baza CHeapPtrBase::~CHeapPtrBase](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[Baza CHeapPtrBase::Przydzielanie bajtów](#allocatebytes)|Wywołanie tej metody, aby przydzielić pamięć.|
|[CHeapPtrBase::Dołącz](#attach)|Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.|
|[CHeapPtrBase::Detach](#detach)|Wywołanie tej metody, aby zwolnić własność wskaźnika.|
|[CHeapPtrBase::Wolny](#free)|Wywołanie tej metody, aby usunąć `CHeapPtrBase`obiekt wskazywał przez .|
|[Baza CHeapPtrBase::Ponowne przydzielanie bajtów](#reallocatebytes)|Wywołanie tej metody, aby ponownie przydzielić pamięć.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrBase::operator T*](#operator_t_star)|Operator odlewu.|
|[CHeapPtrBase::operator &](#operator_amp)|Operator &.|
|[CHeapPtrBase::operator ->](#operator_ptr)|Operator wskaźnik-element.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CHeapPtrBase::m_pData](#m_pdata)|Zmienna elementu członkowskiego danych wskaźnika.|

## <a name="remarks"></a>Uwagi

Ta klasa stanowi podstawę dla kilku klas wskaźnika sterty inteligentnej. Klasy pochodne, na przykład [CHeapPtr](../../atl/reference/cheapptr-class.md) i [CComHeapPtr](../../atl/reference/ccomheapptr-class.md), dodaj własne konstruktory i operatory. Zobacz te klasy przykłady implementacji.

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcore.h

## <a name="cheapptrbaseallocatebytes"></a><a name="allocatebytes"></a>Baza CHeapPtrBase::Przydzielanie bajtów

Wywołanie tej metody, aby przydzielić pamięć.

```
bool AllocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Liczba bajtów pamięci do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli pamięć została pomyślnie przydzielona, false w przeciwnym razie.

### <a name="remarks"></a>Uwagi

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej obecnie wskazuje na istniejącą wartość; oznacza to, że nie jest równa NULL.

## <a name="cheapptrbaseattach"></a><a name="attach"></a>CHeapPtrBase::Dołącz

Wywołanie tej metody, aby przejąć na własność istniejącego wskaźnika.

```
void Attach(T* pData) throw();
```

### <a name="parameters"></a>Parametry

*Pdata*<br/>
Obiekt `CHeapPtrBase` przejmie na własność ten wskaźnik.

### <a name="remarks"></a>Uwagi

Gdy `CHeapPtrBase` obiekt przejmuje na własność wskaźnik, automatycznie usunie wskaźnik i wszystkie przydzielone dane, gdy wyjdzie poza zakres.

W kompilacjach debugowania błąd potwierdzenia wystąpi, jeśli [CHeapPtrBase::m_pData](#m_pdata) zmiennej członkowskiej obecnie wskazuje na istniejącą wartość; oznacza to, że nie jest równa NULL.

## <a name="cheapptrbasecheapptrbase"></a><a name="dtor"></a>Baza CHeapPtrBase::~CHeapPtrBase

Destruktor.

```
~CHeapPtrBase() throw();
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="cheapptrbasedetach"></a><a name="detach"></a>CHeapPtrBase::Detach

Wywołanie tej metody, aby zwolnić własność wskaźnika.

```
T* Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca kopię wskaźnika.

### <a name="remarks"></a>Uwagi

Zwalnia własność wskaźnika, ustawia [zmienną CHeapPtrBase::m_pData](#m_pdata) zmienną elementu członkowskiego na null i zwraca kopię wskaźnika.

## <a name="cheapptrbasefree"></a><a name="free"></a>CHeapPtrBase::Wolny

Wywołanie tej metody, aby usunąć `CHeapPtrBase`obiekt wskazywał przez .

```
void Free() throw();
```

### <a name="remarks"></a>Uwagi

Obiekt wskazany przez `CHeapPtrBase` jest zwolniona, a zmienna [CHeapPtrBase::m_pData](#m_pdata) jest ustawiona na NULL.

## <a name="cheapptrbasem_pdata"></a><a name="m_pdata"></a>CHeapPtrBase::m_pData

Zmienna elementu członkowskiego danych wskaźnika.

```
T* m_pData;
```

### <a name="remarks"></a>Uwagi

Ta zmienna elementu członkowskiego zawiera informacje o wskaźniku.

## <a name="cheapptrbaseoperator-amp"></a><a name="operator_amp"></a>CHeapPtrBase::operator&amp;

Operator &.

```
T** operator&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca adres obiektu wskazywalnego przez `CHeapPtrBase` obiekt.

## <a name="cheapptrbaseoperator--gt"></a><a name="operator_ptr"></a>CHeapPtrBase::operator -&gt;

Operator wskaźnik-element.

```
T* operator->() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość zmiennej [CHeapPtrBase::m_pData](#m_pdata) element członkowski.

### <a name="remarks"></a>Uwagi

Ten operator służy do wywoływania metody w `CHeapPtrBase` klasie wskazywaluj przez obiekt. W kompilacjach debugowania błąd potwierdzenia `CHeapPtrBase` wystąpi, jeśli wskazuje wartość NULL.

## <a name="cheapptrbaseoperator-t"></a><a name="operator_t_star"></a>CHeapPtrBase::operator T*

Operator odlewu.

```
operator T*() const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca [CHeapPtrBase::m_pData](#m_pdata).

## <a name="cheapptrbasereallocatebytes"></a><a name="reallocatebytes"></a>Baza CHeapPtrBase::Ponowne przydzielanie bajtów

Wywołanie tej metody, aby ponownie przydzielić pamięć.

```
bool ReallocateBytes(size_t nBytes) throw();
```

### <a name="parameters"></a>Parametry

*n Bajty*<br/>
Nowa ilość pamięci do przydzielenia w bajtach.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, jeśli pamięć została pomyślnie przydzielona, false w przeciwnym razie.

## <a name="see-also"></a>Zobacz też

[Klasa CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Klasa CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
