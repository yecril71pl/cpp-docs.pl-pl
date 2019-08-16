---
title: Klasa CComBSTR
ms.date: 11/04/2016
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
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
ms.openlocfilehash: dd45c2ff9b43148e0fe27ebd410a2390a4d12ce2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497557"
---
# <a name="ccombstr-class"></a>Klasa CComBSTR

Ta klasa jest otoką dla [BSTR](/previous-versions/windows/desktop/automat/bstr)s.

## <a name="syntax"></a>Składnia

```
class CComBSTR
```

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR:: CComBSTR](#ccombstr)|Konstruktor.|
|[CComBSTR::~CComBSTR](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR:: Append](#append)|Dołącza ciąg do `m_str`.|
|[CComBSTR:: AppendBSTR](#appendbstr)|Dołącza element BSTR do `m_str`.|
|[CComBSTR:: AppendBytes](#appendbytes)|Dołącza określoną liczbę bajtów do `m_str`.|
|[CComBSTR:: ArrayToBSTR](#arraytobstr)|Tworzy element BSTR od pierwszego znaku każdego elementu w elemencie SAFEARRAY i dołącza go do `CComBSTR` obiektu.|
|[CComBSTR:: AssignBSTR](#assignbstr)|Przypisuje element BSTR `m_str`do.|
|[CComBSTR::Attach](#attach)|Dołącza element BSTR do `CComBSTR` obiektu.|
|[CComBSTR:: BSTRToArray](#bstrtoarray)|Tworzy jednowymiarową wartość SAFEARRAY na podstawie zera, gdzie każdy element tablicy jest znakiem z `CComBSTR` obiektu.|
|[CComBSTR:: ByteLength](#bytelength)|Zwraca długość `m_str` w bajtach.|
|[CComBSTR::Copy](#copy)|Zwraca kopię `m_str`.|
|[CComBSTR::CopyTo](#copyto)|Zwraca kopię `m_str` przez parametr **[out]**|
|[CComBSTR::Detach](#detach)|Odłącza `m_str` od obiektu `CComBSTR` .|
|[CComBSTR:: Empty](#empty)|`m_str`Bezpłatnie.|
|[CComBSTR:: length](#length)|Zwraca długość `m_str`.|
|[CComBSTR:: LoadString](#loadstring)|Ładuje zasób ciągu.|
|[CComBSTR:: ReadFromStream](#readfromstream)|Ładuje obiekt BSTR ze strumienia.|
|[CComBSTR:: ToLower](#tolower)|Konwertuje ciąg na małe litery.|
|[CComBSTR:: ToUpper](#toupper)|Konwertuje ciąg na wielkie litery.|
|[CComBSTR:: WriteToStream](#writetostream)|Zapisuje `m_str` w strumieniu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR:: operator BSTR](#operator_bstr)|Rzutuje `CComBSTR` obiekt na BSTR.|
|[CComBSTR:: operator!](#operator_not)|Zwraca wartość true lub false, w zależności od `m_str`tego, czy ma wartość null.|
|[CComBSTR:: operator! =](#operator_neq)|Porównuje `CComBSTR` z ciągiem.|
|[CComBSTR:: operator &](#operator_amp)|Zwraca adres `m_str`.|
|[CComBSTR:: operator + =](#operator_add_eq)|`CComBSTR` Dołącza do obiektu.|
|[CComBSTR:: operator <](#operator_lt)|Porównuje `CComBSTR` z ciągiem.|
|[CComBSTR:: operator =](#operator_eq)|Przypisuje wartość do `m_str`.|
|[CComBSTR:: operator = =](#operator_eq_eq)|Porównuje `CComBSTR` z ciągiem.|
|[CComBSTR:: operator >](#operator_gt)|Porównuje `CComBSTR` z ciągiem.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Zawiera wartość BSTR skojarzoną z `CComBSTR` obiektem.|

## <a name="remarks"></a>Uwagi

`CComBSTR` Klasa jest otoką dla bstrów, które są ciągami z prefiksem. Długość jest przechowywana jako liczba całkowita w lokalizacji pamięci poprzedzającej dane w ciągu.

Element [BSTR](/previous-versions/windows/desktop/automat/bstr) jest zakończony znakiem null po ostatnim liczonym znaku, ale może również zawierać znaki null osadzone w ciągu. Długość ciągu jest określana na podstawie liczby znaków, a nie pierwszego znaku null.

> [!NOTE]
>  `CComBSTR` Klasa zawiera wiele elementów członkowskich (konstruktory, operatory przypisania i operatory porównania), które przyjmują ciągi ANSI lub Unicode jako argumenty. Wersje ANSI tych funkcji są mniej wydajne niż ich odpowiedniki Unicode, ponieważ tymczasowe ciągi Unicode są często tworzone wewnętrznie. W celu zapewnienia wydajności należy użyć wersji Unicode, jeśli jest to możliwe.

> [!NOTE]
>  Ze względu na Ulepszone zachowanie wyszukiwania zaimplementowane w programie Visual Studio .NET, kod `bstr = L"String2" + bstr;`taki jak, który mógł zostać skompilowany w poprzednich wersjach, należy zamiast tego `bstr = CStringW(L"String2") + bstr`zaimplementować jako.

Aby zapoznać się z listą funkcji `CComBSTR`, zobacz [programowanie z CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase. h

##  <a name="append"></a>CComBSTR:: Append

Dołącza *lpsz* lub BSTR element członkowski *bstrSrc* do [m_str](#m_str).

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
podczas `CComBSTR` Obiekt do dołączenia.

*ch*<br/>
podczas Znak do dołączenia.

*lpsz*<br/>
podczas Ciąg znaków zakończony zerem, który ma zostać dołączony. Można przekazać ciąg Unicode za pośrednictwem przeciążenia LPCOLESTR lub ciągu ANSI za pośrednictwem wersji LPCSTR.

*nLen*<br/>
podczas Liczba znaków z *lpsz* do dołączenia.

### <a name="return-value"></a>Wartość zwracana

S_OK po powodzeniu lub dowolna standardowa wartość błędu HRESULT.

### <a name="remarks"></a>Uwagi

Ciąg ANSI zostanie przekonwertowany na Unicode przed dołączeniem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

##  <a name="appendbstr"></a>CComBSTR:: AppendBSTR

Dołącza określony BSTR do [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
podczas Symbol BSTR do dołączenia.

### <a name="return-value"></a>Wartość zwracana

S_OK po powodzeniu lub dowolna standardowa wartość błędu HRESULT.

### <a name="remarks"></a>Uwagi

Nie przekazuj zwykłego ciągu znaków dwubajtowych do tej metody. Kompilator nie może przechwytywać błędu i wystąpią błędy czasu wykonywania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

##  <a name="appendbytes"></a>CComBSTR:: AppendBytes

Dołącza określoną liczbę bajtów do [m_str](#m_str) bez konwersji.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*lpsz*<br/>
podczas Wskaźnik do tablicy bajtów do dołączenia.

*p*<br/>
podczas Liczba bajtów do dołączenia.

### <a name="return-value"></a>Wartość zwracana

S_OK po powodzeniu lub dowolna standardowa wartość błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

##  <a name="arraytobstr"></a>CComBSTR:: ArrayToBSTR

Zwalnia wszystkie istniejące ciągi przechowywane w `CComBSTR` obiekcie, a następnie tworzy BSTR od pierwszego znaku każdego elementu w elemencie SAFEARRAY i dołącza go `CComBSTR` do obiektu.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parametry

*pSrc*<br/>
podczas Element SAFEARRAY zawierający elementy użyte do utworzenia ciągu.

### <a name="return-value"></a>Wartość zwracana

S_OK po powodzeniu lub dowolna standardowa wartość błędu HRESULT.

##  <a name="assignbstr"></a>CComBSTR:: AssignBSTR

Przypisuje element BSTR do [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
podczas Element BSTR do przypisania do bieżącego `CComBSTR` obiektu.

### <a name="return-value"></a>Wartość zwracana

S_OK po powodzeniu lub dowolna standardowa wartość błędu HRESULT.

##  <a name="attach"></a>CComBSTR:: Attach

Dołącza element BSTR do `CComBSTR` obiektu przez ustawienie elementu członkowskiego [m_str](#m_str) na *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parametry

*SRC*<br/>
podczas Wartość BSTR do dołączenia do obiektu.

### <a name="remarks"></a>Uwagi

Nie przekazuj zwykłego ciągu znaków dwubajtowych do tej metody. Kompilator nie może przechwytywać błędu i wystąpią błędy czasu wykonywania.

> [!NOTE]
>  Ta metoda zostanie zatwierdzona `m_str` , jeśli jest inna niż null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="bstrtoarray"></a>CComBSTR:: BSTRToArray

Tworzy jednowymiarową wartość SAFEARRAY na podstawie zera, gdzie każdy element tablicy jest znakiem z `CComBSTR` obiektu.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parametry

*ppArray*<br/>
określoną Wskaźnik do elementu SAFEARRAY używanego do przechowywania wyników funkcji.

### <a name="return-value"></a>Wartość zwracana

S_OK po powodzeniu lub dowolna standardowa wartość błędu HRESULT.

##  <a name="bytelength"></a>CComBSTR:: ByteLength

Zwraca liczbę bajtów w `m_str`, z wyłączeniem kończącego znaku null.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Długość elementu członkowskiego [m_str](#m_str) w bajtach.

### <a name="remarks"></a>Uwagi

Zwraca wartość 0 `m_str` , jeśli ma wartość null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

##  <a name="ccombstr"></a>CComBSTR:: CComBSTR

Konstruktor. Konstruktor domyślny ustawia element członkowski [m_str](#m_str) na wartość null.

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
podczas Liczba znaków, które mają być skopiowane z wartości *sz* lub początkowego rozmiaru w znakach dla `CComBSTR`.

*sz*<br/>
podczas Ciąg do skopiowania. Wersja Unicode określa LPCOLESTR; Wersja ANSI określa LPCSTR.

*pSrc*<br/>
podczas Ciąg do skopiowania. Wersja Unicode określa LPCOLESTR; Wersja ANSI określa LPCSTR.

*SRC*<br/>
podczas `CComBSTR` Obiekt.

*guid*<br/>
podczas Odwołanie do `GUID` struktury.

### <a name="remarks"></a>Uwagi

Konstruktor kopiujący jest `m_str` ustawiony na kopię elementu członkowskiego BSTR. Konstruktor konwertuje identyfikator GUID na ciąg przy użyciu `StringFromGUID2` i zapisuje wynik. `REFGUID`

Inne konstruktory mają `m_str` ustawioną kopię określonego ciągu. W przypadku przekazania wartości dla *nSize*, zostaną skopiowane tylko znaki *nSize* , po których następuje kończący znak null.

`CComBSTR`obsługuje semantykę przenoszenia. Można użyć konstruktora przenoszenia (Konstruktor, który przyjmuje odwołanie rvalue (`&&`), aby utworzyć nowy obiekt, który używa tych samych danych bazowych co stary obiekt, który jest przekazywany jako argument, bez narzutu na kopiowanie obiektu.

Destruktor zwalnia ciąg wskazany przez `m_str`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR

Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Uwagi

Destruktor zwalnia ciąg wskazany przez `m_str`.

##  <a name="copy"></a>CComBSTR:: Copy

Alokuje i zwraca kopię `m_str`.

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Kopia elementu członkowskiego [m_str](#m_str) . Jeśli `m_str` ma wartość null, zwraca wartość null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

##  <a name="copyto"></a>CComBSTR:: CopyTo

Alokuje i zwraca kopię [m_str](#m_str) za pośrednictwem parametru.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
określoną Adres typu BSTR, w którym ma zostać zwrócony ciąg przydzielony przez tę metodę.

*pvarDest*<br/>
określoną Adres WARIANTu, w którym ma zostać zwrócony ciąg przydzielony przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT wskazująca na powodzenie lub niepowodzenie kopiowania.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody wariant wskazywany przez *pvarDest* będzie typem VT_BSTR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

##  <a name="detach"></a>CComBSTR::D etach

Odłącza [m_str](#m_str) od `CComBSTR` obiektu i ustawia `m_str` wartość null.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

Wartość BSTR skojarzona z `CComBSTR` obiektem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

##  <a name="empty"></a>CComBSTR:: Empty

Zwalnia element członkowski [m_str](#m_str) .

```
void Empty() throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

##  <a name="length"></a>CComBSTR:: length

Zwraca liczbę znaków w `m_str`, z wyłączeniem kończącego znaku null.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Długość elementu członkowskiego [m_str](#m_str) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

##  <a name="loadstring"></a>CComBSTR:: LoadString

Ładuje zasób ciągu określony przez *NID* i zapisuje go w tym obiekcie.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parametry

Zobacz [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) w Windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ciąg został pomyślnie załadowany; w przeciwnym razie zwraca wartość FALSE.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja ładuje zasób z modułu identyfikowanego przez użytkownika za pośrednictwem parametru *hinst* . Druga funkcja ładuje zasób z modułu zasobów skojarzonego z obiektem pochodnym [CComModule](../../atl/reference/ccommodule-class.md)używanym w tym projekcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

##  <a name="m_str"></a>CComBSTR:: m_str

Zawiera wartość BSTR skojarzoną z `CComBSTR` obiektem.

```
BSTR m_str;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

##  <a name="operator_bstr"></a>CComBSTR:: operator BSTR

Rzutuje `CComBSTR` obiekt na BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Uwagi

Umożliwia przekazywanie `CComBSTR` obiektów do funkcji, które mają parametry **[in] BSTR** .

### <a name="example"></a>Przykład

Zobacz przykład dla [CComBSTR:: m_str](#m_str).

##  <a name="operator_not"></a>CComBSTR:: operator!

Sprawdza, czy ciąg BSTR ma wartość NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli element członkowski [m_str](#m_str) ma wartość null; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ten operator sprawdza tylko wartość NULL, a nie dla pustego ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

##  <a name="operator_neq"></a>CComBSTR:: operator! =

Zwraca logiczne przeciwieństwo [operatora = =](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
podczas `CComBSTR` Obiekt.

*pszSrc*<br/>
podczas Ciąg zakończony zerem.

*nNull*<br/>
podczas Musi mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element nie jest równy `CComBSTR` obiektowi; w przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

`CComBSTR`s są porównywane w kontekście domyślnych ustawień regionalnych użytkownika. Ostatni operator porównania tylko porównuje zawarty ciąg z wartością NULL.

##  <a name="operator_amp"></a>CComBSTR:: operator&amp;

Zwraca adres typu BSTR przechowywanego w elemencie członkowskim [m_str](#m_str) .

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Uwagi

`CComBstr operator &`do identyfikacji przecieków pamięci jest skojarzone specjalne potwierdzenie. Program zostanie `m_str` poproszony o zainicjowaniu elementu członkowskiego. To potwierdzenie zostało utworzone w celu zidentyfikowania sytuacji, w których `& operator` programista używa do przypisywania nowej wartości do `m_str` elementu członkowskiego bez `m_str`zwalniania pierwszej alokacji. Jeśli `m_str` wartość jest równa null, program zakłada, że nie został jeszcze przydzielono m_str. W takim przypadku program nie zostanie potwierdzony.

To potwierdzenie nie jest domyślnie włączone. Zdefiniuj ATL_CCOMBSTR_ADDRESS_OF_ASSERT, aby włączyć to potwierdzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

##  <a name="operator_add_eq"></a>CComBSTR:: operator + =

Dołącza ciąg do `CComBSTR` obiektu.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
podczas `CComBSTR` Obiekt do dołączenia.

*pszSrc*<br/>
podczas Ciąg zakończony zerem do dołączenia.

### <a name="remarks"></a>Uwagi

`CComBSTR`s są porównywane w kontekście domyślnych ustawień regionalnych użytkownika. Porównanie LPCOLESTR jest wykonywane przy użyciu `memcmp` danych pierwotnych w każdym ciągu. Porównanie LPCSTR jest wykonywane w taki sam sposób po utworzeniu tymczasowej kopii w formacie Unicode *pszSrc* . Ostatni operator porównania tylko porównuje zawarty ciąg z wartością NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

##  <a name="operator_lt"></a>CComBSTR:: operator&lt;

Porównuje `CComBSTR` z ciągiem.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element jest mniejszy niż `CComBSTR` obiekt; w przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Porównanie jest wykonywane przy użyciu domyślnych ustawień regionalnych użytkownika.

##  <a name="operator_eq"></a>CComBSTR:: operator =

Ustawia element członkowski [m_str](#m_str) na kopię *pSrc* lub do kopii elementu członkowskiego BSTR. Operator przypisania przenoszenia `src` bez kopiowania.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Uwagi

Parametr *pSrc* określa LPCOLESTR dla wersji Unicode lub LPCSTR dla wersji ANSI.

### <a name="example"></a>Przykład

Zobacz przykład dla [CComBSTR:: Copy](#copy).

##  <a name="operator_eq_eq"></a>CComBSTR:: operator = =

Porównuje `CComBSTR` z ciągiem. `CComBSTR`s są porównywane w kontekście domyślnych ustawień regionalnych użytkownika.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*bstrSrc*<br/>
podczas `CComBSTR` Obiekt.

*pszSrc*<br/>
podczas Ciąg zakończony zerem.

*nNull*<br/>
podczas Musi mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element jest równy `CComBSTR` obiektowi; w przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Ostatni operator porównania tylko porównuje zawarty ciąg z wartością NULL.

##  <a name="operator_gt"></a>CComBSTR:: operator&gt;

Porównuje `CComBSTR` z ciągiem.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany element jest większy niż `CComBSTR` obiekt; w przeciwnym razie zwraca wartość false.

### <a name="remarks"></a>Uwagi

Porównanie jest wykonywane przy użyciu domyślnych ustawień regionalnych użytkownika.

##  <a name="readfromstream"></a>CComBSTR:: ReadFromStream

Ustawia element członkowski [m_str](#m_str) na BSTR zawarty w określonym strumieniu.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
podczas Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu zawierającym dane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`ReadToStream`wymaga, aby zawartość strumienia w bieżącym położeniu była zgodna z formatem danych zapisanym przez wywołanie do [WriteToStream](#writetostream).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

##  <a name="tolower"></a>CComBSTR:: ToLower

Konwertuje zawarty ciąg na małe litery.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zobacz `CharLowerBuff` , aby uzyskać więcej informacji na temat sposobu przeprowadzania konwersji.

##  <a name="toupper"></a>CComBSTR:: ToUpper

Konwertuje zawarty ciąg na wielkie litery.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zobacz `CharUpperBuff` , aby uzyskać więcej informacji na temat sposobu przeprowadzania konwersji.

##  <a name="writetostream"></a>CComBSTR:: WriteToStream

Zapisuje element członkowski [m_str](#m_str) w strumieniu.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream*<br/>
podczas Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Można odtworzyć BSTR z zawartości strumienia przy użyciu funkcji [readFromStream](#readfromstream) .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Zobacz także

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Makra konwersji ATL i MFC String](string-conversion-macros.md)
