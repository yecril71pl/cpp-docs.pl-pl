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
ms.openlocfilehash: adaad47c49a64c6654b70fa60ef5514e104c50a5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321054"
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
|[CComBSTR::CComBSTR](#ccombstr)|Konstruktor.|
|[CComBSTR::~CComBSTR](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::Dołącz](#append)|Dołącza ciąg do `m_str`.|
|[CComBSTR::DołączBSTR](#appendbstr)|Dołącza BSTR do `m_str`.|
|[CComBSTR::Dodatki](#appendbytes)|Dołącza określoną liczbę bajtów `m_str`do .|
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Tworzy BSTR z pierwszego znaku każdego elementu w safearray i `CComBSTR` dołącza go do obiektu.|
|[CComBSTR::AssignBSTR](#assignbstr)|Przypisuje BSTR do `m_str`pliku .|
|[CComBSTR::Dołącz](#attach)|Dołącza BSTR do `CComBSTR` obiektu.|
|[CComBSTR::BSTRToArray](#bstrtoarray)|Tworzy bezwymiarową jednowymiarową safearray, gdzie każdy element `CComBSTR` tablicy jest znakiem z obiektu.|
|[CComBSTR::ByteLength](#bytelength)|Zwraca długość `m_str` w bajtach.|
|[CComBSTR::Kopiowanie](#copy)|Zwraca kopię `m_str`pliku .|
|[CComBSTR::CopyTo](#copyto)|Zwraca kopię `m_str` parametru **[out]**|
|[CComBSTR::Detach](#detach)|Odłącza `m_str` się `CComBSTR` od obiektu.|
|[CComBSTR::Pusty](#empty)|Darmowe `m_str`.|
|[CComBSTR::Długość](#length)|Zwraca długość `m_str`.|
|[CComBSTR::LoadString](#loadstring)|Ładuje zasób ciągu.|
|[CComBSTR::ReadFromStream](#readfromstream)|Ładuje obiekt BSTR ze strumienia.|
|[CComBSTR::ToLower](#tolower)|Konwertuje ciąg na małe litery.|
|[CComBSTR::Toupper](#toupper)|Konwertuje ciąg na wielkie litery.|
|[CComBSTR::WriteToStream](#writetostream)|Zapisuje `m_str` w strumieniu.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::operator BSTR](#operator_bstr)|Rzutuje `CComBSTR` obiekt na BSTR.|
|[CComBSTR::operator !](#operator_not)|Zwraca wartość PRAWDA lub `m_str`WARTOŚĆ FAŁSZ, w zależności od tego, czy wartość NULL jest wartość NULL.|
|[CComBSTR::operator !=](#operator_neq)|Porównuje a `CComBSTR` z ciągiem.|
|[CComBSTR::operator &](#operator_amp)|Zwraca adres `m_str`.|
|[CComBSTR::operator +=](#operator_add_eq)|Dołącza a `CComBSTR` do obiektu.|
|[CComBSTR::operator <](#operator_lt)|Porównuje a `CComBSTR` z ciągiem.|
|[CComBSTR::operator =](#operator_eq)|Przypisuje wartość do `m_str`pliku .|
|[CComBSTR::operator ==](#operator_eq_eq)|Porównuje a `CComBSTR` z ciągiem.|
|[CComBSTR::operator >](#operator_gt)|Porównuje a `CComBSTR` z ciągiem.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CComBSTR::m_str](#m_str)|Zawiera BSTR skojarzony `CComBSTR` z obiektem.|

## <a name="remarks"></a>Uwagi

Klasa `CComBSTR` jest otoki dla BSTRs, które są ciągi poprzedzone długością. Długość jest przechowywana jako liczba całkowita w lokalizacji pamięci poprzedzającej dane w ciągu.

[BSTR](/previous-versions/windows/desktop/automat/bstr) jest zakończony zerem po ostatnim zliczeniu znaku, ale może również zawierać znaki null osadzone w ciągu. Długość ciągu jest określana przez liczbę znaków, a nie przez pierwszy znak null.

> [!NOTE]
> Klasa `CComBSTR` zawiera szereg elementów członkowskich (konstruktorów, operatorów przypisania i operatorów porównania), które przyjmują ciągi ANSI lub Unicode jako argumenty. Wersje ANSI tych funkcji są mniej wydajne niż ich odpowiedniki Unicode, ponieważ tymczasowe ciągi Unicode są często tworzone wewnętrznie. Aby uzyskać wydajność, należy w miarę możliwości używać wersji Unicode.

> [!NOTE]
> Ze względu na ulepszone zachowanie wyszukiwania zaimplementowane `bstr = L"String2" + bstr;`w programie Visual Studio .NET, kod, taki `bstr = CStringW(L"String2") + bstr`jak , który mógł zostać skompilowany w poprzednich wersjach, powinien zostać zaimplementowany jako .

Aby uzyskać listę przestrog podczas korzystania `CComBSTR`, zobacz [Programowanie z CComBSTR](../../atl/programming-with-ccombstr-atl.md).

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlbase.h

## <a name="ccombstrappend"></a><a name="append"></a>CComBSTR::Dołącz

Dołącza *lpsz* lub członka BSTR *bstrsrc* do [m_str](#m_str).

```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*okręg wyborczy bstrSrc*<br/>
[w] Obiekt `CComBSTR` do doskładniania.

*Ch*<br/>
[w] Znak do doskładniania.

*lpsz (lpsz)*<br/>
[w] Ciąg znaków zakończony zerem do do dołączenia. Ciąg Unicode można przekazać za pośrednictwem przeciążenia LPCOLESTR lub ciągu ANSI za pośrednictwem wersji LPCSTR.

*nLen (nLen)*<br/>
[w] Liczba znaków od *lpsz* do dołączona.

### <a name="return-value"></a>Wartość zwracana

S_OK na sukces lub standardową wartość błędu HRESULT.

### <a name="remarks"></a>Uwagi

Ciąg ANSI zostanie przekonwertowany na Unicode przed dołączeniem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]

## <a name="ccombstrappendbstr"></a><a name="appendbstr"></a>CComBSTR::DołączBSTR

Dołącza określony BSTR do [m_str](#m_str).

```
HRESULT AppendBSTR(BSTR p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[w] BSTR do dokłowego.

### <a name="return-value"></a>Wartość zwracana

S_OK na sukces lub standardową wartość błędu HRESULT.

### <a name="remarks"></a>Uwagi

Nie należy przekazywać zwykłego ciągu znaków szerokoznakowych do tej metody. Kompilator nie może wychwyć błędu i wystąpią błędy czasu wykonywania.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]

## <a name="ccombstrappendbytes"></a><a name="appendbytes"></a>CComBSTR::Dodatki

Dołącza określoną liczbę bajtów, aby [m_str](#m_str) bez konwersji.

```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```

### <a name="parameters"></a>Parametry

*lpsz (lpsz)*<br/>
[w] Wskaźnik do tablicy bajtów do dosyć.

*P*<br/>
[w] Liczba bajtów do dosyć.

### <a name="return-value"></a>Wartość zwracana

S_OK na sukces lub standardową wartość błędu HRESULT.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]

## <a name="ccombstrarraytobstr"></a><a name="arraytobstr"></a>CComBSTR::ArrayToBSTR

Zwalnia wszelkie istniejące ciąg `CComBSTR` przechowywane w obiekcie, a następnie tworzy BSTR z pierwszego znaku każdego `CComBSTR` elementu w safearray i dołącza go do obiektu.

```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```

### <a name="parameters"></a>Parametry

*Psrc*<br/>
[w] Safearray zawierające elementy używane do tworzenia ciągu.

### <a name="return-value"></a>Wartość zwracana

S_OK na sukces lub standardową wartość błędu HRESULT.

## <a name="ccombstrassignbstr"></a><a name="assignbstr"></a>CComBSTR::AssignBSTR

Przypisuje BSTR do [m_str](#m_str).

```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```

### <a name="parameters"></a>Parametry

*okręg wyborczy bstrSrc*<br/>
[w] BSTR przypisać do bieżącego `CComBSTR` obiektu.

### <a name="return-value"></a>Wartość zwracana

S_OK na sukces lub standardową wartość błędu HRESULT.

## <a name="ccombstrattach"></a><a name="attach"></a>CComBSTR::Dołącz

Dołącza BSTR do `CComBSTR` obiektu, ustawiając [m_str](#m_str) element członkowski na *src*.

```
void Attach(BSTR src) throw();
```

### <a name="parameters"></a>Parametry

*src*<br/>
[w] BSTR do dołączenia do obiektu.

### <a name="remarks"></a>Uwagi

Nie należy przekazywać zwykłego ciągu znaków szerokoznakowych do tej metody. Kompilator nie może wychwyć błędu i wystąpią błędy czasu wykonywania.

> [!NOTE]
> Ta metoda będzie `m_str` potwierdzać, jeśli jest null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstrbstrtoarray"></a><a name="bstrtoarray"></a>CComBSTR::BSTRToArray

Tworzy bezwymiarową jednowymiarową safearray, gdzie każdy element `CComBSTR` tablicy jest znakiem z obiektu.

```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```

### <a name="parameters"></a>Parametry

*ppArray (Polski)*<br/>
[na zewnątrz] Wskaźnik do safearray używane do przechowywania wyników funkcji.

### <a name="return-value"></a>Wartość zwracana

S_OK na sukces lub standardową wartość błędu HRESULT.

## <a name="ccombstrbytelength"></a><a name="bytelength"></a>CComBSTR::ByteLength

Zwraca liczbę bajtów `m_str`w , z wyłączeniem kończącego się znaku null.

```
unsigned int ByteLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Długość elementu członkowskiego [m_str](#m_str) w bajtach.

### <a name="remarks"></a>Uwagi

Zwraca wartość `m_str` 0, jeśli jest null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]

## <a name="ccombstrccombstr"></a><a name="ccombstr"></a>CComBSTR::CComBSTR

Konstruktor. Domyślny konstruktor ustawia element członkowski [m_str](#m_str) na NULL.

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

*nSize (rozmiar)*<br/>
[w] Liczba znaków do skopiowania z *sz* lub początkowy `CComBSTR`rozmiar znaków dla .

*Sz*<br/>
[w] Ciąg do skopiowania. Wersja Unicode określa LPCOLESTR; wersja ANSI określa LPCSTR.

*Psrc*<br/>
[w] Ciąg do skopiowania. Wersja Unicode określa LPCOLESTR; wersja ANSI określa LPCSTR.

*src*<br/>
[w] Obiekt. `CComBSTR`

*Identyfikator guid*<br/>
[w] Odwołanie do `GUID` struktury.

### <a name="remarks"></a>Uwagi

Konstruktor kopii `m_str` ustawia kopię członka BSTR *src*. Konstruktor `REFGUID` konwertuje identyfikator GUID `StringFromGUID2` na ciąg przy użyciu i przechowuje wynik.

Inne konstruktory ustawione `m_str` na kopię określonego ciągu. Jeśli przekażesz wartość dla *nSize,* kopiowane będą tylko znaki *nSize,* a następnie kończący się znak null.

`CComBSTR`obsługuje semantykę przenoszenia. Konstruktora przenoszenia (konstruktora, który przyjmuje odwołanie`&&`rvalue ( ) do utworzenia nowego obiektu, który używa tych samych danych źródłowych, co stary obiekt, który przekazujesz jako argument, bez narzutu kopiowania obiektu.

Destruktor uwalnia ciąg wskazany `m_str`przez .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]

## <a name="ccombstrccombstr"></a><a name="dtor"></a>CComBSTR::~CComBSTR

Destruktor.

```
~CComBSTR();
```

### <a name="remarks"></a>Uwagi

Destruktor uwalnia ciąg wskazany `m_str`przez .

## <a name="ccombstrcopy"></a><a name="copy"></a>CComBSTR::Kopiowanie

Przydziela i zwraca kopię `m_str`pliku .

```
BSTR Copy() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Kopia [m_str](#m_str) członka. Jeśli `m_str` ma wartość NULL, zwraca wartość NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]

## <a name="ccombstrcopyto"></a><a name="copyto"></a>CComBSTR::CopyTo

Przydziela i zwraca kopię [m_str](#m_str) za pośrednictwem parametru.

```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```

### <a name="parameters"></a>Parametry

*pbstr (pbstr)*<br/>
[na zewnątrz] Adres BSTR, w którym do zwrócenia ciągu przydzielonego przez tę metodę.

*pvarDest (psk.*<br/>
[na zewnątrz] Adres VARIANT, w którym do zwrócenia ciągu przydzielonego przez tę metodę.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT wskazująca powodzenie lub niepowodzenie kopii.

### <a name="remarks"></a>Uwagi

Po wywołaniu tej metody, VARIANT wskazał przez *pvarDest* będzie typu VT_BSTR.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]

## <a name="ccombstrdetach"></a><a name="detach"></a>CComBSTR::Detach

Odłącza [m_str](#m_str) od `CComBSTR` obiektu i `m_str` ustawia wartość NULL.

```
BSTR Detach() throw();
```

### <a name="return-value"></a>Wartość zwracana

BSTR skojarzony z `CComBSTR` obiektem.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]

## <a name="ccombstrempty"></a><a name="empty"></a>CComBSTR::Pusty

Zwalnia [członka m_str.](#m_str)

```
void Empty() throw();
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]

## <a name="ccombstrlength"></a><a name="length"></a>CComBSTR::Długość

Zwraca liczbę znaków `m_str`w , z wyłączeniem kończącego się znaku null.

```
unsigned int Length() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Długość elementu [członkowskiego m_str.](#m_str)

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]

## <a name="ccombstrloadstring"></a><a name="loadstring"></a>CComBSTR::LoadString

Ładuje zasób ciągu określony przez *nID* i przechowuje go w tym obiekcie.

```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```

### <a name="parameters"></a>Parametry

Zobacz [LoadString](/windows/win32/api/winuser/nf-winuser-loadstringw) w windows SDK.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ciąg został pomyślnie załadowany; w przeciwnym razie zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja ładuje zasób z modułu zidentyfikowanego przez użytkownika za pomocą parametru *hInst.* Druga funkcja ładuje zasób z modułu zasobów skojarzonego z obiektem pochodnym [CComModule](../../atl/reference/ccommodule-class.md)używanym w tym projekcie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]

## <a name="ccombstrm_str"></a><a name="m_str"></a>CComBSTR::m_str

Zawiera BSTR skojarzony `CComBSTR` z obiektem.

```
BSTR m_str;
```

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]

## <a name="ccombstroperator-bstr"></a><a name="operator_bstr"></a>CComBSTR::operator BSTR

Rzutuje `CComBSTR` obiekt na BSTR.

```
operator BSTR() const throw();
```

### <a name="remarks"></a>Uwagi

Umożliwia przekazywanie `CComBSTR` obiektów do funkcji, które mają **parametry BSTR.**

### <a name="example"></a>Przykład

Zobacz przykład [CComBSTR::m_str](#m_str).

## <a name="ccombstroperator-"></a><a name="operator_not"></a>CComBSTR::operator !

Sprawdza, czy ciąg BSTR ma wartość NULL.

```
bool operator!() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli element członkowski [m_str](#m_str) ma wartość NULL; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Ten operator sprawdza tylko wartość NULL, a nie dla pustego ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_neq"></a>CComBSTR::operator !=

Zwraca logiczne przeciwieństwo [operatora ==](#operator_eq_eq).

```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*okręg wyborczy bstrSrc*<br/>
[w] Obiekt. `CComBSTR`

*pszsrc*<br/>
[w] Ciąg zakończony zerem.

*nNull (nNull)*<br/>
[w] Musi mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany `CComBSTR` element nie jest równy obiektowi; w przeciwnym razie zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

`CComBSTR`s są porównywane tekstowie w kontekście domyślnych ustawień regionalnych użytkownika. Operator porównania końcowego po prostu porównuje zawarty ciąg z wartością NULL.

## <a name="ccombstroperator-amp"></a><a name="operator_amp"></a>CComBSTR::operator&amp;

Zwraca adres BSTR przechowywanego w [m_str](#m_str) element członkowski.

```
BSTR* operator&() throw();
```

### <a name="remarks"></a>Uwagi

`CComBstr operator &`ma specjalne twierdzenie skojarzone z nim, aby pomóc zidentyfikować przecieki pamięci. Program będzie potwierdzać, gdy `m_str` element członkowski jest inicjowany. To twierdzenie zostało utworzone w celu zidentyfikowania sytuacji, w których programista używa `& operator` do przypisania nowej wartości do `m_str` elementu członkowskiego bez zwalniania pierwszej alokacji programu `m_str`. Jeśli `m_str` jest równa NULL, program zakłada, że m_str nie został jeszcze przydzielony. W takim przypadku program nie będzie dochodzić.

To twierdzenie nie jest domyślnie włączone. Zdefiniuj ATL_CCOMBSTR_ADDRESS_OF_ASSERT, aby włączyć to twierdzenie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]

[!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]

## <a name="ccombstroperator-"></a><a name="operator_add_eq"></a>CComBSTR::operator +=

Dołącza ciąg do `CComBSTR` obiektu.

```
CComBSTR& operator+= (const CComBSTR& bstrSrc);
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```

### <a name="parameters"></a>Parametry

*okręg wyborczy bstrSrc*<br/>
[w] Obiekt `CComBSTR` do doskładniania.

*pszsrc*<br/>
[w] Ciąg zakończony zerem do dosyć.

### <a name="remarks"></a>Uwagi

`CComBSTR`s są porównywane tekstowie w kontekście domyślnych ustawień regionalnych użytkownika. Porównanie LPCOLESTR odbywa `memcmp` się przy użyciu nieprzetworzonych danych w każdym ciągu. Porównanie LPCSTR odbywa się w ten sam sposób po utworzeniu tymczasowej kopii *Unicode pszSrc.* Operator porównania końcowego po prostu porównuje zawarty ciąg z wartością NULL.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]

## <a name="ccombstroperator-lt"></a><a name="operator_lt"></a>CComBSTR::operator&lt;

Porównuje a `CComBSTR` z ciągiem.

```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany `CComBSTR` element jest mniejszy niż obiekt; w przeciwnym razie zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Porównanie jest wykonywane przy użyciu domyślnych ustawień regionalnych użytkownika.

## <a name="ccombstroperator-"></a><a name="operator_eq"></a>CComBSTR::operator =

Ustawia [m_str](#m_str) element członkowski na kopię *pSrc* lub kopię członka BSTR *src*. Operator przypisania `src` przenoszenia jest przenoszony bez kopiowania.

```
CComBSTR& operator= (const CComBSTR& src);
CComBSTR& operator= (LPCOLESTR pSrc);
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```

### <a name="remarks"></a>Uwagi

Parametr *pSrc* określa LPCOLESTR dla wersji Unicode lub LPCSTR dla wersji ANSI.

### <a name="example"></a>Przykład

Zobacz przykład [CComBSTR::Copy](#copy).

## <a name="ccombstroperator-"></a><a name="operator_eq_eq"></a>CComBSTR::operator ==

Porównuje a `CComBSTR` z ciągiem. `CComBSTR`s są porównywane tekstowie w kontekście domyślnych ustawień regionalnych użytkownika.

```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```

### <a name="parameters"></a>Parametry

*okręg wyborczy bstrSrc*<br/>
[w] Obiekt. `CComBSTR`

*pszsrc*<br/>
[w] Ciąg zakończony zerem.

*nNull (nNull)*<br/>
[w] Musi mieć wartość NULL.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany `CComBSTR` element jest równy obiektowi; w przeciwnym razie zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Operator porównania końcowego po prostu porównuje zawarty ciąg z wartością NULL.

## <a name="ccombstroperator-gt"></a><a name="operator_gt"></a>CComBSTR::operator&gt;

Porównuje a `CComBSTR` z ciągiem.

```
bool operator>(const CComBSTR& bstrSrc) const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli porównywany `CComBSTR` element jest większy niż obiekt; w przeciwnym razie zwraca wartość FAŁSZ.

### <a name="remarks"></a>Uwagi

Porównanie jest wykonywane przy użyciu domyślnych ustawień regionalnych użytkownika.

## <a name="ccombstrreadfromstream"></a><a name="readfromstream"></a>CComBSTR::ReadFromStream

Ustawia [element](#m_str) członkowski m_str na BSTR zawarty w określonym strumieniu.

```
HRESULT ReadFromStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
[w] Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu zawierającym dane.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

`ReadToStream`wymaga, aby zawartość strumienia w bieżącym położeniu była zgodna z formatem danych wypisanym przez wywołanie [WriteToStream](#writetostream).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]

## <a name="ccombstrtolower"></a><a name="tolower"></a>CComBSTR::ToLower

Konwertuje zawarty ciąg na małe litery.

```
HRESULT ToLower() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zobacz `CharLowerBuff` więcej informacji na temat sposobu konwersji.

## <a name="ccombstrtoupper"></a><a name="toupper"></a>CComBSTR::Toupper

Konwertuje zawarty ciąg na wielkie litery.

```
HRESULT ToUpper() throw();
```

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Zobacz `CharUpperBuff` więcej informacji na temat sposobu konwersji.

## <a name="ccombstrwritetostream"></a><a name="writetostream"></a>CComBSTR::WriteToStream

Zapisuje [m_str](#m_str) element członkowski w strumieniu.

```
HRESULT WriteToStream(IStream* pStream) throw();
```

### <a name="parameters"></a>Parametry

*pStream (Strumień)*<br/>
[w] Wskaźnik do interfejsu [IStream](/windows/win32/api/objidl/nn-objidl-istream) w strumieniu.

### <a name="return-value"></a>Wartość zwracana

Standardowa wartość HRESULT.

### <a name="remarks"></a>Uwagi

Można odtworzyć BSTR z zawartości strumienia za pomocą [ReadFromStream](#readfromstream) funkcji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]

## <a name="see-also"></a>Zobacz też

[Przegląd klas](../../atl/atl-class-overview.md)<br/>
[Makra konwersji ciągów ATL i MFC](string-conversion-macros.md)
