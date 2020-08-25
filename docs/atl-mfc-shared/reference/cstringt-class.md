---
title: Klasa CStringT
ms.date: 03/27/2019
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
helpviewer_keywords:
- strings [C++], in ATL
- shared classes, CStringT
- CStringT class
ms.assetid: 7cacc59c-425f-40f1-8f5b-6db921318ec9
ms.openlocfilehash: 3e6d61bdf296e85bee5d41ec2131fa3d83122c2b
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88832090"
---
# <a name="cstringt-class"></a>Klasa CStringT

Ta klasa reprezentuje `CStringT` obiekt.

## <a name="syntax"></a>Składnia

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasy String. Może być jedną z następujących czynności:

- **`char`** (w przypadku ciągów znaków ANSI).

- **`wchar_t`** (w przypadku ciągów znaków Unicode).

- Używanie TCHAR (dla ciągów znaków ANSI i Unicode).

*StringTraits*<br/>
Określa, czy Klasa String wymaga obsługi biblioteki środowiska uruchomieniowego C (CRT) i gdzie znajdują się zasoby ciągu. Może być jedną z następujących czynności:

- **StrTraitATL< wchar_t** &#124; **`char`** &#124; **używanie tchar, ChTraitsCRT< wchar_t** &#124; **`char`** &#124; **Używanie TCHAR > >**

   Klasa wymaga obsługi CRT i wyszukuje ciągi zasobów w module określonym przez `m_hInstResource` (element członkowski klasy modułu aplikacji).

- **StrTraitATL< wchar_t** &#124; **`char`** &#124; **używanie tchar, ChTraitsOS< wchar_t** &#124; **`char`** &#124; **Używanie TCHAR > >**

   Klasa nie wymaga obsługi CRT i wyszukuje ciągi zasobów w module określonym przez `m_hInstResource` (element członkowski klasy modułu aplikacji).

- **StrTraitMFC< wchar_t** &#124; **`char`** &#124; **używanie tchar, ChTraitsCRT< wchar_t** &#124; **`char`** &#124; **Używanie TCHAR > >**

   Klasa wymaga obsługi CRT i wyszukuje ciągi zasobów przy użyciu standardowego algorytmu wyszukiwania MFC.

- **StrTraitMFC< wchar_t** &#124; **`char`** &#124; **używanie tchar, ChTraitsOS< wchar_t** &#124; **`char`** &#124; **Używanie TCHAR > >**

   Klasa nie wymaga obsługi CRT i wyszukuje ciągi zasobów przy użyciu standardowego algorytmu wyszukiwania MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringT:: CStringT](#cstringt)|Tworzy `CStringT` obiekt na różne sposoby.|
|[CStringT:: ~ CStringT](#_dtorcstringt)|Niszczy `CStringT` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringT:: AllocSysString](#allocsysstring)|Alokuje BSTR z `CStringT` danych.|
|[CStringT:: AnsiToOem](#ansitooem)|Wprowadza konwersję w miejscu ze znaku ANSI ustawionym na zestaw znaków OEM.|
|[CStringT:: AppendFormat](#appendformat)|Dołącza dane sformatowane do istniejącego `CStringT` obiektu.|
|[CStringT:: COLLATE](#collate)|Porównuje dwa ciągi (z uwzględnieniem wielkości liter, używa informacji specyficznych dla ustawień regionalnych).|
|[CStringT:: CollateNoCase](#collatenocase)|Porównuje dwa ciągi (bez uwzględniania wielkości liter, używa informacji specyficznych dla ustawień regionalnych).|
|[CStringT:: Compare](#compare)|Porównuje dwa ciągi (z uwzględnieniem wielkości liter).|
|[CStringT:: CompareNoCase](#comparenocase)|Porównuje dwa ciągi (bez uwzględniania wielkości liter).|
|[CStringT::D Usuń](#delete)|Usuwa znak lub znaki z ciągu.|
|[CStringT:: find](#find)|Znajduje znak lub podciąg w większym ciągu.|
|[CStringT:: FindOneOf](#findoneof)|Znajduje pierwszy pasujący znak z zestawu.|
|[CStringT:: format](#format)|Formatuje ciąg jako `sprintf` .|
|[CStringT:: FormatMessage](#formatmessage)|Formatuje ciąg komunikatu.|
|[CStringT:: FormatMessageV](#formatmessagev)|Formatuje ciąg komunikatu przy użyciu listy zmiennych argumentów.|
|[CStringT:: FormatV](#formatv)|Formatuje ciąg przy użyciu zmiennej listy argumentów.|
|[CStringT:: GetEnvironmentVariable](#getenvironmentvariable)|Ustawia ciąg na wartość określonej zmiennej środowiskowej.|
|[CStringT:: INSERT](#insert)|Wstawia pojedynczy znak lub podciąg w danym indeksie w ciągu.|
|[CStringT:: Left](#left)|Wyodrębnia lewą część ciągu.|
|[CStringT:: LoadString](#loadstring)|Ładuje istniejący `CStringT` obiekt z zasobu systemu Windows.|
|[CStringT:: MakeLower](#makelower)|Konwertuje wszystkie znaki w ciągu do małych liter.|
|[CStringT:: MakeReverse](#makereverse)|Odwraca ciąg.|
|[CStringT:: MakeUpper](#makeupper)|Konwertuje wszystkie znaki w tym ciągu na wielkie litery.|
|[CStringT:: Mid](#mid)|Wyodrębnia środkową część ciągu.|
|[CStringT:: OemToAnsi](#oemtoansi)|Wprowadza konwersję w miejscu ze znaku OEM ustawionym na zestaw znaków ANSI.|
|[CStringT:: Remove](#remove)|Usuwa wskazane znaki z ciągu.|
|[CStringT:: Replace](#replace)|Zastępuje znaki oznaczone innymi znakami.|
|[CStringT:: ReverseFind](#reversefind)|Znajduje znak w większym ciągu; zaczyna się od końca.|
|[CStringT:: Right](#right)|Wyodrębnia prawą część ciągu.|
|[CStringT:: SetSysString](#setsysstring)|Ustawia istniejący obiekt BSTR z danymi z `CStringT` obiektu.|
|[CStringT:: SpanExcluding](#spanexcluding)|Wyodrębnia znaki z ciągu, zaczynając od pierwszego znaku, które nie znajdują się w zestawie znaków identyfikowanych przez `pszCharSet` .|
|[CStringT:: SpanIncluding](#spanincluding)|Wyodrębnia podciąg, który zawiera tylko znaki w zestawie.|
|[CStringT:: tokenize](#tokenize)|Wyodrębnia określone tokeny w ciągu docelowym.|
|[CStringT:: Trim](#trim)|Przycina wszystkie wiodące i końcowe znaki odstępu z ciągu.|
|[CStringT:: TrimLeft](#trimleft)|Przycina wiodące znaki odstępu z ciągu.|
|[CStringT:: TrimRight](#trimright)|Przycina końcowe znaki odstępu z ciągu.|

### <a name="operators"></a>Operatory

|Nazwa|Opis|
|-|-|
|[CStringT:: operator =](#operator_eq)|Przypisuje nową wartość do `CStringT` obiektu.|
|[CStringT:: operator +](#operator_add)|Łączy dwa ciągi lub znak i ciąg.|
|[CStringT:: operator + =](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CStringT:: operator = =](#operator_eq_eq)|Określa, czy dwa ciągi są logicznie równe.|
|[CStringT:: operator! =](#operator_neq)|Określa, czy dwa ciągi są logicznie nierówne.|
|[CStringT:: operator &lt;](#operator_lt)|Określa, czy ciąg po lewej stronie operatora jest mniejszy od ciągu po prawej stronie.|
|[CStringT:: operator &gt;](#operator_gt)|Określa, czy ciąg po lewej stronie operatora jest większy niż ciąg po prawej stronie.|
|[CStringT:: operator &lt;=](#operator_lt_eq)|Określa, czy ciąg po lewej stronie operatora jest mniejszy od lub równy ciągowi po prawej stronie.|
|[CStringT:: operator &gt;=](#operator_gt_eq)|Określa, czy ciąg po lewej stronie operatora jest większy od lub równy ciągowi po prawej stronie.|

## <a name="remarks"></a>Uwagi

`CStringT` dziedziczy z [klasy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Funkcje zaawansowane, takie jak manipulowanie znakami, porządkowanie i wyszukiwanie, są implementowane przez program `CStringT` .

> [!NOTE]
> `CStringT` obiekty mogą zgłaszać wyjątki. Dzieje się tak, gdy w `CStringT` przypadku obiektu zabrakło pamięci z dowolnego powodu.

`CStringT`Obiekt składa się z sekwencji o zmiennej długości. `CStringT` Program udostępnia funkcje i operatory używające składni podobnej do języka Basic. Operatory łączenia i porównywania, wraz z uproszczonym zarządzaniem pamięcią, `CStringT` ułatwiają używanie obiektów od zwykłych tablic znaków.

> [!NOTE]
> Chociaż istnieje możliwość utworzenia `CStringT` wystąpień zawierających osadzone znaki o wartości null, zalecamy ich użycie. Wywoływanie metod i operatorów dla `CStringT` obiektów, które zawierają osadzone znaki null, może dawać niezamierzone wyniki.

Korzystając z różnych kombinacji `BaseType` `StringTraits` parametrów i, `CStringT` obiekty mogą znajdować się w następujących typach, które zostały wstępnie zdefiniowane przez biblioteki ATL.

Jeśli używasz w aplikacji ATL:

`CString`, `CStringA` , i `CStringW` są eksportowane z biblioteki MFC dll (MFC90.DLL), nigdy nie z bibliotek DLL użytkownika. Dzieje się tak, aby zapobiec `CStringT` pomnożeniem.

> [!NOTE]
> Jeśli kod zawiera obejście błędów konsolidatora, które opisano w [eksportowaniu klas ciągów przy użyciu CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), należy usunąć ten kod. Nie jest już potrzebny.

Następujące typy ciągów są dostępne w ramach aplikacji opartych na MFC:

|Typ CStringT|Oświadczeń|
|-------------------|-----------------|
|`CStringA`|Ciąg typu znaków ANSI z obsługą CRT.|
|`CStringW`|Ciąg typu znaku Unicode z obsługą CRT.|
|`CString`|Typy znaków ANSI i Unicode z obsługą CRT.|

Następujące typy ciągów są dostępne w projektach, w których zdefiniowano ATL_CSTRING_NO_CRT:

|Typ CStringT|Oświadczeń|
|-------------------|-----------------|
|`CAtlStringA`|Ciąg typu znaku ANSI bez obsługi CRT.|
|`CAtlStringW`|Ciąg typu znaku Unicode bez obsługi CRT.|
|`CAtlString`|Typy znaków ANSI i Unicode bez obsługi CRT.|

Następujące typy ciągów są dostępne w projektach, w których ATL_CSTRING_NO_CRT nie jest zdefiniowany:

|Typ CStringT|Oświadczeń|
|-------------------|-----------------|
|`CAtlStringA`|Ciąg typu znaków ANSI z obsługą CRT.|
|`CAtlStringW`|Ciąg typu znaku Unicode z obsługą CRT.|
|`CAtlString`|Typy znaków ANSI i Unicode z obsługą CRT.|

`CString` obiekty mają również następujące cechy:

- `CStringT` obiekty mogą wzrosnąć w wyniku operacji łączenia.

- `CStringT` obiekty podążają za "semantyką wartości". `CStringT`Należy traktować obiekt jako rzeczywisty ciąg, nie jako wskaźnik do ciągu.

- Można swobodnie zastępować `CStringT` obiekty dla `PCXSTR` argumentów funkcji.

- Niestandardowe zarządzanie pamięcią dla buforów ciągów. Aby uzyskać więcej informacji, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Wstępnie zdefiniowane typy CStringT

Ponieważ `CStringT` program używa argumentu szablonu do zdefiniowania typu znaku (obsługiwanego przez [wchar_t](../../c-runtime-library/standard-types.md) lub [char](../../c-runtime-library/standard-types.md)), typy parametrów metody mogą być skomplikowane w czasie. Aby uprościć ten problem, zestaw wstępnie zdefiniowanych typów jest definiowany i używany w całej `CStringT` klasie. W poniższej tabeli wymieniono różne typy:

|Nazwa|Opis|
|----------|-----------------|
|`XCHAR`|Pojedynczy znak (albo **`wchar_t`** **`char`** ) o tym samym typie znaku co `CStringT` obiekt.|
|`YCHAR`|Pojedynczy znak (albo **`wchar_t`** **`char`** ) z odwrotnym typem znaku jako `CStringT` obiektem.|
|`PXSTR`|Wskaźnik do ciągu znaków (albo **`wchar_t`** **`char`** ) z tym samym typem znaku co `CStringT` obiekt.|
|`PYSTR`|Wskaźnik do ciągu znaków (albo **`wchar_t`** lub **`char`** ) z odwrotnym typem znaku jako `CStringT` obiektem.|
|`PCXSTR`|Wskaźnik do **`const`** ciągu znaków (albo **`wchar_t`** **`char`** ) z tym samym typem znaku co `CStringT` obiekt.|
|`PCYSTR`|Wskaźnik do **`const`** ciągu znaków (albo **`wchar_t`** lub **`char`** ) z odwrotnym typem znaku jako `CStringT` obiektem.|

> [!NOTE]
> Kod, który wcześniej użył nieudokumentowanych metod `CString` (takich jak `AssignCopy` ), musi zostać zastąpiony kodem, który używa następujących udokumentowanych metod `CStringT` (takich jak `GetBuffer` lub `ReleaseBuffer` ). Te metody są dziedziczone z `CSimpleStringT` .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Wymagania

|Header|Na użytek|
|------------|-------------|
|CStringT. h|Tylko MFC — obiekty ciągów|
|pliku atlstr. h|Obiekty ciągów innych niż MFC|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a> CStringT:: AllocSysString

Przypisuje ciąg typu BSTR, który jest zgodny z automatyzacją, i kopiuje `CStringT` do niego zawartość obiektu, w tym kończący znak null.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Wartość zwracana

Nowo przydzielony ciąg.

### <a name="remarks"></a>Uwagi

W programach MFC [Klasa CMemoryException](../../mfc/reference/cmemoryexception-class.md) jest zgłaszana w przypadku braku wystarczającej ilości pamięci. W programach ATL jest zgłaszany [CAtlException](../../atl/reference/catlexception-class.md) . Ta funkcja jest zwykle używana do zwracania ciągów dla automatyzacji.

Często, jeśli ten ciąg jest przenoszona do funkcji COM jako parametr [in], to wymaga, aby obiekt wywołujący zwolnił ciąg. Można to zrobić za pomocą [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), zgodnie z opisem w Windows SDK. Aby uzyskać więcej informacji, zobacz [przydzielanie i zwalnianie pamięci dla typu BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Aby uzyskać więcej informacji na temat funkcji alokacji OLE w systemie Windows, zobacz [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) w Windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CStringT::AllocSysString` .

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a> CStringT:: AnsiToOem

Konwertuje wszystkie znaki w tym `CStringT` obiekcie z zestawu znaków ANSI na zestaw znaków OEM.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Uwagi

Funkcja jest niedostępna, jeśli określono _UNICODE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a> CStringT:: AppendFormat

Dołącza dane sformatowane do istniejącego `CStringT` obiektu.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg kontrolny formatu.

*nFormatID*<br/>
Identyfikator zasobu ciągu, który zawiera ciąg kontrolny formatu.

*argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Ta funkcja służy do formatowania i dołączania serii znaków i wartości w `CStringT` . Każdy opcjonalny argument (jeśli istnieje) jest konwertowany i dołączany zgodnie z odpowiadającą specyfikacją formatu w *pszFormat* lub z zasobu ciągu identyfikowanego przez *nFormatID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a> CStringT:: COLLATE

Porównuje dwa ciągi przy użyciu funkcji generycznej tekstu `_tcscoll` .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Inny ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0, jeśli ten `CStringT` obiekt jest mniejszy niż *PSZ*, lub > 0, jeśli ten `CStringT` obiekt jest większy niż *PSZ*.

### <a name="remarks"></a>Uwagi

Funkcja tekstu ogólnego `_tcscoll` , która jest zdefiniowana w używanie TCHAR. H, mapuje do `strcoll` jednego `wcscoll` lub, lub `_mbscoll` , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów z uwzględnieniem wielkości liter zgodnie z aktualnie używaną stroną kodową. Aby uzyskać więcej informacji, zobacz [strcoll —, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a> CStringT:: CollateNoCase

Porównuje dwa ciągi przy użyciu funkcji generycznej tekstu `_tcscoll` .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Inny ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne (w przypadku ignorowania wielkości liter), < 0, jeśli ten `CStringT` obiekt jest mniejszy niż *PSZ* (bez uwzględnienia wielkości liter) lub > 0, jeśli ten `CStringT` obiekt jest większy niż *PSZ* (bez uwzględnienia wielkości liter).

### <a name="remarks"></a>Uwagi

Funkcja tekstu ogólnego `_tcscoll` , która jest zdefiniowana w używanie TCHAR. H, mapuje do `stricoll` jednego `wcsicoll` lub, lub `_mbsicoll` , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów bez uwzględniania wielkości liter, zgodnie z aktualnie używaną stroną kodową. Aby uzyskać więcej informacji, zobacz [strcoll —, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a> CStringT:: Compare

Porównuje dwa ciągi (z uwzględnieniem wielkości liter).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Inny ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0, jeśli ten `CStringT` obiekt jest mniejszy niż *PSZ*, lub > 0, jeśli ten `CStringT` obiekt jest większy niż *PSZ*.

### <a name="remarks"></a>Uwagi

Funkcja tekstu ogólnego `_tcscmp` , która jest zdefiniowana w używanie TCHAR. H, mapuje do `strcmp` jednego `wcscmp` lub, lub `_mbscmp` , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów z uwzględnieniem wielkości liter i nie wpływa na ustawienia regionalne. Aby uzyskać więcej informacji, zobacz [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Jeśli ciąg zawiera osadzone wartości null, na potrzeby porównania ciąg jest traktowany jako obcięty przy pierwszym osadzonym znaku null.

### <a name="example"></a>Przykład

Poniższy przykład ilustruje użycie `CStringT::Compare` .

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a> CStringT:: CompareNoCase

Porównuje dwa ciągi (bez uwzględniania wielkości liter).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Inny ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne (w przypadku ignorowania wielkości liter), <0, jeśli ten `CStringT` obiekt jest mniejszy niż *PSZ* (bez uwzględnienia wielkości liter) lub >0, jeśli ten `CStringT` obiekt jest większy niż *PSZ* (bez uwzględnienia wielkości liter).

### <a name="remarks"></a>Uwagi

Funkcja tekstu ogólnego `_tcsicmp` , która jest zdefiniowana w używanie TCHAR. H, mapuje do `_stricmp` jednego `_wcsicmp` lub `_mbsicmp` , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów bez uwzględniania wielkości liter. Porównanie jest zależne od LC_CTYPE aspektu ustawień regionalnych, ale nie LC_COLLATE. Aby uzyskać więcej informacji, zobacz [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a> CStringT:: CStringT

Konstruuje `CStringT` obiekt.

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

*PCH*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, a nie zakończony znakiem null.

*nLength*<br/>
Liczba znaków w *PCH*.

*ch*<br/>
Pojedynczy znak.

*pszSrc*<br/>
Ciąg zakończony znakiem null, który ma zostać skopiowany do tego `CStringT` obiektu.

*pStringMgr*<br/>
Wskaźnik do Menedżera pamięci dla `CStringT` obiektu. Aby uzyskać więcej informacji o `IAtlStringMgr` zarządzaniu pamięcią dla programu `CStringT` , zobacz [Zarządzanie pamięcią za pomocą CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Istniejący `CStringT` obiekt do skopiowania do tego `CStringT` obiektu. Aby uzyskać więcej informacji na temat `CThisString` i `CThisSimpleString` , zobacz sekcję Uwagi.

*varSrc*<br/>
Obiekt VARIANT, który ma zostać skopiowany do tego `CStringT` obiektu.

*BaseType*<br/>
Typ znaku klasy String. Może być jedną z następujących czynności:

**`char`** (w przypadku ciągów znaków ANSI).

**`wchar_t`** (w przypadku ciągów znaków Unicode).

Używanie TCHAR (dla ciągów znaków ANSI i Unicode).

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteką DLL MFC (TRUE) czy nie (FALSE).

*SystemString*<br/>
Musi być `System::String` , a projekt musi być skompilowany przy użyciu/CLR.

*pString*<br/>
Uchwyt dla `CStringT` obiektu.

### <a name="remarks"></a>Uwagi

Ponieważ konstruktory kopiuje dane wejściowe do nowego przydzielonego magazynu, należy pamiętać, że mogą wynikać wyjątki pamięci. Należy zauważyć, że niektóre z tych konstruktorów działają jako funkcje konwersji. Pozwala to na przykład zastąpić LPTSTR, gdzie `CStringT` oczekiwany jest obiekt.

- `CStringT`( `LPCSTR` `lpsz` ): Konstruuje Unicode na `CStringT` podstawie ciągu ANSI. Można również użyć tego konstruktora do załadowania zasobu ciągu, jak pokazano w poniższym przykładzie.

- `CStringT(``LPCWSTR` `lpsz` ): Tworzy `CStringT` z ciągu Unicode.

- `CStringT`( `const unsigned char*` `psz` ): Umożliwia utworzenie `CStringT` z wskaźnika do **`unsigned char`** .

> [!NOTE]
> Zdefiniuj makro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION, aby wyłączyć niejawną konwersję ciągów między ciągami ANSI i Unicode. Makro wyklucza z konstruktorów kompilacji, które obsługują konwersję.

Należy pamiętać, że parametr *strSrc* może być `CStringT` `CThisSimpleString` obiektem lub. Dla `CStringT` , użyj jednego z jego domyślnych konkretyzacji ( `CString` , `CStringA` , lub `CStringW` ); w przypadku `CThisSimpleString` , użyj **`this`** wskaźnika. `CThisSimpleString` deklaruje wystąpienie [klasy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md), która jest mniejszą klasą ciągu z mniej wbudowaną funkcjonalnością niż `CStringT` Klasa.

Operator przeciążenia `CSimpleStringT<>&()` konstruuje `CStringT` obiekt z `CSimpleStringT` deklaracji.

> [!NOTE]
> Chociaż istnieje możliwość utworzenia `CStringT` wystąpień zawierających osadzone znaki o wartości null, zalecamy ich użycie. Wywoływanie metod i operatorów dla `CStringT` obiektów, które zawierają osadzone znaki null, może dawać niezamierzone wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a> CStringT:: ~ CStringT

Niszczy `CStringT` obiekt.

```
~CStringT() throw();
```

### <a name="remarks"></a>Uwagi

Niszczy `CStringT` obiekt.

## <a name="cstringtdelete"></a><a name="delete"></a> CStringT::D Usuń

Usuwa znak lub znaki z ciągu, rozpoczynając od znaku w danym indeksie.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Indeks (liczony od zera) pierwszego znaku w `CStringT` obiekcie do usunięcia.

*nCount*<br/>
Liczba znaków do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Długość zmienionego ciągu.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* jest dłuższa niż ciąg, pozostała część ciągu zostanie usunięta.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a> CStringT:: find

Wyszukuje w ciągu pierwsze dopasowanie znaku lub podciągu.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parametry

*pszSub*<br/>
Podciąg, który ma zostać wyszukany.

*isrozpoczęcia*<br/>
Indeks znaku w ciągu, w którym rozpoczyna się wyszukiwanie, lub 0, aby zacząć od początku.

*ch*<br/>
Pojedynczy znak do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) pierwszego znaku w tym `CStringT` obiekcie, który pasuje do żądanego podciągu lub znaków;-1, jeśli nie odnaleziono podciągu lub znaku.

### <a name="remarks"></a>Uwagi

Funkcja jest przeciążona, aby akceptować zarówno pojedyncze znaki (podobne do funkcji Run-Time `strchr` ), jak i ciągi (podobnie jak w przypadku `strstr` ).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a> CStringT:: FindOneOf

Wyszukuje ten ciąg dla pierwszego znaku, który pasuje do dowolnego znaku zawartego w *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg zawierający znaki do dopasowania.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) pierwszego znaku w tym ciągu, który jest również w *pszCharSet*; -1, jeśli nie ma żadnego dopasowania.

### <a name="remarks"></a>Uwagi

Znajduje pierwsze wystąpienie dowolnego ze znaków w *pszCharSet*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a> CStringT:: format

Zapisuje sformatowane dane w taki `CStringT` sam sposób, w jaki [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formatuje dane w tablicy znaków w stylu C.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identyfikator zasobu ciągu, który zawiera ciąg kontrolny formatu.

*pszFormat*<br/>
Ciąg kontrolny formatu.

*argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Ta funkcja formatuje i przechowuje serie znaków i wartości w `CStringT` . Każdy opcjonalny argument (jeśli istnieje) jest konwertowany i wyprowadzany zgodnie ze specyfikacją formatu w *pszFormat* lub z zasobu ciągu identyfikowanego przez *nFormatID*.

Wywołanie zakończy się niepowodzeniem, jeśli obiekt ciągu jest oferowany jako parametr do `Format` . Na przykład poniższy kod spowoduje nieprzewidywalne wyniki:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Aby uzyskać więcej informacji, zobacz [składnia specyfikacji formatowania: printf i wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a> CStringT:: FormatMessage

Formatuje ciąg komunikatu.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identyfikator zasobu ciągu, który zawiera niesformatowany tekst komunikatu.

*pszFormat*<br/>
Wskazuje ciąg kontrolny formatu. Zostanie ona przeskanowana pod kątem wstawiania i sformatowanego odpowiednio. Ciąg formatu jest podobny do *printf*ciągów formatu w funkcji czasu wykonywania, z wyjątkiem tego, że umożliwia wstawianie parametrów w dowolnej kolejności.

*argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Funkcja wymaga definicji komunikatu jako dane wejściowe. Definicja komunikatu jest określana przez *pszFormat* lub z zasobu ciągu identyfikowanego przez *nFormatID*. Funkcja kopiuje sformatowany tekst komunikatu do `CStringT` obiektu, przetwarzając w razie potrzeby wszystkie osadzone sekwencje wstawiania.

> [!NOTE]
> `FormatMessage` próbuje przydzielić pamięć systemową dla nowo sformatowanego ciągu. Jeśli ta próba nie powiedzie się, zostanie automatycznie wygenerowany wyjątek pamięci.

Każdy element INSERT musi mieć odpowiadający mu parametr, który jest zgodny z parametrem *pszFormat* lub *nFormatID* . W tekście komunikatu są obsługiwane różne sekwencje unikowe umożliwiające dynamiczne formatowanie wiadomości. Aby uzyskać więcej informacji, zobacz Funkcja [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) systemu Windows w Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a> CStringT:: FormatMessageV

Formatuje ciąg komunikatu przy użyciu listy zmiennych argumentów.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Wskazuje ciąg kontrolny formatu. Zostanie ona przeskanowana pod kątem wstawiania i sformatowanego odpowiednio. Ciąg formatu jest podobny do ciągów formatu w czasie wykonywania `printf` , z tą różnicą, że umożliwia wstawianie parametrów w dowolnej kolejności.

*pArgList*<br/>
Wskaźnik na listę argumentów.

### <a name="remarks"></a>Uwagi

Funkcja wymaga definicji komunikatu jako dane wejściowe, określonej przez *pszFormat*. Funkcja kopiuje sformatowany tekst komunikatu i zmienną listę argumentów do `CStringT` obiektu, przetwarzając wszystkie osadzone sekwencje wstawiania w razie potrzeby.

> [!NOTE]
> `FormatMessageV` wywołuje [CStringT:: FormatMessage](#formatmessage), które próbuje przydzielić pamięć systemową dla nowo sformatowanego ciągu. Jeśli ta próba nie powiedzie się, zostanie automatycznie wygenerowany wyjątek pamięci.

Aby uzyskać więcej informacji, zobacz Funkcja [FormatMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) systemu Windows w Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a> CStringT:: FormatV

Formatuje ciąg komunikatu przy użyciu listy zmiennych argumentów.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Wskazuje ciąg kontrolny formatu. Zostanie ona przeskanowana pod kątem wstawiania i sformatowanego odpowiednio. Ciąg formatu jest podobny do ciągów formatu w czasie wykonywania `printf` , z tą różnicą, że umożliwia wstawianie parametrów w dowolnej kolejności.

*argumentów*<br/>
Wskaźnik na listę argumentów.

### <a name="remarks"></a>Uwagi

Zapisuje sformatowany ciąg i zmienną listę argumentów do `CStringT` ciągu w taki sam sposób, w jaki `vsprintf_s` formatuje dane w tablicy znaków w stylu C.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a> CStringT:: GetEnvironmentVariable

Ustawia ciąg na wartość określonej zmiennej środowiskowej.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parametry

*pszVar*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa zmienną środowiskową.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli pomyślne; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobiera wartość określonej zmiennej z bloku środowiska procesu wywołującego. Wartość jest w postaci ciągu znaków zakończonych znakiem null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a> CStringT:: INSERT

Wstawia pojedynczy znak lub podciąg w danym indeksie w ciągu.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Indeks znaku, przed którym zostanie wykonane Wstawianie.

*psz*<br/>
Wskaźnik do znacznika podciągu, który ma zostać wstawiony.

*ch*<br/>
Znak, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Długość zmienionego ciągu.

### <a name="remarks"></a>Uwagi

Parametr *IIndex* określa pierwszy znak, który zostanie przeniesiony, aby zwolnić miejsce na znak lub podciąg. Jeśli *nIndex* ma wartość zero, wstawianie zostanie przeprowadzone przed całym ciągiem. Jeśli wartość *nIndex* jest większa niż długość ciągu, funkcja łączy obecny ciąg i nowy materiał dostarczony przez *ch* lub *PSZ*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a> CStringT:: Left

Wyodrębnia skrajne znaki *nCount* z tego `CStringT` obiektu i zwraca kopię wyodrębnionego podciągu.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Liczba znaków do wyodrębnienia z tego `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

`CStringT`Obiekt, który zawiera kopię określonego zakresu znaków. Zwrócony `CStringT` obiekt może być pusty.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* przekracza długość ciągu, cały ciąg zostanie wyodrębniony. `Left` jest podobna do funkcji Basic `Left` .

W przypadku zestawów znaków wielobajtowych (MBCS) *nCount* traktuje każdą 8-bitową sekwencję jako znak, tak że *nCount* zwraca liczbę znaków wielobajtowych pomnożonych przez dwa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a> CStringT:: LoadString

Odczytuje zasób ciągu systemu Windows identyfikowany przez *NID*w istniejącym `CStringT` obiekcie.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście do wystąpienia modułu.

*nID*<br/>
Identyfikator zasobu ciągu systemu Windows.

*wLanguageID*<br/>
Język zasobu ciągu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obciążenie zasobów zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ładuje zasób ciągu (*NID*) z określonego modułu (*HINSTANCE*) przy użyciu określonego języka (*wLanguage*).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a> CStringT:: MakeLower

Konwertuje `CStringT` obiekt na ciąg małymi literami.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg z małymi literami.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a> CStringT:: MakeReverse

Odwraca kolejność znaków w `CStringT` obiekcie.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg odwrócony.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a> CStringT:: MakeUpper

Konwertuje `CStringT` obiekt na ciąg pisany wielką literą.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Wartość zwracana

Ciąg z wielką literą.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a> CStringT:: Mid

Wyodrębnia podciąg o długości *nCount* znaków z tego `CStringT` obiektu, zaczynając od pozycji *iFirst* (liczony od zera).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parametry

*iFirst*<br/>
Indeks (liczony od zera) pierwszego znaku w tym `CStringT` obiekcie, który ma być uwzględniony w wyodrębnionym podciągu.

*nCount*<br/>
Liczba znaków do wyodrębnienia z tego `CStringT` obiektu. Jeśli ten parametr nie zostanie podany, zostanie wyodrębniona pozostała część ciągu.

### <a name="return-value"></a>Wartość zwracana

`CStringT`Obiekt, który zawiera kopię określonego zakresu znaków. Zwróć uwagę, że zwrócony `CStringT` obiekt może być pusty.

### <a name="remarks"></a>Uwagi

Funkcja zwraca kopię wyodrębnionego podciągu. `Mid` jest podobna do podstawowej funkcji Mid (z tą różnicą, że indeksy w warstwie Podstawowa są oparte na jednym z nich).

Dla zestawów znaków wielobajtowych (MBCS) *nCount* odnosi się do każdego znaku 8-bitowego; oznacza to, że bajty wiodące i końcowe w jednym znaku wielobajtowym są zliczane jako dwa znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a> CStringT:: OemToAnsi

Konwertuje wszystkie znaki w tym `CStringT` obiekcie ze znaku OEM ustawionym na zestaw znaków ANSI.

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest niedostępna, jeśli określono _UNICODE.

### <a name="example"></a>Przykład

Zobacz przykład dla [CStringT:: AnsiToOem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a> CStringT:: operator =

Przypisuje nową wartość do ciągu.

```
CStringT& operator=(const CStringT& strSrc);

template<bool bMFCDLL>
CStringT& operator=(const CSimpleStringT<BaseType, bMFCDLL>& str);

CStringT& operator=(PCXSTR pszSrc);
CStringT& operator=(PCYSTR pszSrc);
CStringT& operator=(const unsigned char* pszSrc);
CStringT& operator=(XCHAR ch);
CStringT& operator=(YCHAR ch);
CStringT& operator=(const VARIANT& var);
```

### <a name="parameters"></a>Parametry

*strSrc*<br/>
A, `CStringT` Aby przypisać do tego ciągu.

*str*<br/>
Odwołanie do `CThisSimpleString` obiektu.

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteką MFC DLL, czy nie.

*BaseType*<br/>
Typ podstawowy ciągu.

*funkcję*<br/>
Obiekt VARIANT, który ma zostać przypisany do tego ciągu.

*ch*<br/>
Znak ANSI lub Unicode, który ma zostać przypisany do ciągu.

*pszSrc*<br/>
Wskaźnik do przydzielonego pierwotnego ciągu.

### <a name="remarks"></a>Uwagi

Operator przypisania akceptuje inny `CStringT` obiekt, wskaźnik znaku lub pojedynczy znak. Należy pamiętać, że wyjątki pamięci mogą wystąpić przy każdym użyciu tego operatora, ponieważ można przydzielyć nowy magazyn.

Aby uzyskać informacje na temat `CThisSimpleString` , zobacz sekcję Uwagi w [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Chociaż istnieje możliwość utworzenia `CStringT` wystąpień zawierających osadzone znaki o wartości null, zalecamy ich użycie. Wywoływanie metod i operatorów dla `CStringT` obiektów, które zawierają osadzone znaki null, może dawać niezamierzone wyniki.

## <a name="cstringtoperator-"></a><a name="operator_add"></a> CStringT:: operator +

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

*CH1*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*CH2*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*str1*<br/>
A, aby połączyć się `CStringT` z ciągiem lub znakiem.

*str2*<br/>
A, aby połączyć się `CStringT` z ciągiem lub znakiem.

*psz1*<br/>
Wskaźnik do ciągu zakończonego wartością null, który łączy się z ciągiem lub znakiem.

*psz2*<br/>
Wskaźnik do ciągu, który łączy się z ciągiem lub znakiem.

### <a name="remarks"></a>Uwagi

Istnieją siedem przeciążeń `CStringT::operator+` funkcji. Pierwsza wersja łączy dwa istniejące `CStringT` obiekty. Następne dwa złączą `CStringT` obiekt i ciąg zakończony znakiem null. Następne dwa złączy `CStringT` obiekt i znak ANSI. Ostatnie dwa złączy `CStringT` obiekt i znak Unicode.

> [!NOTE]
> Chociaż istnieje możliwość utworzenia `CStringT` wystąpień zawierających osadzone znaki o wartości null, zalecamy ich użycie. Wywoływanie metod i operatorów dla `CStringT` obiektów, które zawierają osadzone znaki null, może dawać niezamierzone wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a> CStringT:: operator + =

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

*str*<br/>
Odwołanie do `CThisSimpleString` obiektu.

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteką MFC DLL, czy nie.

*BaseType*<br/>
Typ podstawowy ciągu.

*funkcję*<br/>
Obiekt Variant do łączenia z tym ciągiem.

*ch*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*pszSrc*<br/>
Wskaźnik do połączonego ciągu pierwotnego.

*strSrc*<br/>
A, `CStringT` Aby połączyć się z tym ciągiem.

### <a name="remarks"></a>Uwagi

Operator akceptuje inny `CStringT` obiekt, wskaźnik znaku lub pojedynczy znak. Należy pamiętać, że wyjątki pamięci mogą wystąpić za każdym razem, gdy korzystasz z tego operatora łączenia, ponieważ nowy magazyn może być przydzielony do znaków dodanych do tego `CStringT` obiektu.

Aby uzyskać informacje na temat `CThisSimpleString` , zobacz sekcję Uwagi w [CStringT:: CStringT](#cstringt).

> [!NOTE]
> Chociaż istnieje możliwość utworzenia `CStringT` wystąpień zawierających osadzone znaki o wartości null, zalecamy ich użycie. Wywoływanie metod i operatorów dla `CStringT` obiektów, które zawierają osadzone znaki null, może dawać niezamierzone wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a> CStringT:: operator = =

Określa, czy dwa ciągi są logicznie równe.

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

*CH1*<br/>
Znak ANSI lub Unicode do porównania.

*CH2*<br/>
Znak ANSI lub Unicode do porównania.

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Testuje, czy ciąg lub znak po lewej stronie jest równy ciągowi lub znakowi po prawej stronie, i zwraca wartość PRAWDA lub FAŁSZ.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a> CStringT:: operator! =

Określa, czy dwa ciągi są logicznie nierówne.

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

*CH1*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*CH2*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Testuje, czy ciąg lub znak po lewej stronie nie są równe ciągowi lub znakowi po prawej stronie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a> CStringT:: operator &lt;

Określa, czy ciąg po lewej stronie operatora jest mniejszy od ciągu po prawej stronie.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami znaków, znak po znaku do:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, dlatego ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a> CStringT:: operator &gt;

Określa, czy ciąg po lewej stronie operatora jest większy niż ciąg po prawej stronie.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami znaków, znak po znaku do:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a> CStringT:: operator &lt;=

Określa, czy ciąg po lewej stronie operatora jest mniejszy od lub równy ciągowi po prawej stronie.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami znaków, znak po znaku do:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a> CStringT:: operator &gt;=

Określa, czy ciąg po lewej stronie operatora jest większy od lub równy ciągowi po prawej stronie.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik do ciągu do porównania.

*psz2*<br/>
Wskaźnik do ciągu do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami znaków, znak po znaku do:

- Znajduje dwa odpowiednie znaki nierówne, a wynik porównania jest traktowany jako wynik porównania między ciągami.

- Nie ma żadnej nierówności, ale jeden ciąg ma więcej znaków niż drugi, a krótszy ciąg jest uznawany za krótszy niż dłuższy ciąg.

- Nie ma żadnej nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a> CStringT:: Remove

Usuwa wszystkie wystąpienia określonego znaku z ciągu.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parametry

*chRemove*<br/>
Znak, który ma zostać usunięty z ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków usuniętych z ciągu. Zero, jeśli ciąg nie jest zmieniany.

### <a name="remarks"></a>Uwagi

Porównania dla tego znaku są rozróżniana wielkość liter.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a> CStringT:: Replace

Istnieją dwie wersje programu `Replace` . Pierwsza wersja zastępuje jedną lub więcej kopii podciągu przy użyciu innego podciągu. Oba podciągi są zakończone wartością null. Druga wersja zastępuje jedną lub więcej kopii znaku przy użyciu innego znaku. Obie wersje działają na danych znakowych przechowywanych w `CStringT` .

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parametry

*pszOld*<br/>
Wskaźnik do ciągu zakończonego wartością null, który ma zostać zastąpiony przez *pszNew*.

*pszNew*<br/>
Wskaźnik do ciągu zakończonego wartością null, który zastępuje *pszOld*.

*chOld*<br/>
Znak, który ma zostać zastąpiony przez *chNew*.

*chNew*<br/>
Znak zastępujący *chOld*.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę zamienionych wystąpień znaku lub podciągu lub zero, jeśli ciąg nie został zmieniony.

### <a name="remarks"></a>Uwagi

`Replace` można zmienić długość ciągu, ponieważ *pszNew* i *pszOld* nie muszą mieć takiej samej długości, a kilka kopii starego podciągu można zmienić na nowy. Funkcja wykonuje dopasowanie uwzględniające wielkość liter.

Przykłady `CStringT` wystąpień to `CString` , `CStringA` i `CStringW` .

Dla `CStringA` , `Replace` działa z znakami ANSI lub wielobajtowymi (MBCS). Dla programu `CStringW` , `Replace` działa z szeroką literą.

W przypadku `CString` , typ danych znakowych jest wybierany w czasie kompilacji, na podstawie tego, czy są zdefiniowane stałe w poniższej tabeli.

|Zdefiniowana stała|Character — typ danych|
|----------------------|-------------------------|
|_UNICODE|Znaki dwubajtowe|
|_MBCS|Znaki wielobajtowe|
|Żadna|Znaki jednobajtowe|
|Oba|Niezdefiniowane|

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a> CStringT:: ReverseFind

Przeszukuje ten `CStringT` obiekt pod kątem ostatniego dopasowania znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak, który ma zostać wyszukany.

### <a name="return-value"></a>Wartość zwracana

Indeks (liczony od zera) ostatniego znaku w tym `CStringT` obiekcie, który pasuje do żądanego znaku lub-1, jeśli znak nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Funkcja jest podobna do funkcji Run-Time `strrchr` .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a> CStringT:: Right

Wyodrębnia ostatnią (czyli po prawej) znaki *nCount* z tego `CStringT` obiektu i zwraca kopię wyodrębnionego podciągu.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Liczba znaków do wyodrębnienia z tego `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

`CStringT`Obiekt, który zawiera kopię określonego zakresu znaków. Zwróć uwagę, że zwrócony `CStringT` obiekt może być pusty.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* przekracza długość ciągu, cały ciąg zostanie wyodrębniony. `Right` jest podobna do funkcji Basic `Right` (z tą różnicą, że indeksy w warstwie Podstawowa nie są oparte na zero).

Dla zestawów znaków wielobajtowych (MBCS) *nCount* odnosi się do każdego znaku 8-bitowego; oznacza to, że bajty wiodące i końcowe w jednym znaku wielobajtowym są zliczane jako dwa znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a> CStringT:: SetSysString

Ponownie przydziela element BSTR wskazywany przez *pbstr* i kopiuje do `CStringT` niego zawartość obiektu, w tym znak null.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
Wskaźnik do ciągu znaków.

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg.

### <a name="remarks"></a>Uwagi

W zależności od zawartości `CStringT` obiektu można zmienić wartość elementu BSTR, do którego odwołuje się *pbstr* . Funkcja zgłasza, `CMemoryException` Jeśli istnieje niewystarczająca ilość pamięci.

Ta funkcja jest zwykle używana do zmiany wartości ciągów przekazywania przez odwołanie dla automatyzacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a> CStringT:: SpanExcluding

Wyodrębnia znaki z ciągu, zaczynając od pierwszego znaku, które nie znajdują się w zestawie znaków identyfikowanych przez *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg interpretowany jako zestaw znaków.

### <a name="return-value"></a>Wartość zwracana

Podciąg, który zawiera znaki w ciągu, które nie znajdują się w *pszCharSet*, zaczynając od pierwszego znaku w ciągu i kończąc na pierwszym znaku znalezionym w ciągu, który jest również w *pszCharSet* (to jest, zaczynając od pierwszego znaku w ciągu i aż do wykluczenia pierwszego znaku w ciągu, który został znaleziony *pszCharSet*). Zwraca cały ciąg, jeśli w ciągu nie znaleziono żadnego znaku w *pszCharSet* .

### <a name="remarks"></a>Uwagi

`SpanExcluding` wyodrębnia i zwraca wszystkie znaki poprzedzające pierwsze wystąpienie znaku z *pszCharSet* (innymi słowy, znak z *pszCharSet* i wszystkie znaki po nim w ciągu, nie są zwracane). Jeśli w ciągu nie zostanie znaleziony żaden znak z *pszCharSet* , `SpanExcluding` funkcja zwróci cały ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a> CStringT:: SpanIncluding

Wyodrębnia znaki z ciągu, zaczynając od pierwszego znaku, które znajdują się w zestawie znaków identyfikowanych przez *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg interpretowany jako zestaw znaków.

### <a name="return-value"></a>Wartość zwracana

Podciąg zawierający znaki w ciągu, który znajduje się w *pszCharSet*, zaczynając od pierwszego znaku w ciągu i kończąc, gdy znak zostanie znaleziony w ciągu, który nie znajduje się w *pszCharSet*. `SpanIncluding` zwraca pusty ciąg, jeśli pierwszy znak w ciągu nie znajduje się w określonym zestawie.

### <a name="remarks"></a>Uwagi

Jeśli pierwszy znak ciągu nie znajduje się w zestawie znaków, `SpanIncluding` zwracany jest pusty ciąg. W przeciwnym razie zwraca sekwencję kolejnych znaków, które znajdują się w zestawie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a> CStringT:: tokenize

Znajduje następny token w ciągu docelowym

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parametry

*pszTokens*<br/>
Ciąg zawierający ograniczniki tokenu. Kolejność tych ograniczników nie jest ważna.

*isrozpoczęcia*<br/>
Indeks liczony od zera, aby rozpocząć wyszukiwanie.

### <a name="return-value"></a>Wartość zwracana

`CStringT`Obiekt zawierający bieżącą wartość tokenu.

### <a name="remarks"></a>Uwagi

`Tokenize`Funkcja znajduje następny token w ciągu docelowym. Zestaw znaków w *pszTokens* określa możliwe ograniczniki tokenu, który ma zostać znaleziony. Dla każdego wywołania `Tokenize` funkcji rozpoczyna się na isstartu, pomija wiodące ograniczniki i zwraca *iStart* `CStringT` obiekt zawierający bieżący token, który jest ciągiem znaków do następnego znaku ogranicznika. Wartość parametru ispoczątek zostaje zaktualizowana *tak, aby była* pozycją po znaku ogranicznika końcowego, lub-1, jeśli osiągnięto koniec ciągu. Więcej tokenów można rozbić z reszty ciągu docelowego przez serię wywołań do `Tokenize` , za pomocą funkcji ispoczątku *iStart* , aby śledzić miejsce w ciągu, w którym ma zostać odczytany następny token. Gdy nie ma więcej tokenów, funkcja zwróci pusty ciąg, a parametr *isrozpoczęcia* zostanie ustawiony na wartość-1.

W przeciwieństwie do funkcji CRT tokenize, takich jak [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), nie `Tokenize` modyfikuje ciągu docelowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu są następujące:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a> CStringT:: Trim

Przycina wiodące i końcowe znaki z ciągu.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowy, który ma zostać przycięty.

*pszTargets*<br/>
Wskaźnik do ciągu zawierającego znaki docelowe do przycięcia. Wszystkie początkowe i końcowe wystąpienia znaków w *pszTarget* zostaną przycięte z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca przycięty ciąg.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie wystąpienia wiodące i końcowe jednego z następujących elementów:

- Znak określony przez *chTarget*.

- Wszystkie znaki Znalezione w ciągu określonym przez *pszTargets*.

- Odstępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu są następujące:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a> CStringT:: TrimLeft

Przycina znaki wiodące z ciągu.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowy, który ma zostać przycięty.

*pszTargets*<br/>
Wskaźnik do ciągu zawierającego znaki docelowe do przycięcia. Wszystkie wiodące wystąpienia znaków w *pszTarget* zostaną przycięte z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Otrzymany ciąg, który został usunięty.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie wystąpienia wiodące i końcowe jednego z następujących elementów:

- Znak określony przez *chTarget*.

- Wszystkie znaki Znalezione w ciągu określonym przez *pszTargets*.

- Odstępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a> CStringT:: TrimRight

Przycina końcowe znaki z ciągu.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowy, który ma zostać przycięty.

*pszTargets*<br/>
Wskaźnik do ciągu zawierającego znaki docelowe do przycięcia. Wszystkie końcowe wystąpienia znaków w *pszTarget* zostaną przycięte z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CStringT` obiekt, który zawiera przycięty ciąg.

### <a name="remarks"></a>Uwagi

Usuwa końcowe wystąpienia jednego z następujących elementów:

- Znak określony przez *chTarget*.

- Wszystkie znaki Znalezione w ciągu określonym przez *pszTargets*.

- Odstępu.

`CStringT& TrimRight(XCHAR chTarget)`Wersja akceptuje jeden parametr znaku i usuwa wszystkie kopie tego znaku z końca `CStringT` danych ciągu. Zaczyna się od końca ciągu i działa ku przodowi. Jest ona zatrzymywana, gdy odnajdzie inny znak lub gdy `CSTringT` kończy się znakiem danych.

`CStringT& TrimRight(PCXSTR pszTargets)`Wersja akceptuje ciąg zakończony znakiem null, który zawiera wszystkie różne znaki do wyszukania. Usuwa wszystkie kopie tych znaków w `CStringT` obiekcie. Rozpocznie się na końcu ciągu i działa ku przodowi. Kończy się po znalezieniu znaku, który nie znajduje się w ciągu docelowym, lub gdy nie są używane `CStringT` dane znakowe. Nie próbuje dopasować całego docelowego ciągu do podciągu na końcu `CStringT` .

`CStringT& TrimRight()`Wersja nie wymaga żadnych parametrów. Obcina końcowe znaki odstępu od końca `CStringT` ciągu. Znaki odstępu mogą być podziałami wierszy, spacjami lub znakami tabulacji.

-

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy udostępnione ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[Klasa CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)
