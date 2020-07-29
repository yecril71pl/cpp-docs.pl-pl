---
title: Klasa CSimpleStringT
ms.date: 10/18/2018
f1_keywords:
- CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::PCXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::PXSTR
- ATLSIMPSTR/ATL::CSimpleStringT::CSimpleStringT
- ATLSIMPSTR/ATL::CSimpleStringT::Append
- ATLSIMPSTR/ATL::CSimpleStringT::AppendChar
- ATLSIMPSTR/ATL::CSimpleStringT::CopyChars
- ATLSIMPSTR/ATL::CSimpleStringT::CopyCharsOverlapped
- ATLSIMPSTR/ATL::CSimpleStringT::Empty
- ATLSIMPSTR/ATL::CSimpleStringT::FreeExtra
- ATLSIMPSTR/ATL::CSimpleStringT::GetAllocLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetAt
- ATLSIMPSTR/ATL::CSimpleStringT::GetBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::GetBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetLength
- ATLSIMPSTR/ATL::CSimpleStringT::GetManager
- ATLSIMPSTR/ATL::CSimpleStringT::GetString
- ATLSIMPSTR/ATL::CSimpleStringT::IsEmpty
- ATLSIMPSTR/ATL::CSimpleStringT::LockBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::Preallocate
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBuffer
- ATLSIMPSTR/ATL::CSimpleStringT::ReleaseBufferSetLength
- ATLSIMPSTR/ATL::CSimpleStringT::SetAt
- ATLSIMPSTR/ATL::CSimpleStringT::SetManager
- ATLSIMPSTR/ATL::CSimpleStringT::SetString
- ATLSIMPSTR/ATL::CSimpleStringT::StringLength
- ATLSIMPSTR/ATL::CSimpleStringT::Truncate
- ATLSIMPSTR/ATL::CSimpleStringT::UnlockBuffer
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
ms.openlocfilehash: bbbab04ff311d874fc209d2c46fadda57e79a222
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219095"
---
# <a name="csimplestringt-class"></a>Klasa CSimpleStringT

Ta klasa reprezentuje `CSimpleStringT` obiekt.

## <a name="syntax"></a>Składnia

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasy String. Może być jedną z następujących czynności:

- **`char`**(w przypadku ciągów znaków ANSI).

- **`wchar_t`**(w przypadku ciągów znaków Unicode).

- Używanie TCHAR (dla ciągów znaków ANSI i Unicode).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::P CXSTR](#pcxstr)|Wskaźnik do stałego ciągu.|
|[CSimpleStringT::P XSTR](#pxstr)|Wskaźnik do ciągu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Tworzy `CSimpleStringT` obiekty na różne sposoby.|
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT:: Append](#append)|Dołącza `CSimpleStringT` obiekt do istniejącego `CSimpleStringT` obiektu.|
|[CSimpleStringT::AppendChar](#appendchar)|Dołącza znak do istniejącego `CSimpleStringT` obiektu.|
|[CSimpleStringT::CopyChars](#copychars)|Kopiuje znak lub znaki do innego ciągu.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Kopiuje znak lub znaki do innego ciągu, w którym są nakładane bufory.|
|[CSimpleStringT:: Empty](#empty)|Wymusza, aby ciąg miał długość zero.|
|[CSimpleStringT::FreeExtra](#freeextra)|Zwalnia wszelkie dodatkowe pamięci, które zostały wcześniej przydzielone przez obiekt ciągu.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Pobiera przydzieloną długość `CSimpleStringT` obiektu.|
|[CSimpleStringT::GetAt](#getat)|Zwraca znak w danym położeniu.|
|[CSimpleStringT:: GetBuffer](#getbuffer)|Zwraca wskaźnik do znaków w `CSimpleStringT` .|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Zwraca wskaźnik do znaków w `CSimpleStringT` , obcinając do określonej długości.|
|[CSimpleStringT:: GetLength](#getlength)|Zwraca liczbę znaków w `CSimpleStringT` obiekcie.|
|[CSimpleStringT:: GetManager](#getmanager)|Pobiera Menedżera pamięci `CSimpleStringT` obiektu.|
|[CSimpleStringT:: GetString](#getstring)|Pobiera ciąg znaków|
|[CSimpleStringT:: IsEmpty](#isempty)|Testuje, czy `CSimpleStringT` obiekt nie zawiera żadnych znaków.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Wyłącza zliczanie odwołań i chroni ciąg w buforze.|
|[CSimpleStringT::P ponownie przydzielić](#preallocate)|Przydziela określoną ilość pamięci dla buforu znaków.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Umożliwia wydawanie kontroli nad buforem zwracanym przez `GetBuffer` .|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Umożliwia wydawanie kontroli nad buforem zwracanym przez `GetBuffer` .|
|[CSimpleStringT::SetAt](#setat)|Ustawia znak w danym położeniu.|
|[CSimpleStringT:: setmanager](#setmanager)|Ustawia Menedżera pamięci dla `CSimpleStringT` obiektu.|
|[CSimpleStringT:: SetString](#setstring)|Ustawia ciąg `CSimpleStringT` obiektu.|
|[CSimpleStringT::StringLength](#stringlength)|Zwraca liczbę znaków w określonym ciągu.|
|[CSimpleStringT:: Truncate](#truncate)|Obcina ciąg do określonej długości.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Włącza zliczanie odwołań i zwalnia ciąg w buforze.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT:: operator PCXSTR](#operator_pcxstr)|Bezpośrednio uzyskuje dostęp do znaków przechowywanych w `CSimpleStringT` obiekcie jako ciąg w stylu języka C.|
|[CSimpleStringT:: operator\[\]](#operator_at)|Zwraca znak w danej pozycji — podstawienie operatora dla `GetAt` .|
|[CSimpleStringT:: operator + =](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CSimpleStringT:: operator =](#operator_eq)|Przypisuje nową wartość do `CSimpleStringT` obiektu.|

### <a name="remarks"></a>Uwagi

`CSimpleStringT`jest klasą bazową dla różnych klas ciągów obsługiwanych przez Visual C++. Zapewnia ona minimalną obsługę zarządzania pamięcią obiektu String i podstawowego manipulowania buforem. Aby uzyskać bardziej zaawansowane obiekty ciągów, zobacz [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr. h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT:: Append

Dołącza `CSimpleStringT` obiekt do istniejącego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
`CSimpleStringT`Obiekt, który ma zostać dołączony.

*pszSrc*<br/>
Wskaźnik do ciągu zawierającego znaki do dołączenia.

*nLength*<br/>
Liczba znaków do dołączenia.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dołączyć istniejący `CSimpleStringT` obiekt do innego `CSimpleStringT` obiektu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Append` .

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::AppendChar

Dołącza znak do istniejącego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*ch*<br/>
Znak do dołączenia

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dołączyć określony znak do końca istniejącego `CSimpleStringT` obiektu.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

Kopiuje znak lub znaki do `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest*<br/>
Wskaźnik do ciągu znaków.

*pchSrc*<br/>
Wskaźnik do ciągu zawierającego znaki do skopiowania.

*nChar*<br/>
Liczba znaków *pchSrc* do skopiowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby skopiować znaki z *pchSrc* do ciągu *pchDest* .

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::CopyChars` .

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Kopiuje znak lub znaki do `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest*<br/>
Wskaźnik do ciągu znaków.

*pchSrc*<br/>
Wskaźnik do ciągu zawierającego znaki do skopiowania.

*nChar*<br/>
Liczba znaków *pchSrc* do skopiowania.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby skopiować znaki z *pchSrc* do ciągu *pchDest* . W przeciwieństwie do `CopyChars` , `CopyCharsOverlapped` zapewnia bezpieczną metodę kopiowania z buforów znaków, które mogą nakładać się na siebie.

### <a name="example"></a>Przykład

Zobacz przykład dla [CSimpleStringT:: CopyChars](#copychars)lub kodu źródłowego dla `CSimpleStringT::SetString` (znajdującego się w atlsimpstr. h).

## <a name="csimplestringtcsimplestringt"></a><a name="ctor"></a>CSimpleStringT::CSimpleStringT

Konstruuje `CSimpleStringT` obiekt.

### <a name="syntax"></a>Składnia

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Istniejący `CSimpleStringT` obiekt do skopiowania do tego `CSimpleStringT` obiektu.

*pchSrc*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, nieprzekończonej null.

*pszSrc*<br/>
Ciąg zakończony znakiem null, który ma zostać skopiowany do tego `CSimpleStringT` obiektu.

*nLength*<br/>
Liczba znaków w `pch` .

*pStringMgr*<br/>
Wskaźnik do Menedżera pamięci `CSimpleStringT` obiektu. Aby uzyskać więcej informacji o `IAtlStringMgr` zarządzaniu pamięcią dla programu `CSimpleStringT` , zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Utwórz nowy `CSimpleStringT` obiekt. Ponieważ konstruktory kopiuje dane wejściowe do nowego przydzielonego magazynu, mogą wynikać wyjątki pamięci.

### <a name="example"></a>Przykład

Poniższy przykład demonstruje użycie programu przy `CSimpleStringT::CSimpleStringT` użyciu biblioteki ATL **`typedef`** `CSimpleString` . `CSimpleString`jest powszechnie używaną specjalizacją szablonu klasy `CSimpleStringT` .

```cpp
CSimpleString s1(pMgr);
// Empty string
CSimpleString s2(_T("cat"), pMgr);
// From a C string literal

CSimpleString s3(s2);
// Copy constructor
CSimpleString s4(s2 + _T(" ") + s3);

// From a string expression
CSimpleString s5(_T("xxxxxx"), 6, pMgr);
// s5 = "xxxxxx"
```

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT:: Empty

Sprawia, że ten `CSimpleStringT` obiekt jest pustym ciągiem i zwalnia pamięć odpowiednio do potrzeb.

### <a name="syntax"></a>Składnia

```cpp
void Empty() throw();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Strings: CString — oczyszczanie wyjątków](../cstring-exception-cleanup.md).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Empty` .

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

Zwalnia wszelkie dodatkowe pamięci, które wcześniej przydzieliły przez ciąg, ale nie są już potrzebne.

### <a name="syntax"></a>Składnia

```cpp
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Powinno to zmniejszyć obciążenie pamięci zużywane przez obiekt ciągu. Metoda ponownie przydziela bufor do dokładnej długości zwracanej przez [GetLength](#getlength).

### <a name="example"></a>Przykład

```cpp
CAtlString basestr;
IAtlStringMgr* pMgr;

pMgr= basestr.GetManager();
ASSERT(pMgr != NULL);

// Create a CSimpleString with 28 characters
CSimpleString str(_T("Many sports are fun to play."), 28, pMgr);
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// Assigning a smaller string won't cause CSimpleString to free its
// memory, because it assumes the string will grow again anyway.
str = _T("Soccer is best!");
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());

// This call forces CSimpleString to release the extra
// memory it doesn't need.
str.FreeExtra();
_tprintf_s(_T("Alloc length is %d, String length is %d\n"),
   str.GetAllocLength(), str.GetLength());
```

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu są następujące:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

## <a name="csimplestringtgetalloclength"></a><a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Pobiera przydzieloną długość `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków przyznanych dla tego obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić liczbę znaków przyznanych dla tego `CSimpleStringT` obiektu. Zobacz [FreeExtra](#freeextra) , aby zapoznać się z przykładem wywoływania tej funkcji.

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT::GetAt

Zwraca jeden znak z `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w `CSimpleStringT` obiekcie. Parametr *iChar* musi być większy lub równy 0 i mniejszy od wartości zwracanej przez [GetLength](#getlength). W przeciwnym razie program `GetAt` wygeneruje wyjątek.

### <a name="return-value"></a>Wartość zwracana

`XCHAR`Zawiera znak w określonej pozycji w ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić jeden znak określony przez *iChar*. Przeciążony operator indeksu dolnego (**[]**) jest wygodnym aliasem dla `GetAt` . Terminator o wartości null ma adres bez generowania wyjątku przy użyciu `GetAt` . Nie jest to jednak zliczane przez `GetLength` , a zwracana wartość to 0.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia programu `CSimpleStringT::GetAt` .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT:: GetBuffer

Zwraca wskaźnik do wewnętrznego buforu znaków dla `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parametry

*nMinBufferLength*<br/>
Minimalna liczba znaków, jaką może zawierać bufor znaków. Ta wartość nie zawiera spacji dla terminatora o wartości null.

Jeśli wartość *nMinBufferLength* jest większa niż długość bieżącego buforu, `GetBuffer` niszczy bieżący bufor, zastępuje ją buforem żądanego rozmiaru i resetuje liczbę odwołań do obiektów na zero. Jeśli wcześniej wywołano [LockBuffer](#lockbuffer) w tym buforze, utracisz blokadę buforu.

### <a name="return-value"></a>Wartość zwracana

`PXSTR`Wskaźnik do buforu znaków (zakończony wartością null) obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić zawartość buforu `CSimpleStringT` obiektu. Zwracana wartość `PXSTR` nie jest stałą i w związku z tym umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartości.

Jeśli używasz wskaźnika zwróconego przez, `GetBuffer` Aby zmienić zawartość ciągu, należy wywołać [ReleaseBuffer](#releasebuffer) przed użyciem jakichkolwiek innych `CSimpleStringT` metod elementu członkowskiego.

Adres zwrócony przez `GetBuffer` może nie być prawidłowy po wywołaniu, `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacje mogą spowodować ponowne `CSimpleStringT` przydzielenie buforu. Bufor nie jest ponownie alokowany, jeśli nie zmienisz długości `CSimpleStringT` .

Pamięć buforu jest automatycznie zwalniana, gdy `CSimpleStringT` obiekt zostanie zniszczony.

Jeśli stale śledzisz długość ciągu, nie należy dołączać kończącego znaku null. Należy jednak określić końcową długość ciągu podczas zwalniania bufora przy użyciu `ReleaseBuffer` . Jeśli dołączysz kończący znak null, należy przekazać wartość-1 (wartość domyślna) dla długości. `ReleaseBuffer`następnie określa długość buforu.

W przypadku braku wystarczającej ilości pamięci do spełnienia `GetBuffer` żądania ta metoda zgłasza CMemoryException *.

### <a name="example"></a>Przykład

```cpp
CSimpleString s(_T("abcd"), pMgr);
LPTSTR pBuffer = s.GetBuffer(10);
int sizeOfBuffer = s.GetAllocLength();

// Directly access CSimpleString buffer
_tcscpy_s(pBuffer, sizeOfBuffer, _T("Hello"));
ASSERT(_tcscmp(s, _T("Hello")) == 0);
s.ReleaseBuffer();
```

## <a name="csimplestringtgetbuffersetlength"></a><a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Zwraca wskaźnik do wewnętrznego bufora znaków dla `CSimpleStringT` obiektu, obcinając lub rozwijając jego długość, jeśli jest to konieczne, aby dokładnie dopasować długość określoną w *nLength*.

### <a name="syntax"></a>Składnia

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Dokładny rozmiar `CSimpleStringT` buforu znaków w znakach.

### <a name="return-value"></a>Wartość zwracana

`PXSTR`Wskaźnik do buforu znaków (zakończony wartością null) obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać określoną długość buforu wewnętrznego `CSimpleStringT` obiektu. Zwrócony `PXSTR` wskaźnik nie jest **`const`** i w ten sposób umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartości.

Jeśli używasz wskaźnika zwróconego przez [GetBufferSetLength](#getbuffersetlength) do zmiany zawartości ciągu, wywołaj, `ReleaseBuffer` Aby zaktualizować stan wewnętrzny `CsimpleStringT` przed użyciem innych `CSimpleStringT` metod.

Adres zwrócony przez `GetBufferSetLength` może nie być prawidłowy po wywołaniu, `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacje mogą spowodować ponowne `CSimpleStringT` przydzielenie buforu. Bufor nie zostanie ponownie przypisany, jeśli nie zmienisz długości `CSimpleStringT` .

Pamięć buforu jest automatycznie zwalniana, gdy `CSimpleStringT` obiekt zostanie zniszczony.

Jeśli śledzisz długość ciągu samodzielnie, nie dołączaj kończącego znaku null. Po zwolnieniu bufora przy użyciu polecenia należy określić końcową długość ciągu `ReleaseBuffer` . Jeśli dołączysz kończący znak null podczas wywołania `ReleaseBuffer` , pass-1 (wartość domyślna) dla długości do i wykona `ReleaseBuffer` `ReleaseBuffer` `strlen` w buforze, aby określić jego długość.

Aby uzyskać więcej informacji na temat zliczania odwołań, zobacz następujące artykuły:

- [Zarządzanie okresami istnienia obiektu za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting) w Windows SDK.

- [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) w Windows SDK.

- [Reguły dotyczące zarządzania liczbami odwołań](/windows/win32/com/rules-for-managing-reference-counts) w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::GetBufferSetLength` .

```cpp
CSimpleString str(pMgr);
LPTSTR pstr = str.GetBufferSetLength(3);
pstr[0] = _T('C');
pstr[1] = _T('u');
pstr[2] = _T('p');

// No need for trailing zero or call to ReleaseBuffer()
// because GetBufferSetLength() set it for us.

str += _T(" soccer is best!");
ASSERT(_tcscmp(str, _T("Cup soccer is best!")) == 0);
```

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT:: GetLength

Zwraca liczbę znaków w `CSimpleStringT` obiekcie.

### <a name="syntax"></a>Składnia

```
int GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić liczbę znaków w obiekcie. Liczba nie zawiera terminatora o wartości null.

W przypadku zestawów znaków wielobajtowych (MBCS) `GetLength` zlicza każdy znak 8-bitowy, czyli bajt wiodący i końcowy w jednym znaku wielobajtowym jest liczony jako dwa bajty. Zobacz [FreeExtra](#freeextra) , aby zapoznać się z przykładem wywoływania tej funkcji.

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT:: GetManager

Pobiera Menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do Menedżera pamięci dla `CSimpleStringT` obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać Menedżera pamięci używanego przez `CSimpleStringT` obiekt. Aby uzyskać więcej informacji na temat menedżerów pamięci i obiektów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT:: GetString

Pobiera ciąg znaków.

### <a name="syntax"></a>Składnia

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu znaków zakończonych znakiem null.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać ciąg znaków skojarzony z `CSimpleStringT` obiektem.

> [!NOTE]
> Zwrócony `PCXSTR` wskaźnik jest **`const`** i nie zezwala na bezpośrednią modyfikację `CSimpleStringT` zawartości.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::GetString` .

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT:: IsEmpty

Testuje `CSimpleStringT` obiekt dla pustego warunku.

### <a name="syntax"></a>Składnia

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli `CSimpleStringT` obiekt ma 0 długości; w przeciwnym razie wartość false.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić, czy obiekt zawiera pusty ciąg.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::IsEmpty` .

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtlockbuffer"></a><a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Wyłącza zliczanie odwołań i chroni ciąg w buforze.

### <a name="syntax"></a>Składnia

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CSimpleStringT` obiektu lub ciąg zakończony znakiem null.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zablokować bufor `CSimpleStringT` obiektu. Przez wywołanie `LockBuffer` , należy utworzyć kopię ciągu z-1 dla liczby odwołań. Gdy wartość licznika odwołań to-1, ciąg w buforze jest uznawany za w stanie "zablokowany". W stanie zablokowanym, ciąg jest chroniony na dwa sposoby:

- Żaden inny ciąg nie może uzyskać odwołania do danych w zablokowanym ciągu, nawet jeśli ten ciąg jest przypisany do zamkniętego ciągu.

- Zablokowany ciąg nigdy nie odwołuje się do innego ciągu, nawet jeśli inny ciąg jest kopiowany do zamkniętego ciągu.

Przez zablokowanie ciągu w buforze upewnij się, że wyłączne wstrzymanie ciągu w buforze pozostanie nienaruszone.

Po zakończeniu pracy z programem `LockBuffer` Wywołaj [UnlockBuffer](#unlockbuffer) , aby zresetować liczbę odwołań do 1.

> [!NOTE]
> W przypadku wywołania metody [GetBuffer](#getbuffer) w zablokowanym buforze i ustawieniu `GetBuffer` parametru `nMinBufferLength` na wartość większą niż długość bieżącego buforu, blokada buforu zostanie utracona. Takie wywołanie `GetBuffer` niszczy bieżący bufor, zastępuje je buforem żądanego rozmiaru i resetuje liczbę odwołań do zera.

Aby uzyskać więcej informacji na temat zliczania odwołań, zobacz następujące artykuły:

- [Zarządzanie okresami istnienia obiektu za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting) w Windows SDK

- [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) w Windows SDK

- [Reguły dotyczące zarządzania liczbami odwołań](/windows/win32/com/rules-for-managing-reference-counts) w Windows SDK

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::LockBuffer` .

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT:: operator\[\]

Wywołaj tę funkcję, aby uzyskać dostęp do pojedynczego znaku tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążony operator indeksu dolnego (**[]**) zwraca pojedynczy znak określony przez indeks liczony od zera w *iChar*. Ten operator jest wygodnym substytutem funkcji składowej [GetAt](#getat) .

> [!NOTE]
> Można użyć operatora indeks dolny (**[]**), aby uzyskać wartość znaku w `CSimpleStringT` , ale nie można użyć go do zmiany wartości znaku w `CSimpleStringT` .

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator []` .

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT:: operator\[\]

Wywołaj tę funkcję, aby uzyskać dostęp do pojedynczego znaku tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążony operator indeksu dolnego (**[]**) zwraca pojedynczy znak określony przez indeks liczony od zera w *iChar*. Ten operator jest wygodnym substytutem funkcji składowej [GetAt](#getat) .

> [!NOTE]
> Można użyć operatora indeks dolny (**[]**), aby uzyskać wartość znaku w `CSimpleStringT` , ale nie można użyć go do zmiany wartości znaku w `CSimpleStringT` .

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT:: operator + =

Sprzęga nowy ciąg lub znak na końcu istniejącego ciągu.

### <a name="syntax"></a>Składnia

```
CSimpleStringT& operator +=(PCXSTR pszSrc);
CSimpleStringT& operator +=(const CSimpleStringT& strSrc);
template<int t_nSize>
CSimpleStringT& operator+=(const CStaticString< XCHAR, t_nSize >& strSrc);
CSimpleStringT& operator +=(char ch);
CSimpleStringT& operator +=(unsigned char ch);
CSimpleStringT& operator +=(wchar_t ch);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Wskaźnik na ciąg zakończony znakiem null.

*strSrc*<br/>
Wskaźnik do istniejącego `CSimpleStringT` obiektu.

*ch*<br/>
Znak, który ma zostać dołączony.

### <a name="remarks"></a>Uwagi

Operator akceptuje inny `CSimpleStringT` obiekt lub znak. Należy zauważyć, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz tego operatora łączenia, ponieważ nowy magazyn może być przydzielony do znaków dodanych do tego `CSimpleStringT` obiektu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator +=` .

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT:: operator =

Przypisuje nową wartość do `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Wskaźnik na ciąg zakończony znakiem null.

*strSrc*<br/>
Wskaźnik do istniejącego `CSimpleStringT` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli ciąg docelowy (po lewej stronie) jest wystarczająco duży, aby można było zapisać nowe dane, nie jest wykonywana nowa alokacja pamięci. Należy zauważyć, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz operatora przypisania, ponieważ nowy magazyn jest często przydzielony do przechowywania wyniku `CSimpleStringT` obiektu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator =` .

```cpp
CSimpleString s1(pMgr), s2(pMgr);
// Empty CSimpleStringT objects

s1 = _T("cat");
// s1 = "cat"
ASSERT(_tcscmp(s1, _T("cat")) == 0);

s2 = s1;               // s1 and s2 each = "cat"
ASSERT(_tcscmp(s2, _T("cat")) == 0);

s1 = _T("the ") + s1;
// Or expressions
ASSERT(_tcscmp(s1, _T("the cat")) == 0);

s1 = _T("x");
// Or just individual characters
ASSERT(_tcscmp(s1, _T("x")) == 0);
```

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT:: operator PCXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w `CSimpleStringT` obiekcie jako ciąg w stylu języka C.

### <a name="syntax"></a>Składnia

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Nie są kopiowane żadne znaki; zwracany jest tylko wskaźnik. Należy zachować ostrożność przy użyciu tego operatora. Jeśli zmienisz `CString` obiekt po uzyskaniu wskaźnika znaku, może dojść do ponownej alokacji pamięci, która unieważnia wskaźnik.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator PCXSTR` .

```cpp
// If the prototype of a function is known to the compiler,
// the PCXSTR cast operator may be invoked implicitly.

CSimpleString strSports(L"Soccer is Best!", pMgr);
WCHAR sz[1024];

wcscpy_s(sz, strSports);

// If the prototype isn't known or is a va_arg prototype,
// you must invoke the cast operator explicitly. For example,
// the va_arg part of a call to swprintf_s() needs the cast:

swprintf_s(sz, 1024, L"I think that %s!\n", (PCWSTR)strSports);

// While the format parameter is known to be an PCXSTR and
// therefore doesn't need the cast:

swprintf_s(sz, 1024, strSports);

// Note that some situations are ambiguous. This line will
// put the address of the strSports object to stdout:

wcout << strSports;

// while this line will put the content of the string out:

wcout << (PCWSTR)strSports;
```

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::P CXSTR

Wskaźnik do stałego ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::P ponownie przydzielić

Przydziela określoną ilość bajtów dla `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Dokładny rozmiar `CSimpleStringT` buforu znaków w znakach.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby przydzielić określony rozmiar buforu dla `CSimpleStringT` obiektu.

`CSimpleStringT`generuje wyjątek STATUS_NO_MEMORY, jeśli nie może przydzielić miejsca dla buforu znaków. Domyślnie alokacja pamięci jest wykonywana przez funkcje interfejsu API WIN32 `HeapAlloc` lub `HeapReAlloc` .

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Preallocate` .

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::P XSTR

Wskaźnik do ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Udostępnia kontrolę nad buforem przydzielonym przez [GetBuffer](#getbuffer).

### <a name="syntax"></a>Składnia

```cpp
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nowa długość ciągu znaków, która nie zlicza terminatora o wartości null. Jeśli ciąg jest zakończony wartością null, wartość domyślna-1 ustawia `CSimpleStringT` rozmiar na bieżącą długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ponownie przydzielić lub zwolnić bufor obiektu ciągu. Jeśli wiesz, że ciąg w buforze jest zakończony wartością null, możesz pominąć argument *nNewLength* . Jeśli ciąg nie jest zakończony wartością null, użyj *nNewLength* , aby określić jego długość. Adres zwrócony przez metodę [GetBuffer](#getbuffer) jest nieprawidłowy po wywołaniu `ReleaseBuffer` lub dowolnej innej `CSimpleStringT` operacji.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::ReleaseBuffer` .

```cpp
const int bufferSize = 1024;
CSimpleString s(_T("abc"), pMgr);
LPTSTR p = s.GetBuffer(bufferSize);
_tcscpy_s(p, bufferSize, _T("abc"));

// use the buffer directly
ASSERT(s.GetLength() == 3);

// String length = 3
s.ReleaseBuffer();

// Surplus memory released, p is now invalid.
ASSERT(s.GetLength() == 3);

// Length still 3
```

## <a name="csimplestringtreleasebuffersetlength"></a><a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Udostępnia kontrolę nad buforem przydzielonym przez [GetBuffer](#getbuffer).

### <a name="syntax"></a>Składnia

```cpp
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Długość wydanego ciągu

### <a name="remarks"></a>Uwagi

Ta funkcja działa podobnie jak [ReleaseBuffer](#releasebuffer) , z tą różnicą, że należy przesłać prawidłową długość obiektu String.

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::SetAt

Ustawia pojedynczy znak z `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w `CSimpleStringT` obiekcie. Parametr *iChar* musi być większy lub równy 0 i mniejszy od wartości zwracanej przez [GetLength](#getlength).

*ch*<br/>
Nowy znak.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zastąpić znak znajdujący się w *iChar*. Ta metoda nie powiększa ciągu, jeśli *iChar* przekracza granice istniejącego ciągu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::SetAt` .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT:: setmanager

Określa Menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Wskaźnik do nowego menedżera pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić nowy Menedżer pamięci używany przez `CSimpleStringT` obiekt. Aby uzyskać więcej informacji na temat menedżerów pamięci i obiektów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::SetManager` .

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT:: SetString

Ustawia ciąg `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Wskaźnik na ciąg zakończony znakiem null.

*nLength*<br/>
Liczba znaków w *pszSrc*.

### <a name="remarks"></a>Uwagi

Kopiuj ciąg do `CSimpleStringT` obiektu. `SetString`zastępuje starsze dane ciągu w buforze.

Obie wersje programu `SetString` sprawdzają, czy *pszSrc* jest wskaźnikiem o wartości null, a jeśli tak, zgłoś błąd E_INVALIDARG.

Wersja z jednym parametrem `SetString` oczekuje, że *pszSrc* ma wskazywać ciąg zakończony znakiem null.

Wersja z dwoma parametrami `SetString` oczekuje również, że *pszSrc* będzie ciągiem zakończonym wartością null. Używa *nLength* jako długości ciągu, chyba że napotka najpierw terminator o wartości null.

Wersja z dwoma parametrami `SetString` sprawdza także, czy *pszSrc* wskazuje lokalizację w bieżącym buforze w `CSimpleStringT` . W tym specjalnym przypadku `SetString` używa funkcji kopiowania pamięci, która nie zastępuje danych ciągu, ponieważ kopiuje dane ciągu z powrotem do buforu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::SetString` .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

## <a name="csimplestringtstringlength"></a><a name="stringlength"></a>CSimpleStringT::StringLength

Zwraca liczbę znaków w określonym ciągu.

### <a name="syntax"></a>Składnia

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parametry

*psz*<br/>
Wskaźnik na ciąg zakończony znakiem null.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w *PSZ*; nie zliczanie terminatora o wartości null.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę znaków w ciągu wskazywanym przez *PSZ*.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::StringLength` .

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT:: Truncate

Obcina ciąg do nowej długości.

### <a name="syntax"></a>Składnia

```cpp
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nowa długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby obciąć zawartość ciągu do nowej długości.

> [!NOTE]
> Nie ma to wpływu na przydzieloną długość buforu. Aby zmniejszyć lub zwiększyć bieżący bufor, zobacz [FreeExtra](#freeextra) i [preallocate](#preallocate).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Truncate` .

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

## <a name="csimplestringtunlockbuffer"></a><a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Odblokowuje bufor `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```cpp
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zresetować liczbę odwołań ciągu do 1.

`CSimpleStringT`Destruktor automatycznie wywołuje `UnlockBuffer` , aby upewnić się, że bufor nie jest zablokowany w przypadku wywołania destruktora. Aby zapoznać się z przykładem tej metody, zobacz [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT

Niszczy `CSimpleStringT` obiekt.

### <a name="syntax"></a>Składnia

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zniszczyć `CSimpleStringT` obiekt.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
