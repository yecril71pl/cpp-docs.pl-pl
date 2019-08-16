---
title: Klasa CComVariant
ms.date: 11/04/2016
f1_keywords:
- CComVariant
- ATLCOMCLI/ATL::CComVariant
- ATLCOMCLI/ATL::CComVariant::CComVariant
- ATLCOMCLI/ATL::CComVariant::Attach
- ATLCOMCLI/ATL::CComVariant::ChangeType
- ATLCOMCLI/ATL::CComVariant::Clear
- ATLCOMCLI/ATL::CComVariant::Copy
- ATLCOMCLI/ATL::CComVariant::CopyTo
- ATLCOMCLI/ATL::CComVariant::Detach
- ATLCOMCLI/ATL::CComVariant::GetSize
- ATLCOMCLI/ATL::CComVariant::ReadFromStream
- ATLCOMCLI/ATL::CComVariant::SetByRef
- ATLCOMCLI/ATL::CComVariant::WriteToStream
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
ms.openlocfilehash: b4c157435aaffab5f1315fd4636f55f9d4e0d5b4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496861"
---
# <a name="ccomvariant-class"></a>Klasa CComVariant

Ta klasa otacza typ VARIANT, dostarczając element członkowski wskazujący typ przechowywanych danych.

## <a name="syntax"></a>Składnia

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Konstruktor.|
|[CComVariant:: ~ CComVariant](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComVariant:: Attach](#attach)|Dołącza wariant do `CComVariant` obiektu.|
|[CComVariant:: ChangeType](#changetype)|`CComVariant` Konwertuje obiekt na nowy typ.|
|[CComVariant:: Clear](#clear)|`CComVariant` Czyści obiekt.|
|[CComVariant:: Copy](#copy)|Kopiuje wariant do `CComVariant` obiektu.|
|[CComVariant:: CopyTo](#copyto)|Kopiuje zawartość `CComVariant` obiektu.|
|[CComVariant::D etach](#detach)|Odłączenie bazowego wariantu `CComVariant` od obiektu.|
|[CComVariant:: GetSize](#getsize)|Zwraca rozmiar (w bajtach) zawartości `CComVariant` obiektu.|
|[CComVariant::ReadFromStream](#readfromstream)|Ładuje wariant ze strumienia.|
|[CComVariant:: setbyref](#setbyref)|Inicjuje obiekt i `vt` ustawia element członkowski na VT_BYREF. `CComVariant`|
|[CComVariant::WriteToStream](#writetostream)|Zapisuje bazowy wariant do strumienia.|

### <a name="public-operators"></a>Operatory publiczne

|||
|-|-|
|[CComVariant:: operator <](#operator_lt)|Wskazuje, czy `CComVariant` obiekt jest mniejszy niż określony wariant.|
|[CComVariant:: operator >](#operator_gt)|Wskazuje, `CComVariant` czy obiekt jest większy niż określony wariant.|
|[operator! =](#operator_neq)|Wskazuje, czy `CComVariant` obiekt nie jest równy określonemu wariantowi.|
|[operator =](#operator_eq)|Przypisuje wartość do `CComVariant` obiektu.|
|[operator = =](#operator_eq_eq)|Wskazuje, czy `CComVariant` obiekt jest równy podanemu wariantowi.|

## <a name="remarks"></a>Uwagi

`CComVariant`Zawija typ VARIANT i VARIANTARG, który składa się z Unii i składowej wskazujący typ danych przechowywanych w Unii. Warianty są zwykle używane w automatyzacji.

`CComVariant`pochodzi od typu VARIANT, więc można go użyć wszędzie tam, gdzie można użyć elementu VARIANT. Można na przykład użyć makra V_VT, aby wyodrębnić typ elementu `CComVariant` lub uzyskać dostęp do `vt` elementu członkowskiego bezpośrednio tak jak w przypadku wariantu.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli. h

##  <a name="attach"></a>CComVariant:: Attach

Bezpiecznie czyści bieżącą zawartość `CComVariant` obiektu, kopiuje zawartość *pSrc* do tego obiektu, a następnie ustawia typ Variant *pSrc* na VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
podczas Wskazuje [wariant](/windows/win32/api/oaidl/ns-oaidl-variant) , który ma zostać dołączony do obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Własność danych przechowywanych przez *pSrc* jest przekazywana do `CComVariant` obiektu.

##  <a name="ccomvariant"></a>CComVariant::CComVariant

Każdy Konstruktor obsługuje bezpieczne inicjowanie `CComVariant` obiektu przez `VariantInit` wywołanie funkcji Win32 lub przez ustawienie wartości i typu obiektu zgodnie z przekazaniem parametrów.

```
CComVariant() throw();
CComVariant(const CComVariant& varSrc);
CComVariant(const VARIANT& varSrc);
CComVariant(LPCOLESTR lpszSrc);
CComVariant(LPCSTR lpszSrc);
CComVariant(bool bSrc);
CComVariant(BYTE nSrc) throw();
CComVariant(int nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned int  nSrc, VARTYPE vtSrc = VT_UI4) throw();
CComVariant(shor  nSrc) throw();
CComVariant(unsigned short nSrc) throw();
CComVariant(long  nSrc, VARTYPE vtSrc = VT_I4) throw();
CComVariant(unsigned long  nSrc) throw();
CComVariant(LONGLONG  nSrc) throw();
CComVariant(ULONGLONG  nSrc) throw();
CComVariant(float  fltSrc) throw();
CComVariant(double  dblSrc, VARTYPE vtSrc = VT_R8) throw();
CComVariant(CY  cySrc) throw();
CComVariant(IDispatch* pSrc) throw();
CComVariant(IUnknown* pSrc) throw();
CComVariant(const SAFEARRAY* pSrc);
CComVariant(char  cSrc) throw();
CComVariant(const CComBSTR& bstrSrc);
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
podczas Wariant używany do `CComVariant` inicjowania obiektu. `CComVariant` Zawartość wariantu źródłowego jest kopiowana do lokalizacji docelowej bez konwersji.

*lpszSrc*<br/>
podczas Ciąg znaków używany do inicjowania `CComVariant` obiektu. Można przekazać ciąg znaków (Unicode) zakończony zerem do wersji LPCOLESTR konstruktora lub ciąg ANSI do wersji LPCSTR. W każdym przypadku ciąg jest konwertowany na format znaków Unicode alokowany przy użyciu `SysAllocString`. Typ `CComVariant` obiektu będzie VT_BSTR.

*bSrc*<br/>
podczas **Bool** używany do inicjowania `CComVariant` obiektu. Argument **bool** jest konwertowany na element VARIANT_BOOL przed jego zapisaniem. Typ `CComVariant` obiektu będzie VT_BOOL.

*nSrc*<br/>
podczas Int, **Byte**, **Short**, **Long**, longlong, ULONGLONG, unsigned **Short**, unsigned **Long**lub unsigned **int** użyte do zainicjowania `CComVariant` obiektu. Typem `CComVariant` obiektu będzie VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 lub VT_UI4.

*vtSrc*<br/>
podczas Typ wariantu. Gdy pierwszy parametr to **int**, prawidłowe typy to VT_I4 i VT_INT. Gdy pierwszy parametr jest **długi**, prawidłowe typy to VT_I4 i VT_ERROR. Gdy pierwszy parametr jest **podwójny**, prawidłowe typy to VT_R8 i VT_DATE. Gdy pierwszy parametr ma wartość **int bez znaku**, prawidłowe typy to VT_UI4 i VT_UINT.

*fltSrc*<br/>
podczas Wartość **zmiennoprzecinkowa** użyta do `CComVariant` zainicjowania obiektu. Typ `CComVariant` obiektu będzie VT_R4.

*dblSrc*<br/>
podczas **Podwójna** wartość użyta do `CComVariant` zainicjowania obiektu. Typ `CComVariant` obiektu będzie VT_R8.

*cySrc*<br/>
podczas `CY` Używane do`CComVariant` inicjowania obiektu. Typ `CComVariant` obiektu będzie VT_CY.

*pSrc*<br/>
podczas Wskaźnik lub używany`IUnknown` do inicjowania obiektu.`CComVariant` `IDispatch` `AddRef`zostanie wywołana na wskaźniku interfejsu. Typ `CComVariant` obiektu będzie odpowiednio VT_DISPATCH lub VT_UNKNOWN.

Lub wskaźnik SAFERRAY używany do inicjowania `CComVariant` obiektu. Kopia elementu SAFEARRAY jest przechowywana w `CComVariant` obiekcie. Typ `CComVariant` obiektu będzie kombinacją oryginalnego typu parametru SafeArray i VT_ARRAY.

*cSrc*<br/>
podczas **Znak** używany do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu będzie VT_I1.

*bstrSrc*<br/>
podczas BSTR używany do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu będzie VT_BSTR.

### <a name="remarks"></a>Uwagi

Destruktor zarządza oczyszczaniem przez wywołanie [CComVariant:: Clear](#clear).

##  <a name="dtor"></a>CComVariant:: ~ CComVariant

Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda umożliwia zarządzanie oczyszczaniem przez wywołanie [CComVariant:: Clear](#clear).

##  <a name="changetype"></a>CComVariant:: ChangeType

`CComVariant` Konwertuje obiekt na nowy typ.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vtNew*<br/>
podczas Nowy typ dla `CComVariant` obiektu.

*pSrc*<br/>
podczas Wskaźnik do WARIANTu, którego wartość zostanie przekonwertowana na nowy typ. Wartość domyślna to null, co oznacza, `CComVariant` że obiekt zostanie przekonwertowany na miejsce.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

W przypadku przekazania wartości dla *pSrc*, `ChangeType` program będzie używać tego wariantu jako źródła konwersji. W przeciwnym razie obiekt będzie źródłem. `CComVariant`

##  <a name="clear"></a>CComVariant:: Clear

Czyści obiekt, wywołując funkcję `VariantClear` Win32. `CComVariant`

```
HRESULT Clear();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Destruktor automatycznie wywołuje `Clear`.

##  <a name="copy"></a>CComVariant:: Copy

`CComVariant` Zwalnia obiekt, a następnie przypisuje go do kopii określonego wariantu.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
podczas Wskaźnik do wariantu [](/windows/win32/api/oaidl/ns-oaidl-variant) do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

##  <a name="copyto"></a>CComVariant:: CopyTo

Kopiuje zawartość `CComVariant` obiektu.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parametry

*pstrDest*<br/>
Wskazuje BSTR, który będzie otrzymywał kopię zawartości `CComVariant` obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`CComVariant` Obiekt musi być typu VT_BSTR.

##  <a name="detach"></a>CComVariant::D etach

Odłącza bazowy wariant od `CComVariant` obiektu i ustawia typ obiektu na VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parametry

*pDest*<br/>
określoną Zwraca podstawową wartość WARIANTu obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że zawartość wariantu, do której odwołuje się *pDest* , zostanie automatycznie wyczyszczona, zanim zostanie przypisana wartość i typ obiektu wywołującego `CComVariant` .

##  <a name="getsize"></a>CComVariant:: GetSize

W przypadku wariantów o prostym rozmiarze, ta metoda zwraca wartość **sizeof** , a także bazowego typu danych i **sizeof (VARTYPE)** .

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar w bajtach bieżącej zawartości `CComVariant` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli wariant zawiera wskaźnik interfejsu, `GetSize` zapytania dla `IPersistStream` lub `IPersistStreamInit`. Jeśli to się powiedzie, wartość zwracana jest niewielką kolejnością 32 bitów wartości zwracanej `GetSizeMax` przez Plus **sizeof** a CLSID i **sizeof (VARTYPE)** . Jeśli wskaźnik interfejsu ma wartość null, `GetSize` zwraca wartość **sizeof** a CLSID i **sizeof (VARTYPE)** . Jeśli całkowity rozmiar jest większy niż ULONG_MAX, zwraca `GetSize` wartość **sizeof (VARTYPE)** , która wskazuje na błąd.

We wszystkich innych przypadkach tymczasowa ODMIANa typu VT_BSTR jest przekształcana z bieżącego WARIANTu. Długość tego elementu BSTR jest obliczana jako rozmiar długości ciągu plus długość ciągu znaków oraz rozmiar znaku null Plus **sizeof (VARTYPE)** . Jeśli wariant nie może zostać przekształcony na wariant typu VT_BSTR, `GetSize` zwraca **sizeof (VARTYPE)** .

Rozmiar zwrócony przez tę metodę jest zgodny z liczbą bajtów używanych przez [CComVariant:: WriteToStream](#writetostream) w warunkach zakończonych powodzeniem.

##  <a name="operator_eq"></a>CComVariant:: operator =

Przypisuje wartość i odpowiadający jej typ `CComVariant` do obiektu.

```
CComVariant& operator=(const CComVariant& varSrc);
CComVariant& operator=(const VARIANT& varSrc);
CComVariant& operator=(const CComBSTR& bstrSrc);
CComVariant& operator=(LPCOLESTR lpszSrc);
CComVariant& operator=(LPCSTR lpszSrc);
CComVariant& operator=(bool bSrc);
CComVariant& operator=(BYTE nSrc) throw();
CComVariant& operator=int nSrc) throw();
CComVariant& operator=(unsigned int nSrc) throw();
CComVariant& operator=(short nSrc) throw();
CComVariant& operator=(unsigned short nSrc) throw();
CComVariant& operator=(long nSrc) throw();
CComVariant& operator=(unsigned long nSrc) throw();
CComVariant& operator=(LONGLONG nSrc) throw();
CComVariant& operator=(ULONGLONG nSrc) throw();
CComVariant& operator=(float fltSrc) throw();
CComVariant& operator=(double dblSrc) throw();
CComVariant& operator=(CY cySrc) throw();
CComVariant& operator=(IDispatch* pSrc) throw();
CComVariant& operator=(IUnknown* pSrc) throw();
CComVariant& operator=(const SAFEARRAY* pSrc);
CComVariant& operator=(char cSrc) throw();
```

### <a name="parameters"></a>Parametry

*varSrc*<br/>
podczas Wariant `CComVariant` , [](/windows/win32/api/oaidl/ns-oaidl-variant) który ma `CComVariant` zostać przypisany do obiektu. Zawartość wariantu źródłowego jest kopiowana do lokalizacji docelowej bez konwersji.

*bstrSrc*<br/>
podczas Wartość BSTR, która ma zostać przypisana do `CComVariant` obiektu. Typ `CComVariant` obiektu będzie VT_BSTR.

*lpszSrc*<br/>
podczas Ciąg znaków, który ma zostać przypisany do `CComVariant` obiektu. Można przekazać ciąg znaków (Unicode) zakończony zerem do wersji LPCOLESTR operatora lub ciąg ANSI do wersji LPCSTR. W każdym z tych przypadków ciąg jest konwertowany na format znaków Unicode alokowany przy `SysAllocString`użyciu. Typ `CComVariant` obiektu będzie VT_BSTR.

*bSrc*<br/>
podczas Wartość **logiczna** , która ma zostać przypisana do `CComVariant` obiektu. Argument **bool** jest konwertowany na element VARIANT_BOOL przed jego zapisaniem. Typ `CComVariant` obiektu będzie VT_BOOL.

*nSrc*<br/>
podczas Liczba **int**, Byte, **Short**, **Long**, longlong, ULONGLONG, **unsigned Short**, unsigned **Long**lub unsigned **int** , która ma zostać przypisana do `CComVariant` obiektu. Typem `CComVariant` obiektu będzie VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 lub VT_UI4.

*fltSrc*<br/>
podczas Wartość **zmiennoprzecinkowa** , która ma zostać `CComVariant` przypisana do obiektu. Typ `CComVariant` obiektu będzie VT_R4.

*dblSrc*<br/>
podczas Wartość **Double** , która ma zostać przypisana do `CComVariant` obiektu. Typ `CComVariant` obiektu będzie VT_R8.

*cySrc*<br/>
podczas Wartość `CY` do przypisania `CComVariant` do obiektu. Typ `CComVariant` obiektu będzie VT_CY.

*pSrc*<br/>
podczas Wskaźnik `IDispatch` lub `IUnknown` ,`CComVariant` który ma zostać przypisany do obiektu. `AddRef`zostanie wywołana na wskaźniku interfejsu. Typ `CComVariant` obiektu będzie odpowiednio VT_DISPATCH lub VT_UNKNOWN.

Lub wskaźnik SAFEARRAY, który ma zostać przypisany do `CComVariant` obiektu. Kopia elementu SAFEARRAY jest przechowywana w `CComVariant` obiekcie. Typ `CComVariant` obiektu będzie kombinacją oryginalnego typu parametru SafeArray i VT_ARRAY.

*cSrc*<br/>
podczas Znak, który ma zostać przypisany do `CComVariant` obiektu. Typ `CComVariant` obiektu będzie VT_I1.

##  <a name="operator_eq_eq"></a>CComVariant:: operator = =

Wskazuje, czy `CComVariant` obiekt jest równy podanemu wariantowi.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość true, `CComVariant` Jeśli wartość i typ elementu *varSrc* są równe odpowiednio wartości i typu obiektu. W przeciwnym razie FALSE. Operator używa domyślnych ustawień regionalnych użytkownika do przeprowadzenia porównania.

Operator porównuje tylko wartość typów wariantów. Porównuje ciągi, liczby całkowite i punkty zmiennoprzecinkowe, ale nie tablice ani rekordy.

##  <a name="operator_neq"></a>CComVariant:: operator! =

Wskazuje, czy `CComVariant` obiekt nie jest równy określonemu wariantowi.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość true, jeśli wartość lub typ *varSrc* nie jest równa wartości lub typu, odpowiednio, `CComVariant` obiektu. W przeciwnym razie FALSE. Operator używa domyślnych ustawień regionalnych użytkownika do przeprowadzenia porównania.

Operator porównuje tylko wartość typów wariantów. Porównuje ciągi, liczby całkowite i punkty zmiennoprzecinkowe, ale nie tablice ani rekordy.

##  <a name="operator_lt"></a>CComVariant:: operator&lt;

Wskazuje, czy `CComVariant` obiekt jest mniejszy niż określony wariant.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość true, jeśli wartość `CComVariant` obiektu jest mniejsza niż wartość *varSrc*. W przeciwnym razie FALSE. Operator używa domyślnych ustawień regionalnych użytkownika do przeprowadzenia porównania.

##  <a name="operator_gt"></a>CComVariant:: operator&gt;

Wskazuje, `CComVariant` czy obiekt jest większy niż określony wariant.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość true, jeśli wartość `CComVariant` obiektu jest większa niż wartość *varSrc*. W przeciwnym razie FALSE. Operator używa domyślnych ustawień regionalnych użytkownika do przeprowadzenia porównania.

##  <a name="readfromstream"></a>CComVariant::ReadFromStream

Ustawia podstawowy wariant dla WARIANTu zawartego w określonym strumieniu.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
podczas Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu zawierającym dane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`ReadToStream`wymaga wcześniejszego wywołania do [WriteToStream](#writetostream).

##  <a name="setbyref"></a>CComVariant:: setbyref

Inicjuje obiekt i `vt` ustawia element członkowski na VT_BYREF. `CComVariant`

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ VARIANT, na przykład BSTR, **int**lub **char**.

*Zmiennoprzecinkow*<br/>
Wskaźnik używany do inicjowania `CComVariant` obiektu.

### <a name="remarks"></a>Uwagi

`SetByRef`jest szablonem funkcji, który inicjuje `CComVariant` obiekt na wskaźnik *pt* i ustawia `vt` element członkowski na VT_BYREF. Na przykład:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>CComVariant::WriteToStream

Zapisuje bazowy wariant do strumienia.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
podczas Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)
