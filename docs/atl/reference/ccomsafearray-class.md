---
title: CComSafeArray Class
ms.date: 11/04/2016
f1_keywords:
- CComSafeArray
- ATLSAFE/ATL::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::CComSafeArray
- ATLSAFE/ATL::CComSafeArray::Add
- ATLSAFE/ATL::CComSafeArray::Attach
- ATLSAFE/ATL::CComSafeArray::CopyFrom
- ATLSAFE/ATL::CComSafeArray::CopyTo
- ATLSAFE/ATL::CComSafeArray::Create
- ATLSAFE/ATL::CComSafeArray::Destroy
- ATLSAFE/ATL::CComSafeArray::Detach
- ATLSAFE/ATL::CComSafeArray::GetAt
- ATLSAFE/ATL::CComSafeArray::GetCount
- ATLSAFE/ATL::CComSafeArray::GetDimensions
- ATLSAFE/ATL::CComSafeArray::GetLowerBound
- ATLSAFE/ATL::CComSafeArray::GetSafeArrayPtr
- ATLSAFE/ATL::CComSafeArray::GetType
- ATLSAFE/ATL::CComSafeArray::GetUpperBound
- ATLSAFE/ATL::CComSafeArray::IsSizable
- ATLSAFE/ATL::CComSafeArray::MultiDimGetAt
- ATLSAFE/ATL::CComSafeArray::MultiDimSetAt
- ATLSAFE/ATL::CComSafeArray::Resize
- ATLSAFE/ATL::CComSafeArray::SetAt
- ATLSAFE/ATL::CComSafeArray::m_psa
helpviewer_keywords:
- CComSafeArray class
ms.assetid: ee349aef-33db-4c85-bd08-5d86a3c9d53a
ms.openlocfilehash: 0262764c950b01acdb610873a995a9a6fd912997
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259446"
---
# <a name="ccomsafearray-class"></a>CComSafeArray Class

Ta klasa jest otoką `SAFEARRAY` struktury.

## <a name="syntax"></a>Składnia

```
template <typename T, VARTYPE _vartype = _ATL_AutomationType<T>::type>
class CComSafeArray
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ danych, które mają być przechowywane w tablicy.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::CComSafeArray](#ccomsafearray)|Konstruktor.|
|[CComSafeArray::~CComSafeArray](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::Add](#add)|Dodaje jeden lub więcej elementów lub `SAFEARRAY` struktury do `CComSafeArray`.|
|[CComSafeArray::Attach](#attach)|Dołącza `SAFEARRAY` struktury do `CComSafeArray` obiektu.|
|[CComSafeArray::CopyFrom](#copyfrom)|Kopiuje zawartość `SAFEARRAY` struktury do `CComSafeArray` obiektu.|
|[CComSafeArray::CopyTo](#copyto)|Tworzy kopię `CComSafeArray` obiektu.|
|[CComSafeArray::Create](#create)|Tworzy `CComSafeArray` obiektu.|
|[CComSafeArray::Destroy](#destroy)|Niszczy `CComSafeArray` obiektu.|
|[CComSafeArray::Detach](#detach)|Odłącza `SAFEARRAY` z `CComSafeArray` obiektu.|
|[CComSafeArray::GetAt](#getat)|Pobiera pojedynczy element z tablicy jednowymiarowej.|
|[CComSafeArray::GetCount](#getcount)|Zwraca liczbę elementów w tablicy.|
|[CComSafeArray::GetDimensions](#getdimensions)|Zwraca liczbę wymiarów w tablicy.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Zwraca dolną granicę dla danego wymiaru tablicy.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Zwraca adres `m_psa` element członkowski danych.|
|[CComSafeArray::GetType](#gettype)|Zwraca typ danych przechowywanych w tablicy.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Zwraca górną granicę dla każdego wymiaru tablicy.|
|[CComSafeArray::IsSizable](#issizable)|Sprawdza, czy `CComSafeArray` można zmienić rozmiar obiektu.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Pobiera pojedynczy element z tablicy wielowymiarowej.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Ustawia wartość elementu w tablicy wielowymiarowej.|
|[CComSafeArray::Resize](#resize)|Zmienia rozmiar `CComSafeArray` obiektu.|
|[CComSafeArray::SetAt](#setat)|Ustawia wartość elementu w tablicy jednowymiarowej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Rzutuje wartość `SAFEARRAY` wskaźnika.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Pobiera element z tablicy.|
|[CComSafeArray::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Ten element członkowski danych przechowuje adres `SAFEARRAY` struktury.|

## <a name="remarks"></a>Uwagi

`CComSafeArray` udostępnia otokę dla [SAFEARRAY — typ danych](/windows/desktop/api/oaidl/ns-oaidl-tagsafearray) klasy, dzięki czemu polegać na tworzenie i zarządzanie nimi jedno - i tablice wielowymiarowe z niemal dowolnego typu VARIANT, obsługiwane.

`CComSafeArray` upraszcza przekazywanie tablic między procesami, a ponadto oferuje zapewnienia dodatkowego bezpieczeństwa przez sprawdzenie wartości indeksu tablicy względem górnej i dolne granice.

Dolna granica `CComSafeArray` można uruchomić w dowolnej wartości zdefiniowanej przez użytkownika; jednak używać tablic, które są dostępne za pośrednictwem C++ dolna granica 0. Innych języków, takich jak Visual Basic mogą używać innych otaczający wartości (na przykład, -10-10).

Użyj [CComSafeArray::Create](#create) utworzyć `CComSafeArray` obiektu, a [CComSafeArray::Destroy](#destroy) go usunąć.

Element `CComSafeArray` może zawierać następujące podzbiór typów danych VARIANT:

|VARTYPE|Opis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|wskaźnik dziesiętna|
|VT_VARIANT|wskaźnik typu Variant|
|VT_CY|Currency — Typ danych|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsafe.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>  CComSafeArray::Add

Dodaje jeden lub więcej elementów lub `SAFEARRAY` struktury do `CComSafeArray`.

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` obiektu.

*ulCount*<br/>
Liczba obiektów do dodania do tablicy.

*pT*<br/>
Wskaźnik do jednego lub kilku obiektów do dodania do tablicy.

*t*<br/>
Odwołanie do obiektu, który ma zostać dodany do tablicy.

*bCopy*<br/>
Wskazuje, czy należy utworzyć kopię danych. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Nowe obiekty są dołączane na końcu istniejącego `SAFEARRAY` obiektu. Dodanie obiektu do wielowymiarowe `SAFEARRAY` obiekt nie jest obsługiwany. Podczas dodawania istniejącej tablicy obiektów, w obu tablicach musi zawierać elementów tego samego typu.

*BCopy* flaga jest brana pod uwagę podczas dodawania elementów typu BSTR lub wariant do tablicy. Domyślna wartość TRUE gwarantuje, że nowa kopia składa się z danych, gdy element zostanie dodany do tablicy.

##  <a name="attach"></a>  CComSafeArray::Attach

Dołącza `SAFEARRAY` struktury do `CComSafeArray` obiektu.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dołącza `SAFEARRAY` struktury do `CComSafeArray` obiektu, dzięki czemu istniejący `CComSafeArray` dostępnych metod.

##  <a name="ccomsafearray"></a>  CComSafeArray::CComSafeArray

Konstruktor.

```
CComSafeArray();
CComSafeArray(const SAFEARRAYBOUND& bound);
CComSafeArray(ULONG  ulCount, LONG lLBound = 0);
CComSafeArray(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
CComSafeArray(const CComSafeArray& saSrc);
CComSafeArray(const SAFEARRAY& saSrc);
CComSafeArray(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*powiązane*<br/>
A `SAFEARRAYBOUND` struktury.

*ulCount*<br/>
Liczba elementów w tablicy.

*lLBound*<br/>
Dolna granica wartości. oznacza to, że indeks pierwszego elementu w tablicy.

*pBound*<br/>
Wskaźnik do `SAFEARRAYBOUND` struktury.

*uDims*<br/>
Liczba wymiarów w tablicy.

*saSrc*<br/>
Odwołanie do `SAFEARRAY` struktury lub `CComSafeArray` obiektu. W obu przypadkach konstruktora używa tego odwołania do skopiowania tablicy, więc tablicy nie jest wywoływany po konstrukcji.

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` struktury. Konstruktor używa tego adresu do skopiowania tablicy, więc tablicy nie jest wywoływany po konstrukcji.

### <a name="remarks"></a>Uwagi

Tworzy `CComSafeArray` obiektu.

##  <a name="dtor"></a>  CComSafeArray::~CComSafeArray

Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

##  <a name="copyfrom"></a>  CComSafeArray::CopyFrom

Kopiuje zawartość `SAFEARRAY` struktury do `CComSafeArray` obiektu.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Wskaźnik do `SAFEARRAY` do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje zawartość `SAFEARRAY` do bieżącej `CComSafeArray` obiektu. Zastępuje się istniejącą zawartość elementu tablicy.

##  <a name="copyto"></a>  CComSafeArray::CopyTo

Tworzy kopię `CComSafeArray` obiektu.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Wskaźnik do lokalizacji, w której chcesz utworzyć nowy `SAFEARRAY`.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje zawartość `CComSafeArray` do obiektu `SAFEARRAY` struktury.

##  <a name="create"></a>  CComSafeArray::Create

Tworzy `CComSafeArray`.

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Wskaźnik do `SAFEARRAYBOUND` obiektu.

*uDims*<br/>
Liczba wymiarów w tablicy.

*ulCount*<br/>
Liczba elementów w tablicy.

*lLBound*<br/>
Dolna granica wartości. oznacza to, że indeks pierwszego elementu w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

A `CComSafeArray` obiektu można tworzyć na podstawie istniejącego `SAFEARRAYBOUND` struktury i liczbę wymiarów, lub przez określenie liczby elementów w tablicy i dolną granicę. Jeśli tablica jest były dostępne z Visual C++, dolna granica powinna być równa 0. Inne języki mogą zezwalać innych wartości dolna granica (na przykład Visual Basic obsługuje tablic przy użyciu elementów z zakresu, takie jak -10-10).

##  <a name="destroy"></a>  CComSafeArray::Destroy

Niszczy `CComSafeArray` obiektu.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Niszczy istniejące `CComSafeArray` obiekt i wszystkie dane w nim zawarte.

##  <a name="detach"></a>  CComSafeArray::Detach

Odłącza `SAFEARRAY` z `CComSafeArray` obiektu.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `SAFEARRAY` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda powoduje odłączenie `SAFEARRAY` obiektu z `CComSafeArray` obiektu.

##  <a name="getat"></a>  CComSafeArray::GetAt

Pobiera pojedynczy element z tablicy jednowymiarowej.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parametry

*lIndex*<br/>
Numer indeksu wartości w tablicy do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do elementu tablicy wymagane.

##  <a name="getcount"></a>  CComSafeArray::GetCount

Zwraca liczbę elementów w tablicy.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Wymiar tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w tablicy.

### <a name="remarks"></a>Uwagi

W przypadku użycia z tablicą wielowymiarową, ta metoda zwróci liczbę elementów tylko określonego wymiaru.

##  <a name="getdimensions"></a>  CComSafeArray::GetDimensions

Zwraca liczbę wymiarów w tablicy.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wymiarów w tablicy.

##  <a name="getlowerbound"></a>  CComSafeArray::GetLowerBound

Zwraca dolną granicę dla danego wymiaru tablicy.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Wymiar tablicy, dla którego należy pobrać dolną granicę. Jeśli argument jest pominięty, wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Zwraca dolną granicę.

### <a name="remarks"></a>Uwagi

Jeśli dolna granica jest równa 0, oznacza to, tablicy notacji języka C, w której pierwszy element jest elementem numer 0. W przypadku wystąpienia błędu, na przykład wymiar nieprawidłowy argument, ta metoda wywołuje `AtlThrow` z opisem błędu HRESULT.

##  <a name="getsafearrayptr"></a>  CComSafeArray::GetSafeArrayPtr

Zwraca adres `m_psa` element członkowski danych.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do [CComSafeArray::m_psa](#m_psa) element członkowski danych.

##  <a name="gettype"></a>  CComSafeArray::GetType

Zwraca typ danych przechowywanych w tablicy.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca typ danych przechowywanych w tablicy, która może być dowolny z następujących typów:

|VARTYPE|Opis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|longlong|
|VT_UI1|byte|
|VT_UI2|ushort|
|VT_UI4|uint|
|VT_UI4|ulong|
|VT_UI8|ulonglong|
|VT_R4|float|
|VT_R8|double|
|VT_DECIMAL|wskaźnik dziesiętna|
|VT_VARIANT|wskaźnik typu Variant|
|VT_CY|Currency — Typ danych|

##  <a name="getupperbound"></a>  CComSafeArray::GetUpperBound

Zwraca górną granicę dla każdego wymiaru tablicy.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Wymiar tablicy, dla którego należy pobrać górną granicę. Jeśli argument jest pominięty, wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Zwraca górną granicę. Ta wartość jest włącznie, maksymalna wartość indeksu nieprawidłowy dla tego wymiaru.

### <a name="remarks"></a>Uwagi

W przypadku wystąpienia błędu, na przykład wymiar nieprawidłowy argument, ta metoda wywołuje `AtlThrow` z opisem błędu HRESULT.

##  <a name="issizable"></a>  CComSafeArray::IsSizable

Sprawdza, czy `CComSafeArray` można zmienić rozmiar obiektu.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli `CComSafeArray` rozmiar można zmieniać, FAŁSZ. Jeśli jest ona nieosiągalna.

##  <a name="m_psa"></a>  CComSafeArray::m_psa

Przechowuje adres `SAFEARRAY` struktury dostępne.

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>  CComSafeArray::MultiDimGetAt

Pobiera pojedynczy element z tablicy wielowymiarowej.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Wskaźnik do wektora indeksów dla każdego wymiaru tablicy. Skrajnie po lewej stronie (najbardziej znaczących) wymiar jest `alIndex[0]`.

*t*<br/>
Zwracane odwołanie do danych.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

##  <a name="multidimsetat"></a>  CComSafeArray::MultiDimSetAt

Ustawia wartość elementu w tablicy wielowymiarowej.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Wskaźnik do wektora indeksów dla każdego wymiaru tablicy. Po prawej stronie (najmniej znaczący) wymiar jest `alIndex`[0].

*T*<br/>
Określa wartość nowego elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

To jest wersja wielowymiarowe [CComSafeArray::SetAt](#setat).

##  <a name="operator_at"></a>  CComSafeArray::operator \[\]

Pobiera element z tablicy.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parametry

*wartość, nIndex lindex.*<br/>
Numer indeksu wymaganego elementu w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca element odpowiedniej tablicy.

### <a name="remarks"></a>Uwagi

Pełni funkcję podobną do [CComSafeArray::GetAt](#getat), ale ten operator działa tylko tablice jednowymiarowe.

##  <a name="operator_eq"></a>  CComSafeArray::operator =

Operator przypisania.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*saSrc*<br/>
Odwołanie do `CComSafeArray` obiektu.

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca typ danych przechowywanych w tablicy.

##  <a name="operator_lpsafearray"></a>  CComSafeArray::operator LPSAFEARRAY

Rzutuje wartość `SAFEARRAY` wskaźnika.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Wartość zwracana

Rzutuje wartość `SAFEARRAY` wskaźnika.

##  <a name="resize"></a>  CComSafeArray::Resize

Zmienia rozmiar `CComSafeArray` obiektu.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Wskaźnik do `SAFEARRAYBOUND` strukturę, która zawiera informacje na temat liczby elementów i dolną granicę tablicy.

*ulCount*<br/>
Żądana liczba obiektów w tablicy o zmienionym rozmiarze.

*lLBound*<br/>
Dolna granica.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda zmienia tylko po prawej stronie wymiaru. Nie będzie zmiana rozmiaru tablic, które zwracają `IsResizable` jako FAŁSZ.

##  <a name="setat"></a>  CComSafeArray::SetAt

Ustawia wartość elementu w tablicy jednowymiarowej.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*lIndex*<br/>
Numer indeksu elementu tablicy, aby ustawić.

*t*<br/>
Nowa wartość określonego elementu.

*bCopy*<br/>
Wskazuje, czy należy utworzyć kopię danych. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość S_OK w przypadku powodzenia lub błędu HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

*BCopy* flaga jest brana pod uwagę podczas dodawania elementów typu BSTR lub wariant do tablicy. Domyślna wartość TRUE gwarantuje, że nowa kopia składa się z danych, gdy element zostanie dodany do tablicy.

## <a name="see-also"></a>Zobacz także

[SAFEARRAY — typ danych](/windows/desktop/api/oaidl/ns-oaidl-tagsafearray)<br/>
[CComSafeArray::Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Klasa — Przegląd](../../atl/atl-class-overview.md)
