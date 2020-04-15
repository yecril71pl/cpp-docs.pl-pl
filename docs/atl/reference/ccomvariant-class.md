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
ms.openlocfilehash: 9a84d91e20242fb206d1d3f71fcb3dd207561f62
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327228"
---
# <a name="ccomvariant-class"></a>Klasa CComVariant

Ta klasa zawija variant typu, zapewniając element członkowski wskazujący typ danych przechowywanych.

## <a name="syntax"></a>Składnia

```cpp
class CComVariant : public tagVARIANT
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComVariant::CComVariant](#ccomvariant)|Konstruktor.|
|[CComVariant::~CComVariant](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComVariant::Dołącz](#attach)|Dołącza wariant do `CComVariant` obiektu.|
|[CComVariant::ChangeType](#changetype)|Konwertuje `CComVariant` obiekt na nowy typ.|
|[CComVariant::Wyczyść](#clear)|Czyści `CComVariant` obiekt.|
|[CComVariant::Kopiowanie](#copy)|Kopiuje wariant `CComVariant` do obiektu.|
|[CComVariant::CopyTo](#copyto)|Kopiuje zawartość `CComVariant` obiektu.|
|[CComVariant::Detach](#detach)|Odłącza podstawowy wariant `CComVariant` od obiektu.|
|[CComVariant::GetSize](#getsize)|Zwraca rozmiar w liczbie bajtów zawartości `CComVariant` obiektu.|
|[CComVariant::ReadFromStream](#readfromstream)|Ładuje WARIANT ze strumienia.|
|[CComVariant::SetByRef](#setbyref)|Inicjuje `CComVariant` obiekt i `vt` ustawia element członkowski na VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Zapisuje podstawowy wariant w strumieniu.|

### <a name="public-operators"></a>Operatory publiczne

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|Wskazuje, `CComVariant` czy obiekt jest mniejszy niż określony VARIANT.|
|[CComVariant::operator >](#operator_gt)|Wskazuje, `CComVariant` czy obiekt jest większy niż określony WARIANT.|
|[operator !=](#operator_neq)|Wskazuje, `CComVariant` czy obiekt nie jest równy określonej variant.|
|[operator =](#operator_eq)|Przypisuje wartość do `CComVariant` obiektu.|
|[operator ==](#operator_eq_eq)|Wskazuje, `CComVariant` czy obiekt jest równy określonej variant.|

## <a name="remarks"></a>Uwagi

`CComVariant`Zawija VARIANT i VARIANTARG typu, który składa się z unii i elementu członkowskiego wskazując typ danych przechowywanych w unii. VARIANTs są zwykle używane w automatyzacji.

`CComVariant`pochodzi od typu VARIANT, dzięki czemu może być stosowany wszędzie tam, gdzie można użyć wariantu. Można na przykład użyć makra V_VT, aby wyodrębnić `CComVariant` typ lub uzyskać `vt` dostęp do elementu członkowskiego bezpośrednio, tak jak można z VARIANT.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

## <a name="ccomvariantattach"></a><a name="attach"></a>CComVariant::Dołącz

Bezpiecznie czyści bieżącą `CComVariant` zawartość obiektu, kopiuje zawartość *pSrc* do tego obiektu, a następnie ustawia typ wariantu *pSrc* na VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*Psrc*<br/>
[w] Wskazuje [na wariant,](/windows/win32/api/oaidl/ns-oaidl-variant) który ma być dołączony do obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Własność danych przechowywanych przez *pSrc* jest `CComVariant` przekazywana do obiektu.

## <a name="ccomvariantccomvariant"></a><a name="ccomvariant"></a>CComVariant::CComVariant

Każdy konstruktor obsługuje bezpieczne inicjowanie `CComVariant` `VariantInit` obiektu, wywołując funkcję Win32 lub ustawiając wartość i typ obiektu zgodnie z przekazanymi parametrami.

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

*varSrc ( varSrc )*<br/>
[w] Lub `CComVariant` WARIANT używany do `CComVariant` inicjowania obiektu. Zawartość wariantu źródłowego są kopiowane do miejsca docelowego bez konwersji.

*lpszsrc*<br/>
[w] Ciąg znaków używany do `CComVariant` inicjowania obiektu. Ciąg znaków szeroki (Unicode) można przekazać do wersji LPCOLESTR konstruktora lub ciągu ANSI do wersji LPCSTR. W obu przypadkach ciąg jest konwertowany na `SysAllocString`Unicode BSTR przydzielony przy użyciu programu . Typ `CComVariant` obiektu zostanie VT_BSTR.

*bSrc (właz)*<br/>
[w] **Bool** używany do inicjowania `CComVariant` obiektu. Argument **bool** jest konwertowany na VARIANT_BOOL przed zapisaniem. Typ `CComVariant` obiektu zostanie VT_BOOL.

*nSrc (nSrc)*<br/>
[w] **Int**, **BYTE**, **krótki**, **długi,** DŁUGI, ULONGLONG, **niepodpisany krótki,** **niepodpisany**długi `CComVariant` lub **niepodpisany int** używany do inicjowania obiektu. Typ `CComVariant` obiektu zostanie odpowiednio VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 lub VT_UI4.

*Vtsrc*<br/>
[w] Typ wariantu. Gdy pierwszy parametr jest **int**, prawidłowe typy są VT_I4 i VT_INT. Gdy pierwszy parametr jest **długi,** prawidłowe typy są VT_I4 i VT_ERROR. Gdy pierwszy parametr jest **podwójny,** prawidłowe typy są VT_R8 i VT_DATE. Gdy pierwszy parametr jest **niepodpisany int, prawidłowe**typy są VT_UI4 i VT_UINT.

*fltSrc ( fltSrc )*<br/>
[w] Float **float** używany do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie VT_R4.

*dblSrc ( dblSrc )*<br/>
[w] **Double** używane do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie VT_R8.

*cysrc (cysrc)*<br/>
[w] Używany `CY` do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie VT_CY.

*Psrc*<br/>
[w] Lub `IDispatch` `IUnknown` wskaźnik używany do `CComVariant` inicjowania obiektu. `AddRef`zostanie wywołana na wskaźniku interfejsu. Typ `CComVariant` obiektu zostanie odpowiednio VT_DISPATCH lub VT_UNKNOWN.

Lub wskaźnik SAFERRAY używany do `CComVariant` inicjowania obiektu. Kopia SAFEARRAY jest przechowywana `CComVariant` w obiekcie. Typ `CComVariant` obiektu będzie kombinacją oryginalnego typu SAFEARRAY i VT_ARRAY.

*Csrc*<br/>
[w] **Znak** używany do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie VT_I1.

*okręg wyborczy bstrSrc*<br/>
[w] BSTR używane do inicjowania `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie VT_BSTR.

### <a name="remarks"></a>Uwagi

Destruktor zarządza oczyszczaniem, wywołując [CComVariant::Clear](#clear).

## <a name="ccomvariantccomvariant"></a><a name="dtor"></a>CComVariant::~CComVariant

Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda zarządza oczyszczaniem, wywołując [CComVariant::Clear](#clear).

## <a name="ccomvariantchangetype"></a><a name="changetype"></a>CComVariant::ChangeType

Konwertuje `CComVariant` obiekt na nowy typ.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vtNowy*<br/>
[w] Nowy typ `CComVariant` obiektu.

*Psrc*<br/>
[w] Wskaźnik do WARIANT, którego wartość zostanie przekonwertowana na nowy typ. Wartością domyślną jest `CComVariant` NULL, co oznacza, że obiekt zostanie przekonwertowany na miejscu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Jeśli przekażesz wartość dla `ChangeType` *pSrc*, użyje tego wariantu jako źródła konwersji. W przeciwnym `CComVariant` razie obiekt będzie źródłem.

## <a name="ccomvariantclear"></a><a name="clear"></a>CComVariant::Wyczyść

Czyści `CComVariant` obiekt, wywołując `VariantClear` funkcję Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Destruktor automatycznie wywołuje `Clear`.

## <a name="ccomvariantcopy"></a><a name="copy"></a>CComVariant::Kopiowanie

Zwalnia obiekt, `CComVariant` a następnie przypisuje mu kopię określonego wariantu.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*Psrc*<br/>
[w] Wskaźnik do [wariantu](/windows/win32/api/oaidl/ns-oaidl-variant) do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="ccomvariantcopyto"></a><a name="copyto"></a>CComVariant::CopyTo

Kopiuje zawartość `CComVariant` obiektu.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parametry

*pstrDest (pstrDest)*<br/>
Wskazuje BSTR, który otrzyma kopię zawartości `CComVariant` obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Obiekt `CComVariant` musi być typu VT_BSTR.

## <a name="ccomvariantdetach"></a><a name="detach"></a>CComVariant::Detach

Odłącza podstawowy wariant `CComVariant` od obiektu i ustawia typ obiektu na VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parametry

*pDest (właśc.*<br/>
[na zewnątrz] Zwraca podstawową wartość VARIANT obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że zawartość VARIANT odwołuje się *pDest* zostanie automatycznie wyczyszczone przed przypisaniem `CComVariant` wartości i typu obiektu wywołującego.

## <a name="ccomvariantgetsize"></a><a name="getsize"></a>CComVariant::GetSize

W przypadku prostych zmiennic o stałym rozmiarze metoda zwraca **rozmiar** podstawowy typ danych plus **sizeof(VARTYPE).**

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar w bajtach bieżącej `CComVariant` zawartości obiektu.

### <a name="remarks"></a>Uwagi

Jeśli VARIANT zawiera wskaźnik `GetSize` interfejsu, `IPersistStream` kwerendy dla lub `IPersistStreamInit`. Jeśli się powiedzie, zwracana wartość jest niskiej kolejności 32 bity wartości zwracanej przez `GetSizeMax` plus **sizeof** CLSID i **sizeof(VARTYPE)**. Jeśli wskaźnik interfejsu ma `GetSize` wartość NULL, zwraca **rozmiar** identyfikatora CLSID plus **sizeof(VARTYPE).** Jeśli całkowity rozmiar jest większy niż `GetSize` ULONG_MAX, zwraca **sizeof(VARTYPE),** który wskazuje błąd.

We wszystkich innych przypadkach tymczasowy wariant typu VT_BSTR jest wymuszany z bieżącego WARIANTU. Długość tego BSTR jest obliczana jako rozmiar długości ciągu plus długość samego ciągu plus rozmiar znaku zerowego plus **sizeof(VARTYPE).** Jeśli wariant nie może być przymuszony do wariantu typu VT_BSTR, `GetSize` zwraca **sizeof(VARTYPE)**.

Rozmiar zwracany przez tę metodę odpowiada liczbie bajtów używanych przez [CComVariant::WriteToStream](#writetostream) w pomyślnych warunkach.

## <a name="ccomvariantoperator-"></a><a name="operator_eq"></a>CComVariant::operator =

Przypisuje wartość i odpowiedni typ `CComVariant` do obiektu.

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

*varSrc ( varSrc )*<br/>
[w] Lub `CComVariant` [WARIANT, który](/windows/win32/api/oaidl/ns-oaidl-variant) ma `CComVariant` być przypisany do obiektu. Zawartość wariantu źródłowego są kopiowane do miejsca docelowego bez konwersji.

*okręg wyborczy bstrSrc*<br/>
[w] BSTR, który ma zostać `CComVariant` przypisany do obiektu. Typ `CComVariant` obiektu zostanie VT_BSTR.

*lpszsrc*<br/>
[w] Ciąg znaków, który ma `CComVariant` być przypisany do obiektu. Ciąg znaków z zerowym zakończeniem (Unicode) można przekazać do wersji LPCOLESTR operatora lub ciągu ANSI do wersji LPCSTR. W obu przypadkach ciąg jest konwertowany na Unicode BSTR przydzielony przy użyciu `SysAllocString`. Typ `CComVariant` obiektu zostanie VT_BSTR.

*bSrc (właz)*<br/>
[w] **Bool, który** ma zostać `CComVariant` przypisany do obiektu. Argument **bool** jest konwertowany na VARIANT_BOOL przed zapisaniem. Typ `CComVariant` obiektu zostanie VT_BOOL.

*nSrc (nSrc)*<br/>
[w] Int , BYTE, **krótki**, **długi,** DŁUGI, ULONGLONG, **niepodpisany krótki,** **niepodpisany długi**lub `CComVariant` **niepodpisany int,** który ma być przypisany do obiektu. **int** Typ `CComVariant` obiektu zostanie odpowiednio VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 lub VT_UI4.

*fltSrc ( fltSrc )*<br/>
[w] **Pływak,** który ma być `CComVariant` przypisany do obiektu. Typ `CComVariant` obiektu zostanie VT_R4.

*dblSrc ( dblSrc )*<br/>
[w] **Double,** który ma być `CComVariant` przypisany do obiektu. Typ `CComVariant` obiektu zostanie VT_R8.

*cysrc (cysrc)*<br/>
[w] Do `CY` przypisania `CComVariant` do obiektu. Typ `CComVariant` obiektu zostanie VT_CY.

*Psrc*<br/>
[w] Lub `IDispatch` `IUnknown` wskaźnik, który ma `CComVariant` być przypisany do obiektu. `AddRef`zostanie wywołana na wskaźniku interfejsu. Typ `CComVariant` obiektu zostanie odpowiednio VT_DISPATCH lub VT_UNKNOWN.

Lub wskaźnik SAFEARRAY, który ma `CComVariant` być przypisany do obiektu. Kopia SAFEARRAY jest przechowywana `CComVariant` w obiekcie. Typ `CComVariant` obiektu będzie kombinacją oryginalnego typu SAFEARRAY i VT_ARRAY.

*Csrc*<br/>
[w] Znak, który ma zostać `CComVariant` przypisany do obiektu. Typ `CComVariant` obiektu zostanie VT_I1.

## <a name="ccomvariantoperator-"></a><a name="operator_eq_eq"></a>CComVariant::operator ==

Wskazuje, `CComVariant` czy obiekt jest równy określonej variant.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli wartość i typ *varSrc* są równe wartości `CComVariant` i typowi obiektu. W przeciwnym razie FALSE. Operator używa ustawień regionalnych użytkownika do wykonania porównania.

Operator porównuje tylko wartość typów wariantów. Porównuje ciągi, liczby całkowite i zmiennoprzecinkowe, ale nie tablice lub rekordy.

## <a name="ccomvariantoperator-"></a><a name="operator_neq"></a>CComVariant::operator !=

Wskazuje, `CComVariant` czy obiekt nie jest równy określonej variant.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli wartość lub typ *varSrc* nie jest równa wartości `CComVariant` lub typowi obiektu. W przeciwnym razie FALSE. Operator używa ustawień regionalnych użytkownika do wykonania porównania.

Operator porównuje tylko wartość typów wariantów. Porównuje ciągi, liczby całkowite i zmiennoprzecinkowe, ale nie tablice lub rekordy.

## <a name="ccomvariantoperator-lt"></a><a name="operator_lt"></a>CComVariant::operator&lt;

Wskazuje, `CComVariant` czy obiekt jest mniejszy niż określony VARIANT.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, `CComVariant` jeśli wartość obiektu jest mniejsza niż wartość *varSrc*. W przeciwnym razie FALSE. Operator używa ustawień regionalnych użytkownika do wykonania porównania.

## <a name="ccomvariantoperator-gt"></a><a name="operator_gt"></a>CComVariant::operator&gt;

Wskazuje, `CComVariant` czy obiekt jest większy niż określony WARIANT.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, `CComVariant` jeśli wartość obiektu jest większa niż wartość *varSrc*. W przeciwnym razie FALSE. Operator używa ustawień regionalnych użytkownika do wykonania porównania.

## <a name="ccomvariantreadfromstream"></a><a name="readfromstream"></a>CComVariant::ReadFromStream

Ustawia wariant bazowy na WARIANT zawarty w określonym strumieniu.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
[w] Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu zawierającym dane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`ReadToStream`wymaga poprzedniego wywołania [WriteToStream](#writetostream).

## <a name="ccomvariantsetbyref"></a><a name="setbyref"></a>CComVariant::SetByRef

Inicjuje `CComVariant` obiekt i `vt` ustawia element członkowski na VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parametry

*T*<br/>
Typ VARIANT, na przykład BSTR, **int**lub **char**.

*Pt*<br/>
Wskaźnik używany do inicjowania `CComVariant` obiektu.

### <a name="remarks"></a>Uwagi

`SetByRef`jest szablonem funkcji, który `CComVariant` inicjuje obiekt do `vt` wskaźnika *pT* i ustawia element członkowski na VT_BYREF. Przykład:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

## <a name="ccomvariantwritetostream"></a><a name="writetostream"></a>CComVariant::WriteToStream

Zapisuje podstawowy wariant w strumieniu.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
[w] Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)
