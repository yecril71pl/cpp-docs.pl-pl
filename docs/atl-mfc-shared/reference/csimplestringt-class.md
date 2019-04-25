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
ms.openlocfilehash: 1ec28ed5b2f5428cabcf7570c7ac53904e9a64f0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62252641"
---
# <a name="csimplestringt-class"></a>CSimpleStringT, klasa

Ta klasa reprezentuje `CSimpleStringT` obiektu.

## <a name="syntax"></a>Składnia

```
template <typename BaseType>
class CSimpleStringT
```

### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasa string. Może to być jeden z następujących elementów:

- **CHAR** (na ciągi znaków ANSI).

- **wchar_t** (na ciągi znaków Unicode).

- TCHAR (na ciągi znaków ANSI i Unicode).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::PCXSTR](#pcxstr)|Wskaźnik ze stałym ciągiem.|
|[CSimpleStringT::PXSTR](#pxstr)|Wskaźnik do ciągu.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::CSimpleStringT](#ctor)|Konstruuje `CSimpleStringT` obiektów na różne sposoby.|
|[CSimpleStringT::~CSimpleStringT](#dtor)|Destruktor.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::Append](#append)|Dołącza `CSimpleStringT` obiektu do istniejącego `CSimpleStringT` obiektu.|
|[CSimpleStringT::AppendChar](#appendchar)|Dołącza znak do istniejącego `CSimpleStringT` obiektu.|
|[CSimpleStringT::CopyChars](#copychars)|Kopiuje znak / znaki do innego ciągu.|
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Kopiuje znak lub znaki do innego ciągu w którym buforów nakładają się na siebie.|
|[CSimpleStringT::Empty](#empty)|Wymusza ciąg mieć długości zerowej.|
|[CSimpleStringT::FreeExtra](#freeextra)|Zwalnia wszelkie dodatkowe pamięci uprzednio przydzielonej przez obiekt ciągu.|
|[CSimpleStringT::GetAllocLength](#getalloclength)|Pobiera długość przydzielonego `CSimpleStringT` obiektu.|
|[CSimpleStringT::GetAt](#getat)|Zwraca znak na określonej pozycji.|
|[CSimpleStringT::GetBuffer](#getbuffer)|Zwraca wskaźnik do znaków w `CSimpleStringT`.|
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Zwraca wskaźnik do znaków w `CSimpleStringT`, obcinanie do określonej długości.|
|[CSimpleStringT::GetLength](#getlength)|Zwraca liczbę znaków w `CSimpleStringT` obiektu.|
|[CSimpleStringT::GetManager](#getmanager)|Pobiera Menedżera pamięci `CSimpleStringT` obiektu.|
|[CSimpleStringT::GetString](#getstring)|Pobiera ciąg znaków|
|[CSimpleStringT::IsEmpty](#isempty)|Testy czy `CSimpleStringT` obiekt nie zawiera żadnych znaków.|
|[CSimpleStringT::LockBuffer](#lockbuffer)|Wyłącza zliczaniu odwołań i chroni ciąg znaków w buforze.|
|[CSimpleStringT::Preallocate](#preallocate)|Przydziela określoną ilością pamięci buforu znaków.|
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Zwalnia kontrolę nad buforu zwrócony przez `GetBuffer`.|
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Zwalnia kontrolę nad buforu zwrócony przez `GetBuffer`.|
|[CSimpleStringT::SetAt](#setat)|Określa znak na określonej pozycji.|
|[CSimpleStringT::SetManager](#setmanager)|Ustawia Menedżera pamięci `CSimpleStringT` obiektu.|
|[CSimpleStringT::SetString](#setstring)|Ustawia ciąg `CSimpleStringT` obiektu.|
|[CSimpleStringT::StringLength](#stringlength)|Zwraca liczbę znaków w określonym ciągu.|
|[CSimpleStringT::Truncate](#truncate)|Obcina ciąg do określonej długości.|
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Włącza zliczaniu odwołań i zwalnia ciąg znaków w buforze.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Bezpośrednio uzyskuje dostęp do znaków przechowywanych w `CSimpleStringT` obiektu jako ciąg stylu C.|
|[CSimpleStringT::operator\[\]](#operator_at)|Zwraca znak na określonej pozycji — operator podstawienia dla `GetAt`.|
|[CSimpleStringT::operator +=](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CSimpleStringT::operator =](#operator_eq)|Przypisuje nową wartość do `CSimpleStringT` obiektu.|

### <a name="remarks"></a>Uwagi

`CSimpleStringT` jest klasą bazową dla różnych klas ciągów, obsługiwane przez Visual C++. Jego zapewnia minimalną obsługę dla zarządzania pamięcią obiektu ciągu i manipulowanie buforem podstawowe. Dla bardziej zaawansowanych parametrów obiektów, zobacz [CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md).

### <a name="requirements"></a>Wymagania

**Nagłówek:** atlsimpstr.h

## <a name="append"></a> CSimpleStringT::Append

Dołącza `CSimpleStringT` obiektu do istniejącego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void Append(const CSimpleStringT& strSrc);
void Append(PCXSTR pszSrc, int nLength);
void Append(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
`CSimpleStringT` Obiektu do dołączenia.

*pszSrc*<br/>
Wskaźnik na ciąg zawierający znaki, które mają być dołączane.

*nLength*<br/>
Liczba znaków do dołączenia.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby dołączyć do istniejącego `CSimpleStringT` obiektu do drugiego `CSimpleStringT` obiektu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::Append`.

```cpp
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```

##  <a name="appendchar"></a> CSimpleStringT::AppendChar

Dołącza znak do istniejącego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void AppendChar(XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*ch*<br/>
Znak do dołączenia

### <a name="remarks"></a>Uwagi

Wywołaj tę funkcję, aby dołączyć określony znak na końcu istniejącej `CSimpleStringT` obiektu.

##  <a name="copychars"></a> CSimpleStringT::CopyChars

Kopiuje znak lub znaki `CSimpleStringT` obiektu.

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
Wskaźnik na ciąg zawierający znaki, które ma być skopiowany.

*nChars*<br/>
Liczba *pchSrc* znaków do skopiowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować znaków ze zbioru *pchSrc* do *pchDest* ciągu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::CopyChars`.

```cpp
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```

##  <a name="copycharsoverlapped"></a>  CSimpleStringT::CopyCharsOverlapped

Kopiuje znak lub znaki `CSimpleStringT` obiektu.

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
Wskaźnik na ciąg zawierający znaki, które ma być skopiowany.

*nChars*<br/>
Liczba *pchSrc* znaków do skopiowania.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby skopiować znaków ze zbioru *pchSrc* do *pchDest* ciągu. W odróżnieniu od `CopyChars`, `CopyCharsOverlapped` udostępnia bezpieczne metody kopiowania z buforów znaków, które mogą mieć nakładających się.

### <a name="example"></a>Przykład

Zobacz przykład [CSimpleStringT::CopyChars](#copychars), lub kodu źródłowego dla `CSimpleStringT::SetString` (znajdujący się w atlsimpstr.h).

##  <a name="ctor"></a>  CSimpleStringT::CSimpleStringT

Konstruuje `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr);
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr);
CSimpleStringT(const CSimpleStringT& strSrc);
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw();
```

#### <a name="parameters"></a>Parametry

*strSrc*<br/>
Istniejące `CSimpleStringT` obiektu do skopiowania do tego `CSimpleStringT` obiektu.

*pchSrc*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, nie zakończenie wartością null.

*pszSrc*<br/>
Ciąg zakończony wartością null do skopiowania do tego `CSimpleStringT` obiektu.

*nLength*<br/>
Liczbę znaków w `pch`.

*pStringMgr*<br/>
Wskaźnik do Menedżera pamięci `CSimpleStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CSimpleStringT`, zobacz [zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="remarks"></a>Uwagi

Utworzyć nową `CSimpleStringT` obiektu. Ponieważ konstruktory kopiować dane wejściowe do nowego magazynu przydzielone, może spowodować wyjątki pamięci.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::CSimpleStringT` przy użyciu ATL **typedef** `CSimpleString`. `CSimpleString` jest często używane specjalizacją szablonu klasy `CSimpleStringT`.

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

##  <a name="empty"></a>  CSimpleStringT::Empty

Sprawia to, że `CSimpleStringT` obiektu ciąg pusty i zwalnia pamięć zgodnie z potrzebami.

### <a name="syntax"></a>Składnia

```
void Empty() throw();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [ciągów: Cstring — Oczyszczanie wyjątku](../cstring-exception-cleanup.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::Empty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="freeextra"></a>  CSimpleStringT::FreeExtra

Zwalnia wszelkie dodatkowe pamięci uprzednio przydzielonej przez ciąg znaków, ale nie będą już potrzebne.

### <a name="syntax"></a>Składnia

```
void FreeExtra();
```

### <a name="remarks"></a>Uwagi

To powinno zmniejszyć obciążenie pamięci używane przez obiekt string. Metoda przydzieli bufor do dokładną długość zwróconych przez [GetLength](#getlength).

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

Dane wyjściowe z tego przykładu jest następująca:

```Output
Alloc length is 1031, String length is 1024
Alloc length is 1031, String length is 15
Alloc length is 15, String length is 15
```

##  <a name="getalloclength"></a>  CSimpleStringT::GetAllocLength

Pobiera długość przydzielonego `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
int GetAllocLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków przydzielonych do tego obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu określenia liczby znaków przydzielony dla tej `CSimpleStringT` obiektu. Zobacz [FreeExtra](#freeextra) przykład wywołaniu tej funkcji.

##  <a name="getat"></a>  CSimpleStringT::GetAt

Zwraca jeden znak ze zbioru `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
XCHAR GetAt(int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w `CSimpleStringT` obiektu. *IChar* parametr musi być większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [GetLength](#getlength). W przeciwnym razie `GetAt` wygeneruje wyjątek.

### <a name="return-value"></a>Wartość zwracana

`XCHAR` Zawierającą znak w określonej pozycji w ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić jeden znak określony przez *iChar*. Przeciążona indeksu dolnego (**[]**) operator jest wygodne alias dla `GetAt`. Terminator o wartości null jest adresowalne bez generowania wyjątku przy użyciu `GetAt`. Jednak nie jest liczony przez `GetLength`, i wartość zwracana jest 0.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje sposób użycia `CSimpleStringT::GetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```

##  <a name="getbuffer"></a>  CSimpleStringT::GetBuffer

Zwraca wskaźnik do buforu wewnętrznego znaków dla `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
PXSTR GetBuffer(int nMinBufferLength);
PXSTR GetBuffer();
```

#### <a name="parameters"></a>Parametry

*nMinBufferLength*<br/>
Minimalna liczba znaków, które mogą pomieścić buforu znaków. Ta wartość nie obejmuje miejsca dla terminator o wartości null.

Jeśli *nMinBufferLength* jest większa niż długość bieżącego buforu `GetBuffer` niszczy bieżącego buforu, zastępuje go znakiem bufor żądany rozmiar i resetuje licznik odwołań obiektu od zera. Jeśli wcześniej o nazwie [LockBuffer](#lockbuffer) dla tego buforu utracisz blokady buforu.

### <a name="return-value"></a>Wartość zwracana

`PXSTR` Wskaźnik do buforu znaków (zakończony znakiem null) obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zwrócić zawartość buforu `CSimpleStringT` obiektu. Zwrócony `PXSTR` nie jest stałą i w związku z tym umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartość.

Jeśli używasz zwrócony przez wskaźnik `GetBuffer` do zmiany zawartości ciągu, należy wywołać [ReleaseBuffer](#releasebuffer) przed użyciem wszelkich innych `CSimpleStringT` metody elementu członkowskiego.

Zwrócony przez adres `GetBuffer` mogą stać się nieprawidłowe po wywołaniu `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacji może spowodować, że `CSimpleStringT` buforu odbiorczego. Nie alokowaniu buforu, jeśli nie zmienisz długość `CSimpleStringT`.

Pamięć buforu jest automatycznie zwolniony, kiedy `CSimpleStringT` niszczony jest obiekt.

Śledzenie bieżącego długość ciągu samodzielnie, nie należy dołączać kończącego znaku null. Jednak należy określić długość ciągu końcowego podczas zwalniania bufora z `ReleaseBuffer`. Jeśli dołączasz kończącego znaku null, należy przekazać wartość -1 (ustawienie domyślne) dla długości. `ReleaseBuffer` Określa długość buforu.

Jeśli pamięć jest niewystarczająca do zaspokojenia `GetBuffer` żądania, ta metoda wyrzuca CMemoryException *.

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

##  <a name="getbuffersetlength"></a>  CSimpleStringT::GetBufferSetLength

Zwraca wskaźnik do buforu wewnętrznego znaków dla `CSimpleStringT` obiektu, obcinanie lub jej długość rośnie, jeśli to konieczne dokładnie dopasować długość określona w *nLength*.

### <a name="syntax"></a>Składnia

```
PXSTR GetBufferSetLength(int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Dokładny rozmiar `CSimpleStringT` znak buforu w znakach.

### <a name="return-value"></a>Wartość zwracana

A `PXSTR` wskaźnik do buforu znaków (zakończony znakiem null) obiektu.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody można pobrać określonej długości wewnętrznego buforu elementu `CSimpleStringT` obiektu. Zwrócony `PXSTR` wskaźnik nie jest **const** i w związku z tym umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartość.

Jeśli używasz zwrócony przez wskaźnik [GetBufferSetLength](#getbuffersetlength) do zmiany zawartości ciągu, należy wywołać `ReleaseBuffer` można zaktualizować stanu wewnętrznego `CsimpleStringT` przed użyciem wszelkich innych `CSimpleStringT` metody.

Zwrócony przez adres `GetBufferSetLength` mogą stać się nieprawidłowe po wywołaniu `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacji może spowodować, że `CSimpleStringT` buforu odbiorczego. Bufor nie jest ponownie przypisywany Jeśli długość nie należy zmieniać `CSimpleStringT`.

Pamięć buforu jest automatycznie zwolniony, kiedy `CSimpleStringT` niszczony jest obiekt.

Jeśli śledzenie bieżącego długość ciągu samodzielnie, nie dołączaj kończącego znaku null. Należy określić długość ciągu końcowego podczas zwalniania bufora przy użyciu `ReleaseBuffer`. Jeśli dołączasz kończącego znaku null podczas wywoływania `ReleaseBuffer`, przekazać wartość -1 (opcja domyślna) do długości do `ReleaseBuffer`, i `ReleaseBuffer` wykona `strlen` dla buforu, aby ustalić jego długość.

Aby uzyskać więcej informacji na temat zliczanie odwołań zobacz następujące artykuły:

- [Zarządzanie czasów istnienia obiektów za pomocą zliczanie odwołań](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) w Windows SDK.

- [Implementowanie zliczanie odwołań](/windows/desktop/com/implementing-reference-counting) w Windows SDK.

- [Zasady zarządzania odwołań](/windows/desktop/com/rules-for-managing-reference-counts) w Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::GetBufferSetLength`.

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

##  <a name="getlength"></a>  CSimpleStringT::GetLength

Zwraca liczbę znaków w `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
int GetLength() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby wrócić liczbę znaków w obiekcie. Liczba nie obejmuje terminator o wartości null.

Dla znaków wielobajtowych zestawów znaków (MBCS) `GetLength` liczby poszczególnych 8-bitowych znaków; oznacza to, potencjalny klienta i szlak bajtów w jeden znak wielobajtowy są liczone jako dwa bajty. Zobacz [FreeExtra](#freeextra) przykład wywołaniu tej funkcji.

##  <a name="getmanager"></a>  CSimpleStringT::GetManager

Pobiera Menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
IAtlStringMgr* GetManager() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do Menedżera pamięci `CSimpleStringT` obiektu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu pobrania pamięci używane przez menedżera `CSimpleStringT` obiektu. Aby uzyskać więcej informacji na temat menedżerów zarządzania pamięcią i obiektów w postaci ciągów, zobacz [zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

##  <a name="getstring"></a>  CSimpleStringT::GetString

Pobiera ciąg znaków.

### <a name="syntax"></a>Składnia

```
PCXSTR GetString() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do ciągu zakończonego znakiem null.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody można pobrać ciągu znaków skojarzonego z `CSimpleStringT` obiektu.

> [!NOTE]
>  Zwrócony `PCXSTR` wskaźnik jest **const** i nie zezwala na bezpośrednie modyfikowanie `CSimpleStringT` zawartość.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::GetString`.

```cpp
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```

##  <a name="isempty"></a>  CSimpleStringT::IsEmpty

Testy `CSimpleStringT` obiektu pusty warunku.

### <a name="syntax"></a>Składnia

```
bool IsEmpty() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli `CSimpleStringT` obiekt ma 0 długość; w przeciwnym razie wartość FALSE.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby określić, czy obiekt zawiera pusty ciąg.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::IsEmpty`.

```cpp
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```

##  <a name="lockbuffer"></a>  CSimpleStringT::LockBuffer

Wyłącza zliczaniu odwołań i chroni ciąg znaków w buforze.

### <a name="syntax"></a>Składnia

```
PXSTR LockBuffer();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do `CSimpleStringT` obiektu lub ciąg przerwany wartością null.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody do blokowania bufora o `CSimpleStringT` obiektu. Przez wywołanie metody `LockBuffer`, Utwórz kopię ciąg, z -1 dla licznika odwołań. Gdy wartość liczebności referencyjnej jest wartość -1, ciąg znaków w buforze uznaje się być w stanie "zablokowanym". Znajduje się w stanie zablokowanym, ciąg jest chroniony na dwa sposoby:

- Nie ciąg znaków można uzyskać odwołanie do danych w ciągu zablokowany, nawet, jeśli ten ciąg jest przypisany do zablokowanej ciągu.

- Zablokowane ciąg nigdy nie będzie odwoływać inny ciąg, nawet jeśli te inne parametry są kopiowane do ciągu zablokowane.

Blokowanie ciąg znaków w buforze, pewność, wyłącznego wstrzymanie bufor ciągu pozostaną nienaruszone.

Po zakończeniu za pomocą `LockBuffer`, wywołaj [UnlockBuffer](#unlockbuffer) zresetować licznik odwołań do 1.

> [!NOTE]
>  Jeśli wywołasz [getbuffer —](#getbuffer) na zablokowanym buforu, należy ustawić `GetBuffer` parametr `nMinBufferLength` na wartość większą niż długość buforu bieżący, spowoduje utratę blokady buforu. Wywołanie do `GetBuffer` niszczy bieżącego buforu, zastępuje go znakiem bufor żądany rozmiar i resetuje licznik odwołań do zera.

Aby uzyskać więcej informacji na temat zliczanie odwołań zobacz następujące artykuły:

- [Zarządzanie czasów istnienia obiektów za pomocą zliczanie odwołań](/windows/desktop/com/managing-object-lifetimes-through-reference-counting) w Windows SDK

- [Implementowanie zliczanie odwołań](/windows/desktop/com/implementing-reference-counting) w Windows SDK

- [Zasady zarządzania odwołań](/windows/desktop/com/rules-for-managing-reference-counts) w Windows SDK

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::LockBuffer`.

```cpp
CSimpleString str(_T("Hello"), pMgr);
TCHAR ch;

str.LockBuffer();
ch = str.GetAt(2);
_tprintf_s(_T("%c"), ch);
str.UnlockBuffer();
```

##  <a name="operator_at"></a>  CSimpleStringT::operator\[\]

Wywołaj tę funkcję, aby dostęp do pojedynczego znaku w tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążona indeksu dolnego (**[]**) operator zwraca pojedynczy znak określony przez liczony od zera indeks w *iChar*. Ten operator jest wygodne zastępuje [GetAt](#getat) funkcja elementu członkowskiego.

> [!NOTE]
>  Można użyć indeksu dolnego (**[]**) operator, aby uzyskać wartość znaku w `CSimpleStringT`, można użyć, aby zmienić wartość znaku w `CSimpleStringT`.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::operator []`.

```cpp
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```

## <a name="operator_at"></a>  CSimpleStringT::operator \[\]

Wywołaj tę funkcję, aby dostęp do pojedynczego znaku w tablicy znaków.

### <a name="syntax"></a>Składnia

```
XCHAR operator[](int iChar) const;
```

### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w ciągu.

### <a name="remarks"></a>Uwagi

Przeciążona indeksu dolnego (**[]**) operator zwraca pojedynczy znak określony przez liczony od zera indeks w *iChar*. Ten operator jest wygodne zastępuje [GetAt](#getat) funkcja elementu członkowskiego.

> [!NOTE]
>  Można użyć indeksu dolnego (**[]**) operator, aby uzyskać wartość znaku w `CSimpleStringT`, można użyć, aby zmienić wartość znaku w `CSimpleStringT`.

##  <a name="operator_add_eq"></a>  CSimpleStringT::operator +=

Dołącza nowy ciąg lub znak na końcu istniejącego ciągu.

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
Znak, który ma zostać dołączona.

### <a name="remarks"></a>Uwagi

Operator akceptuje innego `CSimpleStringT` obiektu lub znaku. Należy pamiętać, że pamięć wyjątków może wystąpić, gdy możesz użyć tego operatora łączenia, ponieważ nowy magazyn może zostać przydzielona dla znaków dodane do tego `CSimpleStringT` obiektu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::operator +=`.

```cpp
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```

##  <a name="operator_eq"></a>  CSimpleStringT::operator =

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

Jeśli ciąg docelowy (lewa strona) jest już wystarczająco duży, aby przechowywać dane o nowej, jest wykonywane nie nowe alokacji pamięci. Należy pamiętać, że pamięć wyjątki mogą wystąpić przy każdym użyciu operatora przypisania, ponieważ nowy magazyn często jest przeznaczona do przechowywania, wynikowy `CSimpleStringT` obiektu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::operator =`.

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

##  <a name="operator_pcxstr"></a>  CSimpleStringT::operator PCXSTR

Bezpośrednio uzyskuje dostęp do znaków przechowywanych w `CSimpleStringT` obiektu jako ciąg stylu C.

### <a name="syntax"></a>Składnia

```
operator PCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik znaku do danych ciągu.

### <a name="remarks"></a>Uwagi

Żadne znaki nie są kopiowane; zwracany jest tylko wskaźnikiem. Należy zachować ostrożność przy użyciu tego operatora. Jeśli zmienisz `CString` obiektu po uzyskaniu wskaźnik znaku, może spowodować ponowne przydzielenie pamięci, która unieważnia wskaźnika.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::operator PCXSTR`.

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

##  <a name="pcxstr"></a>  CSimpleStringT::PCXSTR

Wskaźnik ze stałym ciągiem.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;
```

##  <a name="preallocate"></a>  CSimpleStringT::Preallocate

Przydziela określonej ilości bajtów `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void Preallocate( int nLength);
```

#### <a name="parameters"></a>Parametry

*nLength*<br/>
Dokładny rozmiar `CSimpleStringT` znak buforu w znakach.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody można przydzielić rozmiar buforu określonego `CSimpleStringT` obiektu.

`CSimpleStringT` generuje wyjątek STATUS_NO_MEMORY, jeśli nie można przydzielić obszaru do buforu znaków. Domyślnie, Alokacja pamięci odbywa się przez funkcji WIN32 API `HeapAlloc` lub `HeapReAlloc`.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::Preallocate`.

```cpp
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```

##  <a name="pxstr"></a>  CSimpleStringT::PXSTR

Wskaźnik do ciągu.

### <a name="syntax"></a>Składnia

```
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;
```

##  <a name="releasebuffer"></a>  CSimpleStringT::ReleaseBuffer

Zwalnia kontrolę nad bufor przydzielony za [getbuffer —](#getbuffer).

### <a name="syntax"></a>Składnia

```
void ReleaseBuffer(int nNewLength = -1);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Długość nowego ciągu znaków, nie licząc zamykającego terminator o wartości null. Jeśli ten ciąg ma wartość null, zakończone, ustawia wartość domyślna-1 `CSimpleStringT` rozmiar do bieżącego długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę w celu ponownego przydzielenia lub zwolnienia buforu z obiektem ciągu. Jeśli wiesz, że ciąg w buforze jest zakończony wartością null, można pominąć *nNewLength* argumentu. Jeśli parametry usługi nie ma wartości null, zakończone, użyj *nNewLength* do określenia jego długość. Zwrócony przez adres [getbuffer —](#getbuffer) będzie nieprawidłowe po wywołaniu `ReleaseBuffer` lub innych `CSimpleStringT` operacji.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::ReleaseBuffer`.

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

##  <a name="releasebuffersetlength"></a>  CSimpleStringT::ReleaseBufferSetLength

Zwalnia kontrolę nad bufor przydzielony za [getbuffer —](#getbuffer).

### <a name="syntax"></a>Składnia

```
void ReleaseBufferSetLength(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Długość ciągu, zostały udostępnione

### <a name="remarks"></a>Uwagi

Ta funkcja jest podobne do [ReleaseBuffer](#releasebuffer) z tą różnicą, że prawidłową długość dla obiektu string muszą być przekazywane.

##  <a name="setat"></a>  CSimpleStringT::SetAt

Ustawia pojedynczy znak z `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void SetAt(int iChar, XCHAR ch);
```

#### <a name="parameters"></a>Parametry

*iChar*<br/>
Liczony od zera indeks znaku w `CSimpleStringT` obiektu. *IChar* parametr musi być większa lub równa 0 i mniejsza niż wartość zwrócona przez obiekt [GetLength](#getlength).

*ch*<br/>
Znak nowego.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zastąpić znak znajdujący się w *iChar*. Ta metoda nie spowoduje powiększenie ciągu, jeśli *iChar* wykracza poza granice istniejących parametrów.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::SetAt`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
```

##  <a name="setmanager"></a>  CSimpleStringT::SetManager

Określa Menedżera pamięci `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void SetManager(IAtlStringMgr* pStringMgr);
```

#### <a name="parameters"></a>Parametry

*pStringMgr*<br/>
Wskaźnik do nowego Menedżera pamięci.

### <a name="remarks"></a>Uwagi

Wywołanie tej metody, aby określić nową pamięć używana przez menedżera `CSimpleStringT` obiektu. Aby uzyskać więcej informacji na temat menedżerów zarządzania pamięcią i obiektów w postaci ciągów, zobacz [zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::SetManager`.

```cpp
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```

##  <a name="setstring"></a>  CSimpleStringT::SetString

Ustawia ciąg `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void SetString(PCXSTR pszSrc, int nLength);
void SetString(PCXSTR pszSrc);
```

#### <a name="parameters"></a>Parametry

*pszSrc*<br/>
Wskaźnik na ciąg zakończony znakiem null.

*nLength*<br/>
Liczbę znaków w *pszSrc*.

### <a name="remarks"></a>Uwagi

Skopiuj ciąg do `CSimpleStringT` obiektu. `SetString` zastępuje starsze dane ciągu w buforze.

Obie wersje `SetString` Sprawdź, czy *pszSrc* jest wskaźnikiem typu null, a jeśli tak jest, należy zgłosić błąd E_INVALIDARG.

Jeden parametr wersję `SetString` oczekuje *pszSrc* wskaż ciąg zakończony znakiem null.

Parametr dwóch wersję `SetString` oczekuje również *pszSrc* oczekiwany jest ciąg zakończony znakiem null. Używa ona *nLength* jako długość ciągu, chyba że najpierw napotka terminator o wartości null.

Parametr dwóch wersję `SetString` sprawdza również, czy *pszSrc* wskazuje na lokalizację w bieżącym buforze w `CSimpleStringT`. W tym przypadku specjalne `SetString` korzysta z funkcji kopiowania pamięci, która nie zastąpi dane ciągu zgodnie z kopiuje dane ciągu do buforu.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::SetString`.

```cpp
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(_tcscmp(s, _T("abcdef")) == 0);
s.SetString(_T("Soccer"), 6);
ASSERT(_tcscmp(s, _T("Soccer")) == 0);
```

##  <a name="stringlength"></a>  CSimpleStringT::StringLength

Zwraca liczbę znaków w określonym ciągu.

### <a name="syntax"></a>Składnia

```
ATL_NOINLINE static int StringLength(PCXSTR psz) throw();
```

#### <a name="parameters"></a>Parametry

*psz*<br/>
Wskaźnik na ciąg zakończony znakiem null.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków w *psz*; nie licząc zamykającego terminator o wartości null.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby pobrać liczbę znaków w ciągu wskazywany przez *psz*.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::StringLength`.

```cpp
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
```

##  <a name="truncate"></a>  CSimpleStringT::Truncate

Obcina ciąg do nowej długości.

### <a name="syntax"></a>Składnia

```
void Truncate(int nNewLength);
```

#### <a name="parameters"></a>Parametry

*nNewLength*<br/>
Nowe długość ciągu.

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby obciąć zawartość ciągu do nowej długości.

> [!NOTE]
>  Nie ma to wpływu na długość przydzielonego buforu. Aby zmniejszyć lub zwiększyć bieżącego buforu, zobacz [FreeExtra](#freeextra) i [Preallocate](#preallocate).

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CSimpleStringT::Truncate`.

```cpp
CSimpleString str(_T("abcdefghi"), pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
str.Truncate(4);
_tprintf_s(_T("Allocated length: %d\n"), str.GetLength());
_tprintf_s(_T("Contents: %s\n"), str);
```

##  <a name="unlockbuffer"></a>  CSimpleStringT::UnlockBuffer

Odblokowuje bufor o `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
void UnlockBuffer() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zresetować licznik odwołań w ciągu 1.

`CSimpleStringT` Destruktor automatycznie wywołuje `UnlockBuffer` aby upewnić się, że bufor nie jest zablokowany, po wywołaniu destruktora. Aby uzyskać przykład tej metody, zobacz [LockBuffer](#lockbuffer).

##  <a name="dtor"></a>  CSimpleStringT:: ~ CSimpleStringT

Niszczy `CSimpleStringT` obiektu.

### <a name="syntax"></a>Składnia

```
~CSimpleStringT() throw();
```

### <a name="remarks"></a>Uwagi

Wywołaj tę metodę, aby zniszczyć `CSimpleStringT` obiektu.

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)
