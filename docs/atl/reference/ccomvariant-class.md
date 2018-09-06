---
title: Klasa CComVariant | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf9fbd4967bbd3091d734f9b70aed9350d63a25e
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753197"
---
# <a name="ccomvariant-class"></a>Klasa CComVariant

Ta klasa opakowuje Typ VARIANT, zapewniając członka, wskazujący typ danych przechowywanych.

## <a name="syntax"></a>Składnia

```  
cpp
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
|[CComVariant::Attach](#attach)|Dołącza wariant do `CComVariant` obiektu.|
|[CComVariant::ChangeType](#changetype)|Konwertuje `CComVariant` obiektu do nowego typu.|
|[CComVariant::Clear](#clear)|Czyści `CComVariant` obiektu.|
|[CComVariant::Copy](#copy)|Kopiuje wariant do `CComVariant` obiektu.|
|[CComVariant::CopyTo](#copyto)|Kopiuje zawartość `CComVariant` obiektu.|
|[CComVariant::Detach](#detach)|Odłącza bazowego wariant ze `CComVariant` obiektu.|
|[CComVariant::GetSize](#getsize)|Zwraca rozmiar liczby bajtów zawartość `CComVariant` obiektu.|
|[CComVariant::ReadFromStream](#readfromstream)|Ładuje wariant ze strumienia.|
|[CComVariant::SetByRef](#setbyref)|Inicjuje `CComVariant` i ustawia `vt` członka do VT_BYREF.|
|[CComVariant::WriteToStream](#writetostream)|Zapisuje wariant podstawowego do strumienia.|

### <a name="public-operators"></a>Operatory publiczne

|||
|-|-|
|[CComVariant::operator <](#operator_lt)|Wskazuje, czy `CComVariant` obiekt jest mniejszy niż określony typ VARIANT.|
|[CComVariant::operator >](#operator_gt)|Wskazuje, czy `CComVariant` obiekt jest większy niż określony typ VARIANT.|
|[operator! =](#operator_neq)|Wskazuje, czy `CComVariant` obiektu nie jest równa określonej wariant.|
|[operator =](#operator_eq)|Przypisuje wartość do `CComVariant` obiektu.|
|[operator ==](#operator_eq_eq)|Wskazuje, czy `CComVariant` obiektu jest równe określonej wariant.|

## <a name="remarks"></a>Uwagi

`CComVariant` opakowuje typ WARIANTU i VARIANTARG, który składa się z Unii i członka, wskazujący typ danych przechowywanych w Unii. Warianty są zwykle używane w usłudze Automation.

`CComVariant` pochodzi z typu VARIANT, dzięki czemu może służyć wszędzie tam, gdzie typ VARIANT może służyć. Na przykład umożliwia makro V_VT wyodrębnić typ `CComVariant` lub możesz uzyskać dostęp `vt` bezpośrednio po prostu, jak w przypadku wariant elementu członkowskiego.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`tagVARIANT`

`CComVariant`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlcomcli.h

##  <a name="attach"></a>  CComVariant::Attach

Bezpiecznie Czyści bieżącą zawartość `CComVariant` obiektów, kopiuje zawartość *pSrc* do tego obiektu, a następnie ustawia typ wariantu *pSrc* do VT_EMPTY.

```
HRESULT Attach(VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*  
[in] Wskazuje [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) dołączony do obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Własność danych przechowywanych w *pSrc* jest przekazywany do `CComVariant` obiektu.

##  <a name="ccomvariant"></a>  CComVariant::CComVariant

Każdy konstruktor obsługuje bezpieczne wątkowo inicjowanie `CComVariant` obiektu przez wywołanie metody `VariantInit` funkcję Win32 lub poprzez skonfigurowanie typu zgodnie z przekazanych parametrów i wartości obiektu.

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

*varSrc*  
[in] `CComVariant` Lub wariant używane do zainicjowania `CComVariant` obiektu. Zawartość wariant źródła są kopiowane do lokalizacji docelowej bez konwersji.

*lpszSrc*  
[in] Ciąg znaków używany do inicjowania `CComVariant` obiektu. Zakończony zerem szerokie (Unicode) ciąg znaków można przekazać do LPCOLESTR wersję konstruktora lub na ciąg ANSI do wersji LPCSTR. W obu przypadkach ten ciąg jest konwertowany na Unicode BSTR przydzielony przy użyciu `SysAllocString`. Typ `CComVariant` obiekt będzie VT_BSTR.

*bSrc*  
[in] **Bool** używane do zainicjowania `CComVariant` obiektu. **Bool** argument jest konwertowany na VARIANT_BOOL przed magazynowana. Typ `CComVariant` obiekt będzie VT_BOOL.

*nSrc*  
[in] **Int**, **BAJTÓW**, **krótki**, **długie**, LONGLONG, ULONGLONG, **typ unsigned short**, **unsigned long**, lub **unsigned int** używane do zainicjowania `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 lub VT_UI4, odpowiednio.

*vtSrc*  
[in] Typ variant. Po pierwszym parametrem jest **int**, prawidłowe typy to VT_I4 i VT_INT. Po pierwszym parametrem jest **długie**, prawidłowe typy to VT_I4 i VT_ERROR. Po pierwszym parametrem jest **double**, prawidłowe typy to VT_R8 i VT_DATE. Po pierwszym parametrem jest **unsigned int**, prawidłowe typy to VT_UI4 i VT_UINT.

*fltSrc*  
[in] **Float** używane do zainicjowania `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_R4.

*dblSrc*  
[in] **Double** używane do zainicjowania `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_R8.

*cySrc*  
[in] `CY` Używane do zainicjowania `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_CY.

*pSrc*  
[in] `IDispatch` Lub `IUnknown` używane do zainicjowania wskaźnika `CComVariant` obiektu. `AddRef` zostanie wywołana na wskaźnik interfejsu. Typ `CComVariant` obiekt będzie VT_DISPATCH lub VT_UNKNOWN, odpowiednio.

Lub wskaźnik SAFERRAY używane do zainicjowania `CComVariant` obiektu. Kopia parametru SafeArray jest przechowywana w `CComVariant` obiektu. Typ `CComVariant` obiekt będzie kombinację SAFEARRAY i VT_ARRAY oryginalnego typu.

*cSrc*  
[in] **Char** używane do zainicjowania `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_I1.

*bstrSrc*  
[in] BSTR używane do zainicjowania `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_BSTR.

### <a name="remarks"></a>Uwagi

Destruktor zarządza oczyszczania, wywołując [CComVariant::Clear](#clear).

##  <a name="dtor"></a>  CComVariant:: ~ CComVariant

Destruktor.

```
~CComVariant() throw();
```

### <a name="remarks"></a>Uwagi

Ta metoda zarządza oczyszczania, wywołując [CComVariant::Clear](#clear).

##  <a name="changetype"></a>  CComVariant::ChangeType

Konwertuje `CComVariant` obiektu do nowego typu.

```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```

### <a name="parameters"></a>Parametry

*vtNew*  
[in] Nowy typ dla `CComVariant` obiektu.

*pSrc*  
[in] Wskaźnik do wariant, którego wartość zostaną przekonwertowane na nowy typ. Wartość domyślna to NULL, co oznacza `CComVariant` obiekt zostanie przekształcony w miejscu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

W przypadku przekazania wartości *pSrc*, `ChangeType` użyje tego wariant jako źródła do konwersji. W przeciwnym razie `CComVariant` obiekt będzie źródła.

##  <a name="clear"></a>  CComVariant::Clear

Czyści `CComVariant` obiektu przez wywołanie metody `VariantClear` funkcję Win32.

```
HRESULT Clear();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Destruktor automatycznie wywołuje `Clear`.

##  <a name="copy"></a>  CComVariant::Copy

Zwalnia `CComVariant` obiektu, a następnie przypisuje go kopię określonego wariant.

```
HRESULT Copy(const VARIANT* pSrc);
```

### <a name="parameters"></a>Parametry

*pSrc*  
[in] Wskaźnik do [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) do skopiowania.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

##  <a name="copyto"></a>  CComVariant::CopyTo

Kopiuje zawartość `CComVariant` obiektu.

```
HRESULT CopyTo(BSTR* pstrDest);
```

### <a name="parameters"></a>Parametry

*pstrDest*  
Wskazuje ciąg BSTR, który otrzyma kopię zawartości `CComVariant` obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

`CComVariant` Obiekt musi być typu VT_BSTR.

##  <a name="detach"></a>  CComVariant::Detach

Odłącza bazowego wariant ze `CComVariant` obiektu i ustawia typ obiektu VT_EMPTY.

```
HRESULT Detach(VARIANT* pDest);
```

### <a name="parameters"></a>Parametry

*pDest*  
[out] Zwraca podstawową wartość WARIANTU obiektu.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Należy zauważyć, że odwołuje się do niego zawartość wariant *pDest* zostaną automatycznie wyczyszczone przed przypisaniem wartości i typu wywołania `CComVariant` obiektu.

##  <a name="getsize"></a>  CComVariant::GetSize

Warianty rozmiarze prosty, ta metoda zwraca **sizeof** odpowiedniego typu danych oraz **sizeof(VARTYPE)**.

```
ULONG GetSize() const;
```

### <a name="return-value"></a>Wartość zwracana

Rozmiar w bajtach Bieżąca zawartość `CComVariant` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli wariant zawiera wskaźnika interfejsu `GetSize` wysyła zapytanie o `IPersistStream` lub `IPersistStreamInit`. Jeśli operacja się powiedzie, wartość zwracana jest niskiego rzędu 32 bity w wartości zwracanej przez `GetSizeMax` plus **sizeof** CLSID i **sizeof(VARTYPE)**. Jeśli wskaźnik interfejsu ma wartość NULL, `GetSize` zwraca **sizeof** CLSID plus **sizeof(VARTYPE)**. Jeśli całkowity rozmiar jest większy niż ULONG_MAX, `GetSize` zwraca **sizeof(VARTYPE)** który wskazuje na błąd.

We wszystkich innych przypadkach tymczasowe wariant typu VT_BSTR jest przekształcone z WARIANTU bieżącego. Długość tego BSTR jest obliczany jako rozmiar długości ciągu plus długość ciągu, sama plus rozmiar oraz znak null **sizeof(VARTYPE)**. Jeśli nie mogą zostać przekształcone wariant wariant typu VT_BSTR, `GetSize` zwraca **sizeof(VARTYPE)**.

Rozmiar zwracanego przez tę metodę jest zgodna z liczbą bajtów używanych przez [CComVariant::WriteToStream](#writetostream) warunkach się pomyślnie.

##  <a name="operator_eq"></a>  CComVariant::operator =

Przypisuje wartość i odpowiedni typ do `CComVariant` obiektu.

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

*varSrc*  
[in] `CComVariant` Lub [VARIANT](/previous-versions/windows/desktop/api/oaidl/ns-oaidl-tagvariant) ma być przypisane do `CComVariant` obiektu. Zawartość wariant źródła są kopiowane do lokalizacji docelowej bez konwersji.

*bstrSrc*  
[in] BSTR ma być przypisane do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_BSTR.

*lpszSrc*  
[in] Ciąg znaków, który ma być przypisane do `CComVariant` obiektu. Zakończony zerem szerokie (Unicode) ciąg znaków można przekazać do wersji LPCOLESTR operatora lub na ciąg ANSI do wersji LPCSTR. W obu przypadkach ten ciąg jest konwertowany na Unicode BSTR przydzielony przy użyciu `SysAllocString`. Typ `CComVariant` obiekt będzie VT_BSTR.

*bSrc*  
[in] **Bool** ma być przypisane do `CComVariant` obiektu. **Bool** argument jest konwertowany na VARIANT_BOOL przed magazynowana. Typ `CComVariant` obiekt będzie VT_BOOL.

*nSrc*  
[in] **Int**, BYTE, **krótki**, **długie**, LONGLONG, ULONGLONG, **typ unsigned short**, **unsigned long**, lub **unsigned int** ma być przypisane do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_I4, VT_UI1, VT_I2, VT_I4, VT_I8, VT_UI8, VT_UI2, VT_UI4 lub VT_UI4, odpowiednio.

*fltSrc*  
[in] **Float** ma być przypisane do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_R4.

*dblSrc*  
[in] **Double** ma być przypisane do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_R8.

*cySrc*  
[in] `CY` Ma być przypisane do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_CY.

*pSrc*  
[in] `IDispatch` Lub `IUnknown` wskaźnika do przypisania do `CComVariant` obiektu. `AddRef` zostanie wywołana na wskaźnik interfejsu. Typ `CComVariant` obiekt będzie VT_DISPATCH lub VT_UNKNOWN, odpowiednio.

Lub wskaźnik SAFEARRAY ma być przypisane do `CComVariant` obiektu. Kopia parametru SafeArray jest przechowywana w `CComVariant` obiektu. Typ `CComVariant` obiekt będzie kombinację SAFEARRAY i VT_ARRAY oryginalnego typu.

*cSrc*  
[in] Znak, który ma być przypisane do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie VT_I1.

##  <a name="operator_eq_eq"></a>  CComVariant::operator ==

Wskazuje, czy `CComVariant` obiektu jest równe określonej wariant.

```
bool operator==(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli wartość i typ *varSrc* są takie same wartości i typu, odpowiednio, `CComVariant` obiektu. W przeciwnym razie wartość FALSE. Operator używa użytkownika domyślne ustawienia regionalne do przeprowadzenia porównania.

Operator porównuje tylko wartości typów variant. Porównuje ciągi, liczby całkowite i zmiennoprzecinkowy punktów, ale nie tablic lub rekordów.

##  <a name="operator_neq"></a>  CComVariant::operator! =

Wskazuje, czy `CComVariant` obiektu nie jest równa określonej wariant.

```
bool operator!=(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli wartość lub typ *varSrc* nie jest równa wartości lub typu, odpowiednio, `CComVariant` obiektu. W przeciwnym razie wartość FALSE. Operator używa użytkownika domyślne ustawienia regionalne do przeprowadzenia porównania.

Operator porównuje tylko wartości typów variant. Porównuje ciągi, liczby całkowite i zmiennoprzecinkowy punktów, ale nie tablic lub rekordów.

##  <a name="operator_lt"></a>  CComVariant::operator &lt;

Wskazuje, czy `CComVariant` obiekt jest mniejszy niż określony typ VARIANT.

```
bool operator<(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli wartość `CComVariant` obiekt jest mniejszy niż wartość *varSrc*. W przeciwnym razie wartość FALSE. Operator używa użytkownika domyślne ustawienia regionalne do przeprowadzenia porównania.

##  <a name="operator_gt"></a>  CComVariant::operator &gt;

Wskazuje, czy `CComVariant` obiekt jest większy niż określony typ VARIANT.

```
bool operator>(const VARIANT& varSrc) const throw();
```

### <a name="remarks"></a>Uwagi

Zwraca wartość PRAWDA, jeśli wartość `CComVariant` obiekt jest większy niż wartość *varSrc*. W przeciwnym razie wartość FALSE. Operator używa użytkownika domyślne ustawienia regionalne do przeprowadzenia porównania.

##  <a name="readfromstream"></a>  CComVariant::ReadFromStream

Ustawia podstawowy typ VARIANT do WARIANTU zawarte w określonej usłudze stream.

```
HRESULT ReadFromStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*  
[in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfejsu w usłudze stream, zawierającą dane.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

`ReadToStream` wymaga poprzednie wywołanie [WriteToStream](#writetostream).

##  <a name="setbyref"></a>  CComVariant::SetByRef

Inicjuje `CComVariant` i ustawia `vt` członka do VT_BYREF.

```
template < typename T >
void SetByRef(T* pT) throw();
```

### <a name="parameters"></a>Parametry

*T*  
Typ WARIANTU, na przykład BSTR **int**, lub **char**.

*(CZAS PACYFICZNY)*  
Wskaźnik, używane do zainicjowania `CComVariant` obiektu.

### <a name="remarks"></a>Uwagi

`SetByRef` jest szablonem funkcji, która inicjuje `CComVariant` obiekt wskaźnika *pT* i ustawia `vt` członka do VT_BYREF. Na przykład:

[!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]

##  <a name="writetostream"></a>  CComVariant::WriteToStream

Zapisuje wariant podstawowego do strumienia.

```
HRESULT WriteToStream(IStream* pStream);
```

### <a name="parameters"></a>Parametry

*pStream*  
[in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfejsu dla strumienia.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)