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
ms.openlocfilehash: c033346b7a687a1c6778ad23e30ee0e73c787ad8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78865085"
---
# <a name="csimplestringt-class"></a>Klasa CSimpleStringT

Ta klasa reprezentuje obiekt `CSimpleStringT`.

## <a name="syntax"></a>Składnia

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasy String. Może to być jeden z następujących modyfikatorów dostępu:

- **char** (dla CIĄGÓW znaków ANSI).

- **wchar_t** (dla ciągów znaków Unicode).

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
|[CSimpleStringT::CSimpleStringT](#ctor)|Konstrukcje `CSimpleStringT` obiektów na różne sposoby.|
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT:: Append](#append)|Dołącza obiekt `CSimpleStringT` do istniejącego obiektu `CSimpleStringT`.|
|[CSimpleStringT::AppendChar](#appendchar)|Dołącza znak do istniejącego obiektu `CSimpleStringT`.|
|[CSimpleStringT::CopyChars](#copychars)|Kopiuje znak lub znaki do innego ciągu.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Kopiuje znak lub znaki do innego ciągu, w którym są nakładane bufory.|
|[CSimpleStringT:: Empty](#empty)|Wymusza, aby ciąg miał długość zero.|
|[CSimpleStringT::FreeExtra](#freeextra)|Zwalnia wszelkie dodatkowe pamięci, które zostały wcześniej przydzielone przez obiekt ciągu.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Pobiera przydzieloną długość obiektu `CSimpleStringT`.|
|[CSimpleStringT::GetAt](#getat)|Zwraca znak w danym położeniu.|
|[CSimpleStringT:: GetBuffer](#getbuffer)|Zwraca wskaźnik do znaków w `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Zwraca wskaźnik do znaków w `CSimpleStringT`, obcinając do określonej długości.|
|[CSimpleStringT:: GetLength](#getlength)|Zwraca liczbę znaków w obiekcie `CSimpleStringT`.|
|[CSimpleStringT:: GetManager](#getmanager)|Pobiera Menedżera pamięci `CSimpleStringT` obiektu.|
|[CSimpleStringT:: GetString](#getstring)|Pobiera ciąg znaków|
|[CSimpleStringT:: IsEmpty](#isempty)|Testuje, czy obiekt `CSimpleStringT` nie zawiera żadnych znaków.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Wyłącza zliczanie odwołań i chroni ciąg w buforze.|
|[CSimpleStringT::P ponownie przydzielić](#preallocate)|Przydziela określoną ilość pamięci dla buforu znaków.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Umożliwia wydawanie kontroli nad buforem zwróconym przez `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Umożliwia wydawanie kontroli nad buforem zwróconym przez `GetBuffer`.|
|[CSimpleStringT::SetAt](#setat)|Ustawia znak w danym położeniu.|
|[CSimpleStringT:: setmanager](#setmanager)|Ustawia Menedżera pamięci dla obiektu `CSimpleStringT`.|
|[CSimpleStringT:: SetString](#setstring)|Ustawia ciąg obiektu `CSimpleStringT`.|
|[CSimpleStringT::StringLength](#stringlength)|Zwraca liczbę znaków w określonym ciągu.|
|[CSimpleStringT:: Truncate](#truncate)|Obcina ciąg do określonej długości.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Włącza zliczanie odwołań i zwalnia ciąg w buforze.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT:: operator PCXSTR](#operator_pcxstr)|Bezpośrednio uzyskuje dostęp do znaków przechowywanych w obiekcie `CSimpleStringT` jako ciąg w stylu C.|
|[CSimpleStringT:: operator\[\]](#operator_at)|Zwraca znak w danej pozycji — podstawienie operatora dla `GetAt`.|
|[CSimpleStringT:: operator + =](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CSimpleStringT:: operator =](#operator_eq)|Przypisuje nową wartość do obiektu `CSimpleStringT`.|

### <a name="remarks"></a>Uwagi

`CSimpleStringT` jest klasą bazową dla różnych klas ciągów obsługiwanych przez wizualizację C++. Zapewnia ona minimalną obsługę zarządzania pamięcią obiektu String i podstawowego manipulowania buforem. Aby uzyskać bardziej zaawansowane obiekty ciągów, zobacz [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr. h

## <a name="append"></a>CSimpleStringT:: Append

Dołącza obiekt `CSimpleStringT` do istniejącego obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Obiekt `CSimpleStringT`, który ma zostać dołączony.

*pszSrc*<br/>
Wskaźnik do ciągu zawierającego znaki do dołączenia.

*nLength*<br/>
Liczba znaków do dołączenia.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dołączyć istniejący obiekt `CSimpleStringT` do innego obiektu `CSimpleStringT`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a>CSimpleStringT::AppendChar

Dołącza znak do istniejącego obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*ch*<br/>
Znak do dołączenia

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dołączyć określony znak do końca istniejącego obiektu `CSimpleStringT`.

##  <a name="copychars"></a>CSimpleStringT::CopyChars

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

Poniższy przykład ilustruje użycie `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

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

Wywołaj tę metodę, aby skopiować znaki z *pchSrc* do ciągu *pchDest* . W przeciwieństwie do `CopyChars`, `CopyCharsOverlapped` zapewnia bezpieczną metodę kopiowania z buforów znaków, które mogą nakładać się na siebie.

### <a name="example"></a>Przykład

Zobacz przykład dla [CSimpleStringT:: CopyChars](#copychars)lub kodu źródłowego dla `CSimpleStringT::SetString` (znajdującego się w atlsimpstr. h).

##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT

Konstruuje obiekt `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Istniejący obiekt `CSimpleStringT`, który ma zostać skopiowany do tego obiektu `CSimpleStringT`.

*pchSrc*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, nieprzekończonej null.

*pszSrc*<br/>
Ciąg zakończony znakiem null, który ma zostać skopiowany do tego obiektu `CSimpleStringT`.

*nLength*<br/>
Liczba znaków w `pch`.

*pStringMgr*<br/>
Wskaźnik do Menedżera pamięci obiektu `CSimpleStringT`. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięcią dla `CSimpleStringT`, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Utwórz nowy obiekt `CSimpleStringT`. Ponieważ konstruktory kopiuje dane wejściowe do nowego przydzielonego magazynu, mogą wynikać wyjątki pamięci.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób użycia `CSimpleStringT::CSimpleStringT` przy użyciu ATL **typedef** `CSimpleString`. `CSimpleString` jest powszechnie używaną specjalizacją szablonu klasy `CSimpleStringT`.

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

##  <a name="empty"></a>CSimpleStringT:: Empty

Sprawia, że ten obiekt `CSimpleStringT` pusty ciąg i zwalnia pamięć odpowiednio do potrzeb.

### <a name="syntax"></a>Składnia

```
void Empty() throw();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Strings: CString — oczyszczanie wyjątków](../cstring-exception-cleanup.md).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>CSimpleStringT::FreeExtra

Zwalnia wszelkie dodatkowe pamięci, które wcześniej przydzieliły przez ciąg, ale nie są już potrzebne.

### <a name="syntax"></a>Składnia

```
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

##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength

Pobiera przydzieloną długość obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków przyznanych dla tego obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić liczbę znaków przydzieloną dla tego obiektu `CSimpleStringT`. Zobacz [FreeExtra](#freeextra) , aby zapoznać się z przykładem wywoływania tej funkcji.

##  <a name="getat"></a>CSimpleStringT::GetAt

Zwraca jeden znak z obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w obiekcie `CSimpleStringT`. Parametr *iChar* musi być większy lub równy 0 i mniejszy od wartości zwracanej przez [GetLength](#getlength). W przeciwnym razie `GetAt` wygeneruje wyjątek.

### <a name="return-value"></a>Wartość zwracana

`XCHAR`, która zawiera znak znajdujący się w określonej pozycji w ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić jeden znak określony przez *iChar*. Przeciążony operator indeksu dolnego ( **[]** ) jest wygodnym aliasem dla `GetAt`. Terminator o wartości null ma adres bez generowania wyjątku przy użyciu `GetAt`. Nie jest to jednak uwzględniane przez `GetLength`, a zwrócona wartość to 0.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje sposób używania `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>CSimpleStringT:: GetBuffer

Zwraca wskaźnik do wewnętrznego buforu znaków dla obiektu `CSimpleStringT`.

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

`PXSTR` wskaźnik do bufora znaków (zakończona wartością null) obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić zawartość buforu obiektu `CSimpleStringT`. Zwrócony `PXSTR` nie jest stałą i w związku z tym umożliwia bezpośrednie modyfikowanie zawartości `CSimpleStringT`.

Jeśli używasz wskaźnika zwróconego przez `GetBuffer`, aby zmienić zawartość ciągu, należy wywołać [ReleaseBuffer](#releasebuffer) przed użyciem innych `CSimpleStringT` metod elementu członkowskiego.

Adres zwrócony przez `GetBuffer` może być nieprawidłowy po wywołaniu `ReleaseBuffer`, ponieważ dodatkowe operacje `CSimpleStringT` mogą spowodować ponowne przydzielenie buforu `CSimpleStringT`. Bufor nie jest ponownie alokowany, jeśli nie zostanie zmieniona długość `CSimpleStringT`.

Pamięć buforu jest automatycznie zwalniana, gdy obiekt `CSimpleStringT` zostanie zniszczony.

Jeśli stale śledzisz długość ciągu, nie należy dołączać kończącego znaku null. Należy jednak określić końcową długość ciągu podczas zwalniania buforu przy użyciu `ReleaseBuffer`. Jeśli dołączysz kończący znak null, należy przekazać wartość-1 (wartość domyślna) dla długości. `ReleaseBuffer` następnie określa długość buforu.

Jeśli jest za mało pamięci, aby spełnić żądanie `GetBuffer`, Metoda ta zgłasza CMemoryException *.

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

##  <a name="getbuffersetlength"></a>CSimpleStringT::GetBufferSetLength

Zwraca wskaźnik do wewnętrznego buforu znaków dla obiektu `CSimpleStringT`, obcinając lub rozwijając jego długość, jeśli jest to konieczne, aby dokładnie dopasować długość określoną w *nLength*.

### <a name="syntax"></a>Składnia

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Dokładny rozmiar buforu znaków `CSimpleStringT` w znakach.

### <a name="return-value"></a>Wartość zwracana

`PXSTR` wskaźnik do bufora znaków (zakończona wartością null) obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać określoną długość bufora wewnętrznego obiektu `CSimpleStringT`. Zwrócony wskaźnik `PXSTR` nie jest wartością **stałą** i w ten sposób umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartości.

Jeśli używasz wskaźnika zwróconego przez [GetBufferSetLength](#getbuffersetlength) , aby zmienić zawartość ciągu, wywołaj `ReleaseBuffer`, aby zaktualizować stan wewnętrzny `CsimpleStringT` przed użyciem innych metod `CSimpleStringT`.

Adres zwrócony przez `GetBufferSetLength` może być nieprawidłowy po wywołaniu `ReleaseBuffer`, ponieważ dodatkowe operacje `CSimpleStringT` mogą spowodować ponowne przydzielenie buforu `CSimpleStringT`. Bufor nie zostanie ponownie przypisany, jeśli nie zostanie zmieniona długość `CSimpleStringT`.

Pamięć buforu jest automatycznie zwalniana, gdy obiekt `CSimpleStringT` zostanie zniszczony.

Jeśli śledzisz długość ciągu samodzielnie, nie dołączaj kończącego znaku null. Po zwolnieniu bufora przy użyciu `ReleaseBuffer`należy określić końcową długość ciągu. Jeśli dołączysz kończący znak null, gdy wywołasz `ReleaseBuffer`, pass-1 (wartość domyślna) dla długości do `ReleaseBuffer`, a `ReleaseBuffer` wykona `strlen` w buforze, aby określić jego długość.

Aby uzyskać więcej informacji na temat zliczania odwołań, zobacz następujące artykuły:

- [Zarządzanie okresami istnienia obiektu za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting) w Windows SDK.

- [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) w Windows SDK.

- [Reguły dotyczące zarządzania liczbami odwołań](/windows/win32/com/rules-for-managing-reference-counts) w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::GetBufferSetLength`.

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

##  <a name="getlength"></a>CSimpleStringT:: GetLength

Zwraca liczbę znaków w obiekcie `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
int GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić liczbę znaków w obiekcie. Liczba nie zawiera terminatora o wartości null.

W przypadku zestawów znaków wielobajtowych (MBCS) `GetLength` zlicza każdy znak 8-bitowy; oznacza to, że bajty wiodące i końcowe w jednym znaku wielobajtowym są zliczane jako dwa bajty. Zobacz [FreeExtra](#freeextra) , aby zapoznać się z przykładem wywoływania tej funkcji.

##  <a name="getmanager"></a>CSimpleStringT:: GetManager

Pobiera Menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do Menedżera pamięci dla obiektu `CSimpleStringT`.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać Menedżera pamięci używanego przez obiekt `CSimpleStringT`. Aby uzyskać więcej informacji na temat menedżerów pamięci i obiektów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>CSimpleStringT:: GetString

Pobiera ciąg znaków.

### <a name="syntax"></a>Składnia

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu znaków zakończonych znakiem null.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać ciąg znaków skojarzony z obiektem `CSimpleStringT`.

> [!NOTE]
>  Zwrócony wskaźnik `PCXSTR` jest wartością **stałą** i nie dopuszcza bezpośredniej modyfikacji zawartości `CSimpleStringT`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>CSimpleStringT:: IsEmpty

Testuje obiekt `CSimpleStringT` dla pustego warunku.

### <a name="syntax"></a>Składnia

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli obiekt `CSimpleStringT` ma 0 długości; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić, czy obiekt zawiera pusty ciąg.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer

Wyłącza zliczanie odwołań i chroni ciąg w buforze.

### <a name="syntax"></a>Składnia

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do obiektu `CSimpleStringT` lub ciąg zakończony znakiem null.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zablokować bufor obiektu `CSimpleStringT`. Wywołując `LockBuffer`, utworzysz kopię ciągu z-1 dla liczby odwołań. Gdy wartość licznika odwołań to-1, ciąg w buforze jest uznawany za w stanie "zablokowany". W stanie zablokowanym, ciąg jest chroniony na dwa sposoby:

- Żaden inny ciąg nie może uzyskać odwołania do danych w zablokowanym ciągu, nawet jeśli ten ciąg jest przypisany do zamkniętego ciągu.

- Zablokowany ciąg nigdy nie odwołuje się do innego ciągu, nawet jeśli inny ciąg jest kopiowany do zamkniętego ciągu.

Przez zablokowanie ciągu w buforze upewnij się, że wyłączne wstrzymanie ciągu w buforze pozostanie nienaruszone.

Po zakończeniu pracy z `LockBuffer`Wywołaj [UnlockBuffer](#unlockbuffer) , aby zresetować liczbę odwołań do 1.

> [!NOTE]
>  W przypadku wywołania metody [GetBuffer](#getbuffer) w zablokowanym buforze i ustawieniu `GetBuffer` parametru `nMinBufferLength` na wartość większą niż długość bieżącego buforu, blokada buforu zostanie utracona. Takie wywołanie `GetBuffer` niszczy bieżący bufor, zastępuje je buforem żądanego rozmiaru i resetuje liczbę odwołań do zera.

Aby uzyskać więcej informacji na temat zliczania odwołań, zobacz następujące artykuły:

- [Zarządzanie okresami istnienia obiektu za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting) w Windows SDK

- [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) w Windows SDK

- [Reguły dotyczące zarządzania liczbami odwołań](/windows/win32/com/rules-for-managing-reference-counts) w Windows SDK

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

##  <a name="operator_at"></a>CSimpleStringT:: operator\[\]

Wywołaj tę funkcję, aby uzyskać dostęp do pojedynczego znaku tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążony operator indeksu dolnego ( **[]** ) zwraca pojedynczy znak określony przez indeks liczony od zera w *iChar*. Ten operator jest wygodnym substytutem funkcji składowej [GetAt](#getat) .

> [!NOTE]
>  Można użyć operatora indeks dolny ( **[]** ), aby uzyskać wartość znaku w `CSimpleStringT`, ale nie można użyć go do zmiany wartości znaku w `CSimpleStringT`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>CSimpleStringT:: operator \[\]

Wywołaj tę funkcję, aby uzyskać dostęp do pojedynczego znaku tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążony operator indeksu dolnego ( **[]** ) zwraca pojedynczy znak określony przez indeks liczony od zera w *iChar*. Ten operator jest wygodnym substytutem funkcji składowej [GetAt](#getat) .

> [!NOTE]
>  Można użyć operatora indeks dolny ( **[]** ), aby uzyskać wartość znaku w `CSimpleStringT`, ale nie można użyć go do zmiany wartości znaku w `CSimpleStringT`.

##  <a name="operator_add_eq"></a>CSimpleStringT:: operator + =

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
Wskaźnik do istniejącego obiektu `CSimpleStringT`.

*ch*<br/>
Znak, który ma zostać dołączony.

### <a name="remarks"></a>Uwagi

Operator akceptuje inny obiekt `CSimpleStringT` lub znak. Należy zauważyć, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz tego operatora łączenia, ponieważ nowy magazyn może być przydzielony do znaków dodawanych do tego obiektu `CSimpleStringT`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>CSimpleStringT:: operator =

Przypisuje nową wartość do obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Wskaźnik na ciąg zakończony znakiem null.

*strSrc*<br/>
Wskaźnik do istniejącego obiektu `CSimpleStringT`.

### <a name="remarks"></a>Uwagi

Jeśli ciąg docelowy (po lewej stronie) jest wystarczająco duży, aby można było zapisać nowe dane, nie jest wykonywana nowa alokacja pamięci. Należy zauważyć, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz operatora przypisania, ponieważ nowy magazyn jest często przydzielony do przechowywania wychodzącego obiektu `CSimpleStringT`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator =`.

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

##  <a name="operator_pcxstr"></a>CSimpleStringT:: operator PCXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w obiekcie `CSimpleStringT` jako ciąg w stylu C.

### <a name="syntax"></a>Składnia

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Nie są kopiowane żadne znaki; zwracany jest tylko wskaźnik. Należy zachować ostrożność przy użyciu tego operatora. Jeśli zmienisz obiekt `CString` po uzyskaniu wskaźnika znakowego, może dojść do ponownej alokacji pamięci, która unieważnia wskaźnik.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::operator PCXSTR`.

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

##  <a name="pcxstr"></a>CSimpleStringT::P CXSTR

Wskaźnik do stałego ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>CSimpleStringT::P ponownie przydzielić

Przydziela określoną ilość bajtów dla obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Dokładny rozmiar buforu znaków `CSimpleStringT` w znakach.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby przydzielić określony rozmiar buforu dla obiektu `CSimpleStringT`.

`CSimpleStringT` generuje wyjątek STATUS_NO_MEMORY, jeśli nie może przydzielić miejsca dla buforu znaków. Domyślnie alokacja pamięci jest wykonywana przez funkcje interfejsu API WIN32 `HeapAlloc` lub `HeapReAlloc`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>CSimpleStringT::P XSTR

Wskaźnik do ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Udostępnia kontrolę nad buforem przydzielonym przez [GetBuffer](#getbuffer).

### <a name="syntax"></a>Składnia

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nowa długość ciągu znaków, która nie zlicza terminatora o wartości null. Jeśli ciąg jest zakończony wartością null, wartość domyślna-1 ustawia rozmiar `CSimpleStringT` na bieżącą długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby ponownie przydzielić lub zwolnić bufor obiektu ciągu. Jeśli wiesz, że ciąg w buforze jest zakończony wartością null, możesz pominąć argument *nNewLength* . Jeśli ciąg nie jest zakończony wartością null, użyj *nNewLength* , aby określić jego długość. Adres zwrócony przez metodę [GetBuffer](#getbuffer) jest nieprawidłowy po wywołaniu `ReleaseBuffer` lub dowolnej innej operacji `CSimpleStringT`.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::ReleaseBuffer`.

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

##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Udostępnia kontrolę nad buforem przydzielonym przez [GetBuffer](#getbuffer).

### <a name="syntax"></a>Składnia

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Długość wydanego ciągu

### <a name="remarks"></a>Uwagi

Ta funkcja działa podobnie jak [ReleaseBuffer](#releasebuffer) , z tą różnicą, że należy przesłać prawidłową długość obiektu String.

##  <a name="setat"></a>CSimpleStringT::SetAt

Ustawia pojedynczy znak z obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w obiekcie `CSimpleStringT`. Parametr *iChar* musi być większy lub równy 0 i mniejszy od wartości zwracanej przez [GetLength](#getlength).

*ch*<br/>
Nowy znak.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zastąpić znak znajdujący się w *iChar*. Ta metoda nie powiększa ciągu, jeśli *iChar* przekracza granice istniejącego ciągu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>CSimpleStringT:: setmanager

Określa Menedżera pamięci obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Wskaźnik do nowego menedżera pamięci.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić nowy Menedżer pamięci używany przez obiekt `CSimpleStringT`. Aby uzyskać więcej informacji na temat menedżerów pamięci i obiektów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>CSimpleStringT:: SetString

Ustawia ciąg obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Wskaźnik na ciąg zakończony znakiem null.

*nLength*<br/>
Liczba znaków w *pszSrc*.

### <a name="remarks"></a>Uwagi

Kopiuj ciąg do obiektu `CSimpleStringT`. `SetString` zastępuje starsze dane ciągu w buforze.

Obie wersje `SetString` sprawdzają, czy *pszSrc* jest wskaźnikiem o wartości null, a jeśli jest, zgłoś błąd E_INVALIDARG.

Jednoparametrowa wersja `SetString` oczekuje, że *pszSrc* ma wskazywać na ciąg zakończony znakiem null.

Dwuparametrowa wersja `SetString` powinna również oczekiwać, że *pszSrc* będzie ciągiem zakończonym wartością null. Używa *nLength* jako długości ciągu, chyba że napotka najpierw terminator o wartości null.

Dwuparametrowa wersja `SetString` sprawdza także, czy *pszSrc* wskazuje lokalizację w bieżącym buforze w `CSimpleStringT`. W tym szczególnym przypadku `SetString` używa funkcji kopiowania pamięci, która nie zastępuje danych ciągu, ponieważ kopiuje dane ciągu z powrotem do buforu.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>CSimpleStringT::StringLength

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

Poniższy przykład ilustruje użycie `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>CSimpleStringT:: Truncate

Obcina ciąg do nowej długości.

### <a name="syntax"></a>Składnia

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nowa długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby obciąć zawartość ciągu do nowej długości.

> [!NOTE]
>  Nie ma to wpływu na przydzieloną długość buforu. Aby zmniejszyć lub zwiększyć bieżący bufor, zobacz [FreeExtra](#freeextra) i [preallocate](#preallocate).

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer

Odblokowuje bufor obiektu `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zresetować liczbę odwołań ciągu do 1.

Destruktor `CSimpleStringT` automatycznie wywołuje `UnlockBuffer`, aby upewnić się, że bufor nie jest zablokowany w przypadku wywołania destruktora. Aby zapoznać się z przykładem tej metody, zobacz [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT

Niszczy obiekt `CSimpleStringT`.

### <a name="syntax"></a>Składnia

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zniszczyć obiekt `CSimpleStringT`.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
