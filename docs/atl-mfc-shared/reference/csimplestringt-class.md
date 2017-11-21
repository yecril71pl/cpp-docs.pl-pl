---
title: Klasa CSimpleStringT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
helpviewer_keywords:
- shared classes, CSimpleStringT
- strings [C++], ATL class
- CSimpleStringT class
ms.assetid: 15814fcb-5b8f-4425-a97e-3b61fc9b48d8
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 27f163b76d037ca91330890c7d38c37c182b6b1b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="csimplestringt-class"></a>Klasa CSimpleStringT
Ta klasa reprezentuje `CSimpleStringT` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```
template <typename BaseType>
class CSimpleStringT
```  
  
### <a name="parameters"></a>Parametry  
 `BaseType`  
 Znak typu klasy ciągu. Może to być jedna z następujących czynności:  
  
- `char`(dla ciągów znaków ANSI).  
  
- `wchar_t`(dla ciągów znaków Unicode).  
  
- **Tchar —** (w przypadku zarówno ANSI i Unicode ciągi znaków).  

## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-typedefs"></a>Definicje typów publicznych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleStringT::PCXSTR](#pcxstr)|Wskaźnik ze stałym ciągiem.|  
|[CSimpleStringT::PXSTR](#pxstr)|Wskaźnik do ciągu.|  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleStringT::CSimpleStringT](#ctor)|Konstruuje `CSimpleStringT` obiektów na różne sposoby.|  
|[CSimpleStringT:: ~ CSimpleStringT](#dtor)|Destruktor.|  

  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleStringT::Append](#append)|Dołącza `CSimpleStringT` obiektu do istniejącego `CSimpleStringT` obiektu.|  
|[CSimpleStringT::AppendChar](#appendchar)|Dołącza znak do istniejącej `CSimpleStringT` obiektu.|  
|[CSimpleStringT::CopyChars](#copychars)|Kopiuje znaki do innego ciągu.|  
|[CSimpleStringT::CopyCharsOverlapped](#copycharsoverlapped)|Kopiuje znaki na inny ciąg nakładają się buforów.|  
|[CSimpleStringT::Empty](#empty)|Wymusza ciąg, aby mieć długości zerowej.|  
|[CSimpleStringT::FreeExtra](#freeextra)|Zwalnia wszelkie dodatkową pamięć przydzielona wcześniej przez z obiektem ciągu.|  
|[CSimpleStringT::GetAllocLength](#getalloclength)|Pobiera długość przydzielone `CSimpleStringT` obiektu.|  
|[CSimpleStringT::GetAt](#getat)|Zwraca znak na określonej pozycji.|  
|[CSimpleStringT::GetBuffer](#getbuffer)|Zwraca wskaźnik do znaków w `CSimpleStringT`.|  
|[CSimpleStringT::GetBufferSetLength](#getbuffersetlength)|Zwraca wskaźnik do znaków w `CSimpleStringT`, obcinanie do określonej długości.|  
|[CSimpleStringT::GetLength](#getlength)|Zwraca liczbę znaków w `CSimpleStringT` obiektu.|  
|[CSimpleStringT::GetManager](#getmanager)|Pobiera Menedżera pamięci `CSimpleStringT` obiektu.|  
|[CSimpleStringT::GetString](#getstring)|Pobiera ciąg znaków|  
|[CSimpleStringT::IsEmpty](#isempty)|Testy czy `CSimpleStringT` obiekt nie zawiera znaków.|  
|[CSimpleStringT::LockBuffer](#lockbuffer)|Powoduje wyłączenie liczenie odwołań i chronione w buforze ciągu.|  
|[CSimpleStringT::Preallocate](#preallocate)|Przydziela określoną ilością pamięci dla buforu znaków.|  
|[CSimpleStringT::ReleaseBuffer](#releasebuffer)|Zwalnia kontroli buforu zwrócony przez `GetBuffer`.|  
|[CSimpleStringT::ReleaseBufferSetLength](#releasebuffersetlength)|Zwalnia kontroli buforu zwrócony przez `GetBuffer`.|  
|[CSimpleStringT::SetAt](#setat)|Ustawia znak na określonej pozycji.|  
|[CSimpleStringT::SetManager](#setmanager)|Ustawia Menedżera pamięci `CSimpleStringT` obiektu.|  
|[CSimpleStringT::SetString](#setstring)|Ustawia ciąg `CSimpleStringT` obiektu.|  
|[CSimpleStringT::StringLength](#stringlength)|Zwraca liczbę znaków w określonym ciągu.|  
|[CSimpleStringT::Truncate](#truncate)|Obcina ciąg do określonej długości.|  
|[CSimpleStringT::UnlockBuffer](#unlockbuffer)|Zapewnia liczenie odwołań i zwalnia ciągu w buforze.|  

### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CSimpleStringT::operator PCXSTR](#operator_pcxstr)|Bezpośredni dostęp do znaków przechowywanych w `CSimpleStringT` obiekt jako ciąg w stylu języka C.|  
|[CSimpleStringT::operator\[\]](#operator_at)|Zwraca znak na określonej pozycji — operator podstawienia dla `GetAt`.|  
|[CSimpleStringT::operator +=](#operator_add_eq)|Łączy nowy ciąg na końcu istniejących parametrów.|  
|[CSimpleStringT::operator =](#operator_eq)|Przypisuje nową wartość do `CSimpleStringT` obiektu.|  
  
### <a name="remarks"></a>Uwagi  
 `CSimpleStringT`jest klasą bazową dla różnych klas ciągu obsługiwane przez Visual C++. Zarządzanie pamięcią obiekt ciągu i manipulowanie buforem podstawowe go zapewnia obsługę minimalny. Dla obiektów ciąg bardziej zaawansowanych, zobacz [CStringT klasy](../../atl-mfc-shared/reference/cstringt-class.md).  
  
### <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlsimpstr.h  


## <a name="append"></a>CSimpleStringT::Append
Dołącza `CSimpleStringT` obiektu do istniejącego `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void Append(const CSimpleStringT& strSrc); 
void Append(PCXSTR pszSrc, int nLength); 
void Append(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Parametry  
 `strSrc`  
 `CSimpleStringT` Obiektu do dołączenia.  
  
 `pszSrc`  
 Wskaźnik do ciąg zawierający znaki, które mają być dołączane.  
  
 `nLength`  
 Liczba znaków do dołączenia.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby dołączyć istniejącą `CSimpleStringT` obiektu do innego `CSimpleStringT` obiektu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::Append`.  
  
```cpp  
CSimpleString str1(pMgr), str2(pMgr);
str1.SetString(_T("Soccer is"));
str2.SetString(_T(" an elegant game"));
str1.Append(str2);
ASSERT(_tcscmp(str1, _T("Soccer is an elegant game")) == 0);
```
  
##  <a name="appendchar"></a>CSimpleStringT::AppendChar
Dołącza znak do istniejącej `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void AppendChar(XCHAR ch);
```  
#### <a name="parameters"></a>Parametry  
 *ch*  
 Znak do dołączenia  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej funkcji, aby dołączyć określony znak na końcu istniejące `CSimpleStringT` obiektu.  
  
##  <a name="copychars"></a>CSimpleStringT::CopyChars  
 Kopiuje znaki do `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
static void CopyChars(
  XCHAR* pchDest,
  const XCHAR* pchSrc, 
  int nChars) throw();
```  
#### <a name="parameters"></a>Parametry  
 `pchDest`  
 Wskaźnik do ciągu znaków.  
  
 `pchSrc`  
 Wskaźnik do ciąg zawierający znaki, które ma zostać skopiowany.  
  
 `nChars`  
 Liczba `pchSrc` znaków do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby skopiować znaków z `pchSrc` do `pchDest` ciągu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::CopyChars`.  
  
```cpp  
CSimpleString str(_T("xxxxxxxxxxxxxxxxxxx"), 20, pMgr);
TCHAR* pszSrc = _T("Hello world!");
_tprintf_s(_T("%s\n"), str);
str.CopyChars(str.GetBuffer(), pszSrc, 12);
_tprintf_s(_T("%s\n"), str);
```
  
##  <a name="copycharsoverlapped"></a>CSimpleStringT::CopyCharsOverlapped
Kopiuje znaki do `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
static void CopyCharsOverlapped(
  XCHAR* pchDest,
  const XCHAR* pchSrc,
  int nChars) throw(); 
```  
#### <a name="parameters"></a>Parametry  
 `pchDest`  
 Wskaźnik do ciągu znaków.  
  
 `pchSrc`  
 Wskaźnik do ciąg zawierający znaki, które ma zostać skopiowany.  
  
 `nChars`  
 Liczba `pchSrc` znaków do skopiowania.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby skopiować znaków z `pchSrc` do `pchDest` ciągu. W odróżnieniu od `CopyChars`, `CopyCharsOverlapped` udostępnia bezpieczne metody kopiowania z buforów znaków, które mogą być pokrywający się.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CSimpleStringT::CopyChars](#copychars), lub kod źródłowy `CSimpleStringT::SetString` (znajdujący się w atlsimpstr.h).  
  
##  <a name="ctor"></a>CSimpleStringT::CSimpleStringT  
 Konstruuje `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
CSimpleStringT(const XCHAR* pchSrc, int nLength, IAtlStringMgr* pStringMgr); 
CSimpleStringT(PCXSTR pszSrc, IAtlStringMgr* pStringMgr); 
CSimpleStringT(const CSimpleStringT& strSrc); 
explicit CSimpleStringT(IAtlStringMgr* pStringMgr) throw(); 
```  
#### <a name="parameters"></a>Parametry  
 `strSrc`  
 Istniejące `CSimpleStringT` obiekt ma zostać skopiowany do tego `CSimpleStringT` obiektu.  
  
 `pchSrc`  
 Wskaźnik do tablicy znaków o długości `nLength`, nie zakończenie wartością null.  
  
 `pszSrc`  
 Ciąg zakończony zerem, ma zostać skopiowany do tego `CSimpleStringT` obiektu.  
  
 `nLength`  
 Liczba liczba znaków w `pch`.  
  
 `pStringMgr`  
 Wskaźnik do Menedżera pamięci `CSimpleStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CSimpleStringT`, zobacz [zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).  
  
### <a name="remarks"></a>Uwagi  
 Utworzyć nową `CSimpleStringT` obiektu. Ponieważ konstruktorów skopiować dane wejściowe do nowego magazynu przydzielone, może spowodować wyjątki pamięci.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::CSimpleStringT` przy użyciu ATL `typedef` `CSimpleString`. `CSimpleString`jest często używane specjalizacja szablonu klasy `CSimpleStringT`.  
  
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

  
##  <a name="empty"></a>CSimpleStringT::Empty
Sprawia to, że `CSimpleStringT` obiektu pustego ciągu i zwolnić pamięć, zależnie od potrzeb.  
  
### <a name="syntax"></a>Składnia  
  
```  
void Empty() throw();  
```  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać więcej informacji, zobacz [ciągów: cstring — wyjątek oczyszczania](../cstring-exception-cleanup.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::Empty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());  
```  
  
##  <a name="freeextra"></a>CSimpleStringT::FreeExtra
Zwalnia wszelkie dodatkową pamięć przydzielona wcześniej przez ciąg, ale nie jest już potrzebne.  
  
### <a name="syntax"></a>Składnia  
  
```  
void FreeExtra(); 
```  
### <a name="remarks"></a>Uwagi  
 Powinno to zmniejszyć koszty pamięci używane przez z obiektem ciągu. Metoda przydziela ponownie bufor do dokładną długość zwróconych przez [GetLength](#getlength).  
  
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
 Dane wyjściowe w tym przykładzie ma następującą składnię:  
  
 `Alloc length is 1031, String length is 1024`  
  
 `Alloc length is 1031, String length is 15`  
  
 `Alloc length is 15, String length is 15`  
  
##  <a name="getalloclength"></a>CSimpleStringT::GetAllocLength  
Pobiera długość przydzielone `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
int GetAllocLength() const throw();  
```  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków przydzielonych do tego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby określić liczbę znaków przydzielone dla tego `CSimpleStringT` obiektu. Zobacz [FreeExtra](#freeextra) przykład wywołanie tej funkcji.  
  
##  <a name="getat"></a>CSimpleStringT::GetAt  
Zwraca jeden znak z `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
XCHAR GetAt(int iChar) const;
```  
#### <a name="parameters"></a>Parametry  
 `iChar`  
 Liczony od zera indeks znaku w `CSimpleStringT` obiektu. `iChar` Parametr musi być większa lub równa 0 i mniejsza niż wartość zwrócona przez [GetLength](#getlength). W przeciwnym razie `GetAt` wygeneruje wyjątek.  
  
### <a name="return-value"></a>Wartość zwracana  
 `XCHAR` Zawiera znak na określonej pozycji w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca jeden znak określony przez tę metodę należy wywołać `iChar`. Przeciążenia indeksu dolnego (`[]`) operator jest wygodne alias dla `GetAt`. Terminatorem null jest adresowana bez generowania wyjątku przy użyciu `GetAt`. Jednak nie jest traktowane przez `GetLength`, a wartość zwracana jest 0.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia `CSimpleStringT::GetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
ASSERT(s.GetAt(2) == _T('c'));
```
  
##  <a name="getbuffer"></a>CSimpleStringT::GetBuffer  
Zwraca wskaźnik do buforu wewnętrznego znaków dla `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
PXSTR GetBuffer(int nMinBufferLength); 
PXSTR GetBuffer();
```  
#### <a name="parameters"></a>Parametry  
 `nMinBufferLength`  
 Minimalna liczba znaków, które można zapisać w buforze znak. Ta wartość nie obejmuje miejsca dla terminatora o wartości null.  
  
 Jeśli `nMinBufferLength` jest większa niż długość buforu bieżącego `GetBuffer` niszczy bieżący bufor, zastępuje on buforu żądany rozmiar i resetuje liczba odwołań obiektu od zera. Jeśli wcześniej o nazwie [LockBuffer](#lockbuffer) na buforu, utracisz blokady buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `PXSTR` Wskaźnika do obiektu buforu znaków (zakończonym znakiem null).  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby zwrócić zawartość buforu `CSimpleStringT` obiektu. Zwrócona `PXSTR` nie jest stałą i w związku z tym umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartość.  
  
 Jeśli używasz zwrócony przez wskaźnik `GetBuffer` zmiany zawartości ciągu, należy wywołać [ReleaseBuffer](#releasebuffer) przed skorzystaniem z wszystkimi innymi `CSimpleStringT` metody elementu członkowskiego.  
  
 Zwrócony przez adres `GetBuffer` jest nieprawidłowy po wywołaniu `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacji może spowodować `CSimpleStringT` buforu odbiorczego. Bufor nie jest przydzielić, jeśli nie zmienisz długość `CSimpleStringT`.  
  
 Bufor pamięci jest automatycznie zwolniony, kiedy `CSimpleStringT` obiekt zostanie zniszczony.  
  
 Możesz zachować informacje o długości ciągu samodzielnie, nie należy dołączać znak końcowy null. Jednak należy określić długość ciągu końcowego podczas zwalniania bufora o `ReleaseBuffer`. Jeśli dołączyć znak końcowy null, należy przekazać wartość -1 (opcja domyślna) długości. `ReleaseBuffer`Określa długość buforu.  
  
 Jeśli jest za mało pamięci by spełnić `GetBuffer` poprosić, ta metoda zgłasza CMemoryException *.  
  
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
Zwraca wskaźnik do buforu wewnętrznego znaków dla `CSimpleStringT` obiektu, obcinanie lub jej długość rośnie, jeśli to konieczne dokładnie dopasować długości określonej w `nLength`.  
  
### <a name="syntax"></a>Składnia  
  
```  
PXSTR GetBufferSetLength(int nLength);
```  
#### <a name="parameters"></a>Parametry  
 `nLength`  
 Dokładny rozmiar `CSimpleStringT` buforu znak w znakach.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `PXSTR` wskaźnika do obiektu buforu znaków (zakończonym znakiem null).  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można pobrać określonej długości buforu wewnętrznego elementu `CSimpleStringT` obiektu. Zwrócona `PXSTR` wskaźnik nie jest `const` i w związku z tym umożliwia bezpośrednie modyfikowanie `CSimpleStringT` zawartość.  
  
 Jeśli używasz zwrócony przez wskaźnik [GetBufferSetLength](#getbuffersetlength) zmiany zawartości ciągu, wywołaj `ReleaseBuffer` zaktualizowany stan wewnętrzny `CsimpleStringT` przed skorzystaniem z wszystkimi innymi `CSimpleStringT` metody.  
  
 Zwrócony przez adres `GetBufferSetLength` jest nieprawidłowy po wywołaniu `ReleaseBuffer` ponieważ dodatkowe `CSimpleStringT` operacji może spowodować `CSimpleStringT` buforu odbiorczego. Bufor nie jest przypisane, jeśli nie zmienisz długość `CSimpleStringT`.  
  
 Bufor pamięci jest automatycznie zwolniony, kiedy `CSimpleStringT` obiekt zostanie zniszczony.  
  
 Jeśli możesz zachować informacje o długości ciągu samodzielnie, nie nie dodają znak końcowy null. Długość ciągu końcowego należy określić podczas zwalniania bufora przy użyciu `ReleaseBuffer`. Jeśli Dołącz znak końcowy null podczas wywoływania `ReleaseBuffer`, podaj wartość -1 (opcja domyślna) dla długości do `ReleaseBuffer`, i `ReleaseBuffer` wykona `strlen` dla buforu, aby ustalić jego długość.  
  
 Aby uzyskać więcej informacji na temat liczenie odwołań zobacz następujące artykuły:  
  
- [Zarządzanie okresy istnienia obiektu przez liczenie odwołań w](http://msdn.microsoft.com/library/windows/desktop/ms687260) w systemie Windows SDK. 
  
- [Implementowanie liczenie odwołań w](http://msdn.microsoft.com/library/windows/desktop/ms693431) w systemie Windows SDK.
  
- [Zasady zarządzania liczby odwołań](http://msdn.microsoft.com/library/windows/desktop/ms692481) w systemie Windows SDK.  
  
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
  
##  <a name="getlength"></a>CSimpleStringT::GetLength  
Zwraca liczbę znaków w `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
int GetLength() const throw();  
```  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby zwrócić liczbę znaków w obiekcie. Liczba nie obejmuje terminatorem null.  
  
 Dla zestawy znaków wielobajtowych (MBCS) `GetLength` liczby 8-bitową znaku; oznacza to, potencjalnych klientów i dziennik bajtami poszczególnych znaków wielobajtowych jeden są liczone jako dwa bajty. Zobacz [FreeExtra](#freeextra) przykład wywołanie tej funkcji.  
  
##  <a name="getmanager"></a>CSimpleStringT::GetManager  
Pobiera Menedżera pamięci `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
IAtlStringMgr* GetManager() const throw();  
```  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do Menedżera pamięci dla `CSimpleStringT` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można pobrać pamięci używane przez menedżera `CSimpleStringT` obiektu. Aby uzyskać więcej informacji na ciąg obiektów i menedżerów zarządzania pamięcią, zobacz [zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).  
  
##  <a name="getstring"></a>CSimpleStringT::GetString
Pobiera ciąg znaków.  
  
### <a name="syntax"></a>Składnia  
  
```  
PCXSTR GetString() const throw();
```  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik na ciąg znaków zakończony znakiem null.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można pobrać ciągu znaków skojarzone z `CSimpleStringT` obiektu.  
  
> [!NOTE]
>  Zwrócona `PCXSTR` wskaźnika jest `const` i nie zezwala na bezpośrednie modyfikowanie `CSimpleStringT` zawartość.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::GetString`.  
  
```cpp  
CSimpleString str(pMgr);
str += _T("Cup soccer is best!");
_tprintf_s(_T("%s"), str.GetString());
```
  
##  <a name="isempty"></a>CSimpleStringT::IsEmpty  
Testy `CSimpleStringT` obiektu pusty warunku.  
  
### <a name="syntax"></a>Składnia  
  
```  
bool IsEmpty() const throw();  
```  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli `CSimpleStringT` obiekt ma długość 0; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę w celu określenia, czy obiekt zawiera pusty ciąg.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::IsEmpty`.  
  
```cpp  
CSimpleString s(pMgr);
ASSERT(s.IsEmpty());
```
  
##  <a name="lockbuffer"></a>CSimpleStringT::LockBuffer  
Powoduje wyłączenie liczenie odwołań i chronione w buforze ciągu.  
  
### <a name="syntax"></a>Składnia  
  
```  
PXSTR LockBuffer();
```  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do `CSimpleStringT` obiektu lub ciąg znaków zakończony znakiem null.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody do blokowania bufora o `CSimpleStringT` obiektu. Wywołując `LockBuffer`, Utwórz kopię ciągu znaków na -1 dla liczebności referencyjnej. Jeśli wartość liczebności referencyjnej jest wartość -1, ciąg w buforze uważa się w stanie "zablokowanym". Znajduje się w stanie zablokowanym, ten ciąg jest chroniony na dwa sposoby:  
  
-   Ciąg nie może odwołać się do danych w ciągu zablokowane, nawet jeśli ten ciąg jest przypisany do zablokowanej ciągu.  
  
-   Zablokowane ciąg nigdy nie będzie odwoływać innego ciągu, nawet jeśli ten ciąg znaków zostanie skopiowany do zablokowanej ciągu.  
  
 Blokowanie ciąg w buforze, upewnij, ciąg wyłącznego wstrzymanie buforu pozostaną nienaruszone.  
  
 Po zakończeniu `LockBuffer`, wywołaj [UnlockBuffer](#unlockbuffer) zresetować liczba odwołań do 1.  
  
> [!NOTE]
>  Jeśli należy wywołać [GetBuffer](#getbuffer) na zablokowanym buforu, należy ustawić `GetBuffer` parametr `nMinBufferLength` na wartość większą niż długość buforu bieżący, spowoduje utratę blokady buforu. Wywołanie do `GetBuffer` niszczy bieżący bufor, zastępuje on buforu żądany rozmiar i resetuje liczba odwołań do zera.  
  
 Aby uzyskać więcej informacji na temat liczenie odwołań zobacz następujące artykuły:  
  
- [Zarządzanie okresy istnienia obiektu przez liczenie odwołań w](http://msdn.microsoft.com/library/windows/desktop/ms687260) w systemie Windows SDK  
  
- [Implementowanie liczenie odwołań w](http://msdn.microsoft.com/library/windows/desktop/ms693431) w systemie Windows SDK  
  
- [Zasady zarządzania liczby odwołań](http://msdn.microsoft.com/library/windows/desktop/ms692481) w systemie Windows SDK  
  
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
  
##  <a name="operator_at"></a>CSimpleStringT::operator\[\]  
Wywołanie tej funkcji do pojedynczego znaku tablicy znaków.  
  
### <a name="syntax"></a>Składnia  
  
```  
XCHAR operator[](int iChar) const;
```  
#### <a name="parameters"></a>Parametry  
 `iChar`  
 Liczony od zera indeks znaku w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Przeciążenia indeksu dolnego (`[]`) zwraca pojedynczy znak określony przez ten liczony od zera indeks `iChar`. Ten operator jest wygodne zastępuje [GetAt](#getat) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Można użyć indeks dolny (`[]`) operatora, aby uzyskać wartość znaku w `CSimpleStringT`, można użyć, aby zmienić wartość znaku w `CSimpleStringT`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie **[CSimpleStringT::operator]**.  
  
```cpp  
CSimpleString s(_T("abc"), pMgr);
ASSERT(s[1] == _T('b'));
```
  
## <a name="operator_at"></a>CSimpleStringT::operator\[\]
Wywołanie tej funkcji do pojedynczego znaku tablicy znaków.  
  
### <a name="syntax"></a>Składnia  
  
```   
XCHAR operator[](int iChar) const;
```  
  
### <a name="parameters"></a>Parametry  
 `iChar`  
 Liczony od zera indeks znaku w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Przeciążenia indeksu dolnego (`[]`) zwraca pojedynczy znak określony przez ten liczony od zera indeks `iChar`. Ten operator jest wygodne zastępuje [GetAt](#getat) funkcję elementu członkowskiego.  
  
> [!NOTE]
>  Można użyć indeks dolny (`[]`) operatora, aby uzyskać wartość znaku w `CSimpleStringT`, można użyć, aby zmienić wartość znaku w `CSimpleStringT`.  
  
  
##  <a name="operator_add_eq"></a>CSimpleStringT::operator +=  
Dołącza nowy ciąg lub znak na końcu istniejących parametrów.  
  
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
 `pszSrc`  
 Wskaźnik do ciągu zakończonego wartością null.  
  
 `strSrc`  
 Wskaźnik do istniejącej `CSimpleStringT` obiektu.  
  
 *ch*  
 Znak do dołączenia.  
  
### <a name="remarks"></a>Uwagi  
 Operator akceptuje innego `CSimpleStringT` obiektu lub znak. Należy pamiętać, że pamięć wyjątki może wystąpić, gdy Użyj tego operatora łączenia, ponieważ nowego magazynu mogą być przydzielone znaków dodane do tego `CSimpleStringT` obiektu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie **CSimpleStringT::operator +=**.  
  
```cpp  
CSimpleString str(_T("abc"), pMgr);
ASSERT(_tcscmp((str += _T("def")), _T("abcdef")) == 0);
```
  
##  <a name="operator_eq"></a>CSimpleStringT::operator =  
Przypisuje nową wartość do `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
CSimpleStringT& operator =(PCXSTR pszSrc); 
CSimpleStringT& operator =(const CSimpleStringT& strSrc);
```  
#### <a name="parameters"></a>Parametry  
 `pszSrc`  
 Wskaźnik do ciągu zakończonego wartością null.  
  
 `strSrc`  
 Wskaźnik do istniejącej `CSimpleStringT` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli ciąg docelowego (po lewej stronie) jest już wystarczająco duże, aby zapisać nowe dane, jest wykonywane nie nowe alokacji pamięci. Należy pamiętać, że pamięć wyjątki zawsze, gdy używasz operator przypisania, ponieważ nowy magazyn jest często przydzielone do przechowywania powstałe w ten sposób `CSimpleStringT` obiektu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie **CSimpleStringT::operator =**.  
  
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
  
##  <a name="operator_pcxstr"></a>CSimpleStringT::operator PCXSTR  

 Bezpośredni dostęp do znaków przechowywanych w `CSimpleStringT` obiekt jako ciąg w stylu języka C.  
  
### <a name="syntax"></a>Składnia  
  
```  
operator PCXSTR() const throw();
```  
### <a name="return-value"></a>Wartość zwracana  
 Znak wskaźnikiem do danych ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Żadne znaki nie są kopiowane; zwracany jest tylko wskaźnik. Należy zachować ostrożność przy tego operatora. Jeśli zmienisz `CString` obiektu po uzyskaniu znak wskaźnika może spowodować ponowne przydzielenie pamięci, która unieważnia wskaźnika.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie **CSimpleStringT::operator PCXSTR**.  
  
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
  
##  <a name="pcxstr"></a>CSimpleStringT::PCXSTR
Wskaźnik ze stałym ciągiem.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef ChTraitsBase< BaseType >::PCXSTR PCXSTR;    
```  
##  <a name="preallocate"></a>CSimpleStringT::Preallocate  
Przydziela określonej ilości bajtów `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void Preallocate( int nLength);
```  
#### <a name="parameters"></a>Parametry  
 `nLength`  
 Dokładny rozmiar `CSimpleStringT` buforu znak w znakach.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można przydzielić rozmiar buforu określonych dla `CSimpleStringT` obiektu.  
  
 `CSimpleStringT`generuje `STATUS_NO_MEMORY` wyjątek, jeśli nie można przydzielić miejsce dla buforu znaków. Domyślnie, Alokacja pamięci odbywa się za pomocą funkcji WIN32 API `HeapAlloc` lub `HeapReAlloc`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::Preallocate`.  
  
```cpp  
CSimpleString str(pMgr);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
str.Preallocate(100);
_tprintf_s(_T("Allocated length: %d\n"), str.GetAllocLength());
```
  
##  <a name="pxstr"></a>CSimpleStringT::PXSTR  
Wskaźnik do ciągu.  
  
### <a name="syntax"></a>Składnia  
  
```  
typedef ChTraitsBase< BaseType >::PXSTR PXSTR;  
```  
##  <a name="releasebuffer"></a>CSimpleStringT::ReleaseBuffer  
Zwalnia kontrolę nad bufor przydzielony przez [GetBuffer](#getbuffer).  
  
### <a name="syntax"></a>Składnia  
  
```  
void ReleaseBuffer(int nNewLength = -1);
```  
#### <a name="parameters"></a>Parametry  
 `nNewLength`  
 Długość nowego ciągu w znaków, nie licząc terminatorem null. Jeśli ten ciąg ma wartość null, zakończone, wartość domyślna-1 ustawia `CSimpleStringT` rozmiar do bieżącej długości ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby ponowne przydzielenie lub zwolnij na nim buforu z obiektem ciągu. Jeśli wiesz, że w buforze ciągu jest zakończenie wartością null, można pominąć `nNewLength` argumentu. Jeśli na ciąg nie jest zerowa, zakończone, użyj `nNewLength` do określania długości. Zwrócony przez adres [GetBuffer](#getbuffer) jest nieprawidłowy po wywołaniu `ReleaseBuffer` lub innych `CSimpleStringT` operacji.  
  
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
  
##  <a name="releasebuffersetlength"></a>CSimpleStringT::ReleaseBufferSetLength

Zwalnia kontrolę nad bufor przydzielony przez [GetBuffer](#getbuffer).  
  
### <a name="syntax"></a>Składnia  
  
```  
void ReleaseBufferSetLength(int nNewLength);
```  
#### <a name="parameters"></a>Parametry  
 `nNewLength`  
 Długość ciągu zwalnianie  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest podobne do [ReleaseBuffer](#releasebuffer) z tą różnicą, że prawidłową długość dla obiekt string muszą być przekazywane.  
  
##  <a name="setat"></a>CSimpleStringT::SetAt  
Ustawia pojedynczy znak z `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void SetAt(int iChar, XCHAR ch);
```  
#### <a name="parameters"></a>Parametry  
 `iChar`  
 Liczony od zera indeks znaku w `CSimpleStringT` obiektu. `iChar` Parametr musi być większa lub równa 0 i mniejsza niż wartość zwrócona przez [GetLength](#getlength).  
  
 *ch*  
 Znak nowego.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby zastąpić znak znajdujący się w `iChar`. Ta metoda nie zostanie powiększony ciąg, jeśli `iChar` wykracza poza granice istniejące parametry.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::SetAt`.  
  
```cpp  
CSimpleString s(_T("abcdef"), pMgr);
s.SetAt(1, _T('a'));
ASSERT(_tcscmp(s, _T("aacdef")) == 0);
``` 
  
##  <a name="setmanager"></a>CSimpleStringT::SetManager  
Określa Menedżera pamięci `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void SetManager(IAtlStringMgr* pStringMgr);
```  
#### <a name="parameters"></a>Parametry  
 `pStringMgr`  
 Wskaźnik do nowego Menedżera pamięci.  
  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody do określenia nowej pamięci używane przez menedżera `CSimpleStringT` obiektu. Aby uzyskać więcej informacji na ciąg obiektów i menedżerów zarządzania pamięcią, zobacz [zarządzanie pamięcią i CStringT](../memory-management-with-cstringt.md).  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::SetManager`.  
  
```cpp  
CSimpleString s(pMgr);
s.SetManager(pCustomMgr);
```
  
##  <a name="setstring"></a>CSimpleStringT::SetString  
Ustawia ciąg `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void SetString(PCXSTR pszSrc, int nLength); 
void SetString(PCXSTR pszSrc);
```  
#### <a name="parameters"></a>Parametry  
 `pszSrc`  
 Wskaźnik do ciągu zakończonego wartością null.  
  
 `nLength`  
 Liczba liczba znaków w `pszSrc`.  
  
### <a name="remarks"></a>Uwagi  
 Kopiuj ciąg do `CSimpleStringT` obiektu. `SetString`zastępuje starsze dane ciągu w buforze.  
  
 Obie wersje `SetString` Sprawdź, czy `pszSrc` jest wskaźnika o wartości null, a jeśli tak jest, throw **E_INVALIDARG** błędu.  
  
 Wersja jeden parametr `SetString` oczekuje `pszSrc` wskaż ciąg znaków zakończony znakiem null.  
  
 Parametr dwóch wersji `SetString` również oczekuje `pszSrc` jako ciąg znaków zakończony znakiem null. Używa `nLength` jako długość ciągu, chyba że najpierw napotkania terminatorem null.  
  
 Parametr dwóch wersji `SetString` sprawdza również, czy `pszSrc` wskazuje lokalizację, w bieżącym buforze w `CSimpleStringT`. W tym przypadku specjalne `SetString` korzysta z funkcji kopiowania pamięci, który nie powoduje zastąpienia danych ciągu jako ciąg danych są kopiowane do swojego bufora.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::SetString`.  
  
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
 `psz`  
 Wskaźnik do ciągu zakończonego wartością null.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków w `psz`; bez uwzględnienia terminatorem null.  
  
### <a name="remarks"></a>Uwagi  
 Wywołaj tę metodę, aby pobrać liczbę znaków w ciągu wskazywana przez `psz`.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CSimpleStringT::StringLength`.  
  
```cpp  
ASSERT(CSimpleString::StringLength(_T("soccer")) == 6);
``` 
  
##  <a name="truncate"></a>CSimpleStringT::Truncate
Obcina ciąg do nowego długości.  
  
### <a name="syntax"></a>Składnia  
  
```  
void Truncate(int nNewLength);
```  
#### <a name="parameters"></a>Parametry  
 `nNewLength`  
 Nowe długość ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołać tę metodę do obcięcia zawartość do nowego długości ciągu.  
  
> [!NOTE]
>  Nie dotyczy to przydzielone długość buforu. Aby zmniejszyć lub zwiększyć bieżącego buforu, zobacz [FreeExtra](#freeextra) i [Preallocate](#preallocate).  
  
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
  
##  <a name="unlockbuffer"></a>CSimpleStringT::UnlockBuffer
 Odblokowuje bufor o `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
void UnlockBuffer() throw();
```  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody, aby przywrócić liczba odwołań w ciągu 1.  
  
 `CSimpleStringT` Destruktora automatycznie wywołuje `UnlockBuffer` aby upewnić się, że wywołanego destruktor bufor nie jest zablokowany. Na przykład tej metody, zobacz [LockBuffer](#lockbuffer).  
  
##  <a name="dtor"></a>CSimpleStringT:: ~ CSimpleStringT
Niszczy `CSimpleStringT` obiektu.  
  
### <a name="syntax"></a>Składnia  
  
```  
~CSimpleStringT() throw();
```  
### <a name="remarks"></a>Uwagi  
 Wywołanie tej metody można zniszczyć `CSimpleStringT` obiektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)