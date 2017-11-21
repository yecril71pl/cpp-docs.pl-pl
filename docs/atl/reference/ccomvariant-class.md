---
title: Klasa CComVariant | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- VARIANT macro
- CComVariant class
- VARIANT macro, ATL
ms.assetid: 4d31149c-d005-44b5-a509-10f84afa2b61
caps.latest.revision: "26"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 153c71f36eb56ce9d848b791e9a2ef16d9f6a6d0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccomvariant-class"></a>Klasa CComVariant
Ta klasa jest zawijana `VARIANT` typu, zapewniając członka wskazujący typ danych przechowywanych.  
  
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
|[CComVariant::Attach](#attach)|Dołącza **VARIANT** do `CComVariant` obiektu.|  
|[CComVariant::ChangeType](#changetype)|Konwertuje `CComVariant` obiektu do nowego typu.|  
|[CComVariant::Clear](#clear)|Czyści `CComVariant` obiektu.|  
|[CComVariant::Copy](#copy)|Kopie **VARIANT** do `CComVariant` obiektu.|  
|[CComVariant::CopyTo](#copyto)|Kopiuje zawartość `CComVariant` obiektu.|  
|[CComVariant::Detach](#detach)|Odłącza odpowiadającego **VARIANT** z `CComVariant` obiektu.|  
|[CComVariant::GetSize](#getsize)|Zwraca liczbę bajtów zawartość rozmiar `CComVariant` obiektu.|  
|[CComVariant::ReadFromStream](#readfromstream)|Ładunki **VARIANT** ze strumienia.|  
|[CComVariant::SetByRef](#setbyref)|Inicjuje `CComVariant` obiektu i zestawy **vt** członka **VT_BYREF**.|  
|[CComVariant::WriteToStream](#writetostream)|Zapisuje odpowiadającego **VARIANT** do strumienia.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|||  
|-|-|  
|[CComVariant::operator <](#operator_lt)|Wskazuje, czy `CComVariant` obiekt jest mniejszy niż określony **VARIANT**.|  
|[CComVariant::operator >](#operator_gt)|Wskazuje, czy `CComVariant` obiekt jest większy niż określony **VARIANT**.|  
|[operator! =](#operator_neq)|Wskazuje, czy `CComVariant` obiektu nie jest równa określonej **VARIANT**.|  
|[operator =](#operator_eq)|Przypisuje wartość do `CComVariant` obiektu.|  
|[operator ==](#operator_eq_eq)|Wskazuje, czy `CComVariant` obiektu jest równe określonej **VARIANT**.|  
  
## <a name="remarks"></a>Uwagi  
 `CComVariant`opakowuje `VARIANT and VARIANTARG` typu, który składa się Unii i wskazujący typ danych przechowywanych w Unii członka. **VARIANT**s są zazwyczaj używane w automatyzacji.  
  
 `CComVariant`pochodzi z **VARIANT** wpisz, więc może być używane wszędzie tam, gdzie **VARIANT** mogą być używane. Na przykład można używać **V_VT** makra w celu wyodrębnienia typ `CComVariant` lub można uzyskać dostępu do **vt** bezpośrednio tak samo, jak w przypadku elementu członkowskiego **VARIANT**.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 `tagVARIANT`  
  
 `CComVariant`  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlcomcli.h  
  
##  <a name="attach"></a>CComVariant::Attach  
 Bezpiecznie Czyści bieżącą zawartość `CComVariant` obiektów, kopiuje zawartość `pSrc` do tego obiektu, a następnie ustawia typ wariantu `pSrc` do `VT_EMPTY`.  
  
```
HRESULT Attach(VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pSrc`  
 [in] Wskazuje [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) jest dołączony do obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Własność dane przechowywane przez `pSrc` jest przenoszona do `CComVariant` obiektu.  
  
##  <a name="ccomvariant"></a>CComVariant::CComVariant  
 Bezpieczne Inicjowanie obsługi każdego konstruktora `CComVariant` obiektu przez wywołanie metody `VariantInit` funkcji Win32 lub przez ustawienie wartości i typ zgodnie z parametrów przekazanych obiektu.  
  
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
 [in] `CComVariant` Lub `VARIANT` używaną do inicjalizacji `CComVariant` obiektu. Zawartość variant źródła są kopiowane do lokalizacji docelowej bez użycia konwersji.  
  
 `lpszSrc`  
 [in] Ciąg znaków używany do inicjowania `CComVariant` obiektu. Można przekazać zakończony zerem dwubajtowe (Unicode) ciągu znaków na **LPCOLESTR** wersję konstruktora lub ciągu ANSI na `LPCSTR` wersji. W obu przypadkach ten ciąg jest konwertowana na ciąg Unicode `BSTR` przydzielony przy użyciu **SysAllocString**. Typ `CComVariant` obiekt będzie `VT_BSTR`.  
  
 `bSrc`  
 [in] `bool` Używaną do inicjalizacji `CComVariant` obiektu. `bool` Argument jest konwertowana na **VARIANT_BOOL** przed są przechowywane. Typ `CComVariant` obiekt będzie `VT_BOOL`.  
  
 `nSrc`  
 [in] `int`, **BAJTÓW**, **krótki**, **długi**, **LONGLONG**, **ULONGLONG**, **niepodpisane krótko**, `unsigned long`, lub `unsigned int` używaną do inicjalizacji `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, lub **VT_UI4**odpowiednio.  
  
 `vtSrc`  
 [in] Typ wariantu. Po pierwszym parametrem jest `int`, prawidłowe typy to `VT_I4` i **VT_INT**. Po pierwszym parametrem jest **długi**, prawidłowe typy to `VT_I4` i `VT_ERROR`. Po pierwszym parametrem jest **podwójne**, prawidłowe typy to `VT_R8` i `VT_DATE`. Po pierwszym parametrem jest `unsigned int`, prawidłowe typy to **VT_UI4** i **VT_UINT**.  
  
 `fltSrc`  
 [in] **Float** używaną do inicjalizacji `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_R4`.  
  
 `dblSrc`  
 [in] **Podwójne** używaną do inicjalizacji `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_R8`.  
  
 `cySrc`  
 [in] **CY** używaną do inicjalizacji `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_CY`.  
  
 `pSrc`  
 [in] `IDispatch` Lub **IUnknown** wskaźnika używaną do inicjalizacji `CComVariant` obiektu. `AddRef`zostanie wywołana na wskaźnik interfejsu. Typ `CComVariant` obiekt będzie **VT_DISPATCH** lub **VT_UNKNOWN**odpowiednio.  
  
 Lub, **SAFERRAY** wskaźnika używaną do inicjalizacji `CComVariant` obiektu. Kopię **SAFEARRAY** są przechowywane w `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie kombinację pierwotny typ **SAFEARRAY** i **VT_ARRAY**.  
  
 `cSrc`  
 [in] `char` Używaną do inicjalizacji `CComVariant` obiektu. Typ `CComVariant` obiekt będzie **VT_I1**.  
  
 `bstrSrc`  
 [in] BSTR używaną do inicjalizacji `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_BSTR`.  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zarządza oczyszczania przez wywołanie metody [CComVariant::Clear](#clear).  
  
##  <a name="dtor"></a>CComVariant:: ~ CComVariant  
 Destruktor.  
  
```
~CComVariant() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta metoda zarządza oczyszczania przez wywołanie metody [CComVariant::Clear](#clear).  
  
##  <a name="changetype"></a>CComVariant::ChangeType  
 Konwertuje `CComVariant` obiektu do nowego typu.  
  
```
HRESULT ChangeType(VARTYPE vtNew, const VARIANT* pSrc = NULL);
```  
  
### <a name="parameters"></a>Parametry  
 `vtNew`  
 [in] Nowy typ dla `CComVariant` obiektu.  
  
 `pSrc`  
 [in] Wskaźnik do `VARIANT` którego wartość zostanie przekonwertowany do nowego typu. Wartość domyślna to **NULL**, co oznacza `CComVariant` obiekt zostanie przekonwertowany na miejscu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli przekazuj wartości dla `pSrc`, `ChangeType` zostanie ona użyta **VARIANT** jako źródło do konwersji. W przeciwnym razie `CComVariant` obiekt będzie źródła.  
  
##  <a name="clear"></a>CComVariant::Clear  
 Czyści `CComVariant` obiektu przez wywołanie metody `VariantClear` funkcji Win32.  
  
```
HRESULT Clear();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Destruktor automatycznie wywołuje **wyczyść**.  
  
##  <a name="copy"></a>CComVariant::Copy  
 Zwalnia `CComVariant` obiekt, a następnie przypisuje go kopię określonego **VARIANT**.  
  
```
HRESULT Copy(const VARIANT* pSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `pSrc`  
 [in] Wskaźnik do [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) do skopiowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
##  <a name="copyto"></a>CComVariant::CopyTo  
 Kopiuje zawartość `CComVariant` obiektu.  
  
```
HRESULT CopyTo(BSTR* pstrDest);
```  
  
### <a name="parameters"></a>Parametry  
 *pstrDest*  
 Wskazuje `BSTR` który otrzyma kopię zawartości `CComVariant` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 **CComVariant** obiekt musi być typu `VT_BSTR`.  
  
##  <a name="detach"></a>CComVariant::Detach  
 Odłącza odpowiadającego **VARIANT** z `CComVariant` obiektu i ustawia typ obiektu `VT_EMPTY`.  
  
```
HRESULT Detach(VARIANT* pDest);
```  
  
### <a name="parameters"></a>Parametry  
 `pDest`  
 [out] Zwraca odpowiadającego `VARIANT` wartość obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Należy pamiętać, że zawartość `VARIANT` odwołuje `pDest` zostaną automatycznie wyczyszczone przed przypisaniem wartości i typ wywołujący **CComVariant** obiektu.  
  
##  <a name="getsize"></a>CComVariant::GetSize  
 Dla rozmiarze prosty `VARIANT`s, ta metoda zwraca `sizeof` podstawowy typ danych oraz `sizeof(VARTYPE)`.  
  
```
ULONG GetSize() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Rozmiar w bajtach bieżącą zawartość `CComVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `VARIANT` zawiera wskaźnika interfejsu `GetSize` kwerendy o `IPersistStream` lub `IPersistStreamInit`. Jeśli się powiedzie, wartość zwracana jest 32-bitowy znaczącymi bitami wartości zwróconej przez `GetSizeMax` oraz `sizeof` `CLSID` i `sizeof(VARTYPE)`. Jeśli jest wskaźnik interfejsu `NULL`, `GetSize` zwraca `sizeof` `CLSID` plus `sizeof(VARTYPE)`. Jeśli całkowity rozmiar jest większy niż `ULONG_MAX`, `GetSize` zwraca `sizeof(VARTYPE)` co wskazuje błąd.  
  
 We wszystkich innych przypadkach tymczasowej `VARIANT` typu `VT_BSTR` jest traktowany jak z bieżącego `VARIANT`. Długość to `BSTR` jest obliczany jako rozmiar długości ciągu plus długość sam ciąg powiększony o rozmiar plus znak null `sizeof(VARTYPE)`. Jeśli `VARIANT` nie można przekształcić `VARIANT` typu `VT_BSTR`, `GetSize` zwraca `sizeof(VARTYPE)`.  
  
 Liczba bajtów używanych przez dopasowuje rozmiar zwracane przez tę metodę [CComVariant::WriteToStream](#writetostream) warunkach powiodło się.  
  
##  <a name="operator_eq"></a>CComVariant::operator =  
 Przypisuje wartość i odpowiedni typ `CComVariant` obiektu.  
  
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
 [in] `CComVariant` Lub [VARIANT](http://msdn.microsoft.com/en-us/e305240e-9e11-4006-98cc-26f4932d2118) do przypisania do `CComVariant` obiektu. Zawartość variant źródła są kopiowane do lokalizacji docelowej bez użycia konwersji.  
  
 `bstrSrc`  
 [in] BSTR, który ma zostać przypisany do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_BSTR`.  
  
 `lpszSrc`  
 [in] Ciąg znaków ma być przypisany do `CComVariant` obiektu. Można przekazać zakończony zerem dwubajtowe (Unicode) ciągu znaków na **LPCOLESTR** wersji operator lub ciągu ANSI na `LPCSTR` wersji. W obu przypadkach jest przekonwertowanie ciągu na Unicode `BSTR` przydzielony przy użyciu **SysAllocString**. Typ `CComVariant` obiekt będzie `VT_BSTR`.  
  
 `bSrc`  
 [in] `bool` Do przypisania do `CComVariant` obiektu. `bool` Argument jest konwertowana na **VARIANT_BOOL** przed są przechowywane. Typ `CComVariant` obiekt będzie `VT_BOOL`.  
  
 `nSrc`  
 [in] `int`, **BAJTÓW**, **krótki**, **długi**, **LONGLONG**, **ULONGLONG**, **niepodpisane krótko**, `unsigned long`, lub `unsigned int` do przypisania do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_I4`, `VT_UI1`, `VT_I2`, `VT_I4`, **VT_I8**, **VT_UI8**, **VT_UI2**,  **VT_UI4**, lub **VT_UI4**odpowiednio.  
  
 `fltSrc`  
 [in] **Float** do przypisania do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_R4`.  
  
 `dblSrc`  
 [in] **Podwójne** do przypisania do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_R8`.  
  
 `cySrc`  
 [in] **CY** do przypisania do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie `VT_CY`.  
  
 `pSrc`  
 [in] `IDispatch` Lub **IUnknown** wskaźnika do przypisania do `CComVariant` obiektu. `AddRef`zostanie wywołana na wskaźnik interfejsu. Typ `CComVariant` obiekt będzie **VT_DISPATCH** lub **VT_UNKNOWN**odpowiednio.  
  
 Lub, **SAFEARRAY** wskaźnika do przypisania do `CComVariant` obiektu. Kopię **SAFEARRAY** są przechowywane w `CComVariant` obiektu. Typ `CComVariant` obiektu zostanie kombinację pierwotny typ **SAFEARRAY** i **VT_ARRAY**.  
  
 `cSrc`  
 [in] Znak, który ma zostać przypisany do `CComVariant` obiektu. Typ `CComVariant` obiekt będzie **VT_I1**.  
  
##  <a name="operator_eq_eq"></a>CComVariant::operator ==  
 Wskazuje, czy `CComVariant` obiektu jest równe określonej **VARIANT**.  
  
```
bool operator==(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** Jeśli wartości i typ *varSrc* jest równa wartości i typ, odpowiednio `CComVariant` obiektu. W przeciwnym razie **false**. Operator używa użytkownika domyślne ustawienia regionalne do porównania.  
  
 Operator porównuje tylko wartość typu variant. Porównuje ciągów, liczb całkowitych i przestawne punkty, ale nie tablice lub rekordów.  
  
##  <a name="operator_neq"></a>CComVariant::operator! =  
 Wskazuje, czy `CComVariant` obiektu nie jest równa określonej **VARIANT**.  
  
```
bool operator!=(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** Jeśli wartość lub typ *varSrc* nie jest równa wartości lub typ, odpowiednio `CComVariant` obiektu. W przeciwnym razie **false**. Operator używa użytkownika domyślne ustawienia regionalne do porównania.  
  
 Operator porównuje tylko wartość typu variant. Porównuje ciągów, liczb całkowitych i przestawne punkty, ale nie tablice lub rekordów.  
  
##  <a name="operator_lt"></a>CComVariant::operator&lt;  
 Wskazuje, czy `CComVariant` obiekt jest mniejszy niż określony **VARIANT**.  
  
```
bool operator<(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** Jeśli wartość `CComVariant` obiektów jest mniejsza niż wartość *varSrc*. W przeciwnym razie **false**. Operator używa użytkownika domyślne ustawienia regionalne do porównania.  
  
##  <a name="operator_gt"></a>CComVariant::operator&gt;  
 Wskazuje, czy `CComVariant` obiekt jest większy niż określony **VARIANT**.  
  
```
bool operator>(const VARIANT& varSrc) const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Zwraca **true** Jeśli wartość `CComVariant` obiektu jest większa niż wartość *varSrc*. W przeciwnym razie **false**. Operator używa użytkownika domyślne ustawienia regionalne do porównania.  
  
##  <a name="readfromstream"></a>CComVariant::ReadFromStream  
 Ustawia odpowiadającego **VARIANT** do **VARIANT** zawartych w określonego strumienia.  
  
```
HRESULT ReadFromStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik do [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfejsu w strumieniu, zawierający dane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 **ReadToStream** wymaga poprzednie wywołanie [WriteToStream](#writetostream).  
  
##  <a name="setbyref"></a>CComVariant::SetByRef  
 Inicjuje `CComVariant` obiektu i zestawy **vt** członka **VT_BYREF**.  
  
```
template < typename T >
void SetByRef(T* pT) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `T`  
 Typ **VARIANT**, na przykład `BSTR`, `int`, lub `char`.  
  
 *pT*  
 Wskaźnik używaną do inicjalizacji `CComVariant` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 `SetByRef`jest to szablon funkcji, który inicjuje `CComVariant` obiektu do wskaźnika *pT* i ustawia **vt** członka **VT_BYREF**. Na przykład:  
  
 [!code-cpp[NVC_ATL_Utilities#76](../../atl/codesnippet/cpp/ccomvariant-class_1.cpp)]  
  
##  <a name="writetostream"></a>CComVariant::WriteToStream  
 Zapisuje odpowiadającego **VARIANT** do strumienia.  
  
```
HRESULT WriteToStream(IStream* pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik do [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfejsu w strumieniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)