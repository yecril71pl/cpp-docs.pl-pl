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
ms.openlocfilehash: d1e72d364858ea31541d574ed77bdc8ccca7d748
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327389"
---
# <a name="ccomsafearray-class"></a>Klasa CComSafeArray

Ta klasa jest otoką `SAFEARRAY` dla struktury.

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
|[CComSafeArray::Dodaj](#add)|Dodaje jeden lub więcej `SAFEARRAY` elementów lub `CComSafeArray`strukturę do pliku .|
|[CComSafeArray::Dołącz](#attach)|Dołącza strukturę `SAFEARRAY` do `CComSafeArray` obiektu.|
|[CComSafeArray::CopyFrom](#copyfrom)|Kopiuje zawartość `SAFEARRAY` struktury do `CComSafeArray` obiektu.|
|[CComSafeArray::CopyTo](#copyto)|Tworzy kopię `CComSafeArray` obiektu.|
|[CComSafeArray::Tworzenie](#create)|Tworzy obiekt `CComSafeArray`.|
|[CComSafeArray::Destroy](#destroy)|Niszczy `CComSafeArray` obiekt.|
|[CComSafeArray::Detach](#detach)|Odłącza `SAFEARRAY` a `CComSafeArray` od obiektu.|
|[CComSafeArray::GetAt](#getat)|Pobiera pojedynczy element z tablicy jednowymiarowej.|
|[CComSafeArray::GetCount](#getcount)|Zwraca liczbę elementów w tablicy.|
|[CComSafeArray::GetDimensions](#getdimensions)|Zwraca liczbę wymiarów w tablicy.|
|[CComSafeArray::GetLowerBound](#getlowerbound)|Zwraca dolną granicę dla danego wymiaru tablicy.|
|[CComSafeArray::GetSafeArrayPtr](#getsafearrayptr)|Zwraca adres elementu `m_psa` członkowskiego danych.|
|[CComSafeArray::GetType](#gettype)|Zwraca typ danych przechowywanych w tablicy.|
|[CComSafeArray::GetUpperBound](#getupperbound)|Zwraca górną granicę dla dowolnego wymiaru tablicy.|
|[CComSafeArray::IsSizable](#issizable)|Sprawdza, `CComSafeArray` czy można zwymiarować obiekt.|
|[CComSafeArray::MultiDimGetAt](#multidimgetat)|Pobiera pojedynczy element z tablicy wielowymiarowej.|
|[CComSafeArray::MultiDimSetAt](#multidimsetat)|Ustawia wartość elementu w tablicy wielowymiarowej.|
|[CComSafeArray::Resize](#resize)|Rozmiar obiektu jest `CComSafeArray` wymieńny.|
|[CComSafeArray::SetAt](#setat)|Ustawia wartość elementu w tablicy jednowymiarowej.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::operator LPSAFEARRAY](#operator_lpsafearray)|Rzutuje wartość na `SAFEARRAY` wskaźnik.|
|[CComSafeArray::operator\[\]](ccomsafearray-class.md#operator_at)|Pobiera element z tablicy.|
|[CComSafeArray::operator =](#operator_eq)|Operator przypisania.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComSafeArray::m_psa](#m_psa)|Ten element członkowski danych `SAFEARRAY` przechowuje adres struktury.|

## <a name="remarks"></a>Uwagi

`CComSafeArray`zapewnia otokę dla klasy [safearray data type,](/windows/win32/api/oaidl/ns-oaidl-safearray) co ułatwia tworzenie i zarządzanie tablicami jedno- i wielowymiarowymi prawie każdego typu obsługiwanego przez wariant.

`CComSafeArray`upraszcza przekazywanie tablic między procesami, a ponadto zapewnia dodatkowe zabezpieczenia, sprawdzając wartości indeksu tablicy względem górnej i dolnej granicy.

Dolna granica `CComSafeArray` może zaczynać się od dowolnej wartości zdefiniowanej przez użytkownika; jednak tablice, które są dostępne za pośrednictwem języka C++ należy użyć dolnej granicy 0. Inne języki, takie jak Visual Basic, mogą używać innych wartości ograniczających (na przykład od -10 do 10).

Użyj [CComSafeArray::Create,](#create) `CComSafeArray` aby utworzyć obiekt, a [CComSafeArray::Destroy,](#destroy) aby go usunąć.

A `CComSafeArray` może zawierać następujący podzbiór typów danych VARIANT:

|Vartype|Opis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|długi|
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

**Nagłówek:** atlsafe.h

## <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#75](../../atl/codesnippet/cpp/ccomsafearray-class_1.cpp)]

## <a name="ccomsafearrayadd"></a><a name="add"></a>CComSafeArray::Dodaj

Dodaje jeden lub więcej `SAFEARRAY` elementów lub `CComSafeArray`strukturę do pliku .

```
HRESULT Add(const SAFEARRAY* psaSrc);
HRESULT Add(ULONG ulCount, const T* pT, BOOL bCopy = TRUE);
HRESULT Add(const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*psaSrc (psaSrc)*<br/>
Wskaźnik do `SAFEARRAY` obiektu.

*UlCount (ulCount)*<br/>
Liczba obiektów do dodania do tablicy.

*Pt*<br/>
Wskaźnik do jednego lub więcej obiektów, które mają zostać dodane do tablicy.

*t*<br/>
Odwołanie do obiektu, który ma zostać dodany do tablicy.

*bCopy (kopia)*<br/>
Wskazuje, czy należy utworzyć kopię danych. Wartością domyślną jest PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Nowe obiekty są dołączane na końcu `SAFEARRAY` istniejącego obiektu. Dodawanie obiektu do obiektu wielowymiarowego `SAFEARRAY` nie jest obsługiwane. Podczas dodawania istniejącej tablicy obiektów, obie tablice muszą zawierać elementy tego samego typu.

Flaga *bCopy* jest brana pod uwagę podczas dodawania elementów typu BSTR lub VARIANT do tablicy. Domyślna wartość TRUE zapewnia, że nowa kopia jest wykonana z danych, gdy element jest dodawany do tablicy.

## <a name="ccomsafearrayattach"></a><a name="attach"></a>CComSafeArray::Dołącz

Dołącza strukturę `SAFEARRAY` do `CComSafeArray` obiektu.

```
HRESULT Attach(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*psaSrc (psaSrc)*<br/>
Wskaźnik do `SAFEARRAY` struktury.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Dołącza strukturę `SAFEARRAY` do `CComSafeArray` obiektu, udostępniając istniejące `CComSafeArray` metody.

## <a name="ccomsafearrayccomsafearray"></a><a name="ccomsafearray"></a>CComSafeArray::CComSafeArray

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

*Powiązane*<br/>
Struktura. `SAFEARRAYBOUND`

*UlCount (ulCount)*<br/>
Liczba elementów w tablicy.

*lLZrójdą*<br/>
Dolna wartość granicy; oznacza to, że indeks pierwszego elementu w tablicy.

*pBound (Przyjemnie)*<br/>
Wskaźnik do `SAFEARRAYBOUND` struktury.

*uDims*<br/>
Liczba wymiarów w tablicy.

*saSrc ( saSrc )*<br/>
Odwołanie do `SAFEARRAY` struktury `CComSafeArray` lub obiektu. W obu przypadkach konstruktor używa tego odwołania, aby utworzyć kopię tablicy, więc tablica nie odwołuje się po konstrukcji.

*psaSrc (psaSrc)*<br/>
Wskaźnik do `SAFEARRAY` struktury. Konstruktor używa tego adresu, aby utworzyć kopię tablicy, więc tablica nie odwołuje się po konstrukcji.

### <a name="remarks"></a>Uwagi

Tworzy obiekt `CComSafeArray`.

## <a name="ccomsafearrayccomsafearray"></a><a name="dtor"></a>CComSafeArray::~CComSafeArray

Destruktor.

```
~CComSafeArray() throw()
```

### <a name="remarks"></a>Uwagi

Zwalnia wszystkie przydzielone zasoby.

## <a name="ccomsafearraycopyfrom"></a><a name="copyfrom"></a>CComSafeArray::CopyFrom

Kopiuje zawartość `SAFEARRAY` struktury do `CComSafeArray` obiektu.

```
HRESULT CopyFrom(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray (Polski)*<br/>
Wskaźnik do `SAFEARRAY` do kopiowania.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje `SAFEARRAY` zawartość a `CComSafeArray` do bieżącego obiektu. Istniejąca zawartość tablicy zostanie zastąpiona.

## <a name="ccomsafearraycopyto"></a><a name="copyto"></a>CComSafeArray::CopyTo

Tworzy kopię `CComSafeArray` obiektu.

```
HRESULT CopyTo(LPSAFEARRAY* ppArray);
```

### <a name="parameters"></a>Parametry

*ppArray (Polski)*<br/>
Wskaźnik do lokalizacji, w której `SAFEARRAY`ma być utworzony nowy plik .

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda kopiuje `CComSafeArray` zawartość obiektu `SAFEARRAY` do struktury.

## <a name="ccomsafearraycreate"></a><a name="create"></a>CComSafeArray::Tworzenie

Tworzy `CComSafeArray`plik .

```
HRESULT Create(const SAFEARRAYBOUND* pBound, UINT uDims = 1);
HRESULT Create(ULONG ulCount = 0, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound (Przyjemnie)*<br/>
Wskaźnik do `SAFEARRAYBOUND` obiektu.

*uDims*<br/>
Liczba wymiarów w tablicy.

*UlCount (ulCount)*<br/>
Liczba elementów w tablicy.

*lLZrójdą*<br/>
Dolna wartość granicy; oznacza to, że indeks pierwszego elementu w tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Obiekt `CComSafeArray` można utworzyć na `SAFEARRAYBOUND` podstawie istniejącej struktury i liczby wymiarów lub określając liczbę elementów w tablicy i dolnej granicy. Jeśli tablica ma być dostępny z języka C++, dolna granica powinna być 0. Inne języki mogą zezwalać na inne wartości dla dolnej granicy (na przykład Visual Basic obsługuje tablice z elementami o zakresie, takimi jak -10 do 10).

## <a name="ccomsafearraydestroy"></a><a name="destroy"></a>CComSafeArray::Destroy

Niszczy `CComSafeArray` obiekt.

```
HRESULT Destroy();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Niszczy istniejący `CComSafeArray` obiekt i wszystkie dane, które zawiera.

## <a name="ccomsafearraydetach"></a><a name="detach"></a>CComSafeArray::Detach

Odłącza `SAFEARRAY` a `CComSafeArray` od obiektu.

```
LPSAFEARRAY Detach();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do `SAFEARRAY` obiektu.

### <a name="remarks"></a>Uwagi

Ta metoda odłącza `SAFEARRAY` obiekt `CComSafeArray` od obiektu.

## <a name="ccomsafearraygetat"></a><a name="getat"></a>CComSafeArray::GetAt

Pobiera pojedynczy element z tablicy jednowymiarowej.

```
T& GetAt(LONG lIndex) const;
```

### <a name="parameters"></a>Parametry

*Lindex*<br/>
Numer indeksu wartości w tablicy do zwrócenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca odwołanie do wymaganego elementu tablicy.

## <a name="ccomsafearraygetcount"></a><a name="getcount"></a>CComSafeArray::GetCount

Zwraca liczbę elementów w tablicy.

```
ULONG GetCount(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim ( uDim )*<br/>
Wymiar tablicy.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę elementów w tablicy.

### <a name="remarks"></a>Uwagi

W przypadku użycia z tablicą wielowymiarową ta metoda zwróci tylko liczbę elementów w określonym wymiarze.

## <a name="ccomsafearraygetdimensions"></a><a name="getdimensions"></a>CComSafeArray::GetDimensions

Zwraca liczbę wymiarów w tablicy.

```
UINT GetDimensions() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wymiarów w tablicy.

## <a name="ccomsafearraygetlowerbound"></a><a name="getlowerbound"></a>CComSafeArray::GetLowerBound

Zwraca dolną granicę dla danego wymiaru tablicy.

```
LONG GetLowerBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim ( uDim )*<br/>
Wymiar tablicy, dla którego ma zostać świązany dolna granica. Jeśli pominięto, wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Zwraca dolną granicę.

### <a name="remarks"></a>Uwagi

Jeśli dolna granica wynosi 0, oznacza to tablicę podobną do C, której pierwszym elementem jest numer elementu 0. W przypadku błędu, na przykład nieprawidłowy argument wymiaru, `AtlThrow` ta metoda wywołuje z HRESULT opisujące błąd.

## <a name="ccomsafearraygetsafearrayptr"></a><a name="getsafearrayptr"></a>CComSafeArray::GetSafeArrayPtr

Zwraca adres elementu `m_psa` członkowskiego danych.

```
LPSAFEARRAY* GetSafeArrayPtr() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wskaźnik do elementu członkowskiego [CComSafeArray::m_psa](#m_psa) danych.

## <a name="ccomsafearraygettype"></a><a name="gettype"></a>CComSafeArray::GetType

Zwraca typ danych przechowywanych w tablicy.

```
VARTYPE GetType() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca typ danych przechowywanych w tablicy, który może być dowolny z następujących typów:

|Vartype|Opis|
|-------------|-----------------|
|VT_I1|char|
|VT_I2|short|
|VT_I4|int|
|VT_I4|long|
|VT_I8|długi|
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

## <a name="ccomsafearraygetupperbound"></a><a name="getupperbound"></a>CComSafeArray::GetUpperBound

Zwraca górną granicę dla dowolnego wymiaru tablicy.

```
LONG GetUpperBound(UINT uDim = 0) const;
```

### <a name="parameters"></a>Parametry

*uDim ( uDim )*<br/>
Wymiar tablicy, dla którego ma zostać śwolta górna. Jeśli pominięto, wartość domyślna to 0.

### <a name="return-value"></a>Wartość zwracana

Zwraca górną granicę. Ta wartość jest włącznie, maksymalny prawidłowy indeks dla tego wymiaru.

### <a name="remarks"></a>Uwagi

W przypadku błędu, na przykład nieprawidłowy argument wymiaru, `AtlThrow` ta metoda wywołuje z HRESULT opisujące błąd.

## <a name="ccomsafearrayissizable"></a><a name="issizable"></a>CComSafeArray::IsSizable

Sprawdza, `CComSafeArray` czy można zwymiarować obiekt.

```
bool IsSizable() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CComSafeArray` PRAWDA, jeśli można zwymiarować, FALSE, jeśli nie.

## <a name="ccomsafearraym_psa"></a><a name="m_psa"></a>CComSafeArray::m_psa

Przechowuje adres `SAFEARRAY` struktury dostęp.

```
LPSAFEARRAY m_psa;
```

## <a name="ccomsafearraymultidimgetat"></a><a name="multidimgetat"></a>CComSafeArray::MultiDimGetAt

Pobiera pojedynczy element z tablicy wielowymiarowej.

```
HRESULT MultiDimGetAt(const LONG* alIndex, T& t);
```

### <a name="parameters"></a>Parametry

*alIndex ( alIndex )*<br/>
Wskaźnik do wektora indeksów dla każdego wymiaru w tablicy. Najbardziej lewicowym (najbardziej znaczącym) wymiarem jest `alIndex[0]`.

*t*<br/>
Odwołanie do zwróconych danych.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

## <a name="ccomsafearraymultidimsetat"></a><a name="multidimsetat"></a>CComSafeArray::MultiDimSetAt

Ustawia wartość elementu w tablicy wielowymiarowej.

```
HRESULT MultiDimSetAt(const LONG* alIndex, const T& t);
```

### <a name="parameters"></a>Parametry

*alIndex ( alIndex )*<br/>
Wskaźnik do wektora indeksów dla każdego wymiaru w tablicy. Wymiarem po prawej stronie `alIndex`(najmniej znaczącym) jest [0].

*T*<br/>
Określa wartość nowego elementu.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Jest to wielowymiarowa wersja [CComSafeArray::SetAt](#setat).

## <a name="ccomsafearrayoperator-"></a><a name="operator_at"></a>CComSafeArray::operator\[\]

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

Wykonuje podobną funkcję do [CComSafeArray::GetAt](#getat), jednak ten operator działa tylko z tablicami jednowymiarowymi.

## <a name="ccomsafearrayoperator-"></a><a name="operator_eq"></a>CComSafeArray::operator =

Operator przypisania.

```
ATL::CComSafeArray<T>& operator=(const ATL::CComSafeArray& saSrc);
ATL::CComSafeArray<T>& operator=(const SAFEARRAY* psaSrc);
```

### <a name="parameters"></a>Parametry

*saSrc ( saSrc )*<br/>
Odwołanie do `CComSafeArray` obiektu.

*psaSrc (psaSrc)*<br/>
Wskaźnik do `SAFEARRAY` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca typ danych przechowywanych w tablicy.

## <a name="ccomsafearrayoperator-lpsafearray"></a><a name="operator_lpsafearray"></a>CComSafeArray::operator LPSAFEARRAY

Rzutuje wartość na `SAFEARRAY` wskaźnik.

```
operator LPSAFEARRAY() const;
```

### <a name="return-value"></a>Wartość zwracana

Rzutuje wartość na `SAFEARRAY` wskaźnik.

## <a name="ccomsafearrayresize"></a><a name="resize"></a>CComSafeArray::Resize

Rozmiar obiektu jest `CComSafeArray` wymieńny.

```
HRESULT Resize(const SAFEARRAYBOUND* pBound);
HRESULT Resize(ULONG ulCount, LONG lLBound = 0);
```

### <a name="parameters"></a>Parametry

*pBound (Przyjemnie)*<br/>
Wskaźnik do `SAFEARRAYBOUND` struktury, który zawiera informacje na temat liczby elementów i dolnej granicy tablicy.

*UlCount (ulCount)*<br/>
Żądana liczba obiektów w tablicy o przesłomiona.

*lLZrójdą*<br/>
Dolna granica.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Ta metoda tylko zmienić rozmiar wymiaru po prawej stronie. Nie będzie zmienić rozmiar tablic, które zwracają `IsResizable` jako FALSE.

## <a name="ccomsafearraysetat"></a><a name="setat"></a>CComSafeArray::SetAt

Ustawia wartość elementu w tablicy jednowymiarowej.

```
HRESULT SetAt(LONG lIndex, const T& t, BOOL bCopy = TRUE);
```

### <a name="parameters"></a>Parametry

*Lindex*<br/>
Numer indeksu elementu tablicy do skonfigurowania.

*t*<br/>
Nowa wartość określonego elementu.

*bCopy (kopia)*<br/>
Wskazuje, czy należy utworzyć kopię danych. Wartością domyślną jest PRAWDA.

### <a name="return-value"></a>Wartość zwracana

Zwraca S_OK na sukces lub błąd HRESULT na niepowodzenie.

### <a name="remarks"></a>Uwagi

Flaga *bCopy* jest brana pod uwagę podczas dodawania elementów typu BSTR lub VARIANT do tablicy. Domyślna wartość TRUE zapewnia, że nowa kopia jest wykonana z danych, gdy element jest dodawany do tablicy.

## <a name="see-also"></a>Zobacz też

[Typ danych SAFEARRAY](/windows/win32/api/oaidl/ns-oaidl-safearray)<br/>
[CComSafeArray::Tworzenie](#create)<br/>
[CComSafeArray::Destroy](#destroy)<br/>
[Przegląd klas](../../atl/atl-class-overview.md)
