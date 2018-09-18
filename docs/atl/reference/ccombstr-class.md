---
title: Klasa CComBSTR | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComBSTR
- ATLBASE/ATL::CComBSTR
- ATLBASE/ATL::CComBSTR::CComBSTR
- ATLBASE/ATL::CComBSTR::Append
- ATLBASE/ATL::CComBSTR::AppendBSTR
- ATLBASE/ATL::CComBSTR::AppendBytes
- ATLBASE/ATL::CComBSTR::ArrayToBSTR
- ATLBASE/ATL::CComBSTR::AssignBSTR
- ATLBASE/ATL::CComBSTR::Attach
- ATLBASE/ATL::CComBSTR::BSTRToArray
- ATLBASE/ATL::CComBSTR::ByteLength
- ATLBASE/ATL::CComBSTR::Copy
- ATLBASE/ATL::CComBSTR::CopyTo
- ATLBASE/ATL::CComBSTR::Detach
- ATLBASE/ATL::CComBSTR::Empty
- ATLBASE/ATL::CComBSTR::Length
- ATLBASE/ATL::CComBSTR::LoadString
- ATLBASE/ATL::CComBSTR::ReadFromStream
- ATLBASE/ATL::CComBSTR::ToLower
- ATLBASE/ATL::CComBSTR::ToUpper
- ATLBASE/ATL::CComBSTR::WriteToStream
- ATLBASE/ATL::CComBSTR::m_str
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d2045a6c14a37d270d895a5eeb4fa455711e7354
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46097682"
---
# <a name="ccombstr-class"></a>CComBSTR, klasa

Ta klasa jest otoką BSTR.

## <a name="syntax"></a>Składnia

```
class CComBSTR
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::CComBSTR](#ccombstr)|Konstruktor.|
|[CComBSTR:: ~ CComBSTR](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::Append](#append)|Dołącza ciąg `m_str`.|
|[CComBSTR::AppendBSTR](#appendbstr)|Dołącza ciąg BSTR do `m_str`.|
|[CComBSTR::AppendBytes](#appendbytes)|Dołącza określoną liczbę bajtów do `m_str`.|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Tworzy ciąg BSTR z pierwszym znakiem każdego elementu w safearray i dołącza je do `CComBSTR` obiektu.|
|[CComBSTR::AssignBSTR](#assignbstr)|Przypisuje BSTR do `m_str`.|
|[CComBSTR::Attach](#attach)|Dołącza ciąg BSTR do `CComBSTR` obiektu.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Tworzy safearray jednowymiarowa liczony od zera, w której każdy element tablicy jest znak z `CComBSTR` obiektu.|
|[CComBSTR::ByteLength](#bytelength)|Zwraca długość `m_str` w bajtach.|
|[CComBSTR::Copy](#copy)|Zwraca kopię obiektu `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Zwraca kopię obiektu `m_str` za pośrednictwem **[out]** parametru|
|[CComBSTR::Detach](#detach)|Odłącza `m_str` z `CComBSTR` obiektu.|
|[CComBSTR::Empty](#empty)|Zwalnia `m_str`.|
|[CComBSTR::Length](#length)|Zwraca długość `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Ładuje zasób w postaci ciągu.|
|[CComBSTR::ReadFromStream](#readfromstream)|Ładuje BSTR — obiekt ze strumienia.|
|[CComBSTR::ToLower](#tolower)|Konwertuje ciąg na małe litery.|
|[CComBSTR::ToUpper](#toupper)|Konwertuje ciąg na wielkie litery.|
|[CComBSTR::WriteToStream](#writetostream)|Zapisuje `m_str` do strumienia.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::operator BSTR](#operator_bstr)|Rzutowania `CComBSTR` obiekt na ciąg BSTR.|
|[CComBSTR::operator!](#operator_not)|Zwraca wartość PRAWDA lub FAŁSZ, w zależności od tego, czy `m_str`ma wartość NULL.|
|[CComBSTR::operator! =](#operator_neq)|Porównuje `CComBSTR` przy użyciu parametrów.|
|[CComBSTR::operator &](#operator_amp)|Zwraca adres `m_str`.|
|[CComBSTR::operator +=](#operator_add_eq)|Dołącza `CComBSTR` do obiektu.|
|[CComBSTR::operator <](#operator_lt)|Porównuje `CComBSTR` przy użyciu parametrów.|
|[CComBSTR::operator =](#operator_eq)|Przypisuje wartość do `m_str`.|
|[CComBSTR::operator ==](#operator_eq_eq)|Porównuje `CComBSTR` przy użyciu parametrów.|
|[CComBSTR::operator >](#operator_gt)|Porównuje `CComBSTR` przy użyciu parametrów.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Zawiera BSTR skojarzony `CComBSTR` obiektu.|

## <a name="remarks"></a>Uwagi

`CComBSTR` Klasy jest otoką BStr, które są poprzedzone długości ciągów. Długość jest przechowywana jako liczba całkowita w lokalizacji pamięci poprzedzający dane w ciągu.

A [BSTR](/previous-versions/windows/desktop/automat/bstr) jest zakończony znakiem null po ostatniej liczone znaków, ale może również zawierać znaki null osadzone w ciągu. Długość ciągu jest określana przez liczbę znaków, nie pierwszego znaku null.

> [!NOTE]
>  `CComBSTR` Klasa oferuje pewną liczbę elementów członkowskich (konstruktory, operatory przypisania i operatorów porównania), które pobierają ciągi ANSI lub Unicode jako argumenty. ANSI wersje tych funkcji są mniej wydajne niż ich odpowiedniki Unicode, ponieważ tymczasowych ciągów Unicode są często tworzone wewnętrznie. W celu zwiększenia wydajności należy użyć wersji Unicode, gdzie to możliwe.

> [!NOTE]
>  Ze względu na to zachowanie wyszukiwania ulepszone zaimplementowane w Visual Studio .NET, takich jak kod `bstr = L"String2" + bstr;`, może być skompilowany w poprzednich wersjach, zamiast tego należy wdrożyć jako `bstr = CStringW(L"String2") + bstr`.

Aby uzyskać listę ostrzeżenia w przypadku korzystania z `CComBSTR`, zobacz [Programowanie przy użyciu CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

##  <a name="append"></a>  CComBSTR::Append

Dołącza jedną *lpsz* lub członek BSTR *bstrSrc* do [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] Element `CComBSTR` obiektu do dołączenia.

*ch*<br/>
[in] Znak do dołączenia.

*lpsz*<br/>
[in] Ciąg znaków zakończony zerem do dołączenia. Ciąg Unicode można przekazać za pomocą przeciążenia LPCOLESTR lub na ciąg ANSI za pomocą wersji LPCSTR.

*nLen*<br/>
[in] Liczba znaków z *lpsz* do dołączenia.

### <a name="return-value"></a>Wartość zwracana

S_OK na powodzenie lub dowolnej standardowej wartości błąd HRESULT.

### <a name="remarks"></a>Uwagi

Na ciąg ANSI zostanie przekonwertowany na ciąg Unicode przed dołączanie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>  CComBSTR::AppendBSTR

Dołącza określony BSTR do [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ciąg BSTR do dołączenia.

### <a name="return-value"></a>Wartość zwracana

S_OK na powodzenie lub dowolnej standardowej wartości błąd HRESULT.

### <a name="remarks"></a>Uwagi

Nie przekazuj zwykły ciąg znaków dwubajtowych do tej metody. Kompilator nie może wychwycić błąd, a następnie uruchom razem, gdy wystąpią błędy.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>  CComBSTR::AppendBytes

Dołącza określoną liczbę bajtów do [m_str](#m_str) bez konwersji.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
[in] Wskaźnik do tablicy bajtów do dołączenia.

*p*<br/>
[in] Liczba bajtów do dołączenia.

### <a name="return-value"></a>Wartość zwracana

S_OK na powodzenie lub dowolnej standardowej wartości błąd HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>  CComBSTR::ArrayToBSTR

Zwalnia wszelkie istniejących parametrów przechowywanych w `CComBSTR` obiektu, a następnie tworzy ciąg BSTR z pierwszym znakiem każdego elementu w safearray i dołącza go do `CComBSTR` obiektu.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
[in] Safearray, zawierający elementy służące do tworzenia ciągu.

### <a name="return-value"></a>Wartość zwracana

S_OK na powodzenie lub dowolnej standardowej wartości błąd HRESULT.

##  <a name="assignbstr"></a>  CComBSTR::AssignBSTR

Przypisuje BSTR do [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] Ciąg BSTR można przypisać do bieżącego `CComBSTR` obiektu.

### <a name="return-value"></a>Wartość zwracana

S_OK na powodzenie lub dowolnej standardowej wartości błąd HRESULT.

##  <a name="attach"></a>  CComBSTR::Attach

Dołącza ciąg BSTR do `CComBSTR` obiektu przez ustawienie [m_str](#m_str) członka do *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parametry

*src*<br/>
[in] BSTR do dołączenia do obiektu.

### <a name="remarks"></a>Uwagi

Nie przekazuj zwykły ciąg znaków dwubajtowych do tej metody. Kompilator nie może wychwycić błąd, a następnie uruchom razem, gdy wystąpią błędy.

> [!NOTE]
>  Ta metoda będzie potwierdzenia, jeśli `m_str` jest różna od NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>  CComBSTR::BSTRToArray

Tworzy safearray jednowymiarowa liczony od zera, w której każdy element tablicy jest znak z `CComBSTR` obiektu.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
[out] Wskaźnik do elementu safearray używane do przechowywania wyników funkcji.

### <a name="return-value"></a>Wartość zwracana

S_OK na powodzenie lub dowolnej standardowej wartości błąd HRESULT.

##  <a name="bytelength"></a>  CComBSTR::ByteLength

Zwraca liczbę bajtów w `m_str`, z wyjątkiem kończącego znaku null.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Długość [m_str](#m_str) elementu członkowskiego, w bajtach.

### <a name="remarks"></a>Uwagi

Zwraca wartość 0, jeśli `m_str` ma wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>  CComBSTR::CComBSTR

Konstruktor. Ustawia konstruktora domyślnego [m_str](#m_str) elementu członkowskiego na wartość NULL.

```
CComBSTR() throw();
CComBSTR(const CComBSTR& src);
CComBSTR(REFGUID  guid);
CComBSTR(int nSize);
CComBSTR(int nSize, LPCOLESTR sz);
CComBSTR(int nSize, LPCSTR sz);
CComBSTR(LPCOLESTR pSrc);
CComBSTR(LPCSTR pSrc);
CComBSTR(CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="parameters"></a>Parametry

*nSize*<br/>
[in] Liczba znaków do skopiowania *sz* lub początkowy rozmiar w znakach `CComBSTR`.

*Sz*<br/>
[in] Ciąg do skopiowania. Wersja Unicode określa LPCOLESTR; wersji ANSI określa LPCSTR.

*pSrc*<br/>
[in] Ciąg do skopiowania. Wersja Unicode określa LPCOLESTR; wersji ANSI określa LPCSTR.

*src*<br/>
[in] Element `CComBSTR` obiektu.

*Identyfikator GUID*<br/>
[in] Odwołanie do `GUID` struktury.

### <a name="remarks"></a>Uwagi

Ustawia konstruktora kopiowania `m_str` kopię BSTR członkiem *src*. `REFGUID` Konstruktor identyfikator GUID jest konwertowany na ciąg za pośrednictwem `StringFromGUID2` i zapisuje wynik.

Drugi zestaw konstruktory `m_str` kopię określonego ciągu. W przypadku przekazania wartości *nSize*, a następnie tylko *nSize* znaki zostaną skopiowane, a następnie kończącego znaku null.

`CComBSTR` obsługuje semantyki przenoszenia. Można użyć konstruktora przenoszącego (Konstruktor, który przyjmuje odwołanie rvalue (`&&`) można utworzyć nowego obiektu, który używa tych samych danych, jak stary obiekt można przekazać jako argument, bez potrzeby kopiowania obiektu.

Destruktor zwalnia ciągu wskazywany przez `m_str`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>  CComBSTR:: ~ CComBSTR

Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia ciągu wskazywany przez `m_str`.

##  <a name="copy"></a>  CComBSTR::Copy

Przydziela i zwraca kopię obiektu `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Kopię [m_str](#m_str) elementu członkowskiego. Jeśli `m_str` ma wartość NULL, zwraca wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>  CComBSTR::CopyTo

Przydziela i zwraca kopię obiektu [m_str](#m_str) za pomocą parametru.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
[out] Adres BSTR, w których ma zostać zwrócony ciąg przydzielone przez tę metodę.

*pvarDest*<br/>
[out] Adres typu Variant, w których ma zostać zwrócony ciąg przydzielone przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT oznaczający powodzenie lub niepowodzenie kopiowania.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody, wariant wskazywanej przez *pvarDest* będzie mieć typ VT_BSTR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>  CComBSTR::Detach

Odłącza [m_str](#m_str) z `CComBSTR` i ustawia `m_str` na wartość NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Skojarzony BSTR `CComBSTR` obiektu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>  CComBSTR::Empty

Zwalnia [m_str](#m_str) elementu członkowskiego.

```
void Empty() throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>  CComBSTR::Length

Zwraca liczbę znaków w `m_str`, z wyjątkiem kończącego znaku null.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Długość [m_str](#m_str) elementu członkowskiego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>  CComBSTR::LoadString

Ładuje określony przez zasób w postaci ciągu *nID* i zapisuje go w tym obiekcie.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parametry

Zobacz [LoadString](/windows/desktop/api/winuser/nf-winuser-loadstringa) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ciąg zostanie pomyślnie załadowana; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja ładuje zasobu z modułu zidentyfikowane przez użytkownika za pośrednictwem *hInst* parametru. Druga funkcja ładowania zasobu z modułu zasobów skojarzonych z [CComModule](../../atl/reference/ccommodule-class.md)-pochodnych obiektu użytego w tym projekcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>  CComBSTR::m_str

Zawiera BSTR skojarzony `CComBSTR` obiektu.

```
BSTR m_str;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>  CComBSTR::operator BSTR

Rzutowania `CComBSTR` obiekt na ciąg BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Uwagi

Umożliwia przekazywanie `CComBSTR` obiektów funkcji, które mają **[in] BSTR** parametrów.

### <a name="example"></a>Przykład

Zobacz przykład [CComBSTR::m_str](#m_str).

##  <a name="operator_not"></a>  CComBSTR::operator!

Sprawdza, czy ciąg BSTR ma wartość NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli [m_str](#m_str) elementu członkowskiego jest wartość NULL; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Ten operator tylko sprawdza, czy wartość NULL, nie dla pustego ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>  CComBSTR::operator! =

Zwraca przeciwną wartość logiczną z [operator ==](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] Element `CComBSTR` obiektu.

*pszSrc*<br/>
[in] Ciąg zakończony zerem.

*nNull*<br/>
[in] Musi mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element, którą jest porównywany nie jest równa `CComBSTR` obiektu; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

`CComBSTR`s są porównywane w formie tekstu w kontekście użytkownika domyślnych ustawień regionalnych. Operator porównania końcowego porównuje tylko zawarte parametry mają wartości null.

##  <a name="operator_amp"></a>  CComBSTR::operator &amp;

Zwraca adres BSTR przechowywane w [m_str](#m_str) elementu członkowskiego.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Uwagi

`CComBstr operator &` Potwierdzenie specjalne skojarzył z nim ułatwiających znajdowanie przecieków pamięci. Program będzie assert, kiedy `m_str` zainicjować składowej. Ta asercja została utworzona w celu identyfikowania sytuacji, w których używa się programistą `& operator` można przypisać nową wartość do `m_str` składowej bez zwalniania pierwszy alokacja `m_str`. Jeśli `m_str` jest równa NULL, program zakłada, że m_str nie został jeszcze przydzielony. W takim przypadku program nie będzie potwierdzenia.

Ta asercja nie jest włączona domyślnie. Zdefiniuj ATL_CCOMBSTR_ADDRESS_OF_ASSERT umożliwia potwierdzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>  CComBSTR::operator +=

Dołącza ciąg `CComBSTR` obiektu.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] Element `CComBSTR` obiektu do dołączenia.

*pszSrc*<br/>
[in] Ciąg zakończony zerem do dołączenia.

### <a name="remarks"></a>Uwagi

`CComBSTR`s są porównywane w formie tekstu w kontekście użytkownika domyślnych ustawień regionalnych. Porównanie LPCOLESTR jest wykonywane przy użyciu `memcmp` na danych pierwotnych w każdym ciągu. Porównanie LPCSTR odbywa się tak samo jak po Unicode tymczasowej, kopię *pszSrc* została utworzona. Operator porównania końcowego porównuje tylko zawarte parametry mają wartości null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>  CComBSTR::operator &lt;

Porównuje `CComBSTR` przy użyciu parametrów.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element, którą jest porównywany jest mniejsza niż `CComBSTR` obiektu; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Porównanie jest wykonywane przy użyciu jego domyślne ustawienia regionalne.

##  <a name="operator_eq"></a>  CComBSTR::operator =

Zestawy [m_str](#m_str) elementu członkowskiego kopię *pSrc* lub kopię BSTR członkiem *src*. Operator przypisania przenoszenia przenosi `src` bez kopiowania go.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Uwagi

*PSrc* parametr określa LPCOLESTR dla wersji standardu Unicode albo LPCSTR dla wersji ANSI.

### <a name="example"></a>Przykład

Zobacz przykład [CComBSTR::Copy](#copy).

##  <a name="operator_eq_eq"></a>  CComBSTR::operator ==

Porównuje `CComBSTR` przy użyciu parametrów. `CComBSTR`s są porównywane w formie tekstu w kontekście użytkownika domyślnych ustawień regionalnych.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
[in] Element `CComBSTR` obiektu.

*pszSrc*<br/>
[in] Ciąg zakończony zerem.

*nNull*<br/>
[in] Musi mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ma wartość elementu, którą jest porównywany `CComBSTR` obiektu; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Operator porównania końcowego porównuje tylko zawarte parametry mają wartości null.

##  <a name="operator_gt"></a>  CComBSTR::operator &gt;

Porównuje `CComBSTR` przy użyciu parametrów.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element, którą jest porównywany jest większa niż `CComBSTR` obiektu; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Porównanie jest wykonywane przy użyciu jego domyślne ustawienia regionalne.

##  <a name="readfromstream"></a>  CComBSTR::ReadFromStream

Zestawy [m_str](#m_str) członek BSTR zawarte w określonego strumienia.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfejsu w usłudze stream, zawierającą dane.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

`ReadToStream` wymaga zawartość strumienia w bieżącym położeniu, aby był zgodny z formatem danych napisanych przez wywołanie [WriteToStream](#writetostream).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>  CComBSTR::ToLower

Konwertuje ciąg zawarte na małe litery.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Zobacz `CharLowerBuff` więcej informacji na temat sposobu konwersja jest wykonywana.

##  <a name="toupper"></a>  CComBSTR::ToUpper

Konwertuje ciąg zawarte na wielkie litery.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Zobacz `CharUpperBuff` więcej informacji na temat sposobu konwersja jest wykonywana.

##  <a name="writetostream"></a>  CComBSTR::WriteToStream

Zapisuje [m_str](#m_str) członka do strumienia.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
[in] Wskaźnik do [IStream](/windows/desktop/api/objidl/nn-objidl-istream) interfejsu dla strumienia.

### <a name="return-value"></a>Wartość zwracana

Standardowe wartości HRESULT.

### <a name="remarks"></a>Uwagi

Można odtworzyć BSTR z zawartości strumienia z wykorzystaniem [ReadFromStream](#readfromstream) funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Zobacz też

[Klasa — Przegląd](../../atl/atl-class-overview.md)<br/>
[ATL i makr konwersji ciągu MFC](string-conversion-macros.md)
