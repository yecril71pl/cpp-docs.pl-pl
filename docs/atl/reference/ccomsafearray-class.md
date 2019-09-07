---
title: Klasa CComSafeArray
ms.date: 05/06/2019
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
ms.openlocfilehash: 79b1dc844f53f739dc48eb6177e57810ff0c8412
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2019
ms.locfileid: "70739592"
---
# <a name="ccomsafearray-class"></a>Klasa CComSafeArray

Ta klasa jest otoką dla `SAFEARRAY` struktury.

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
|[CComSafeArray:: Add](#add)|Dodaje co najmniej jeden element lub `SAFEARRAY` strukturę do elementu. `CComSafeArray`|
|[CComSafeArray::Attach](#attach)|`SAFEARRAY` Dołącza strukturę`CComSafeArray` do obiektu.|
|[CComSafeArray::CopyFrom](#copyfrom)|Kopiuje zawartość `SAFEARRAY` struktury `CComSafeArray` do obiektu.|
|[CComSafeArray::CopyTo](#copyto)|Tworzy kopię `CComSafeArray` obiektu.|
|[CComSafeArray:: Create](#create)|`CComSafeArray` Tworzy obiekt.|
|[CComSafeArray::Destroy](#destroy)|`CComSafeArray` Niszczy obiekt.|
|[CComSafeArray::Detach](#detach)|`SAFEARRAY` Odłącza`CComSafeArray` od obiektu.|
|[CComSafeArray::GetAt](#getat)|Pobiera pojedynczy element z tablicy jednowymiarowej.|
|[CComSafeArray:: GetCount](#getcount)|Zwraca liczbę elementów w tablicy.|
|[CComSafeArray:: GetDimensions](#getdimensions)|Zwraca liczbę wymiarów w tablicy.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Zwraca dolną granicę dla danego wymiaru tablicy.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Zwraca adres `m_psa` elementu członkowskiego danych.|
|[CComSafeArray::GetType](#gettype)|Zwraca typ danych przechowywanych w tablicy.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Zwraca górną granicę dla każdego wymiaru tablicy.|
|[CComSafeArray::IsSizable](#issizable)|Testuje, `CComSafeArray` czy można zmienić rozmiar obiektu.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Pobiera pojedynczy element z tablicy wielowymiarowej.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Ustawia wartość elementu w tablicy wielowymiarowej.|
|[CComSafeArray:: Resize](#resize)|Zmienia rozmiar `CComSafeArray` obiektu.|
|[CComSafeArray::SetAt](#setat)|Ustawia wartość elementu w tablicy jednowymiarowej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray:: operator LPSAFEARRAY](#operator_lpsafearray)|Rzutuje wartość na `SAFEARRAY` wskaźnik.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Pobiera element z tablicy.|
|[CComSafeArray:: operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Ten element członkowski danych przechowuje adres `SAFEARRAY` struktury.|

## <a name="remarks"></a>Uwagi

`CComSafeArray`udostępnia otokę dla klasy [typu danych SAFEARRAY](/windows/win32/api/oaidl/ns-oaidl-safearray) , co sprawia, że proste tworzenie i zarządzanie tablicą pojedynczą i wielowymiarową niemal dowolnego typu obsługiwanego przez warianty.

`CComSafeArray`upraszcza Przekazywanie tablic między procesami, a ponadto zapewnia dodatkowe zabezpieczenia, sprawdzając wartości indeksu tablicy względem górnego i dolnego granic.

Dolna granica `CComSafeArray` może rozpoczynać się od dowolnej wartości zdefiniowanej przez użytkownika, natomiast tablice, do których C++ dostęp odbywa się za pomocą powinny używać dolnej granicy 0. Inne języki, takie jak Visual Basic mogą używać innych wartości związanych z wartościami (na przykład-10 do 10).

Użyj [CComSafeArray:: Create](#create) , aby utworzyć `CComSafeArray` obiekt, i [CComSafeArray::D Estroy](#destroy) , aby go usunąć.

`CComSafeArray` Może zawierać następujący podzbiór typów danych Variant:

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
|VT_DECIMAL|wskaźnik dziesiętny|
|VT_VARIANT|wskaźnik wariantu|
|VT_CY|Currency — Typ danych|

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlsafe. h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

##  <a name="add"></a>CComSafeArray:: Add

Dodaje co najmniej jeden element lub `SAFEARRAY` strukturę do elementu. `CComSafeArray`

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

*Zmiennoprzecinkow*<br/>
Wskaźnik do co najmniej jednego obiektu, który ma zostać dodany do tablicy.

*t*<br/>
Odwołanie do obiektu, który ma zostać dodany do tablicy.

*bCopy*<br/>
Wskazuje, czy ma zostać utworzona kopia danych. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Nowe obiekty są dołączane na końcu istniejącego `SAFEARRAY` obiektu. Dodawanie obiektu do obiektu wielowymiarowego `SAFEARRAY` nie jest obsługiwane. Podczas dodawania istniejącej tablicy obiektów obie tablice muszą zawierać elementy tego samego typu.

Flaga *bCopy* jest brana pod uwagę, gdy elementy typu BSTR lub Variant są dodawane do tablicy. Wartość domyślna TRUE zapewnia nową kopię danych, gdy element zostanie dodany do tablicy.

##  <a name="attach"></a>CComSafeArray:: Attach

`SAFEARRAY` Dołącza strukturę`CComSafeArray` do obiektu.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Dołącza strukturę do obiektu, udostępniając istniejące `CComSafeArray` dostępne metody. `CComSafeArray` `SAFEARRAY`

##  <a name="ccomsafearray"></a>CComSafeArray::CComSafeArray

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

*obowiązując*<br/>
`SAFEARRAYBOUND` Struktura.

*ulCount*<br/>
Liczba elementów w tablicy.

*lLBound*<br/>
Dolna granica wartości; oznacza to indeks pierwszego elementu w tablicy.

*pBound*<br/>
Wskaźnik do `SAFEARRAYBOUND` struktury.

*uDims*<br/>
Liczba wymiarów w tablicy.

*saSrc*<br/>
Odwołanie do `SAFEARRAY` struktury lub `CComSafeArray` obiektu. W obu przypadkach Konstruktor używa tego odwołania, aby utworzyć kopię tablicy, więc tablica nie jest przywoływana po konstrukcji.

*psaSrc*<br/>
Wskaźnik do `SAFEARRAY` struktury. Konstruktor używa tego adresu, aby utworzyć kopię tablicy, więc tablica nie jest przywoływana po konstrukcji.

### <a name="remarks"></a>Uwagi

`CComSafeArray` Tworzy obiekt.

##  <a name="dtor"></a>CComSafeArray:: ~ CComSafeArray

Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzieloną zasoby.

##  <a name="copyfrom"></a>CComSafeArray::CopyFrom

Kopiuje zawartość `SAFEARRAY` struktury `CComSafeArray` do obiektu.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
`SAFEARRAY` Wskaźnik na kopię.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje zawartość `SAFEARRAY` do bieżącego `CComSafeArray` obiektu. Istniejąca zawartość tablicy zostanie zastąpiona.

##  <a name="copyto"></a>CComSafeArray:: CopyTo

Tworzy kopię `CComSafeArray` obiektu.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
Wskaźnik do lokalizacji, w której ma zostać utworzony nowy `SAFEARRAY`.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje zawartość `CComSafeArray` obiektu `SAFEARRAY` do struktury.

##  <a name="create"></a>CComSafeArray:: Create

`CComSafeArray`Tworzy.

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
Dolna granica wartości; oznacza to indeks pierwszego elementu w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Obiekt można utworzyć na podstawie istniejącej `SAFEARRAYBOUND` struktury i liczby wymiarów lub określić liczbę elementów w tablicy oraz dolną granicę. `CComSafeArray` Jeśli tablica ma być dostępna z C++, Dolna granica powinna być równa 0. Inne języki mogą zezwalać na inne wartości dla dolnego ograniczenia (na przykład Visual Basic obsługuje tablice z elementami o zakresie od-10 do 10).

##  <a name="destroy"></a>  CComSafeArray::Destroy

`CComSafeArray` Niszczy obiekt.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Niszczy istniejący `CComSafeArray` obiekt i wszystkie zawarte w nim dane.

##  <a name="detach"></a>CComSafeArray::D etach

`SAFEARRAY` Odłącza`CComSafeArray` od obiektu.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `SAFEARRAY` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda odłącza `SAFEARRAY` obiekt `CComSafeArray` od obiektu.

##  <a name="getat"></a>CComSafeArray::GetAt

Pobiera pojedynczy element z tablicy jednowymiarowej.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parametry

*lIndex*<br/>
Numer indeksu wartości w tablicy, która ma zostać zwrócona.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wymaganego elementu tablicy.

##  <a name="getcount"></a>CComSafeArray:: GetCount

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

Gdy jest używana z tablicą wielowymiarową, ta metoda zwróci liczbę elementów tylko w określonym wymiarze.

##  <a name="getdimensions"></a>CComSafeArray:: GetDimensions

Zwraca liczbę wymiarów w tablicy.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wymiarów w tablicy.

##  <a name="getlowerbound"></a>CComSafeArray::GetLowerBound

Zwraca dolną granicę dla danego wymiaru tablicy.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Wymiar tablicy, dla którego należy uzyskać dolną granicę. W przypadku pominięcia wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Zwraca dolną granicę.

### <a name="remarks"></a>Uwagi

Jeśli Dolna granica to 0, oznacza to tablicę podobną do języka C, której pierwszy element jest elementem o numerze 0. W przypadku błędu, na przykład nieprawidłowego argumentu wymiaru, ta metoda wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

##  <a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Zwraca adres `m_psa` elementu członkowskiego danych.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do elementu członkowskiego danych [CComSafeArray:: m_psa](#m_psa) .

##  <a name="gettype"></a>CComSafeArray:: GetType

Zwraca typ danych przechowywanych w tablicy.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca typ danych przechowywanych w tablicy, które mogą być jednym z następujących typów:

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
|VT_DECIMAL|wskaźnik dziesiętny|
|VT_VARIANT|wskaźnik wariantu|
|VT_CY|Currency — Typ danych|

##  <a name="getupperbound"></a>CComSafeArray::GetUpperBound

Zwraca górną granicę dla każdego wymiaru tablicy.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim*<br/>
Wymiar tablicy, dla którego należy uzyskać górną granicę. W przypadku pominięcia wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Zwraca górną granicę. Ta wartość obejmuje maksymalny prawidłowy indeks dla tego wymiaru.

### <a name="remarks"></a>Uwagi

W przypadku błędu, na przykład nieprawidłowego argumentu wymiaru, ta metoda wywołuje `AtlThrow` wynik HRESULT opisujący błąd.

##  <a name="issizable"></a>CComSafeArray:: iszmienny

Testuje, `CComSafeArray` czy można zmienić rozmiar obiektu.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość true, `CComSafeArray` Jeśli można zmienić rozmiar rozmiaru, FAŁSZ, jeśli nie.

##  <a name="m_psa"></a>  CComSafeArray::m_psa

Przechowuje adres `SAFEARRAY` używanej struktury.

```
LPSAFEARRAY m_psa;
```

##  <a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt

Pobiera pojedynczy element z tablicy wielowymiarowej.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Wskaźnik do wektora indeksów dla każdego wymiaru w tablicy. Skrajny lewy (najbardziej znaczący) `alIndex[0]`wymiar to.

*t*<br/>
Odwołanie do zwracanych danych.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

##  <a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt

Ustawia wartość elementu w tablicy wielowymiarowej.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parametry

*alIndex*<br/>
Wskaźnik do wektora indeksów dla każdego wymiaru w tablicy. Skrajny prawy (najmniej znaczący) `alIndex`wymiar to [0].

*T*<br/>
Określa wartość nowego elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Jest to wielowymiarowa wersja [CComSafeArray:: SetAt](#setat).

##  <a name="operator_at"></a>CComSafeArray:: operator\[\]

Pobiera element z tablicy.

```
T& operator[](long lindex) const;
T& operator[]int nindex) const;
```

### <a name="parameters"></a>Parametry

*lIndex, nIndex*<br/>
Numer indeksu wymaganego elementu w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca odpowiedni element tablicy.

### <a name="remarks"></a>Uwagi

Wykonuje podobną funkcję do [CComSafeArray:: GetAt](#getat), jednak ten operator działa tylko w przypadku tablic jednowymiarowych.

##  <a name="operator_eq"></a>CComSafeArray:: operator =

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

##  <a name="operator_lpsafearray"></a>CComSafeArray:: operator LPSAFEARRAY

Rzutuje wartość na `SAFEARRAY` wskaźnik.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Wartość zwracana

Rzutuje wartość na `SAFEARRAY` wskaźnik.

##  <a name="resize"></a>CComSafeArray:: Resize

Zmienia rozmiar `CComSafeArray` obiektu.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound*<br/>
Wskaźnik do `SAFEARRAYBOUND` struktury zawierającej informacje o liczbie elementów i dolnej granicy tablicy.

*ulCount*<br/>
Żądana liczba obiektów w tablicy o zmienionym rozmiarze.

*lLBound*<br/>
Dolna granica.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Ta metoda zmienia rozmiar tylko wymiaru po prawej stronie. Nie spowoduje to zmiany rozmiaru tablic, `IsResizable` które zwracają wartość false.

##  <a name="setat"></a>CComSafeArray::SetAt

Ustawia wartość elementu w tablicy jednowymiarowej.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*lIndex*<br/>
Numer indeksu elementu tablicy, który ma zostać ustawiony.

*t*<br/>
Nowa wartość określonego elementu.

*bCopy*<br/>
Wskazuje, czy ma zostać utworzona kopia danych. Wartość domyślna to TRUE.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK po powodzeniu lub błąd HRESULT w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Flaga *bCopy* jest brana pod uwagę, gdy elementy typu BSTR lub Variant są dodawane do tablicy. Wartość domyślna TRUE zapewnia nową kopię danych, gdy element zostanie dodany do tablicy.

## <a name="see-also"></a>Zobacz także

[SAFEARRAY — typ danych](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray:: Create](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
