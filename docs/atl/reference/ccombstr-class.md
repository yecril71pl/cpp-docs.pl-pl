---
title: CComBSTR, klasa | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- BSTRs, wrapper
- CComBSTR class
- CComBSTR
ms.assetid: 8fea1879-a05e-47a5-a803-8dec60eaa534
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3b6bda561c1461053a3a835f1d42e72471346895
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="ccombstr-class"></a>CComBSTR, klasa
Ta klasa jest otoki dla `BSTR`s.  
  
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
|[CComBSTR::AppendBSTR](#appendbstr)|Dołącza `BSTR` do `m_str`.|  
|[CComBSTR::AppendBytes](#appendbytes)|Dołącza określoną liczbę bajtów do `m_str`.|  
|[CComBSTR::ArrayToBSTR](#arraytobstr)|Tworzy `BSTR` od pierwszego znaku każdy element parametru safearray i dołącza go do `CComBSTR` obiektu.|  
|[CComBSTR::AssignBSTR](#assignbstr)|Przypisuje `BSTR` do `m_str`.|  
|[CComBSTR::Attach](#attach)|Dołącza `BSTR` do `CComBSTR` obiektu.|  
|[CComBSTR::BSTRToArray](#bstrtoarray)|Tworzy safearray jednowymiarowa liczony od zera, w której każdy element tablicy jest znak z `CComBSTR` obiektu.|  
|[CComBSTR::ByteLength](#bytelength)|Zwraca długość `m_str` w bajtach.|  
|[CComBSTR::Copy](#copy)|Zwraca kopię `m_str`.|  
|[CComBSTR::CopyTo](#copyto)|Zwraca kopię `m_str` za pośrednictwem **[out]** parametru|  
|[CComBSTR::Detach](#detach)|Odłącza `m_str` z `CComBSTR` obiektu.|  
|[CComBSTR::Empty](#empty)|Zwalnia `m_str`.|  
|[CComBSTR::Length](#length)|Zwraca długość `m_str`.|  
|[CComBSTR::LoadString](#loadstring)|Ładuje zasobu ciągu.|  
|[CComBSTR::ReadFromStream](#readfromstream)|Ładunki `BSTR` obiektu ze strumienia.|  
|[CComBSTR::ToLower](#tolower)|Konwertuje ciąg na małe litery.|  
|[CComBSTR::ToUpper](#toupper)|Konwertuje ciąg na wielkie litery.|  
|[CComBSTR::WriteToStream](#writetostream)|Zapisuje `m_str` do strumienia.|  
  
### <a name="public-operators"></a>Operatory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComBSTR::operator BSTR](#operator_bstr)|Rzutowania `CComBSTR` do obiektu `BSTR`.|  
|[CComBSTR::operator!](#operator_not)|Zwraca `true` lub `false`w zależności od tego, czy `m_str`jest `NULL`.|  
|[CComBSTR::operator! =](#operator_neq)|Porównuje `CComBSTR` z ciągiem.|  
|[CComBSTR::operator &](#operator_amp)|Zwraca adres `m_str`.|  
|[CComBSTR::operator +=](#operator_add_eq)|Dołącza `CComBSTR` do obiektu.|  
|[CComBSTR::operator <](#operator_lt)|Porównuje `CComBSTR` z ciągiem.|  
|[CComBSTR::operator =](#operator_eq)|Przypisuje wartość do `m_str`.|  
|[CComBSTR::operator ==](#operator_eq_eq)|Porównuje `CComBSTR` z ciągiem.|  
|[CComBSTR::operator >](#operator_gt)|Porównuje `CComBSTR` z ciągiem.|  
  
### <a name="public-data-members"></a>Publiczne elementy członkowskie danych  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CComBSTR::m_str](#m_str)|Zawiera `BSTR` skojarzone z `CComBSTR` obiektu.|  
  
## <a name="remarks"></a>Uwagi  
 `CComBSTR` Klasy jest otoki dla `BSTR`s, która jest prefiksem długość ciągów. Długość jest przechowywany jako liczba całkowita w lokalizacji pamięci poprzedzających danych w ciągu.  
  
 A [BSTR](http://msdn.microsoft.com/en-us/1b2d7d2c-47af-4389-a6b6-b01b7e915228) jest zerem po ostatniej zliczane znaków, ale mogą także zawierać osadzone w ciągu znaków wartości null. Długość ciągu jest określana przez liczba znaków, nie pierwszym znakiem null.  
  
> [!NOTE]
>  `CComBSTR` Klasa zawiera liczbę elementów członkowskich (konstruktorów operatory przypisania i operatory porównania), które przyjmują argumentów ciągów ANSI lub Unicode. Wersje ANSI te funkcje są mniej wydajne niż ich odpowiedniki Unicode, ponieważ tymczasowego ciągi Unicode są często utworzone wewnętrznie. W celu zwiększenia wydajności należy użyć wersji Unicode, gdy jest to możliwe.  
  
> [!NOTE]
>  Ze względu na zachowanie ulepszone wyszukiwania w programie Visual Studio .NET, takie jak kod `bstr = L"String2" + bstr;`, może być skompilowany w poprzednich wersjach, zamiast tego należy wdrożyć jako `bstr = CStringW(L"String2") + bstr`.  
  
 Lista ostrzeżenia, korzystając z `CComBSTR`, zobacz [Programowanie przy użyciu CComBSTR](../../atl/programming-with-ccombstr-atl.md).  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** atlbase.h  
  
##  <a name="append"></a>CComBSTR::Append  
 Dołącza albo `lpsz` lub `BSTR` członkiem `bstrSrc` do [m_str](#m_str).  
  
```
HRESULT Append(const CComBSTR& bstrSrc) throw();
HRESULT Append(wchar_t ch) throw();
HRESULT Append(char ch) throw();
HRESULT Append(LPCOLESTR lpsz) throw();
HRESULT Append(LPCSTR lpsz) throw();
HRESULT Append(LPCOLESTR lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [in] A `CComBSTR` obiekt ma zostać dołączony.  
  
 *ch*  
 [in] Znak do dołączenia.  
  
 `lpsz`  
 [in] Ciąg znaków zakończony zerem do dołączenia. Można przekazać ciągu Unicode za pomocą **LPCOLESTR** przeciążenia lub ciągu ANSI za pomocą `LPCSTR` wersji.  
  
 `nLen`  
 [in] Liczba znaków z `lpsz` do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub wszystkie standardowe `HRESULT` wartość błędu.  
  
### <a name="remarks"></a>Uwagi  
 Ciąg ANSI zostanie przekonwertowany na ciąg Unicode przed są dołączone.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#32](../../atl/codesnippet/cpp/ccombstr-class_1.cpp)]  
  
##  <a name="appendbstr"></a>CComBSTR::AppendBSTR  
 Dołącza określony `BSTR` do [m_str](#m_str).  
  
```
HRESULT AppendBSTR(BSTR p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [in] A `BSTR` do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub wszystkie standardowe `HRESULT` wartość błędu.  
  
### <a name="remarks"></a>Uwagi  
 Nie przekazuj zwykłej ciąg znaków dwubajtowych do tej metody. Kompilator nie można przechwycić błąd i uruchom razem, gdy wystąpią błędy.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#33](../../atl/codesnippet/cpp/ccombstr-class_2.cpp)]  
  
##  <a name="appendbytes"></a>CComBSTR::AppendBytes  
 Dołącza określoną liczbę bajtów do [m_str](#m_str) bez użycia konwersji.  
  
```
HRESULT AppendBytes(const char* lpsz, int nLen) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `lpsz`  
 [in] Wskaźnik do tablicy bajtów do dołączenia.  
  
 `p`  
 [in] Liczba bajtów do dołączenia.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub wszystkie standardowe `HRESULT` wartość błędu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#34](../../atl/codesnippet/cpp/ccombstr-class_3.cpp)]  
  
##  <a name="arraytobstr"></a>CComBSTR::ArrayToBSTR  
 Zwalnia wszelkie istniejące parametry przechowywać w formacie `CComBSTR` obiekt, a następnie tworzy `BSTR` od pierwszego znaku każdy element parametru safearray i dołącza go do `CComBSTR` obiektu.  
  
```
HRESULT ArrayToBSTR(const SAFEARRAY* pSrc) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pSrc`  
 [in] Parametru safearray zawierający elementy używany do tworzenia ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub wszystkie standardowe `HRESULT` wartość błędu.  
  
##  <a name="assignbstr"></a>CComBSTR::AssignBSTR  
 Przypisuje `BSTR` do [m_str](#m_str).  
  
```
HRESULT AssignBSTR(const BSTR bstrSrc) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [in] A `BSTR` można przypisać do bieżącego `CComBSTR` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub wszystkie standardowe `HRESULT` wartość błędu.  
  
##  <a name="attach"></a>CComBSTR::Attach  
 Dołącza `BSTR` do `CComBSTR` obiektu przez ustawienie [m_str](#m_str) członka *src*.  
  
```
void Attach(BSTR src) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *src*  
 [in] `BSTR` Do dołączenia do obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Nie przekazuj zwykłej ciąg znaków dwubajtowych do tej metody. Kompilator nie można przechwycić błąd i uruchom razem, gdy wystąpią błędy.  
  
> [!NOTE]
>  Ta metoda będzie assert, jeśli `m_str` ma wartość inną niż **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="bstrtoarray"></a>CComBSTR::BSTRToArray  
 Tworzy safearray jednowymiarowa liczony od zera, w której każdy element tablicy jest znak z `CComBSTR` obiektu.  
  
```
HRESULT BSTRToArray(LPSAFEARRAY* ppArray) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ppArray`  
 [out] Wskaźnik do parametru safearray używany do przechowywania wyników funkcji.  
  
### <a name="return-value"></a>Wartość zwracana  
 `S_OK`na powodzenie lub wszystkie standardowe `HRESULT` wartość błędu.  
  
##  <a name="bytelength"></a>CComBSTR::ByteLength  
 Zwraca liczbę bajtów w `m_str`, z wyłączeniem znak końcowy null.  
  
```
unsigned int ByteLength() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość [m_str](#m_str) elementu członkowskiego w bajtach.  
  
### <a name="remarks"></a>Uwagi  
 Zwraca wartość 0, jeśli `m_str` jest **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#36](../../atl/codesnippet/cpp/ccombstr-class_5.cpp)]  
  
##  <a name="ccombstr"></a>CComBSTR::CComBSTR  
 Konstruktor. Ustawia konstruktora domyślnego [m_str](#m_str) członka **NULL**.  
  
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
 `nSize`  
 [in] Liczba znaków do skopiowania `sz` lub początkowy rozmiar w znakach `CComBSTR`.  
  
 `sz`  
 [in] Ciąg do skopiowania. Określa wersję Unicode **LPCOLESTR**; wersji ANSI Określa `LPCSTR`.  
  
 `pSrc`  
 [in] Ciąg do skopiowania. Określa wersję Unicode **LPCOLESTR**; wersji ANSI Określa `LPCSTR`.  
  
 *src*  
 [in] A `CComBSTR` obiektu.  
  
 `guid`  
 [in] Odwołanie do **GUID** struktury.  
  
### <a name="remarks"></a>Uwagi  
 Ustawia konstruktora kopiowania `m_str` kopię `BSTR` członkiem *src*. **REFGUID** konwertuje konstruktora **GUID** je przy użyciu ciągu **StringFromGUID2** i zapisuje wynik.  
  
 Zestaw konstruktorów `m_str` kopię określonego ciągu. Jeśli przekazuj wartości dla `nSize`, a następnie tylko `nSize` znaki zostaną skopiowane, a po niej znak końcowy null.  
  
 `CComBSTR`obsługuje przenoszenie semantyki. Można użyć Konstruktor przenoszenia (Konstruktor, który pobiera odwołanie do r-wartości ( `&&`) można utworzyć nowego obiektu, który używa tych samych danych, jak stary obiekt przekazywanie jako argument, bez potrzeby kopiowania obiektu.  
  
 Destruktor zwalnia ciąg wskazywana przez `m_str`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#37](../../atl/codesnippet/cpp/ccombstr-class_6.cpp)]  
  
##  <a name="dtor"></a>CComBSTR:: ~ CComBSTR  
 Destruktor.  
  
```
~CComBSTR();
```  
  
### <a name="remarks"></a>Uwagi  
 Destruktor zwalnia ciąg wskazywana przez `m_str`.  
  
##  <a name="copy"></a>CComBSTR::Copy  
 Przydziela i zwraca kopię `m_str`.  
  
```
BSTR Copy() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Kopię [m_str](#m_str) elementu członkowskiego. Jeśli `m_str` jest **NULL**, zwraca **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#38](../../atl/codesnippet/cpp/ccombstr-class_7.cpp)]  
  
##  <a name="copyto"></a>CComBSTR::CopyTo  
 Przydziela i zwraca kopię [m_str](#m_str) za pomocą parametru.  
  
```
HRESULT CopyTo(BSTR* pbstr) throw();

HRESULT CopyTo(VARIANT* pvarDest) throw();
```  
  
### <a name="parameters"></a>Parametry  
 *pbstr*  
 [out] Adres `BSTR` w których ma zostać zwrócony ciąg przydzielone przez tę metodę.  
  
 `pvarDest`  
 [out] Adres **VARIANT** w których ma zostać zwrócony ciąg przydzielone przez tę metodę.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość oznaczający powodzenie lub niepowodzenie kopii.  
  
### <a name="remarks"></a>Uwagi  
 Po wywołaniu tej metody **VARIANT** wskazywana przez `pvarDest` będzie typu `VT_BSTR`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#39](../../atl/codesnippet/cpp/ccombstr-class_8.cpp)]  
  
##  <a name="detach"></a>CComBSTR::Detach  
 Odłącza [m_str](#m_str) z `CComBSTR` obiektu i zestawy `m_str` do **NULL**.  
  
```
BSTR Detach() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 `BSTR` Skojarzone z `CComBSTR` obiektu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#40](../../atl/codesnippet/cpp/ccombstr-class_9.cpp)]  
  
##  <a name="empty"></a>CComBSTR::Empty  
 Zwalnia [m_str](#m_str) elementu członkowskiego.  
  
```
void Empty() throw();
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#41](../../atl/codesnippet/cpp/ccombstr-class_10.cpp)]  
  
##  <a name="length"></a>CComBSTR::Length  
 Zwraca liczbę znaków w `m_str`, z wyłączeniem znak końcowy null.  
  
```
unsigned int Length() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość [m_str](#m_str) elementu członkowskiego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#42](../../atl/codesnippet/cpp/ccombstr-class_11.cpp)]  
  
##  <a name="loadstring"></a>CComBSTR::LoadString  
 Ładuje określony przez zasób ciągu `nID` i zapisuje go w tym obiekcie.  
  
```
bool LoadString(HINSTANCE hInst, UINT nID) throw();
bool LoadString(UINT nID) throw();
```  
  
### <a name="parameters"></a>Parametry  
 Zobacz [LoadString](http://msdn.microsoft.com/library/windows/desktop/ms647486) w systemie Windows SDK.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli ciąg jest pomyślnie załadować; w przeciwnym razie, zwraca **false**.  
  
### <a name="remarks"></a>Uwagi  
 Pierwsza funkcja ładuje zasobu z modułu zidentyfikowane przez użytkownika za pośrednictwem `hInst` parametru. Druga funkcja ładuje zasobu z modułu zasobów skojarzonych z [ccommodule —](../../atl/reference/ccommodule-class.md)-pochodnych obiekt używany w tym projekcie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#43](../../atl/codesnippet/cpp/ccombstr-class_12.cpp)]  
  
##  <a name="m_str"></a>CComBSTR::m_str  
 Zawiera `BSTR` skojarzone z `CComBSTR` obiektu.  
  
```
BSTR m_str;
```  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#49](../../atl/codesnippet/cpp/ccombstr-class_13.cpp)]  
  
##  <a name="operator_bstr"></a>CComBSTR::operator BSTR  
 Rzutowania `CComBSTR` do obiektu `BSTR`.  
  
```  
operator BSTR() const throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Umożliwia przekazywanie `CComBSTR` obiektów do funkcje, które mają **[in] BSTR** parametrów.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CComBSTR::m_str](#m_str).  
  
##  <a name="operator_not"></a>CComBSTR::operator!  
 Sprawdza, czy `BSTR` ciąg ma wartość NULL.  
  
```
bool operator!() const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli [m_str](#m_str) element członkowski jest **NULL**; w przeciwnym razie **false**.  
  
### <a name="remarks"></a>Uwagi  
 Ten operator tylko sprawdza, czy wartość NULL, nie dla pustego ciągu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#35](../../atl/codesnippet/cpp/ccombstr-class_4.cpp)]  
  
##  <a name="operator_neq"></a>CComBSTR::operator! =  
 Zwraca wartość logiczną przeciwieństwem [operator ==](#operator_eq_eq).  
  
```
bool operator!= (const CComBSTR& bstrSrc) const throw();
bool operator!= (LPCOLESTR pszSrc) const;
bool operator!= (LPCSTR pszSrc) const;
bool operator!= (int nNull) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [in] A `CComBSTR` obiektu.  
  
 `pszSrc`  
 [in] Ciąg zakończony zerem.  
  
 `nNull`  
 [in] Musi być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywane nie jest równa `CComBSTR` obiektu; w przeciwnym razie zwraca **false**.  
  
### <a name="remarks"></a>Uwagi  
 `CComBSTR`s są porównywane w postaci tekstu w kontekście użytkownika domyślnych ustawień regionalnych. Operator porównania końcowego tylko porównuje zawartych w niej ciąg przed **NULL**.  
  
##  <a name="operator_amp"></a>CComBSTR::operator&amp;  
 Zwraca adres `BSTR` przechowywane w [m_str](#m_str) elementu członkowskiego.  
  
```
BSTR* operator&() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 `CComBstr operator &`specjalne potwierdzenia skojarzone z nią, aby ułatwić identyfikację przecieki pamięci. Program będzie assert, kiedy `m_str` zainicjować elementu członkowskiego. Potwierdzenie został utworzony w celu identyfikowania sytuacji, w których używa programisty `& operator` można przypisać nową wartość do `m_str` Członkowskie bez zwalnianie pierwszy alokacja `m_str`. Jeśli `m_str` jest równa NULL, program zakłada, że m_str nie został jeszcze przydzielony. W takim przypadku program nie będzie potwierdzenia.  
  
 Ta asercja nie jest domyślnie włączona. Zdefiniuj `ATL_CCOMBSTR_ADDRESS_OF_ASSERT` umożliwia potwierdzenie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#46](../../atl/codesnippet/cpp/ccombstr-class_14.cpp)]  
  
 [!code-cpp[NVC_ATL_Utilities#47](../../atl/codesnippet/cpp/ccombstr-class_15.cpp)]  
  
##  <a name="operator_add_eq"></a>CComBSTR::operator +=  
 Dołącza ciąg `CComBSTR` obiektu.  
  
```
CComBSTR& operator+= (const CComBSTR& bstrSrc);  
CComBSTR& operator+= (const LPCOLESTR pszSrc);
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [in] A `CComBSTR` obiekt ma zostać dołączony.  
  
 `pszSrc`  
 [in] Ciąg zakończony zerem do dołączenia.  
  
### <a name="remarks"></a>Uwagi  
 `CComBSTR`s są porównywane w postaci tekstu w kontekście użytkownika domyślnych ustawień regionalnych. **LPCOLESTR** porównanie wykonuje się przy użyciu `memcmp` w danych pierwotnych w każdym ciągu. `LPCSTR` Porównania odbywa się samo po tymczasową kopię Unicode `pszSrc` został utworzony. Operator porównania końcowego tylko porównuje zawartych w niej ciąg przed **NULL**.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#48](../../atl/codesnippet/cpp/ccombstr-class_16.cpp)]  
  
##  <a name="operator_lt"></a>CComBSTR::operator&lt;  
 Porównuje `CComBSTR` z ciągiem.  
  
```
bool operator<(const CComBSTR& bstrSrc) const throw();
bool operator<(LPCOLESTR pszSrc) const throw();
bool operator<(LPCSTR pszSrc) const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywana jest mniejsza niż `CComBSTR` obiektu; w przeciwnym razie zwraca **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie odbywa się przy użyciu jego domyślnych ustawień regionalnych.  
  
##  <a name="operator_eq"></a>CComBSTR::operator =  
 Ustawia [m_str](#m_str) członka kopię `pSrc` lub kopię `BSTR` członkiem *src*. Operator przypisania przenoszenia przenosi `src` bez kopiowania go.   
  
```
CComBSTR& operator= (const CComBSTR& src);  
CComBSTR& operator= (LPCOLESTR pSrc);  
CComBSTR& operator= (LPCSTR pSrc);
CComBSTR& operator= (CComBSTR&& src) throw(); // (Visual Studio 2017)
```  
  
### <a name="remarks"></a>Uwagi  
 `pSrc` Parametr określa albo **LPCOLESTR** dla wersji Unicode lub `LPCSTR` wersje ANSI.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CComBSTR::Copy](#copy).  
  
##  <a name="operator_eq_eq"></a>CComBSTR::operator ==  
 Porównuje `CComBSTR` z ciągiem. `CComBSTR`s są porównywane w postaci tekstu w kontekście użytkownika domyślnych ustawień regionalnych.  
  
```
bool operator== (const CComBSTR& bstrSrc) const throw();
bool operator== (LPCOLESTR pszSrc) const;
bool operator== (LPCSTR pszSrc) const;
bool operator== (int nNull) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `bstrSrc`  
 [in] A `CComBSTR` obiektu.  
  
 `pszSrc`  
 [in] Ciąg zakończony zerem.  
  
 `nNull`  
 [in] Musi być **NULL**.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywana jest równa `CComBSTR` obiektu; w przeciwnym razie zwraca **false**.  
  
### <a name="remarks"></a>Uwagi  
 Operator porównania końcowego tylko porównuje zawartych w niej ciąg przed **NULL**.  
  
##  <a name="operator_gt"></a>CComBSTR::operator&gt;  
 Porównuje `CComBSTR` z ciągiem.  
  
```
bool operator>(const CComBSTR& bstrSrc) const throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca **true** Jeśli element porównywana jest większa niż `CComBSTR` obiektu; w przeciwnym razie zwraca **false**.  
  
### <a name="remarks"></a>Uwagi  
 Porównanie odbywa się przy użyciu jego domyślnych ustawień regionalnych.  
  
##  <a name="readfromstream"></a>CComBSTR::ReadFromStream  
 Ustawia [m_str](#m_str) członka `BSTR` zawartych w określonego strumienia.  
  
```
HRESULT ReadFromStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik do [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfejsu w strumieniu, zawierający dane.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 **ReadToStream** wymaga zawartość strumienia w bieżącym położeniu, aby był zgodny z formatem danych zapisywane przez wywołanie do [WriteToStream](#writetostream).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#44](../../atl/codesnippet/cpp/ccombstr-class_17.cpp)]  
  
##  <a name="tolower"></a>CComBSTR::ToLower  
 Konwertuje ciąg zawarte na małe litery.  
  
```
HRESULT ToLower() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz **CharLowerBuff** uzyskać więcej informacji na temat sposobu konwersja jest wykonywana.  
  
##  <a name="toupper"></a>CComBSTR::ToUpper  
 Konwertuje ciąg zawarte na wielkie litery.  
  
```
HRESULT ToUpper() throw();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz **CharUpperBuff** uzyskać więcej informacji na temat sposobu konwersja jest wykonywana.  
  
##  <a name="writetostream"></a>CComBSTR::WriteToStream  
 Zapisuje [m_str](#m_str) elementu członkowskiego do strumienia.  
  
```
HRESULT WriteToStream(IStream* pStream) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pStream`  
 [in] Wskaźnik do [IStream](http://msdn.microsoft.com/library/windows/desktop/aa380034) interfejsu w strumieniu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Standard `HRESULT` wartość.  
  
### <a name="remarks"></a>Uwagi  
 Można ponownie utworzyć BSTR z zawartości przy użyciu strumienia [ReadFromStream](#readfromstream) funkcji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATL_Utilities#45](../../atl/codesnippet/cpp/ccombstr-class_18.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd klas](../../atl/atl-class-overview.md)   
 [ATL i makr konwersji MFC ciągu](string-conversion-macros.md)
