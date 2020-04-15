---
title: CSimpleStringT, klasa
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
ms.openlocfilehash: dce33289699b9e7b7484d1feb6335476f93dee9b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81317683"
---
# <a name="csimplestringt-class"></a>CSimpleStringT, klasa

Ta klasa `CSimpleStringT` reprezentuje obiekt.

## <a name="syntax"></a>Składnia

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasy string. Może być jedną z następujących czynności:

- **char** (dla ciągów znaków ANSI).

- **wchar_t** (dla ciągów znaków Unicode).

- TCHAR (dla ciągów znaków ANSI i Unicode).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne typedefs

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Wskaźnik do stałego ciągu.|
|[CSimpleStringT::PXSTR](#pxstr)|Wskaźnik do ciągu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Konstruuje `CSimpleStringT` obiekty na różne sposoby.|
|[CSimpleStringT::~CSimpleStringT](#dtor)|Destruktora.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::Dołącz](#append)|Dołącza `CSimpleStringT` obiekt do istniejącego `CSimpleStringT` obiektu.|
|[CSimpleStringT::DodatekChar](#appendchar)|Dołącza znak do istniejącego `CSimpleStringT` obiektu.|
|[CSimpleStringT::CopyChars](#copychars)|Kopiuje znak lub znaki do innego ciągu.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Kopiuje znak lub znaki do innego ciągu, w którym bufory nakładają się.|
|[CSimpleStringT::Pusty](#empty)|Wymusza ciąg mieć długość zero.|
|[CSimpleStringT::FreeExtra](#freeextra)|Zwalnia wszelkie dodatkowe pamięci wcześniej przydzielone przez obiekt ciągu.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Pobiera przydzieloną długość `CSimpleStringT` obiektu.|
|[CSimpleStringT::GetAt](#getat)|Zwraca znak w danej pozycji.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Zwraca wskaźnik do znaków `CSimpleStringT`w pliku .|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Zwraca wskaźnik do znaków `CSimpleStringT`w , obcięcie do określonej długości.|
|[CSimpleStringT::GetLength](#getlength)|Zwraca liczbę znaków w `CSimpleStringT` obiekcie.|
|[CSimpleStringT::GetManager](#getmanager)|Pobiera menedżera pamięci `CSimpleStringT` obiektu.|
|[CSimpleStringT::GetString](#getstring)|Pobiera ciąg znaków|
|[CSimpleStringT::IsEmpty](#isempty)|Sprawdza, `CSimpleStringT` czy obiekt nie zawiera żadnych znaków.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Wyłącza zliczanie odwołań i chroni ciąg w buforze.|
|[CSimpleStringT::Preallocate](#preallocate)|Przydziela określoną ilość pamięci dla buforu znaków.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Zwalnia kontrolę buforu `GetBuffer`zwróconego przez .|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Zwalnia kontrolę buforu `GetBuffer`zwróconego przez .|
|[CSimpleStringT::SetAt](#setat)|Ustawia znak w danej pozycji.|
|[CSimpleStringT::SetManager](#setmanager)|Ustawia menedżera pamięci `CSimpleStringT` obiektu.|
|[CSimpleStringT::SetString](#setstring)|Ustawia ciąg `CSimpleStringT` obiektu.|
|[CSimpleStringT::StringLength](#stringlength)|Zwraca liczbę znaków w określonym ciągu.|
|[CSimpleStringT::Obcinanie](#truncate)|Obcina ciąg do określonej długości.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Włącza zliczanie odwołań i zwalnia ciąg w buforze.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Bezpośredni dostęp do znaków `CSimpleStringT` przechowywanych w obiekcie jako ciąg w stylu C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Zwraca znak w danej pozycji — `GetAt`zastępowanie operatora dla .|
|[CSimpleStringT::operator +=](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CSimpleStringT::operator =](#operator_eq)|Przypisuje nową wartość do `CSimpleStringT` obiektu.|

### <a name="remarks"></a>Uwagi

`CSimpleStringT`jest klasą podstawową dla różnych klas ciągów obsługiwanych przez visual C++. Zapewnia minimalną obsługę zarządzania pamięcią obiektu ciągu i manipulacji buforem podstawowym. Aby uzyskać bardziej zaawansowane obiekty ciągów, zobacz [CStringT Class](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

## <a name="csimplestringtappend"></a><a name="append"></a>CSimpleStringT::Dołącz

Dołącza `CSimpleStringT` obiekt do istniejącego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc ( strSrc )*<br/>
Obiekt, `CSimpleStringT` który ma zostać dołączona.

*pszsrc*<br/>
Wskaźnik do ciągu zawierającego znaki, które mają być dołączone.

*nLength (nLength)*<br/>
Liczba znaków do doskładniania.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, `CSimpleStringT` aby dołączyć `CSimpleStringT` istniejący obiekt do innego obiektu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

## <a name="csimplestringtappendchar"></a><a name="appendchar"></a>CSimpleStringT::DodatekChar

Dołącza znak do istniejącego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*Ch*<br/>
Znak, który ma być dołączona

### <a name="remarks"></a>Uwagi

Wywołanie tej funkcji, aby dołączyć określony znak `CSimpleStringT` na końcu istniejącego obiektu.

## <a name="csimplestringtcopychars"></a><a name="copychars"></a>CSimpleStringT::CopyChars

Kopiuje znak lub `CSimpleStringT` znaki do obiektu.

### <a name="syntax"></a>Składnia

```
static void CopyChars(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest (psż.*<br/>
Wskaźnik do ciągu znaków.

*pchSrc ( pchSrc )*<br/>
Wskaźnik do ciągu zawierającego znaki do skopiowania.

*NChary*<br/>
Liczba znaków *pchSrc* do skopiowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować znaki z *pchSrc* do *pchDest* ciąg.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

## <a name="csimplestringtcopycharsoverlapped"></a><a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped

Kopiuje znak lub `CSimpleStringT` znaki do obiektu.

### <a name="syntax"></a>Składnia

```
static void CopyCharsOverlapped(
    XCHAR* pchDest,
    const XCHAR* pchSrc,
    int nChars) throw();
```

#### <a name="parameters"></a>Parametry

*pchDest (psż.*<br/>
Wskaźnik do ciągu znaków.

*pchSrc ( pchSrc )*<br/>
Wskaźnik do ciągu zawierającego znaki do skopiowania.

*NChary*<br/>
Liczba znaków *pchSrc* do skopiowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować znaki z *pchSrc* do *pchDest* ciąg. W `CopyChars` `CopyCharsOverlapped` przeciwieństwie do programu , zapewnia bezpieczną metodę kopiowania z buforów znaków, które mogą się pokrywać.

### <a name="example"></a>Przykład

Zobacz przykład [CSimpleStringT::CopyChars](#copychars)lub kod źródłowy dla `CSimpleStringT::SetString` (znajduje się w atlsimpstr.h).

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

*strSrc ( strSrc )*<br/>
Istniejący `CSimpleStringT` obiekt do skopiowania `CSimpleStringT` do tego obiektu.

*pchSrc ( pchSrc )*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, nie null zakończone.

*pszsrc*<br/>
Ciąg zakończony z wartością null ma `CSimpleStringT` zostać skopiowany do tego obiektu.

*nLength (nLength)*<br/>
Liczba znaków w pliku `pch`.

*pStringMgr*<br/>
Wskaźnik do menedżera pamięci `CSimpleStringT` obiektu. Aby uzyskać `IAtlStringMgr` więcej informacji `CSimpleStringT`na temat zarządzania pamięcią i zarządzania pamięcią dla , zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Skonstruuj nowy `CSimpleStringT` obiekt. Ponieważ konstruktory skopiować dane wejściowe do nowego przydzielonego magazynu, wyjątki pamięci może spowodować.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::CSimpleStringT` przy użyciu ATL **typedef** `CSimpleString`. `CSimpleString`jest powszechnie stosowaną specjalizacją szablonu `CSimpleStringT`klasy .

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

## <a name="csimplestringtempty"></a><a name="empty"></a>CSimpleStringT::Pusty

Sprawia, `CSimpleStringT` że ten obiekt pusty ciąg i zwalnia pamięci, zgodnie z potrzebami.

### <a name="syntax"></a>Składnia

```
void Empty() throw();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [Ciągi: CString Exception Cleanup](../cstring-exception-cleanup.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

## <a name="csimplestringtfreeextra"></a><a name="freeextra"></a>CSimpleStringT::FreeExtra

Zwalnia wszelkie dodatkowe pamięci wcześniej przydzielone przez ciąg, ale nie jest już potrzebne.

### <a name="syntax"></a>Składnia

```
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

Powinno to zmniejszyć obciążenie pamięci zużywane przez obiekt ciągu. Metoda ponownie przydziela bufor do dokładnej długości zwróconej przez [GetLength](#getlength).

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

Liczba znaków przydzielonych dla tego obiektu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić `CSimpleStringT` liczbę znaków przydzielonych dla tego obiektu. Zobacz [FreeExtra](#freeextra) na przykład wywoływania tej funkcji.

## <a name="csimplestringtgetat"></a><a name="getat"></a>CSimpleStringT::GetAt

Zwraca jeden znak `CSimpleStringT` z obiektu.

### <a name="syntax"></a>Składnia

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar ( iChar )*<br/>
Indeks znaku w obiekcie `CSimpleStringT` oparty na wartości zerowej. Parametr *iChar* musi być większy lub równy 0 i mniejszy niż wartość zwracana przez [GetLength](#getlength). W `GetAt` przeciwnym razie wygeneruje wyjątek.

### <a name="return-value"></a>Wartość zwracana

Znak, `XCHAR` który zawiera znak w określonej pozycji w ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zwrócić jeden znak określony przez *iChar*. Przeciążony indeks dolny (**[]**) operator `GetAt`jest wygodny alias dla . Terminator zerowy można rozwiązać bez generowania `GetAt`wyjątku przy użyciu programu . Jednak nie jest liczony `GetLength`przez , a zwracana wartość wynosi 0.

### <a name="example"></a>Przykład

W poniższym przykładzie `CSimpleStringT::GetAt`pokazano, jak używać .

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

## <a name="csimplestringtgetbuffer"></a><a name="getbuffer"></a>CSimpleStringT::GetBuffer

Zwraca wskaźnik do wewnętrznego buforu `CSimpleStringT` znaków dla obiektu.

### <a name="syntax"></a>Składnia

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parametry

*nMinBufferLength*<br/>
Minimalna liczba znaków, które bufor znaków może pomieścić. Ta wartość nie zawiera miejsca dla terminatora zerowego.

Jeśli *nMinBufferLength* jest większy niż długość `GetBuffer` bieżącego buforu, niszczy bieżący bufor, zastępuje go buforem żądanego rozmiaru i resetuje liczbę odwołań do obiektu do zera. Jeśli wcześniej nazywano [LockBuffer](#lockbuffer) w tym buforze, utracisz blokadę buforu.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik `PXSTR` do buforu znaków obiektu (zakończonej z wartością null).

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby `CSimpleStringT` zwrócić zawartość buforu obiektu. Zwrócony `PXSTR` nie jest stałą i dlatego `CSimpleStringT` umożliwia bezpośrednią modyfikację zawartości.

Jeśli używasz wskaźnika `GetBuffer` zwrócony przez aby zmienić zawartość ciągu, należy `CSimpleStringT` [wywołać ReleaseBuffer](#releasebuffer) przed użyciem innych metod członkowskich.

Adres zwracany `GetBuffer` przez może być nieprawidłowy po wywołaniu, `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacje mogą spowodować ponowne przydzielenie `CSimpleStringT` buforu. Bufor nie zostanie ponownie przydzielony, jeśli nie `CSimpleStringT`zmienisz długości pliku .

Pamięć buforu jest automatycznie `CSimpleStringT` zwalniana, gdy obiekt zostanie zniszczony.

Jeśli samodzielnie śledzisz długość ciągu, nie należy dołączać kończącego się znaku null. Należy jednak określić ostateczną długość ciągu podczas `ReleaseBuffer`zwalniania buforu za pomocą pliku . Jeśli dodasz kończący się znak null, należy przekazać -1 (domyślnie) dla długości. `ReleaseBuffer`następnie określa długość buforu.

Jeśli istnieje za mało `GetBuffer` pamięci, aby spełnić żądanie, ta metoda zgłasza CMemoryException*.

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

Zwraca wskaźnik do wewnętrznego buforu `CSimpleStringT` znaków dla obiektu, obcinając lub powiększając jego długość, jeśli to konieczne, aby dokładnie dopasować długość określoną w *nLength*.

### <a name="syntax"></a>Składnia

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength (nLength)*<br/>
Dokładny rozmiar buforu `CSimpleStringT` znaków w znakach.

### <a name="return-value"></a>Wartość zwracana

Wskaźnik `PXSTR` do buforu znaków obiektu (zakończonej z wartością null).

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać określoną `CSimpleStringT` długość buforu wewnętrznego obiektu. Zwrócony `PXSTR` wskaźnik nie jest **const** i `CSimpleStringT` w związku z tym umożliwia bezpośrednią modyfikację zawartości.

Jeśli używasz wskaźnika zwróconego przez [GetBufferSetLength,](#getbuffersetlength) aby zmienić zawartość ciągu, wywołanie, `ReleaseBuffer` aby zaktualizować stan wewnętrzny `CsimpleStringT` przed użyciem innych `CSimpleStringT` metod.

Adres zwracany `GetBufferSetLength` przez może być nieprawidłowy po wywołaniu, `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacje mogą spowodować ponowne przydzielenie `CSimpleStringT` buforu. Bufor nie zostanie ponownie przypisany, jeśli nie `CSimpleStringT`zmienisz długości pliku .

Pamięć buforu jest automatycznie `CSimpleStringT` zwalniana, gdy obiekt zostanie zniszczony.

Jeśli samodzielnie śledzisz długość ciągu, nie dołączaj kończącego się znaku null. Podczas zwalniania buforu należy określić ostateczną długość ciągu przy użyciu programu `ReleaseBuffer`. Jeśli dołączysz kończący się znak null `ReleaseBuffer`podczas wywoływania , przekaż -1 `ReleaseBuffer`(domyślnie) dla długości do , i `ReleaseBuffer` wykona `strlen` na buforze, aby określić jego długość.

Aby uzyskać więcej informacji na temat zliczania odwołań, zobacz następujące artykuły:

- [Zarządzanie okresami istnienia obiektów za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting) w panelu Windows SDK.

- [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) w programie Windows SDK.

- [Reguły zarządzania liczbami odwołań](/windows/win32/com/rules-for-managing-reference-counts) w sdku windows.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::GetBufferSetLength`.

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

## <a name="csimplestringtgetlength"></a><a name="getlength"></a>CSimpleStringT::GetLength

Zwraca liczbę znaków w `CSimpleStringT` obiekcie.

### <a name="syntax"></a>Składnia

```
int GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zwrócić liczbę znaków w obiekcie. Liczba nie zawiera zerowego terminatora.

W przypadku zestawów znaków wielobajtowych (MBCS) `GetLength` zlicza każdy znak 8-bitowy; oznacza to, że ołów i bajt szlaku w jednym znaku wielobajtowym są liczone jako dwa bajty. Zobacz [FreeExtra](#freeextra) na przykład wywoływania tej funkcji.

## <a name="csimplestringtgetmanager"></a><a name="getmanager"></a>CSimpleStringT::GetManager

Pobiera menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do menedżera pamięci `CSimpleStringT` dla obiektu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać `CSimpleStringT` menedżera pamięci używanego przez obiekt. Aby uzyskać więcej informacji na temat menedżerów pamięci i obiektów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

## <a name="csimplestringtgetstring"></a><a name="getstring"></a>CSimpleStringT::GetString

Pobiera ciąg znaków.

### <a name="syntax"></a>Składnia

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu znaków zakończonych z wartością null.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby pobrać ciąg `CSimpleStringT` znaków skojarzonych z obiektem.

> [!NOTE]
> Zwrócony `PCXSTR` wskaźnik jest **const** i nie `CSimpleStringT` zezwala na bezpośrednią modyfikację zawartości.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

## <a name="csimplestringtisempty"></a><a name="isempty"></a>CSimpleStringT::IsEmpty

Testuje `CSimpleStringT` obiekt pod kątem pustego warunku.

### <a name="syntax"></a>Składnia

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość `CSimpleStringT` PRAWDA, jeśli obiekt ma długość 0; w przeciwnym razie FALSE.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby ustalić, czy obiekt zawiera pusty ciąg.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::IsEmpty`.

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

Wskaźnik do `CSimpleStringT` obiektu lub ciąg zakończony z wartością null.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby `CSimpleStringT` zablokować bufor obiektu. Wywołując `LockBuffer`, można utworzyć kopię ciągu, z -1 dla liczby odwołań. Gdy wartość liczby odwołań wynosi -1, ciąg w buforze jest uważany za "zablokowany" stan. W stanie zablokowanym ciąg jest chroniony na dwa sposoby:

- Żaden inny ciąg nie może uzyskać odwołania do danych w zablokowanym ciągu, nawet jeśli ten ciąg jest przypisany do zablokowanego ciągu.

- Zablokowany ciąg nigdy nie będzie odwoływać się do innego ciągu, nawet jeśli ten inny ciąg jest kopiowany do zablokowanego ciągu.

Blokując ciąg w buforze, upewnij się, że wyłączne przytrzymanie ciągu w buforze pozostanie nienaruszone.

Po zakończeniu z `LockBuffer`, [wywołać UnlockBuffer](#unlockbuffer) zresetować liczbę odwołań do 1.

> [!NOTE]
> Jeśli wywołasz [GetBuffer](#getbuffer) w zablokowanym buforze i ustawisz `GetBuffer` parametr `nMinBufferLength` na większą niż długość bieżącego buforu, utracisz blokadę buforu. Takie wywołanie, aby zniszczyć `GetBuffer` bieżący bufor, zastępuje go buforem żądanego rozmiaru i resetuje liczbę odwołań do zera.

Aby uzyskać więcej informacji na temat zliczania odwołań, zobacz następujące artykuły:

- [Zarządzanie okresami istnienia obiektów za pomocą zliczania odwołań](/windows/win32/com/managing-object-lifetimes-through-reference-counting) w programie Windows SDK

- [Implementowanie zliczania odwołań](/windows/win32/com/implementing-reference-counting) w programie Windows SDK

- [Reguły zarządzania liczbami odwołań](/windows/win32/com/rules-for-managing-reference-counts) w programie Windows SDK

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

## <a name="csimplestringtoperator"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]

Wywołanie tej funkcji, aby uzyskać dostęp do pojedynczego znaku tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar ( iChar )*<br/>
Indeks od zera znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążony indeks dolny (**[]**) zwraca pojedynczy znak określony przez indeks od zera w *iChar*. Ten operator jest wygodnym substytutem funkcji elementu członkowskiego [GetAt.](#getat)

> [!NOTE]
> Można użyć operatora indeksu dolnego (**[]**), aby `CSimpleStringT`uzyskać wartość znaku w , ale nie `CSimpleStringT`można go użyć do zmiany wartości znaku w .

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="csimplestringtoperator-"></a><a name="operator_at"></a>CSimpleStringT::operator\[\]

Wywołanie tej funkcji, aby uzyskać dostęp do pojedynczego znaku tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar ( iChar )*<br/>
Indeks od zera znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążony indeks dolny (**[]**) zwraca pojedynczy znak określony przez indeks od zera w *iChar*. Ten operator jest wygodnym substytutem funkcji elementu członkowskiego [GetAt.](#getat)

> [!NOTE]
> Można użyć operatora indeksu dolnego (**[]**), aby `CSimpleStringT`uzyskać wartość znaku w , ale nie `CSimpleStringT`można go użyć do zmiany wartości znaku w .

## <a name="csimplestringtoperator-"></a><a name="operator_add_eq"></a>CSimpleStringT::operator +=

Łączy nowy ciąg lub znak na końcu istniejącego ciągu.

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

*pszsrc*<br/>
Wskaźnik do ciągu zakończonego wartością null.

*strSrc ( strSrc )*<br/>
Wskaźnik do istniejącego `CSimpleStringT` obiektu.

*Ch*<br/>
Znak, który ma zostać dołączona.

### <a name="remarks"></a>Uwagi

Operator akceptuje inny `CSimpleStringT` obiekt lub znak. Należy zauważyć, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz `CSimpleStringT` tego operatora łączenia, ponieważ nowy magazyn może być przydzielony dla znaków dodanych do tego obiektu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

## <a name="csimplestringtoperator-"></a><a name="operator_eq"></a>CSimpleStringT::operator =

Przypisuje nową wartość do `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
CSimpleStringT& operator =(PCXSTR pszSrc);
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```

#### <a name="parameters"></a>Parametry

*pszsrc*<br/>
Wskaźnik do ciągu zakończonego wartością null.

*strSrc ( strSrc )*<br/>
Wskaźnik do istniejącego `CSimpleStringT` obiektu.

### <a name="remarks"></a>Uwagi

Jeśli ciąg docelowy (po lewej stronie) jest już wystarczająco duży, aby przechowywać nowe dane, nie jest wykonywana alokacja nowej pamięci. Należy zauważyć, że wyjątki pamięci mogą wystąpić za każdym razem, gdy `CSimpleStringT` używasz operatora przypisania, ponieważ nowy magazyn jest często przydzielany do przechowywania wynikowego obiektu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::operator =`.

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

## <a name="csimplestringtoperator-pcxstr"></a><a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR

Bezpośredni dostęp do znaków `CSimpleStringT` przechowywanych w obiekcie jako ciąg w stylu C.

### <a name="syntax"></a>Składnia

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Żadne znaki nie są kopiowane; zwracany jest tylko wskaźnik. Należy zachować ostrożność z tym operatorem. Jeśli obiekt `CString` zostanie zmieniona po uzyskaniu wskaźnika znaków, może spowodować ponowne przydzielenie pamięci, która unieważnia wskaźnik.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::operator PCXSTR`.

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

## <a name="csimplestringtpcxstr"></a><a name="pcxstr"></a>CSimpleStringT::PCXSTR

Wskaźnik do stałego ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

## <a name="csimplestringtpreallocate"></a><a name="preallocate"></a>CSimpleStringT::Preallocate

Przydziela określoną ilość bajtów `CSimpleStringT` dla obiektu.

### <a name="syntax"></a>Składnia

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength (nLength)*<br/>
Dokładny rozmiar buforu `CSimpleStringT` znaków w znakach.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby przydzielić określony rozmiar buforu `CSimpleStringT` dla obiektu.

`CSimpleStringT`generuje wyjątek STATUS_NO_MEMORY, jeśli nie jest w stanie przydzielić miejsca dla buforu znaków. Domyślnie alokacja pamięci jest wykonywana przez `HeapAlloc` `HeapReAlloc`funkcje interfejsu API systemu WIN32 lub .

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

## <a name="csimplestringtpxstr"></a><a name="pxstr"></a>CSimpleStringT::PXSTR

Wskaźnik do ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

## <a name="csimplestringtreleasebuffer"></a><a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer

Zwalnia kontrolę nad buforem przydzielonym przez [GetBuffer](#getbuffer).

### <a name="syntax"></a>Składnia

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNowyLength*<br/>
Nowa długość ciągu w znakach, nie licząc zerowego terminatora. Jeśli ciąg jest zakończony wartością null, wartość `CSimpleStringT` domyślna -1 ustawia rozmiar na bieżącą długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby ponownie przydzielić lub zwolnić bufor obiektu ciągu. Jeśli wiesz, że ciąg w buforze jest zakończony zerem, możesz pominąć argument *nNewLength.* Jeśli ciąg nie jest zakończony z wartością null, użyj *nNewLength,* aby określić jego długość. Adres zwrócony przez [GetBuffer](#getbuffer) jest `ReleaseBuffer` nieprawidłowy `CSimpleStringT` po wywołaniu lub innej operacji.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::ReleaseBuffer`.

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

Zwalnia kontrolę nad buforem przydzielonym przez [GetBuffer](#getbuffer).

### <a name="syntax"></a>Składnia

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNowyLength*<br/>
Długość zwolnionego ciągu

### <a name="remarks"></a>Uwagi

Ta funkcja jest funkcjonalnie podobna do [ReleaseBuffer,](#releasebuffer) z tą różnicą, że musi zostać przekazana prawidłowa długość obiektu ciągu.

## <a name="csimplestringtsetat"></a><a name="setat"></a>CSimpleStringT::SetAt

Ustawia pojedynczy znak `CSimpleStringT` z obiektu.

### <a name="syntax"></a>Składnia

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar ( iChar )*<br/>
Indeks znaku w obiekcie `CSimpleStringT` oparty na wartości zerowej. Parametr *iChar* musi być większy lub równy 0 i mniejszy niż wartość zwracana przez [GetLength](#getlength).

*Ch*<br/>
Nowa postać.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zastąpić znak znajdujący się w *iChar*. Ta metoda nie powiększy ciąg, jeśli *iChar* przekracza granice istniejącego ciągu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

## <a name="csimplestringtsetmanager"></a><a name="setmanager"></a>CSimpleStringT::SetManager

Określa menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Wskaźnik do nowego menedżera pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić `CSimpleStringT` nowy menedżer pamięci używany przez obiekt. Aby uzyskać więcej informacji na temat menedżerów pamięci i obiektów ciągów, zobacz [Zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

## <a name="csimplestringtsetstring"></a><a name="setstring"></a>CSimpleStringT::SetString

Ustawia ciąg `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*pszsrc*<br/>
Wskaźnik do ciągu zakończonego wartością null.

*nLength (nLength)*<br/>
Liczba znaków w *pszSrc*.

### <a name="remarks"></a>Uwagi

Skopiuj `CSimpleStringT` ciąg do obiektu. `SetString`zastępuje starsze dane ciągu w buforze.

Obie wersje `SetString` sprawdź czy *pszSrc* jest wskaźnikiem null, a jeśli tak, to zrzuć E_INVALIDARG błąd.

Wersja jednoparametrowa `SetString` oczekuje *pszSRC* wskazać ciąg zakończony zerem.

Dwuparametryczny `SetString` wersja również oczekuje *pszSrc* być ciąg zakończony zerem. Używa *nLength* jako długość ciągu, chyba że napotka null terminator pierwszy.

Dwuparametryczowa `SetString` wersja sprawdza również, czy *pszSrc* wskazuje `CSimpleStringT`lokalizację w bieżącym buforze w . W tym szczególnym `SetString` przypadku używa funkcji kopiowania pamięci, która nie zastępuje danych ciągu, ponieważ kopiuje dane ciągu z powrotem do buforu.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::SetString`.

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

*Psz*<br/>
Wskaźnik do ciągu zakończonego wartością null.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w *psz*; nie licząc zerowego terminatora.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę znaków w ciągu wskazanym przez *psz*.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

## <a name="csimplestringttruncate"></a><a name="truncate"></a>CSimpleStringT::Obcinanie

Obcina ciąg do nowej długości.

### <a name="syntax"></a>Składnia

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNowyLength*<br/>
Nowa długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby obciąć zawartość ciągu do nowej długości.

> [!NOTE]
> Nie ma to wpływu na przydzieloną długość buforu. Aby zmniejszyć lub zwiększyć bieżący bufor, zobacz [FreeExtra](#freeextra) i [Preallocate](#preallocate).

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CSimpleStringT::Truncate`.

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

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zresetować liczbę odwołań ciągu do 1.

Destruktor `CSimpleStringT` automatycznie wywołuje, `UnlockBuffer` aby upewnić się, że bufor nie jest zablokowany, gdy wywoływany jest destruktor. Na przykład tej metody zobacz [LockBuffer](#lockbuffer).

## <a name="csimplestringtcsimplestringt"></a><a name="dtor"></a>CSimpleStringT::~CSimpleStringT

Niszczy `CSimpleStringT` obiekt.

### <a name="syntax"></a>Składnia

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby zniszczyć `CSimpleStringT` obiekt.

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
