---
title: Klasa CStringT | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringT
- ATLSTR/ATL::CStringT
- ATLSTR/ATL::CStringT::CStringT
- ATLSTR/ATL::CStringT::AllocSysString
- ATLSTR/ATL::CStringT::AnsiToOem
- ATLSTR/ATL::CStringT::AppendFormat
- ATLSTR/ATL::CStringT::Collate
- ATLSTR/ATL::CStringT::CollateNoCase
- ATLSTR/ATL::CStringT::Compare
- ATLSTR/ATL::CStringT::CompareNoCase
- ATLSTR/ATL::CStringT::Delete
- ATLSTR/ATL::CStringT::Find
- ATLSTR/ATL::CStringT::FindOneOf
- ATLSTR/ATL::CStringT::Format
- ATLSTR/ATL::CStringT::FormatMessage
- ATLSTR/ATL::CStringT::FormatMessageV
- ATLSTR/ATL::CStringT::FormatV
- ATLSTR/ATL::CStringT::GetEnvironmentVariable
- ATLSTR/ATL::CStringT::Insert
- ATLSTR/ATL::CStringT::Left
- ATLSTR/ATL::CStringT::LoadString
- ATLSTR/ATL::CStringT::MakeLower
- ATLSTR/ATL::CStringT::MakeReverse
- ATLSTR/ATL::CStringT::MakeUpper
- ATLSTR/ATL::CStringT::Mid
- ATLSTR/ATL::CStringT::OemToAnsi
- ATLSTR/ATL::CStringT::Remove
- ATLSTR/ATL::CStringT::Replace
- ATLSTR/ATL::CStringT::ReverseFind
- ATLSTR/ATL::CStringT::Right
- ATLSTR/ATL::CStringT::SetSysString
- ATLSTR/ATL::CStringT::SpanExcluding
- ATLSTR/ATL::CStringT::SpanIncluding
- ATLSTR/ATL::CStringT::Tokenize
- ATLSTR/ATL::CStringT::Trim
- ATLSTR/ATL::CStringT::TrimLeft
- ATLSTR/ATL::CStringT::TrimRight
- CSTRINGT/CStringT
- CSTRINGT/CStringT::CStringT
- CSTRINGT/CStringT::AllocSysString
- CSTRINGT/CStringT::AnsiToOem
- CSTRINGT/CStringT::AppendFormat
- CSTRINGT/CStringT::Collate
- CSTRINGT/CStringT::CollateNoCase
- CSTRINGT/CStringT::Compare
- CSTRINGT/CStringT::CompareNoCase
- CSTRINGT/CStringT::Delete
- CSTRINGT/CStringT::Find
- CSTRINGT/CStringT::FindOneOf
- CSTRINGT/CStringT::Format
- CSTRINGT/CStringT::FormatMessage
- CSTRINGT/CStringT::FormatMessageV
- CSTRINGT/CStringT::FormatV
- CSTRINGT/CStringT::GetEnvironmentVariable
- CSTRINGT/CStringT::Insert
- CSTRINGT/CStringT::Left
- CSTRINGT/CStringT::LoadString
- CSTRINGT/CStringT::MakeLower
- CSTRINGT/CStringT::MakeReverse
- CSTRINGT/CStringT::MakeUpper
- CSTRINGT/CStringT::Mid
- CSTRINGT/CStringT::OemToAnsi
- CSTRINGT/CStringT::Remove
- CSTRINGT/CStringT::Replace
- CSTRINGT/CStringT::ReverseFind
- CSTRINGT/CStringT::Right
- CSTRINGT/CStringT::SetSysString
- CSTRINGT/CStringT::SpanExcluding
- CSTRINGT/CStringT::SpanIncluding
- CSTRINGT/CStringT::Tokenize
- CSTRINGT/CStringT::Trim
- CSTRINGT/CStringT::TrimLeft
- CSTRINGT/CStringT::TrimRight
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2d3b718249603c34d5a9a13eec966b586151f2e7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="cstringt-class"></a>Klasa CStringT
Ta klasa reprezentuje `CStringT` obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```  
 
template<typename BaseType, class StringTraits>  
class CStringT :   
public CSimpleStringT<BaseType,
                      _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                      ::c_bIsMFCDLLTraits>  
 
```  
  
#### <a name="parameters"></a>Parametry  
 `BaseType`  
 Znak typu klasy ciągu. Może to być jedna z następujących czynności:  
  
- `char`(dla ciągów znaków ANSI).  
  
- `wchar_t`(dla ciągów znaków Unicode).  
  
- **Tchar —** (w przypadku zarówno ANSI i Unicode ciągi znaków).  
  
 `StringTraits`  
 Określa, czy klasa string mają Obsługa bibliotek C Run-Time (CRT) i gdzie znajdują się zasoby ciągów. Może to być jedna z następujących czynności:  
  
- **StrTraitATL < wchar_t** &#124; `char` &#124; **Tchar —, ChTraitsCRT < wchar_t** &#124; `char` &#124; **Tchar — >>**  
  
     Klasa wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów w moduł określony przez `m_hInstResource` (członka klasy modułu aplikacji).  
  
- **StrTraitATL < wchar_t** &#124; `char` &#124; **Tchar —, ChTraitsOS < wchar_t** &#124; `char` &#124; **Tchar — >>**  
  
     Klasa nie wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów w moduł określony przez `m_hInstResource` (członka klasy modułu aplikacji).  
  
- **StrTraitMFC < wchar_t** &#124; `char` &#124; **Tchar —, ChTraitsCRT < wchar_t** &#124; `char` &#124; **Tchar — >>**  
  
     Klasa wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów przy użyciu standardowego MFC algorytmu wyszukiwania.  
  
- **StrTraitMFC < wchar_t** &#124; `char` &#124; **Tchar —, ChTraitsOS < wchar_t** &#124; `char` &#124; **Tchar — >>**  
  
     Klasa nie wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów przy użyciu standardowego MFC algorytmu wyszukiwania.  
  
## <a name="members"></a>Elementy członkowskie  
  
### <a name="public-constructors"></a>Konstruktory publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringT::CStringT](#cstringt)|Konstruuje `CStringT` obiektu na różne sposoby.|  
|[CStringT:: ~ CStringT](#_dtorcstringt)|Niszczy `CStringT` obiektu.|  
  
### <a name="public-methods"></a>Metody publiczne  
  
|Nazwa|Opis|  
|----------|-----------------|  
|[CStringT::AllocSysString](#allocsysstring)|Przydziela `BSTR` z `CStringT` danych.|  
|[CStringT::AnsiToOem](#ansitooem)|Powoduje, że konwersja w miejscu z zestawu do zestawu znaków OEM znaków ANSI.|  
|[CStringT::AppendFormat](#appendformat)|Dołącza sformatowanych danych do istniejącego `CStringT` obiektu.|  
|[CStringT::Collate](#collate)|Porównuje dwa ciągi (uwzględniana wielkość liter, używa informacje specyficzne dla ustawień regionalnych).|  
|[CStringT::CollateNoCase](#collatenocase)|Porównuje dwa ciągi (bez uwzględniania wielkości liter, używa informacje specyficzne dla ustawień regionalnych).|  
|[CStringT::Compare](#compare)|Porównuje dwa ciągi (z uwzględnieniem wielkości liter).|  
|[CStringT::CompareNoCase](#comparenocase)|Porównuje dwa ciągi (bez uwzględniania wielkości liter).|  
|[CStringT::Delete](#delete)|Usuwa znaki z ciągu.|  
|[CStringT::Find](#find)|Wyszukuje znak lub podciąg wewnątrz większy ciąg.|  
|[CStringT::FindOneOf](#findoneof)|Znajduje pierwszy znak zgodnych z zestawem.|  
|[CStringT::Format](#format)|Formatuje ciąg jako `sprintf` jest.|  
|[CStringT::FormatMessage](#formatmessage)|Formatuje ciąg komunikatu.|  
|[CStringT::FormatMessageV](#formatmessagev)|Formatuje ciąg komunikatu przy użyciu listy zmiennych argumentów.|  
|[CStringT::FormatV](#formatv)|Formatuje ciąg przy użyciu listy zmiennych argumentów.|  
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Ustawia wartość zmiennej środowiskowej określonego ciągu.|  
|[CStringT::Insert](#insert)|Wstawia pojedynczy znak lub podciąg pod danym indeksem w ciągu.|  
|[CStringT::Left](#left)|Wyodrębnia lewej części ciągu.|  
|[CStringT::LoadString](#loadstring)|Ładuje istniejące `CStringT` obiektu z zasobów systemu Windows.|  
|[CStringT::MakeLower](#makelower)|Konwertuje wszystkie znaki w tym ciągu na małe litery.|  
|[CStringT::MakeReverse](#makereverse)|Odwraca ciąg.|  
|[CStringT::MakeUpper](#makeupper)|Konwertuje wszystkie znaki w tym ciągu na wielkie litery.|  
|[CStringT::Mid](#mid)|Wyodrębnia środkowa część ciągu.|  
|[CStringT::OemToAnsi](#oemtoansi)|Powoduje, że konwersja w miejscu z zestawu do zestawu znaków ANSI znaków OEM.|  
|[CStringT::Remove](#remove)|Usuwa wskazane znaków z ciągu.|  
|[CStringT::Replace](#replace)|Zastępuje wskazany znaków z innymi znakami.|  
|[CStringT::ReverseFind](#reversefind)|Wyszukuje znak wewnątrz ciąg większy. rozpoczyna się od końca.|  
|[CStringT::Right](#right)|Wyodrębnia prawa część ciągu.|  
|[CStringT::SetSysString](#setsysstring)|Ustawia istniejące `BSTR` obiektu przy użyciu danych z `CStringT` obiektu.|  
|[CStringT::SpanExcluding](#spanexcluding)|Wyodrębnia znaków z ciągu, rozpoczynając od pierwszego znaku, które nie znajdują się w zestawie znaków identyfikowane przez `pszCharSet`.|  
|[CStringT::SpanIncluding](#spanincluding)|Wyodrębnianie podciągu, który zawiera tylko znaki w zestawie.|  
|[CStringT::Tokenize](#tokenize)|Wyodrębnia określony tokenów w ciągu docelowego.|  
|[CStringT::Trim](#trim)|Usuwa wszystkie znaki odstępy wiodące i końcowe z ciągu.|  
|[CStringT::TrimLeft](#trimleft)|Przycina początkowe z ciągu znaków odstępu.|  
|[CStringT::TrimRight](#trimright)|Przycina końcowe znaki odstępu z ciągu.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#operator_eq)|Przypisuje nową wartość do `CStringT` obiektu.|  
|[CStringT::operator +](#operator_add)|Łączy dwa ciągi lub znak i ciąg.|  
|[CStringT::operator +=](#operator_add_eq)|Łączy nowy ciąg na końcu istniejących parametrów.|  
|[CStringT::operator ==](#operator_eq_eq)|Określa, czy dwa ciągi, które są logicznie równe.|  
|[CStringT::operator! =](#operator_neq)|Określa, czy dwa ciągi logicznie nie są takie same.|  
|[CStringT::operator&lt;](#operator_lt)|Określa, czy ciąg po lewej stronie operatora jest mniejsza niż do ciągu po prawej stronie.|  
|[CStringT::operator&gt;](#operator_gt)|Określa, czy ciąg po lewej stronie operatora jest większa niż ciąg po prawej stronie.|  
|[CStringT::operator&lt;=](#operator_lt_eq)|Określa, czy ciąg po lewej stronie operatora jest mniejsza lub równa ciągu po prawej stronie.|  
|[CStringT::operator&gt;=](#operator_gt_eq)|Określa, czy ciąg po lewej stronie operatora jest większa niż lub równa ciągu po prawej stronie.|  
  
## <a name="remarks"></a>Uwagi  
 `CStringT`dziedziczy [CSimpleStringT klasy](../../atl-mfc-shared/reference/csimplestringt-class.md). Zaawansowane funkcje, takie jak znak manipulowanie, porządkowanie, a wyszukiwanie, są implementowane przez `CStringT`.  
  
> [!NOTE]
> `CStringT`obiekty są w stanie zgłaszanie wyjątków. Dzieje się tak, gdy `CStringT` obiektu zabraknie pamięci różnych przyczyn.  
  
 A `CStringT` obiekt składa się z sekwencji znaków o zmiennej długości. `CStringT`udostępnia funkcje i operatory przy użyciu składni podobny do Basic. Łączenie i operatory porównania, wraz z pamięci uproszczonego zarządzania, należy `CStringT` łatwiejsze niż tablice znaków zwykłej korzystanie z obiektów.  
  
> [!NOTE]
>  Chociaż można utworzyć `CStringT` wystąpień, które zawierają osadzone znaki null, zaleca się przed nim. Wywołanie metody i operatory w `CStringT` obiektów, które zawierają znaki null osadzonych może spowodować niezamierzone wyników.  
  
 Przy użyciu różnych kombinacji `BaseType` i `StringTraits` parametrów `CStringT` obiekty można dostarczanych w następujących typów, które zostały wstępnie zdefiniowane przez biblioteki ATL.  
  
 Jeśli używany w aplikacji ATL:  
  
 `CString`, `CStringA`, i `CStringW` są eksportowane z biblioteki DLL MFC (MFC90. Biblioteki DLL), nigdy nie od użytkownika biblioteki dll. Pozwala to zapobiec `CStringT` z jest zdefiniowany wiele razy.  
  
> [!NOTE]
>  Jeśli kod zawiera rozwiązania błędów konsolidatora, które opisano w [klasy Linking Errors When You Import CString-Derived "(Q309801)](https://support.microsoft.com/help/309801/you-may-receive-an-lnk2019-error-message-when-you-build-a-visual-c-200), należy usunąć ten kod. Nie jest już potrzebne.  
  
 Następujące typy ciągu są dostępne w aplikacjach MFC:  
  
|Typ CStringT|Deklaracja|  
|-------------------|-----------------|  
|`CStringA`|Znak ANSI wpisz ciąg z obsługą CRT.|  
|`CStringW`|Znak Unicode, wpisz ciąg z obsługą CRT.|  
|`CString`|Zarówno ANSI i Unicode typy znaków z obsługą CRT.|  
  
 Następujący ciąg w dostępnych typów projektów where **ATL_CSTRING_NO_CRT** zdefiniowano:  
  
|Typ CStringT|Deklaracja|  
|-------------------|-----------------|  
|**CAtlStringA**|Znak ANSI wpisz ciąg bez obsługi CRT.|  
|**CAtlStringW**|Znak Unicode, wpisz ciąg bez obsługi CRT.|  
|**CAtlString**|Zarówno ANSI i Unicode typy znaków bez obsługi CRT.|  
  
 Następujący ciąg w dostępnych typów projektów where **ATL_CSTRING_NO_CRT** nie jest zdefiniowana:  
  
|Typ CStringT|Deklaracja|  
|-------------------|-----------------|  
|**CAtlStringA**|Znak ANSI wpisz ciąg z obsługą CRT.|  
|**CAtlStringW**|Znak Unicode, wpisz ciąg z obsługą CRT.|  
|**CAtlString**|Zarówno ANSI i Unicode typy znaków z obsługą CRT.|  
  
 `CString`obiekty są również następujące cechy:  
  
- `CStringT`obiekty mogą rosnąć w wyniku operacji łączenia.  
  
- `CStringT`obiekty wykonaj "wartość semantyki". Pomyśl o `CStringT` obiektu jako rzeczywisty ciąg, a nie jako wskaźnik do ciągu.  
  
-   Można zastąpić za darmo `CStringT` obiektów na `PCXSTR` argumentów funkcji.  
  
-   Zarządzanie pamięcią niestandardowych dla buforów ciągu. Aby uzyskać więcej informacji, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
## <a name="cstringt-predefined-types"></a>CStringT wstępnie zdefiniowanych typów  
 Ponieważ `CStringT` używa argument szablonu w celu zdefiniowania typu znaków (albo [wchar_t](../../c-runtime-library/standard-types.md) lub [char](../../c-runtime-library/standard-types.md)) obsługiwane typy parametrów metody może być skomplikowane w czasie. Aby uprościć ten problem, zestaw wstępnie zdefiniowanych typów jest zdefiniowana i używanych w całym `CStringT` klasy. W poniższej tabeli wymieniono różne typy:  
  
|Nazwa|Opis|  
|----------|-----------------|  
|`XCHAR`|Pojedynczy znak (albo `wchar_t` lub `char`) z tego samego typu znak jako `CStringT` obiektu.|  
|**YCHAR**|Pojedynczy znak (albo `wchar_t` lub `char`) z typem przeciwny znak jako `CStringT` obiektu.|  
|`PXSTR`|Wskaźnik do ciągu znaków (albo `wchar_t` lub `char`) z tego samego typu znak jako `CStringT` obiektu.|  
|**PYSTR**|Wskaźnik do ciągu znaków (albo `wchar_t` lub `char`) z typem przeciwny znak jako `CStringT` obiektu.|  
|`PCXSTR`|Wskaźnik do **const** ciąg znaków (albo `wchar_t` lub `char`) z tego samego typu znak jako `CStringT` obiektu.|  
|**PCYSTR**|Wskaźnik do **const** ciąg znaków (albo `wchar_t` lub `char`) z typem przeciwny znak jako `CStringT` obiektu.|  
  
> [!NOTE]
>  Kod, który korzystał wcześniej z metody nieudokumentowanej `CString` (takich jak **AssignCopy**) muszą zostać zastąpione przez kod, który korzysta z następujących metod udokumentowane `CStringT` (takich jak `GetBuffer` lub `ReleaseBuffer`). Te metody są dziedziczone z `CSimpleStringT`.  
  
## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia  
 [CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)  
  
 `CStringT`  
  
## <a name="requirements"></a>Wymagania  
  
|nagłówek|Na użytek|  
|------------|-------------|  
|cstringt.h|Obiekty MFC — tylko do ciągów|  
|atlstr.h|Obiekty ciąg inne niż MFC|  
  
##  <a name="allocsysstring"></a>CStringT::AllocSysString  
 Przydziela ciągu automatyzacji typu `BSTR` i kopiuje zawartość `CStringT` obiektu, w tym znak końcowy null.  
  
```  
BSTR AllocSysString() const;  
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowoprzydzielonych ciąg.  
  
### <a name="remarks"></a>Uwagi  
 W programach MFC [CMemoryException klasy](../../mfc/reference/cmemoryexception-class.md) jest generowany, jeśli istnieje za mało pamięci. W programach ATL [CAtlException](../../atl/reference/catlexception-class.md) jest generowany. Funkcja ta używa się zazwyczaj w celu zwracać ciągi automatyzacji.  
  

 Często Jeśli ten ciąg jest przekazywany do funkcji modelu COM jako [in] parametr, a następnie to wymaga obiekt wywołujący, aby zwolnić ciąg. Można to zrobić za pomocą [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx), zgodnie z opisem w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [Allocating i zwalniając pamięć dla typu BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).  
  
 Aby uzyskać więcej informacji na temat funkcji alokacji OLE w systemie Windows, zobacz [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx) w zestawie Windows SDK.  

  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CStringT::AllocSysString`.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]  
  
##  <a name="ansitooem"></a>CStringT::AnsiToOem  
 Konwertuje wszystkie znaki w tym `CStringT` obiekt z zestawu do zestawu znaków OEM znaków ANSI.  
  
```  
void AnsiToOem();
```  
  
### <a name="remarks"></a>Uwagi  
 Funkcja jest niedostępna, jeśli `_UNICODE` jest zdefiniowany.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]  
  
##  <a name="appendformat"></a>CStringT::AppendFormat  
 Dołącza sformatowanych danych do istniejącego `CStringT` obiektu.  
  
```  
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Ciąg formatu formantu.  
  
 `nFormatID`  
 Identyfikator zasobu ciągu zawierającego ciąg formatu kontroli.  
  
 `argument`  
 Argumenty opcjonalne.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja formatuje i dołącza serii znaków i wartościami w `CStringT`. Każdy argument opcjonalne (jeśli istnieje) jest konwertowane i według specyfikacji formatu w `pszFormat` lub ciąg zasobu określonego przez `nFormatID`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]  
  
##  <a name="collate"></a>CStringT::Collate  
 Porównuje dwa ciągi, przy użyciu funkcji zwykłego tekstu `_tcscoll`.  
  
```  
int Collate(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Inne ciąg używany do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne, < 0, jeśli `CStringT` obiekt jest mniejszy niż `psz`, lub > 0, jeśli `CStringT` obiekt jest większy niż `psz`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwykłego tekstu `_tcscoll`, która jest zdefiniowana w tchar —. Mapuje jedną H, `strcoll`, `wcscoll`, lub `_mbscoll`, w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każdej funkcji wykonuje porównania z uwzględnieniem wielkości liter ciągi zgodnie ze strony kodowej obecnie w użyciu. Aby uzyskać więcej informacji, zobacz [strcoll —, wcscoll —, _mbscoll —, _strcoll_l —, _wcscoll_l —, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).  
  
##  <a name="collatenocase"></a>CStringT::CollateNoCase  
 Porównuje dwa ciągi, przy użyciu funkcji zwykłego tekstu `_tcscoll`.  
  
```  
int CollateNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Inne ciąg używany do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne (bez uwzględnienia wielkości liter), < 0, jeśli `CStringT` obiekt jest mniejszy niż `psz` (bez uwzględnienia wielkości liter), lub > 0, jeśli ten `CStringT` obiekt jest większy niż `psz` (bez uwzględnienia wielkości liter).  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwykłego tekstu `_tcscoll`, która jest zdefiniowana w tchar —. Mapuje jedną H, `stricoll`, `wcsicoll`, lub `_mbsicoll`, w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje bez uwzględniania wielkości liter porównania ciągów, zgodnie z aktualnie używanej strony kodowej. Aby uzyskać więcej informacji, zobacz [strcoll —, wcscoll —, _mbscoll —, _strcoll_l —, _wcscoll_l —, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]  
  
##  <a name="compare"></a>CStringT::Compare  
 Porównuje dwa ciągi (z uwzględnieniem wielkości liter).  
  
```  
int Compare(PCXSTR psz) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Inne ciąg używany do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne, < 0, jeśli `CStringT` obiekt jest mniejszy niż `psz`, lub > 0, jeśli `CStringT` obiekt jest większy niż `psz`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwykłego tekstu `_tcscmp`, która jest zdefiniowana w tchar —. Mapuje jedną H, `strcmp`, `wcscmp`, lub `_mbscmp`, w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje z uwzględnieniem wielkości liter porównania ciągów i nie ma wpływu na ustawienia regionalne. Aby uzyskać więcej informacji, zobacz [strcmp —, wcscmp —, _mbscmp —](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).  
  
 Jeśli ciąg zawiera osadzone wartości, na potrzeby porównania ciągu jest uważana za obcięta na pierwszym znakiem null osadzonych.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano użycie `CStringT::Compare`.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]  
  
##  <a name="comparenocase"></a>CStringT::CompareNoCase  
 Porównuje dwa ciągi (bez uwzględniania wielkości liter).  
  
```  
int CompareNoCase(PCXSTR psz) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `psz`  
 Inne ciąg używany do porównania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zero, jeśli ciągi są identyczne (bez uwzględnienia wielkości liter) < 0, jeśli ta `CStringT` obiekt jest mniejszy niż `psz` (bez uwzględnienia wielkości liter), lub > 0, jeśli ten `CStringT` obiekt jest większy niż `psz` (bez uwzględnienia wielkości liter).  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwykłego tekstu `_tcsicmp`, która jest zdefiniowana w tchar —. Mapuje jedną H, `_stricmp`, `_wcsicmp` lub `_mbsicmp`, w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje bez uwzględniania wielkości liter porównania ciągów. Porównanie jest zależna od `LC_CTYPE` aspekt ustawień regionalnych, ale nie `LC_COLLATE`. Aby uzyskać więcej informacji, zobacz [_stricmp —, _wcsicmp —, _mbsicmp —, _stricmp_l —, _wcsicmp_l —, _mbsicmp_l —](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]  
  
##  <a name="cstringt"></a>CStringT::CStringT  
 Konstruuje `CStringT` obiektu.  
  
```  
CStringT() throw() :   
    CThisSimpleString(StringTraits::GetDefaultManager());
 
explicit CStringT(IAtlStringMgr* pStringMgr) throw() :   
    CThisSimpleString( pStringMgr); 

CStringT(const VARIANT& varSrc);
 
CStringT(const VARIANT& varSrc, IAtlStringMgr* pStringMgr);
 
CStringT(const CStringT& strSrc) :   
    CThisSimpleString( strSrc);

 operator CSimpleStringT<
                    BaseType, 
                    !_CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>
                    :: c_bIsMFCDLLTraits> &()  
 
template <bool bMFCDLL>  
CStringT(const CSimpleStringT<BaseType, bMFCDLL>& strSrc) :   
    CThisSimpleString( strSrc);
 
template <class SystemString>  
CStringT(SystemString^ pString) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const XCHAR* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(const YCHAR* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(LPCSTR pszSrc, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
 
CStringT(LPCWSTR pszSrc, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
 
CSTRING_EXPLICIT CStringT(const unsigned char* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
/*CSTRING_EXPLICIT*/ CStringT(char* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(unsigned char* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(wchar_t* pszSrc) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const unsigned char* pszSrc, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
 
CSTRING_EXPLICIT CStringT(char ch, int nLength = 1) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CSTRING_EXPLICIT CStringT(wchar_t ch, int nLength = 1) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const XCHAR* pch, int nLength) :   
    CThisSimpleString( pch, nLength, StringTraits::GetDefaultManager());
 
CStringT(const YCHAR* pch, int nLength) :   
    CThisSimpleString( StringTraits::GetDefaultManager());
 
CStringT(const XCHAR* pch, int nLength, AtlStringMgr* pStringMgr) :   
    CThisSimpleString( pch, nLength, pStringMgr);
 
CStringT(const YCHAR* pch, int nLength, IAtlStringMgr* pStringMgr) :   
    CThisSimpleString( pStringMgr);
```  
  
### <a name="parameters"></a>Parametry  
 `pch`  
 Wskaźnik do tablicy znaków o długości `nLength`, nie zakończonym znakiem null.  
  
 `nLength`  
 Liczba liczba znaków w `pch`.  
  
 `ch`  
 Pojedynczy znak.  
  
 `pszSrc`  
 Ciąg zakończony zerem, ma zostać skopiowany do tego `CStringT` obiektu.  
  
 `pStringMgr`  
 Wskaźnik do Menedżera pamięci dla `CStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CStringT`, zobacz [zarządzania pamięcią z CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).  
  
 `strSrc`  
 Istniejące `CStringT` obiekt ma zostać skopiowany do tego `CStringT` obiektu. Aby uzyskać więcej informacji na temat `CThisString` i `CThisSimpleString`, zobacz sekcję uwag.  
  
 `varSrc`  
 Variant — obiekt ma zostać skopiowany do tego `CStringT` obiektu.  
  
 `BaseType`  
 Znak typu klasy ciągu. Może to być jedna z następujących czynności:  
  
 `char`(dla ciągów znaków ANSI).  
  
 `wchar_t`(dla ciągów znaków Unicode).  
  
 `TCHAR`(w przypadku zarówno ANSI i Unicode ciągi znaków).  
  
 `bMFCDLL`  
 Wartość logiczna określająca, czy projekt jest biblioteki DLL MFC (TRUE) czy nie (FALSE).  
  
 `SystemString`  
 Musi być `System::String`, i projektu muszą być skompilowane z/CLR.  
  
 `pString`  
 Dojście do `CStringT` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Ponieważ konstruktorów skopiować dane wejściowe do nowego magazynu przydzielonego, należy zwrócić uwagę pamięci może spowodować wyjątków. Należy pamiętać, niektóre z tych konstruktorów pełnienie funkcji konwersji. Dzięki temu można podstawić, na przykład `LPTSTR` gdzie `CStringT` oczekuje się obiektu.  
  
- `CStringT`( `LPCSTR` `lpsz` ): Tworzy Unicode `CStringT` z ciągu ANSI. Ten konstruktor służy również do załadowania zasobów ciągu, jak pokazano w poniższym przykładzie.  
  
- `CStringT(``LPCWSTR` `lpsz` ): Tworzy `CStringT` z ciągiem Unicode.  
  
- `CStringT`( `const unsigned char*` `psz` ): Służy do tworzenia `CStringT` ze wskaźnika do `unsigned char`.  
  
> [!NOTE]
>  Zdefiniuj **_CSTRING_DISABLE_NARROW_WIDE_CONVERSION** makra, aby wyłączyć ciąg niejawna konwersja między [!INCLUDE[vcpransi](../../atl-mfc-shared/reference/includes/vcpransi_md.md)] i [!INCLUDE[TLA#tla_unicode](../../atl-mfc-shared/reference/includes/tlasharptla_unicode_md.md)] ciągów. Makro wyklucza z konstruktorów kompilacji, które obsługują konwersji.  
  
 Należy pamiętać, że `strSrc` parametr może być albo `CStringT` lub `CThisSimpleString` obiektu. Dla `CStringT`, użyj jednej z jego wystąpień domyślnego ( `CString`, `CStringA`, lub `CStringW`); w przypadku `CThisSimpleString`, użyj `this` wskaźnika. `CThisSimpleString`deklaruje wystąpienia [klasy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), który jest mniejszy klasy ciągu z mniej wbudowanej funkcji niż `CStringT` klasy.  
  
 Przeciążaj operator `CSimpleStringT<>&()` tworzy `CStringT` obiekt z `CSimpleStringT` deklaracji.  
  
> [!NOTE]
>  Chociaż można utworzyć `CStringT` wystąpień, które zawierają osadzone znaki null, zaleca się przed nim. Wywołanie metody i operatory w `CStringT` obiektów, które zawierają znaki null osadzonych może spowodować niezamierzone wyników.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]  
  
##  <a name="_dtorcstringt"></a>CStringT:: ~ CStringT  
 Niszczy `CStringT` obiektu.  
  
```  
~CStringT() throw();
```  
  
### <a name="remarks"></a>Uwagi  
 Niszczy `CStringT` obiektu.  
  
##  <a name="delete"></a>CStringT::Delete  
 Usuwa znaki z ciągu, począwszy od znaku pod danym indeksem.  
  
```  
int Delete(int iIndex, int nCount = 1);
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Liczony od zera indeks pierwszego znaku w `CStringT` obiektu do usunięcia.  
  
 `nCount`  
 Liczba znaków, które zostaną usunięte.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość ciągu zmienione.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nCount` jest dłuższa niż ciąg pozostała część ciągu zostaną usunięte.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]  
  
```Output  
Before: Soccer is best,
    but hockey is quicker!  
After: Soccer best,
    but hockey is quicker!  
```  
  
##  <a name="find"></a>CStringT::Find  
 Przeszukuje tego ciągu pierwszego dopasowania znaku lub podciąg.  
  
```  
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszSub`  
 Ciąg do wyszukania.  
  
 `iStart`  
 Indeks znaków w ciągu, aby rozpocząć wyszukiwanie przy użyciu lub 0, aby rozpocząć od początku.  
  
 `ch`  
 Pojedynczy znak do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pierwszego znaku, w tym `CStringT` obiekt, który odpowiada żądanej podciąg ani znaków; -1, jeśli nie zostanie znaleziony podciąg lub znak.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja jest przeciążony do akceptowania zarówno pojedynczy znaki (podobne do funkcji środowiska wykonawczego `strchr`) i ciągi (podobnie jak `strstr`).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]  
  
##  <a name="findoneof"></a>CStringT::FindOneOf  
 Wyszukuje tego ciągu pierwszego znaku, który dopasowuje dowolny znak zawarte w `pszCharSet`.  
  
```  
int FindOneOf(PCXSTR pszCharSet) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `pszCharSet`  
 Ciąg zawierający znaki do dopasowania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks pierwszego znaku, w tym ciągu, który jest również w `pszCharSet`; -1, jeśli nie zostanie odnaleziony odpowiednik.  
  
### <a name="remarks"></a>Uwagi  
 Znajduje pierwsze wystąpienie znaków w `pszCharSet`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]  
  
##  <a name="format"></a>CStringT::Format  
 Zapisy sformatowanych danych do `CStringT` tak samo jak robi [sprintf_s —](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formatuje dane do tablicy znaków stylu języka C.  
  
```  
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```  
  
### <a name="parameters"></a>Parametry  
 `nFormatID`  
 Identyfikator zasobu ciągu zawierającego ciąg formatu kontroli.  
  
 `pszFormat`  
 Ciąg formatu formantu.  
  
 `argument`  
 Argumenty opcjonalne.  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja formatuje i przechowuje serii znaków i wartościami w `CStringT`. Każdy argument opcjonalne (jeśli istnieje) jest konwertowana i dane wyjściowe według specyfikacji formatu w `pszFormat` lub ciąg zasobu określonego przez `nFormatID`.  
  
 Wywołanie zakończy się niepowodzeniem, jeśli sam obiekt ciągu jest oferowany jako parametr `Format`. Na przykład następujący kod spowoduje nieoczekiwane wyniki:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]  
  
 Aby uzyskać więcej informacji, zobacz [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]  
  
##  <a name="formatmessage"></a>CStringT::FormatMessage  
 Formatuje ciąg komunikatu.  
  
```  
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```  
  
### <a name="parameters"></a>Parametry  
 `nFormatID`  
 Identyfikator zasobu ciągu zawierającego tekst komunikatu niesformatowany.  
  
 `pszFormat`  
 Wskazuje ciąg formatu formantu. Zostanie ono skanowany w poszukiwaniu wstawia i odpowiednio sformatowane. Ciąg formatu jest podobna do funkcji środowiska wykonawczego `printf`— styl ciągi formatów z wyjątkiem umożliwia parametrów, które ma zostać wstawiony w dowolnej kolejności.  
  
 `argument`  
 Argumenty opcjonalne.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja wymaga definicji komunikatu jako dane wejściowe. Definicji komunikatu jest określany przez `pszFormat` lub ciąg zasobu określonego przez `nFormatID`. Funkcja kopiuje tekst sformatowany komunikat `CStringT` obiektu przetwarzania żadnego osadzonych Wstaw sekwencji żądanie.  
  
> [!NOTE]
> `FormatMessage`próbuje przydzielić pamięci dla nowo sformatowanego ciągu. Jeśli ta próba nie powiedzie się, pamięć jest automatycznie wyjątek.  
  
 Każdy insert musi mieć odpowiedni parametr po `pszFormat` lub `nFormatID` parametru. W tekście wiadomości kilka sekwencji unikowych są obsługiwane dla dynamicznie formatowania komunikatu. Aby uzyskać więcej informacji, zobacz Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkcji w zestawie Windows SDK.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]  
  
##  <a name="formatmessagev"></a>CStringT::FormatMessageV  
 Formatuje ciąg komunikatu przy użyciu listy zmiennych argumentów.  
  
```  
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Wskazuje ciąg formatu formantu. Zostanie ono skanowany w poszukiwaniu wstawia i odpowiednio sformatowane. Ciąg formatu jest podobna do funkcji środowiska wykonawczego `printf`— styl ciągi formatów z wyjątkiem umożliwia parametrów, które ma zostać wstawiony w dowolnej kolejności.  
  
 `pArgList`  
 Wskaźnik do listy argumentów.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja wymaga definicji komunikatu jako dane wejściowe, określany przez `pszFormat`. Funkcja kopiuje tekst sformatowany komunikat i listy zmiennych argumentów `CStringT` obiektu przetwarzania żadnego osadzonych Wstaw sekwencji żądanie.  
  
> [!NOTE]
> `FormatMessageV`wywołania [CStringT::FormatMessage](#formatmessage), który próbuje przydzielić pamięci dla nowo sformatowanego ciągu. Jeśli ta próba nie powiedzie się, pamięć jest automatycznie wyjątek.  
  
 Aby uzyskać więcej informacji, zobacz Windows [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351) funkcji w zestawie Windows SDK.  
  
##  <a name="formatv"></a>CStringT::FormatV  
 Formatuje ciąg komunikatu przy użyciu listy zmiennych argumentów.  
  
```  
void FormatV(PCXSTR pszFormat, va_list args);
```  
  
### <a name="parameters"></a>Parametry  
 `pszFormat`  
 Wskazuje ciąg formatu formantu. Zostanie ono skanowany w poszukiwaniu wstawia i odpowiednio sformatowane. Ciąg formatu jest podobna do funkcji środowiska wykonawczego `printf`— styl ciągi formatów z wyjątkiem umożliwia parametrów, które ma zostać wstawiony w dowolnej kolejności.  
  
 `args`  
 Wskaźnik do listy argumentów.  
  
### <a name="remarks"></a>Uwagi  
 Zapisuje ciąg sformatowany i listy zmiennych argumentów `CStringT` ciąg w taki sam jak robi `vsprintf_s` formatuje dane do tablicy znaków stylu języka C.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]  
  
 [!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]  
  
##  <a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable  
 Ustawia wartość zmiennej środowiskowej określonego ciągu.  
  
```  
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```  
  
### <a name="parameters"></a>Parametry  
 `pszVar`  
 Wskaźnik do zerem ciąg, który określa zmiennej środowiskowej.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, w przypadku powodzenia; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Pobiera wartość zmiennej określonej z bloku środowiska procesu wywołującego. Wartość jest w formie ciąg znaków zakończony znakiem null.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]  
  
##  <a name="insert"></a>CStringT::Insert  
 Wstawia pojedynczy znak lub podciąg pod danym indeksem w ciągu.  
  
```  
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```  
  
### <a name="parameters"></a>Parametry  
 `iIndex`  
 Indeks znaków, przed którym odbędzie się wstawiania.  
  
 `psz`  
 Wskaźnik do podciąg do wstawienia.  
  
 `ch`  
 Znak do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Długość ciągu zmienione.  
  
### <a name="remarks"></a>Uwagi  
 `iIndex` Parametr identyfikuje pierwszego znaku, który zostanie przeniesiony do przygotowania miejsca na znak lub podciąg. Jeśli `nIndex` wynosi zero, nastąpi wstawiania przed cały ciąg. Jeśli `nIndex` jest większa niż długość ciągu, funkcja będzie Połącz występuje ciąg i złożone nowe materiały `ch` lub `psz`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]  
  
##  <a name="left"></a>CStringT::Left  
 Wyodrębnia lewej `nCount` znaków z tego `CStringT` obiektu i zwraca kopię wyodrębnionego podciąg.  
  
```  
CStringT Left(int nCount) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `nCount`  
 Liczba znaków to wyodrębniania `CStringT` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CStringT` obiekt, który zawiera kopię określony zakres znaków. Zwrócona `CStringT` obiekt może być pusty.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nCount` przekracza długość ciągu, a następnie cały ciąg jest wyodrębniana. `Left`jest podobny do podstawowego `Left` funkcji.  
  
 Dla zestawy wielobajtowego znaków (MBCS) `nCount` traktuje każdej kolejny 8-bitową jako znak, dzięki czemu `nCount` zwraca liczbę znaków wielobajtowego pomnożona przez dwa.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]  
  
##  <a name="loadstring"></a>CStringT::LoadString  
 Odczytuje zasób ciągu Windows identyfikowane przez `nID`, do istniejącej `CStringT` obiektu.  
  
```  
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `hInstance`  
 Dojście do wystąpienia modułu.  
  
 `nID`  
 Identyfikator Windows ciągu zasobu.  
  
 `wLanguageID`  
 Język zasobu ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Różna od zera, jeśli obciążenie zasobów zakończyło się pomyślnie; w przeciwnym razie 0.  
  
### <a name="remarks"></a>Uwagi  
 Ładuje zasobu ciągu ( `nID`) od określonego modułu ( `hInstance`) przy użyciu określonego języka ( `wLanguage`).  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]  
  
##  <a name="makelower"></a>CStringT::MakeLower  
 Konwertuje `CStringT` obiektu na ciąg małe litery.  
  
```  
CStringT& MakeLower();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowy ciąg małe litery.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]  
  
##  <a name="makereverse"></a>CStringT::MakeReverse  
 Odwraca kolejność znaków w `CStringT` obiektu.  
  
```  
CStringT& MakeReverse();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Powstałe w ten sposób odwrócona ciągu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]  
  
##  <a name="makeupper"></a>CStringT::MakeUpper  
 Konwertuje `CStringT` obiektu na ciąg wielkie litery.  
  
```  
CStringT& MakeUpper();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowy ciąg wielkie litery.  
  
### <a name="remarks"></a>Uwagi  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]  
  
##  <a name="mid"></a>CStringT::Mid  
 Zwraca podciąg o długości `nCount` znaków z to `CStringT` obiektu, zaczynając od pozycji `iFirst` (liczony od zera).  
  
```  
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `iFirst`  
 Liczony od zera indeks pierwszego znaku, w tym `CStringT` obiekt, który ma być zawarty w wyodrębnionego podciąg.  
  
 `nCount`  
 Liczba znaków to wyodrębniania `CStringT` obiektu. Jeśli ten parametr nie zostanie podany, jest wyodrębniany do końca ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CStringT` obiekt, który zawiera kopię określony zakres znaków. Należy pamiętać, że zwracana `CStringT` obiekt może być pusty.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja zwraca kopię wyodrębnionego podciąg. `Mid`jest podobne do funkcji podstawowych Mid (z wyjątkiem tego, że indeksy Basic są oparte na jeden).  
  
 Dla zestawy znaków wielobajtowych (MBCS) `nCount` odwołuje się do każdego 8-bitową znaku; oznacza to, potencjalnych klientów i ślad bajtów w jednym znaków wielobajtowych są liczone jako dwa znaki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]  
  
##  <a name="oemtoansi"></a>CStringT::OemToAnsi  
 Konwertuje wszystkie znaki w tym `CStringT` obiekt z zestawu do zestawu znaków ANSI znaków OEM.  
  
```  
void OemToAnsi();
```  
  
### <a name="remarks"></a>Uwagi  
 Ta funkcja jest niedostępna, jeśli `_UNICODE` jest zdefiniowany.  
  
### <a name="example"></a>Przykład  
 Zobacz przykład [CStringT::AnsiToOem](#ansitooem).  
  
##  <a name="operator_add"></a>CStringT::operator +  
 Łączy dwa ciągi lub znak i ciąg.  
  
```  
friend CStringT operator+(const CStringT& str1, const CStringT& str2);
friend CStringT operator+(const CStringT& str1, PCXSTR psz2);
friend CStringT operator+(PCXSTR psz1, const CStringT& str2,);
friend CStringT operator+(char ch1, const CStringT& str2,);
friend CStringT operator+(const CStringT& str1, char ch2);
friend CStringT operator+(const CStringT& str1, wchar_t ch2);
friend CStringT operator+(wchar_t ch1, const CStringT& str2,);
```  
  
### <a name="parameters"></a>Parametry  
 `ch1`  
 Znak ANSI lub Unicode do łączenia z ciągiem.  
  
 `ch2`  
 Znak ANSI lub Unicode do łączenia z ciągiem.  
  
 `str1`  
 A `CStringT` do łączenia z ciąg lub znak.  
  
 `str2`  
 A `CStringT` do łączenia z ciąg lub znak.  
  
 `psz1`  
 Wskaźnik do zerem ciągu do łączenia z ciąg lub znak.  
  
 `psz2`  
 Wskaźnik do ciągu do łączenia z ciąg lub znak.  
  
### <a name="remarks"></a>Uwagi  
 Istnieje siedem form przeciążenia `CStringT::operator+` funkcji. Pierwsza wersja łączy dwa istniejące `CStringT` obiektów. Dwie ZŁĄCZ.teksty `CStringT` obiekt i ciąg znaków zakończony znakiem null. Dwie ZŁĄCZ.teksty `CStringT` obiekt i znaków ANSI. Ostatnie dwa ZŁĄCZ.teksty `CStringT` obiekt i znak Unicode.  
  
> [!NOTE]
>  Chociaż można utworzyć `CStringT` wystąpień, które zawierają osadzone znaki null, zaleca się przed nim. Wywołanie metody i operatory w `CStringT` obiektów, które zawierają znaki null osadzonych może spowodować niezamierzone wyników.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]  
  
##  <a name="operator_add_eq"></a>CStringT::operator +=  
 Łączy znaki na końcu ciągu.  
  
```  
CStringT& operator+=(const CThisSimpleString& str);

template<bool bMFCDLL>  
CStringT& operator+=(const const CSimpleStringT<BaseType, bMFCDLL>& str);

template<int t_nSize>  
CStringT& operator+=(const CStaticString<XCHAR, t_nSize>& strSrc);
CStringT& operator+=(PCXSTR pszSrc);
CStringT& operator+=(PCYSTR pszSrc);
CStringT& operator+=(char ch);
CStringT& operator+=(unsigned char ch);
CStringT& operator+=(wchar_t ch);
CStringT& operator+=(const VARIANT& var);
```  
  
### <a name="parameters"></a>Parametry  
 str  
 Odwołanie do `CThisSimpleString` obiektu.  
  
 `bMFCDLL`  
 Wartość logiczna określająca, czy projekt jest biblioteki MFC DLL.  
  
 `BaseType`  
 Typ podstawowy ciągu.  
  
 `var`  
 Obiekt typu variant do połączenia do tego ciągu.  
  
 `ch`  
 Znak ANSI lub Unicode do łączenia z ciągiem.  
  
 `pszSrc`  
 Wskaźnik do oryginalnego ciągu, są połączone.  
  
 `strSrc`  
 A `CStringT` do konkatenacji z tych parametrów.  
  
### <a name="remarks"></a>Uwagi  
 Operator akceptuje innego `CStringT` obiektu, wskaźnik znak lub pojedynczy znak. Należy zwrócić uwagę pamięci, wyjątki może wystąpić, gdy Użyj tego operatora łączenia, ponieważ można przydzielić nowego magazynu znaków dodane do tego `CStringT` obiektu.  
  
 Aby uzyskać informacje dotyczące `CThisSimpleString`, zobacz sekcję uwag [CStringT::CStringT](#cstringt).  
  
> [!NOTE]
>  Chociaż można utworzyć `CStringT` wystąpień, które zawierają osadzone znaki null, zaleca się przed nim. Wywołanie metody i operatory w `CStringT` obiektów, które zawierają znaki null osadzonych może spowodować niezamierzone wyników.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]  
  
##  <a name="operator_eq_eq"></a>CStringT::operator ==  
 Określa, czy dwa ciągi, które są logicznie takie same.  
  
```  
friend bool operator==(const CStringT& str1, const CStringT& str2) throw();
friend bool operator==(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator==(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator==(const CStringT& str1, XCHAR ch2) throw();
friend bool operator==(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator==(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator==(XCHAR ch1, const CStringT& str2,) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ch1`  
 Znak ANSI lub Unicode do porównania.  
  
 `ch2`  
 Znak ANSI lub Unicode do porównania.  
  
 `str1`  
 A `CStringT` do porównania.  
  
 `str2`  
 A `CStringT` do porównania.  
  
 `psz1`  
 Wskaźnik do zerem ciągu do porównania.  
  
 `psz2`  
 Wskaźnik do zerem ciągu do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Sprawdza, czy ciąg lub znak z lewej strony jest taki sam ciąg lub znak po prawej stronie i zwraca wartość PRAWDA lub FAŁSZ w związku z tym.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]  
  
##  <a name="operator_neq"></a>CStringT::operator! =  
 Określa, czy dwa ciągi logicznie nie są takie same.  
  
```  
friend bool operator!=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator!=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator!=(const CStringT& str1, PCYSTR psz2) throw();
friend bool operator!=(const CStringT& str1, XCHAR ch2) throw();
friend bool operator!=(PCXSTR psz1, const CStringT& str2) throw();
friend bool operator!=(PCYSTR psz1, const CStringT& str2,) throw();
friend bool operator!=(XCHAR ch1, const CStringT& str2,) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ch1`  
 Znak ANSI lub Unicode do łączenia z ciągiem.  
  
 `ch2`  
 Znak ANSI lub Unicode do łączenia z ciągiem.  
  
 `str1`  
 A `CStringT` do porównania.  
  
 `str2`  
 A `CStringT` do porównania.  
  
 `psz1`  
 Wskaźnik do zerem ciągu do porównania.  
  
 `psz2`  
 Wskaźnik do zerem ciągu do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Testy, jeśli ciąg lub znak po lewej stronie nie jest równa ciąg lub znak po prawej stronie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]  
  
##  <a name="operator_lt"></a>CStringT::operator&lt;  
 Określa, czy ciąg po lewej stronie operatora jest mniejsza niż ciąg po prawej stronie.  
  
```  
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` do porównania.  
  
 `str2`  
 A `CStringT` do porównania.  
  
 `psz1`  
 Wskaźnik do zerem ciągu do porównania.  
  
 `psz2`  
 Wskaźnik do zerem ciągu do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów, znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i wyszukuje czy ciągi mają taką samą liczbę znaków, a więc ciągi są takie same.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]  
  
##  <a name="operator_gt"></a>CStringT::operator&gt;  
 Określa, czy ciąg po lewej stronie operatora jest większy niż ciąg po prawej stronie.  
  
```  
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` do porównania.  
  
 `str2`  
 A `CStringT` do porównania.  
  
 `psz1`  
 Wskaźnik do zerem ciągu do porównania.  
  
 `psz2`  
 Wskaźnik do zerem ciągu do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów, znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, dlatego ciągi są takie same.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]  
  
##  <a name="operator_lt_eq"></a>CStringT::operator&lt;=  
 Określa, czy ciąg po lewej stronie operatora jest mniejsza lub równa ciągu po prawej stronie.  
  
```  
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` do porównania.  
  
 `str2`  
 A `CStringT` do porównania.  
  
 `psz1`  
 Wskaźnik do zerem ciągu do porównania.  
  
 `psz2`  
 Wskaźnik do zerem ciągu do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów, znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, dlatego ciągi są takie same.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]  
  
##  <a name="operator_gt_eq"></a>CStringT::operator&gt;=  
 Określa, czy ciąg po lewej stronie operatora jest większa niż lub równa ciągu po prawej stronie.  
  
```  
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `str1`  
 A `CStringT` do porównania.  
  
 `str2`  
 A `CStringT` do porównania.  
  
 `psz1`  
 Wskaźnik do ciągu do porównania.  
  
 `psz2`  
 Wskaźnik do ciągu do porównania.  
  
### <a name="remarks"></a>Uwagi  
 Lexicographical porównania ciągów, znak po znaku do:  
  
-   Znajdzie odpowiedniego znakami nierówne i pochodzi wynik ich porównanie wyniku porównania ciągów.  
  
-   Znalezione nie nierówności, ale jeden ciąg ma więcej znaków niż innych i krótszego ciągu jest uważany za mniej niż ciąg dłużej.  
  
-   Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, dlatego ciągi są takie same.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]  
  
##  <a name="remove"></a>CStringT::Remove  
 Usuwa wszystkie wystąpienia określonej znaków z ciągu.  
  
```  
int Remove(XCHAR chRemove);
```  
  
### <a name="parameters"></a>Parametry  
 `chRemove`  
 Znak, który ma zostać usunięty z ciągu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Usunięte liczbę znaków z ciągu. Zero, jeśli ciąg nie zostanie zmieniona.  
  
### <a name="remarks"></a>Uwagi  
 Porównywanie znaku jest uwzględniana wielkość liter.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]  
  
##  <a name="replace"></a>CStringT::Replace  
 Istnieją dwie wersje `Replace`. Pierwszą wersję zamienia jedną lub więcej kopii podciągu inny podciąg. Zarówno podciągów są zakończone wartością null. Druga wersja zastępuje kopie co najmniej jeden znak, przy użyciu innego znaku. Obie wersje działać na znak danych przechowywanych w `CStringT`.  
  
```  
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```  
  
### <a name="parameters"></a>Parametry  
 `pszOld`  
 Wskaźnik do zerem ciągu mają zostać zastąpione przez `pszNew`.  
  
 `pszNew`  
 Wskaźnik do zerem ciągu, który zastępuje `pszOld`.  
  
 `chOld`  
 Znak, który ma zostać zastąpione przez `chNew`.  
  
 `chNew`  
 Zastępowanie znaku `chOld`.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca liczbę wystąpień zastąpionego znak lub podciąg lub zero, jeśli ciąg nie zostanie zmieniona.  
  
### <a name="remarks"></a>Uwagi  
 `Replace`można zmienić długość ciągu, ponieważ `pszNew` i `pszOld` nie muszą mieć taką samą długość i wiele kopii starego podciąg może być zmieniona na nową. Funkcja wykonuje uwzględniające wielkość liter dopasowanie.  
  
 Przykłady `CStringT` wystąpienia są `CString`, `CStringA`, i `CStringW`.  
  
 Aby uzyskać `CStringA`, `Replace` współpracuje z ANSI lub znaków wielobajtowych (MBCS). Aby uzyskać `CStringW`, `Replace` współpracuje z znaki dwubajtowe.  
  
 Aby uzyskać `CString`, dane znakowe wybiera się w czasie kompilacji na podstawie tego, czy stałe w poniższej tabeli są zdefiniowane.  
  
|Zdefiniowaną stałą|Dane znakowe|  
|----------------------|-------------------------|  
|`_UNICODE`|Znaki dwubajtowe|  
|`_MBCS`|Znaki wielobajtowe|  
|Ani|Znaki jednobajtowe|  
|Zarówno|Niezdefiniowana|  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]  
  
##  <a name="reversefind"></a>CStringT::ReverseFind  
 Wyszukuje to `CStringT` obiekt do dopasowania ostatniego znaku.  
  
```  
int ReverseFind(XCHAR ch) const throw();
```  
  
### <a name="parameters"></a>Parametry  
 `ch`  
 Znak do wyszukania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczony od zera indeks ostatni znak w tym `CStringT` obiekt, który odpowiada żądanej znak lub wartość -1, jeśli znak nie zostanie znaleziony.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja jest podobne do funkcji środowiska wykonawczego `strrchr`.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]  
  
##  <a name="right"></a>CStringT::Right  
 Wyodrębnia ostatniego (oznacza to, że po prawej stronie) `nCount` znaków z tego `CStringT` obiektu i zwraca kopię wyodrębnionego podciąg.  
  
```  
CStringT Right(int nCount) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `nCount`  
 Liczba znaków to wyodrębniania `CStringT` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CStringT` obiekt, który zawiera kopię określony zakres znaków. Należy pamiętać, że zwracana `CStringT` obiekt może być pusta.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `nCount` przekracza długość ciągu, a następnie cały ciąg jest wyodrębniana. `Right`jest podobny do podstawowego `Right` funkcji (z wyjątkiem tego, że indeksy Basic są liczony od zera).  
  
 Dla zestawy znaków wielobajtowych (MBCS) `nCount` odwołuje się do każdego 8-bitową znaku; oznacza to, potencjalnych klientów i ślad bajtów w jednym znaków wielobajtowych są liczone jako dwa znaki.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]  
  
##  <a name="setsysstring"></a>CStringT::SetSysString  
 Przydziela ponownie `BSTR` wskazywana przez `pbstr` i kopiuje zawartość `CStringT` obiektu, w tym `NULL` znaków.  
  
```  
BSTR SetSysString(BSTR* pbstr) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pbstr`  
 Wskaźnik do ciągu znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowe parametry.  
  
### <a name="remarks"></a>Uwagi  
 W zależności od zawartości `CStringT` obiekt, wartość `BSTR` odwołuje `pbstr` można zmienić. Funkcja zwraca `CMemoryException` Jeśli istnieje za mało pamięci.  
  
 Ta funkcja używa się zazwyczaj w celu zmiany wartości ciągów przekazana przez odwołanie do automatyzacji.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]  
  
##  <a name="spanexcluding"></a>CStringT::SpanExcluding  
 Wyodrębnia znaków z ciągu, rozpoczynając od pierwszego znaku, które nie znajdują się w zestawie znaków identyfikowane przez `pszCharSet`.  
  
```  
CStringT SpanExcluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszCharSet`  
 Ciąg jest interpretowany jako zbiór znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawiera znaki w ciągu znaków, które nie znajdują się w `pszCharSet`, począwszy od pierwszego znaku w ciągu i kończąc pierwszego znaku w ciągu, który jest również w `pszCharSet` (oznacza to, rozpoczynając od pierwszego znaku w ciąg i stwierdziliśmy, ale nie więcej niż pierwszy znak w ciągu, który jest `pszCharSet`). Zwraca cały ciąg, jeśli żadne znaki w `pszCharSet` znajduje się w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 `SpanExcluding`wyodrębnia i zwraca wszystkie znaki poprzedzających pierwszego wystąpienia znak z `pszCharSet` (innymi słowy, znaku z `pszCharSet` i nie są zwracane wszystkie znaki w ciągu znaków). Jeśli żadne znaki z `pszCharSet` znajduje się w ciągu, następnie `SpanExcluding` zwraca cały ciąg.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]  
  
##  <a name="spanincluding"></a>CStringT::SpanIncluding  
 Wyodrębnia znaków z ciągu, rozpoczynając od pierwszego znaku, które znajdują się w zestawie znaków identyfikowane przez `pszCharSet`.  
  
```  
CStringT SpanIncluding(PCXSTR pszCharSet) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszCharSet`  
 Ciąg jest interpretowany jako zbiór znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Ciąg zawiera znaki w ciągu, w której znajdują się `pszCharSet`, począwszy od pierwszego znaku w ciągu i końcowa po znalezieniu znak w ciągu, który nie znajduje się w `pszCharSet`. `SpanIncluding`Zwraca podciąg puste, jeśli pierwszy znak w ciągu nie jest w określonym zestawie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pierwszym znakiem ciągu nie jest w zestawie znaków następnie `SpanIncluding` zwraca pusty ciąg. W przeciwnym wypadku zwraca sekwencji kolejnych znaków, które znajdują się w zestawie.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]  
  
##  <a name="tokenize"></a>CStringT::Tokenize  
 Znajduje następny token w ciągu docelowego  
  
```  
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const; 
```  
  
### <a name="parameters"></a>Parametry  
 `pszTokens`  
 Ciąg zawierający token ograniczników. Kolejność tych ograniczników nie jest ważna.  
  
 `iStart`  
 Liczony od zera indeks, aby rozpocząć wyszukiwanie.  
  
### <a name="return-value"></a>Wartość zwracana  
 A `CStringT` obiekt zawierający bieżącą wartość tokenu.  
  
### <a name="remarks"></a>Uwagi  
 `Tokenize` Funkcja znajduje następny token w ciągu docelowego. Zestaw znaków `pszTokens` określa możliwe ograniczniki tokenu, który ma zostać odnaleziona. Na każde wywołanie `Tokenize` funkcja rozpoczyna się od `iStart`pomija ograniczniki początkowych i zwraca `CStringT` obiekt zawierający tokenu bieżącego, która jest ciąg znaków do następnej znak ogranicznika. Wartość `iStart` zaktualizowania pozycji po końcowy znak ogranicznika lub wartość -1, jeśli osiągnięto końca ciągu. Więcej tokenów można uszkodzony poza pozostałej części ciąg docelowego przez szereg wywołań `Tokenize`za pomocą `iStart` do śledzenia, gdzie w ciągu następnej token jest do odczytu. Jeśli istnieją żadnych kolejnych tokenów funkcja zwróci ciąg pusty i `iStart` ustawioną wartość -1.  
  
 W odróżnieniu od CRT tokenizacji funkcji, takich jak [strtok_s —, _strtok_s_l —, wcstok_s —, _wcstok_s_l —, _mbstok_s —, _mbstok_s_l —](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` nie modyfikuje ciąg docelowego.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]  
  
### <a name="remarks"></a>Uwagi  
 Dane wyjściowe w tym przykładzie ma następującą składnię:  
  
 `Resulting Token: First`  
  
 `Resulting Token: Second`  
  
 `Resulting Token: Third`  
  
##  <a name="trim"></a>CStringT::Trim  
 Przycina początkowe i końcowe znaków z ciągu.  
  
```  
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```  
  
### <a name="parameters"></a>Parametry  
 `chTarget`  
 Znak docelowy przycięcia.  
  
 `pszTargets`  
 Wskaźnik do ciąg zawierający docelowy znaki przycięcia. Wszystkich spacji wiodących i końcowych wystąpień znaków `pszTarget` będą usuwane z `CStringT` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca ciąg przycięte.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie wystąpienia wiodące i końcowe w jednej z następujących czynności:  
  
-   Znak określony przez`chTarget.`  
  
-   Wszystkie znaki w ciągu określonego przez`pszTargets.`  
  
-   Odstępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]  
  
### <a name="remarks"></a>Uwagi  
 Dane wyjściowe w tym przykładzie ma następującą składnię:  
  
 `Before: "******Soccer is best, but liquor is quicker!!!!!"`  
  
 `After : "Soccer is best, but liquor is quicker"`  
  
##  <a name="trimleft"></a>CStringT::TrimLeft  
 Przycina początkowe znaków z ciągu.  
  
```  
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```  
  
### <a name="parameters"></a>Parametry  
 `chTarget`  
 Znak docelowy przycięcia.  
  
 `pszTargets`  
 Wskaźnik do ciąg zawierający docelowy znaki przycięcia. Wszystkie wystąpienia wiodących znaków w `pszTarget` będą usuwane z `CStringT` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Wynikowy ciąg przycięte.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa wszystkie wystąpienia wiodące i końcowe w jednej z następujących czynności:  
  
-   Znak określony przez`chTarget.`  
  
-   Wszystkie znaki w ciągu określonego przez`pszTargets.`  
  
-   Odstępu.  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]  
  
##  <a name="trimright"></a>CStringT::TrimRight  
 Przycina końcowe znaków z ciągu.  
  
```  
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```  
  
### <a name="parameters"></a>Parametry  
 `chTarget`  
 Znak docelowy przycięcia.  
  
 `pszTargets`  
 Wskaźnik do ciąg zawierający docelowy znaki przycięcia. Końcowe wszystkie wystąpienia znaków w `pszTarget` będą usuwane z `CStringT` obiektu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `CStringT` obiekt, który zawiera ciąg przycięte.  
  
### <a name="remarks"></a>Uwagi  
 Usuwa końcowe wystąpienia jednego z następujących czynności:  
  
-   Znak określony przez`chTarget.`  
  
-   Wszystkie znaki w ciągu określonego przez`pszTargets.`  
  
-   Odstępu.  
  
 `CStringT& TrimRight(XCHAR chTarget)` Wersja przyjmuje jeden parametr znaku i usuwa wszystkie kopie tego znaku od końca `CStringT` dane ciągu. Rozpoczyna się od końca ciągu, a działa do przodu. Zatrzymuje się, gdy znajdzie innego znaku lub gdy `CSTringT` zabraknie danych znakowych.  
  
 `CStringT& TrimRight(PCXSTR pszTargets)` Wersji akceptuje zerem ciąg, który zawiera różne znaki do wyszukania. Usuwa wszystkie kopie tych znaków `CStringT` obiektu. Rozpoczyna się od końca ciągu, a działa do przodu. Zatrzymuje się, gdy znajdzie się znak, który nie znajduje się w ciągu docelowego lub gdy `CStringT` zabraknie danych znakowych. Nie próbuje zgodny z ciągiem całego docelowych do podciągu na końcu `CStringT`.  
  
 `CStringT& TrimRight()` Wersji nie wymaga parametrów. Przycina go białych znaków końcowe od końca `CStringT` ciągu. Odstęp może być podziałów wierszy, spacji lub kart.  
  
-  
  
### <a name="example"></a>Przykład  
 [!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Diagram hierarchii](../../mfc/hierarchy-chart.md)   
 [ATL/MFC udostępnionych klas](../../atl-mfc-shared/atl-mfc-shared-classes.md)   
 [CSimpleStringT, klasa](../../atl-mfc-shared/reference/csimplestringt-class.md)


