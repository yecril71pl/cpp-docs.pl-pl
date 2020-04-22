---
title: CStringT, klasa
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
ms.openlocfilehash: 8fcce4c426cd99785d34dc080f238cc78cdfee36
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746710"
---
# <a name="cstringt-class"></a>CStringT, klasa

Ta klasa `CStringT` reprezentuje obiekt.

## <a name="syntax"></a>Składnia

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasy string. Może być jedną z następujących czynności:

- **char** (dla ciągów znaków ANSI).

- **wchar_t** (dla ciągów znaków Unicode).

- TCHAR (dla ciągów znaków ANSI i Unicode).

*StringTraits (StringTraits)*<br/>
Określa, czy klasa ciągu wymaga obsługi biblioteki c run-time (CRT) i gdzie znajdują się zasoby ciągów. Może być jedną z następujących czynności:

- **StrTraitATL< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Klasa wymaga obsługi CRT i wyszukuje ciągi zasobów w module określonym przez `m_hInstResource` (element członkowski klasy modułu aplikacji).

- **StrTraitATL< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Klasa nie wymaga obsługi CRT i wyszukuje ciągi zasobów w module określonym przez `m_hInstResource` (element członkowski klasy modułu aplikacji).

- **StrTraitMFC< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT< wchar_t** &#124; **char** &#124; **TCHAR > >**

   Klasa wymaga obsługi CRT i wyszukuje ciągi zasobów przy użyciu standardowego algorytmu wyszukiwania MFC.

- **StrTraitMFC< wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS< wchar_t &#124;** **char** &#124; **TCHAR > >**

   Klasa nie wymaga obsługi CRT i wyszukuje ciągi zasobów przy użyciu standardowego algorytmu wyszukiwania MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Konstruuje `CStringT` obiekt na różne sposoby.|
|[CStringT::~CStringT](#_dtorcstringt)|Niszczy `CStringT` obiekt.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Przydziela BSTR z `CStringT` danych.|
|[CStringT::AnsiToOem](#ansitooem)|Dokonuje konwersji w miejscu z zestawu znaków ANSI do zestawu znaków OEM.|
|[CStringT::Dołączformat](#appendformat)|Dołącza sformatowane dane `CStringT` do istniejącego obiektu.|
|[CStringT::Sortuj](#collate)|Porównuje dwa ciągi (wielkość liter, używa informacji specyficznych dla ustawień regionalnych).|
|[CStringT::CollateNoCase](#collatenocase)|Porównuje dwa ciągi (bez uwzględniania wielkości liter, używa informacji specyficznych dla ustawień regionalnych).|
|[CStringT::Porównaj](#compare)|Porównuje dwa ciągi (z uwzględnieniem wielkości liter).|
|[CStringT::CompareNoCase](#comparenocase)|Porównuje dwa ciągi (bez uwzględniania wielkości liter).|
|[CStringT::Delete](#delete)|Usuwa znak lub znaki z ciągu.|
|[CStringT::Znajdź](#find)|Znajduje znak lub podciąg wewnątrz większego ciągu.|
|[CStringT::FindOneOf](#findoneof)|Znajduje pierwszy pasujący znak z zestawu.|
|[CStringT::Format](#format)|Formatuje ciąg `sprintf` tak samo jak ten.|
|[CStringT::FormatMessage](#formatmessage)|Formatuje ciąg wiadomości.|
|[CStringT::FormatMessageV](#formatmessagev)|Formatuje ciąg wiadomości przy użyciu listy argumentów zmiennej.|
|[CStringT::FormatV](#formatv)|Formatuje ciąg przy użyciu listy argumentów zmiennych.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Ustawia ciąg na wartość określonej zmiennej środowiskowej.|
|[CStringT::Wstaw](#insert)|Wstawia pojedynczy znak lub podciąg w danym indeksie w ciągu.|
|[CStringT::Po lewej](#left)|Wyodrębnia lewą część ciągu.|
|[CStringT::LoadString](#loadstring)|Ładuje istniejący `CStringT` obiekt z zasobu systemu Windows.|
|[CStringT::MakeLower](#makelower)|Konwertuje wszystkie znaki w tym ciągu na małe litery.|
|[CStringT::MakeReverse](#makereverse)|Odwraca ciąg.|
|[CStringt::MakeUpper](#makeupper)|Konwertuje wszystkie znaki w tym ciągu na wielkie litery.|
|[CStringT::Mid](#mid)|Wyodrębnia środkową część ciągu.|
|[CStringT::OemToAnsi](#oemtoansi)|Dokonuje konwersji w miejscu z zestawu znaków OEM do zestawu znaków ANSI.|
|[CStringT::Usuń](#remove)|Usuwa wskazane znaki z ciągu.|
|[CStringT::Zamień](#replace)|Zastępuje wskazane znaki innymi znakami.|
|[CStringT::ReverseFind](#reversefind)|Znajduje znak wewnątrz większego ciągu; zaczyna się od końca.|
|[CStringT::Prawy](#right)|Wyodrębnia prawą część ciągu.|
|[CStringT::SetSysString](#setsysstring)|Ustawia istniejący obiekt BSTR `CStringT` z danymi z obiektu.|
|[CStringT::SpanExcluding](#spanexcluding)|Wyodrębnia znaki z ciągu, zaczynając od pierwszego znaku, które nie `pszCharSet`znajdują się w zestawie znaków identyfikowanych przez .|
|[CStringT::SpanWcluding](#spanincluding)|Wyodrębnia podciąg, który zawiera tylko znaki w zestawie.|
|[CStringT::Tokenize](#tokenize)|Wyodrębnia określone tokeny w ciągu docelowym.|
|[CStringT::Przytnij](#trim)|Przycina wszystkie znaki odstępu początkowego i końcowego z ciągu.|
|[CStringT::TrimLeft](#trimleft)|Przycina wiodące znaki odstępu z ciągu.|
|[CStringT::TrimRight](#trimright)|Przycina końcowe znaki odstępu z ciągu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[CStringT::operator =](#operator_eq)|Przypisuje nową wartość do `CStringT` obiektu.|
|[CStringT::operator +](#operator_add)|Łączy dwa ciągi znaków lub znak i ciąg.|
|[CStringT::operator +=](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CStringT::operator ==](#operator_eq_eq)|Określa, czy dwa ciągi są logicznie równe.|
|[CStringT::operator !=](#operator_neq)|Określa, czy dwa ciągi logicznie nie są równe.|
|[CStringT::operator&lt;](#operator_lt)|Określa, czy ciąg po lewej stronie operatora jest mniejsza niż ciąg po prawej stronie.|
|[CStringT::operator&gt;](#operator_gt)|Określa, czy ciąg po lewej stronie operatora jest większy niż ciąg po prawej stronie.|
|[CStringT::operator&lt;=](#operator_lt_eq)|Określa, czy ciąg po lewej stronie operatora jest mniejsza lub równa ciąg po prawej stronie.|
|[CStringT::operator&gt;=](#operator_gt_eq)|Określa, czy ciąg po lewej stronie operatora jest większa lub równa ciąg po prawej stronie.|

## <a name="remarks"></a>Uwagi

`CStringT`dziedziczy z [klasy CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md). Zaawansowane funkcje, takie jak manipulowanie znakami, porządkowanie i wyszukiwanie, są implementowane przez `CStringT`polecenie .

> [!NOTE]
> `CStringT`obiekty są w stanie zgłaszać wyjątki. Dzieje się `CStringT` tak, gdy obiekt zabraknie pamięci z jakiegokolwiek powodu.

Obiekt `CStringT` składa się z sekwencji znaków o zmiennej długości. `CStringT`udostępnia funkcje i operatory używające składni podobnej do podstawowej. Konkadyjnie i porównywanie operatorów, `CStringT` wraz z uproszczonym zarządzaniem pamięcią, sprawiają, że obiekty są łatwiejsze w użyciu niż zwykłe tablice znaków.

> [!NOTE]
> Chociaż istnieje możliwość `CStringT` tworzenia wystąpień, które zawierają osadzone znaki null, zaleca się przeciwko niemu. Wywoływanie metod `CStringT` i operatorów na obiektach zawierających osadzone znaki null może tworzyć niezamierzone wyniki.

Za pomocą różnych kombinacji `BaseType` `StringTraits` i `CStringT` parametrów, obiekty mogą być dostępne w następujących typach, które zostały wstępnie zdefiniowane przez biblioteki ATL.

W przypadku korzystania z aplikacji ATL:

`CString`, `CStringA`i `CStringW` są eksportowane z biblioteki DLL MFC (MFC90. DLL), nigdy z bibliotek DLL użytkowników. Odbywa się to, aby zapobiec `CStringT` mnożeniu zdefiniowane.

> [!NOTE]
> Jeśli kod zawiera obejście błędów konsolidatora, który jest opisany w [eksportowanie klas ciągów przy użyciu CStringT](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), należy usunąć ten kod. Nie jest już potrzebny.

Następujące typy ciągów są dostępne w aplikacjach opartych na MFC:

|Typ CStringT|Deklaracji|
|-------------------|-----------------|
|`CStringA`|Ciąg typu znaku ANSI z obsługą CRT.|
|`CStringW`|Ciąg typu znaku Unicode z obsługą CRT.|
|`CString`|Zarówno typy znaków ANSI, jak i Unicode z obsługą CRT.|

Następujące typy ciągów są dostępne w projektach, w których zdefiniowano ATL_CSTRING_NO_CRT:

|Typ CStringT|Deklaracji|
|-------------------|-----------------|
|`CAtlStringA`|Ciąg typu znaku ANSI bez obsługi CRT.|
|`CAtlStringW`|Ciąg typu znaku Unicode bez obsługi CRT.|
|`CAtlString`|Typy znaków ANSI i Unicode bez obsługi CRT.|

Następujące typy ciągów są dostępne w projektach, w których ATL_CSTRING_NO_CRT nie jest zdefiniowany:

|Typ CStringT|Deklaracji|
|-------------------|-----------------|
|`CAtlStringA`|Ciąg typu znaku ANSI z obsługą CRT.|
|`CAtlStringW`|Ciąg typu znaku Unicode z obsługą CRT.|
|`CAtlString`|Zarówno typy znaków ANSI, jak i Unicode z obsługą CRT.|

`CString`obiekty mają również następujące cechy:

- `CStringT`obiekty mogą rosnąć w wyniku operacji łączenia.

- `CStringT`obiekty podążają za "semantyki wartości". Obiekt należy `CStringT` myśleć jako rzeczywisty ciąg, a nie jako wskaźnik do ciągu.

- Można dowolnie `CStringT` zastępować obiekty argumentami `PCXSTR` funkcji.

- Niestandardowe zarządzanie pamięcią dla buforów ciągów. Aby uzyskać więcej informacji, zobacz [Zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>Wstępnie zdefiniowane typy CStringT

Ponieważ `CStringT` używa argumentu szablonu do definiowania typu znaku [(wchar_t](../../c-runtime-library/standard-types.md) lub [char](../../c-runtime-library/standard-types.md)) obsługiwane, typy parametrów metody mogą być skomplikowane czasami. Aby uprościć ten problem, zestaw wstępnie zdefiniowanych typów `CStringT` jest zdefiniowany i używany w całej klasie. W poniższej tabeli wymieniono różne typy:

|Nazwa|Opis|
|----------|-----------------|
|`XCHAR`|Pojedynczy znak **(wchar_t** lub **char)** o tym samym typie `CStringT` znaku co obiekt.|
|`YCHAR`|Pojedynczy znak **(wchar_t** lub **char)** z przeciwległym typem `CStringT` znaku jako obiekt.|
|`PXSTR`|Wskaźnik do ciągu znaków **(wchar_t** lub **char)** o tym samym `CStringT` typie znaku co obiekt.|
|`PYSTR`|Wskaźnik do ciągu znaków **(wchar_t** lub **char)** z przeciwległym `CStringT` typem znaku jako obiekt.|
|`PCXSTR`|Wskaźnik do ciągu znaków **const** **(wchar_t** lub **char)** o tym samym `CStringT` typie znaku co obiekt.|
|`PCYSTR`|Wskaźnik do ciągu znaków **const** **(wchar_t** lub **char)** z przeciwległym `CStringT` typem znaku jako obiekt.|

> [!NOTE]
> Kod, który wcześniej używał `CString` nieudokumentowanych `AssignCopy`metod (takich jak) musi zostać zastąpiony `CStringT` kodem, `GetBuffer` `ReleaseBuffer`który używa następujących udokumentowanych metod (takich jak lub ). Metody te są `CSimpleStringT`dziedziczone z .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[Csimplestringt](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Wymagania

|Nagłówek|Na użytek|
|------------|-------------|
|cstringt.h|Obiekty ciągu tylko do MFC|
|atlstr.h|Obiekty ciągu innych niż MFC|

## <a name="cstringtallocsysstring"></a><a name="allocsysstring"></a>CStringT::AllocSysString

Przydziela ciąg zgodny z automatyzacją typu BSTR i kopiuje do niego zawartość `CStringT` obiektu, w tym kończący się znak null.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Wartość zwracana

Nowo przydzielony ciąg.

### <a name="remarks"></a>Uwagi

W programach MFC [CMemoryException Klasa](../../mfc/reference/cmemoryexception-class.md) jest zgłaszany, jeśli istnieje niewystarczająca ilość pamięci. W programach ATL [CAtlException](../../atl/reference/catlexception-class.md) jest wyrzucany. Ta funkcja jest zwykle używana do zwracania ciągów dla automatyzacji.

Często, jeśli ten ciąg jest przekazywany do funkcji COM jako parametr [in], wymaga to od wywołującego zwolnienia ciągu. Można to zrobić za pomocą [SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring), zgodnie z opisem w windows SDK. Aby uzyskać więcej informacji, zobacz [Przydzielanie i zwalnianie pamięci dla BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Aby uzyskać więcej informacji na temat funkcji alokacji OLE w systemie Windows, zobacz [SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring) w windows SDK.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

## <a name="cstringtansitooem"></a><a name="ansitooem"></a>CStringT::AnsiToOem

Konwertuje wszystkie znaki `CStringT` w tym obiekcie z zestawu znaków ANSI na zestaw znaków OEM.

```cpp
void AnsiToOem();
```

### <a name="remarks"></a>Uwagi

Funkcja nie jest dostępna, jeśli zdefiniowano _UNICODE.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

## <a name="cstringtappendformat"></a><a name="appendformat"></a>CStringT::Dołączformat

Dołącza sformatowane dane `CStringT` do istniejącego obiektu.

```cpp
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg kontroli formatu.

*nFormatID*<br/>
Identyfikator zasobu ciągu zawierający ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Ta funkcja formatuje i dołącza serię znaków i `CStringT`wartości w pliku . Każdy opcjonalny argument (jeśli istnieje) jest konwertowany i dołączany zgodnie z odpowiednią specyfikacją formatu w *pszFormat* lub z zasobu ciągu identyfikowany przez *nFormatID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

## <a name="cstringtcollate"></a><a name="collate"></a>CStringT::Sortuj

Porównuje dwa ciągi przy użyciu `_tcscoll`funkcji tekstu ogólnego .

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Drugi ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < `CStringT` 0, jeśli ten obiekt jest mniejszy niż `CStringT` *psz*, lub > 0, jeśli ten obiekt jest większy niż *psz*.

### <a name="remarks"></a>Uwagi

Funkcja `_tcscoll`tekstu ogólnego , która jest zdefiniowana w TCHAR. H, mapuje `strcoll`na `wcscoll`jeden `_mbscoll`, lub , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów z uwzględnieniem wielkości liter zgodnie ze stroną kodową aktualnie używaną. Aby uzyskać więcej informacji, zobacz [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

## <a name="cstringtcollatenocase"></a><a name="collatenocase"></a>CStringT::CollateNoCase

Porównuje dwa ciągi przy użyciu `_tcscoll`funkcji tekstu ogólnego .

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Drugi ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne (ignorowanie sprawy), `CStringT` < 0, jeśli ten obiekt jest mniejszy niż *psz* (ignorowanie sprawy) lub > 0, jeśli ten `CStringT` obiekt jest większy niż *psz* (ignorowanie sprawy).

### <a name="remarks"></a>Uwagi

Funkcja `_tcscoll`tekstu ogólnego , która jest zdefiniowana w TCHAR. H, mapuje `stricoll`na `wcsicoll`jeden `_mbsicoll`, lub , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie bez uwzględniania wielkości liter ciągów, zgodnie ze stroną kodową aktualnie używaną. Aby uzyskać więcej informacji, zobacz [strcoll, wcscoll, _mbscoll, _strcoll_l, _wcscoll_l, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

## <a name="cstringtcompare"></a><a name="compare"></a>CStringT::Porównaj

Porównuje dwa ciągi (z uwzględnieniem wielkości liter).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Drugi ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < `CStringT` 0, jeśli ten obiekt jest mniejszy niż `CStringT` *psz*, lub > 0, jeśli ten obiekt jest większy niż *psz*.

### <a name="remarks"></a>Uwagi

Funkcja `_tcscmp`tekstu ogólnego , która jest zdefiniowana w TCHAR. H, mapuje `strcmp`na `wcscmp`jeden `_mbscmp`, lub , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów z uwzględnieniem wielkości liter i nie ma na nie wpływu ustawienia regionalne. Aby uzyskać więcej informacji, zobacz [strcmp, wcscmp, _mbscmp](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Jeśli ciąg zawiera osadzone wartości null, na potrzeby porównania ciąg jest uważany za obcięty przy pierwszym osadzonym znaku null.

### <a name="example"></a>Przykład

Poniższy przykład pokazuje użycie `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

## <a name="cstringtcomparenocase"></a><a name="comparenocase"></a>CStringT::CompareNoCase

Porównuje dwa ciągi (bez uwzględniania wielkości liter).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*Psz*<br/>
Drugi ciąg używany do porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne (ignorowanie sprawy), `CStringT` <0, jeśli ten obiekt jest mniejszy niż *psz* (ignorowanie sprawy) lub >0, jeśli ten `CStringT` obiekt jest większy niż *psz* (ignorowanie sprawy).

### <a name="remarks"></a>Uwagi

Funkcja `_tcsicmp`tekstu ogólnego , która jest zdefiniowana w TCHAR. H, mapuje `_stricmp`do `_wcsicmp` `_mbsicmp`jednego lub , w zależności od zestawu znaków, który jest zdefiniowany w czasie kompilacji. Każda funkcja wykonuje porównanie ciągów bez uwzględniania wielkości liter. Porównanie zależy od LC_CTYPE aspektu ustawień regionalnych, ale nie LC_COLLATE. Aby uzyskać więcej informacji, zobacz [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

## <a name="cstringtcstringt"></a><a name="cstringt"></a>CStringT::CStringT

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

*Pch*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, nie zakończonej zerem.

*nLength (nLength)*<br/>
Liczba znaków w *pch*.

*Ch*<br/>
Pojedynczy znak.

*pszsrc*<br/>
Ciąg zakończony z wartością null ma `CStringT` zostać skopiowany do tego obiektu.

*pStringMgr*<br/>
Wskaźnik do menedżera pamięci `CStringT` dla obiektu. Aby uzyskać `IAtlStringMgr` więcej informacji `CStringT`na temat zarządzania pamięcią i zarządzania pamięcią dla , zobacz [Zarządzanie pamięcią z CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc ( strSrc )*<br/>
Istniejący `CStringT` obiekt do skopiowania `CStringT` do tego obiektu. Aby uzyskać `CThisString` więcej `CThisSimpleString`informacji na temat i , zobacz uwagi sekcji.

*varSrc ( varSrc )*<br/>
Obiekt wariantu, który ma `CStringT` zostać skopiowany do tego obiektu.

*BaseType*<br/>
Typ znaku klasy string. Może być jedną z następujących czynności:

**char** (dla ciągów znaków ANSI).

**wchar_t** (dla ciągów znaków Unicode).

TCHAR (dla ciągów znaków ANSI i Unicode).

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteką DLL MFC (PRAWDA), czy nie (FALSE).

*SystemString*<br/>
Musi `System::String`być , a projekt musi być skompilowany z /clr.

*pString*<br/>
Dojście `CStringT` dla obiektu.

### <a name="remarks"></a>Uwagi

Ponieważ konstruktory skopiować dane wejściowe do nowego przydzielonego magazynu, należy pamiętać, że wyjątki pamięci może spowodować. Należy zauważyć, że niektóre z tych konstruktorów działają jako funkcje konwersji. Dzięki temu można zastąpić, na przykład, LPTSTR, gdzie `CStringT` oczekuje się obiektu.

- `CStringT`( `LPCSTR` `lpsz` ): Tworzy Unicode `CStringT` z ciągu ANSI. Można również użyć tego konstruktora, aby załadować zasób ciągu, jak pokazano w poniższym przykładzie.

- `CStringT(`): Tworzy `CStringT` ciąg Unicode. `LPCWSTR` `lpsz`

- `CStringT`( `const unsigned char*` `psz` ): Umożliwia skonstruowanie `CStringT` od wskaźnika do **niepodpisanego znaku**.

> [!NOTE]
> Zdefiniuj makro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION, aby wyłączyć niejawną konwersję ciągów między ciągami ANSI i Unicode. Makro wyklucza z konstruktorów kompilacji, które obsługują konwersji.

Należy zauważyć, że parametr *strSrc* `CThisSimpleString` może być albo obiektem. `CStringT` W `CStringT`przypadku , użyj jednego z`CString` `CStringA`jego `CStringW`domyślnych wystąpienia ( , , lub ); for `CThisSimpleString`, użyj **tego** wskaźnika. `CThisSimpleString`deklaruje wystąpienie [CSimpleStringT Class](../../atl-mfc-shared/reference/csimplestringt-class.md), która jest mniejszą klasą ciągu z `CStringT` mniej wbudowaną funkcjonalnością niż klasa.

Operator przeciążenia `CSimpleStringT<>&()` konstruuje `CSimpleStringT` `CStringT` obiekt z deklaracji.

> [!NOTE]
> Chociaż istnieje możliwość `CStringT` tworzenia wystąpień, które zawierają osadzone znaki null, zaleca się przeciwko niemu. Wywoływanie metod `CStringT` i operatorów na obiektach zawierających osadzone znaki null może tworzyć niezamierzone wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

## <a name="cstringtcstringt"></a><a name="_dtorcstringt"></a>CStringT::~CStringT

Niszczy `CStringT` obiekt.

```
~CStringT() throw();
```

### <a name="remarks"></a>Uwagi

Niszczy `CStringT` obiekt.

## <a name="cstringtdelete"></a><a name="delete"></a>CStringT::Delete

Usuwa znak lub znaki z ciągu, począwszy od znaku w danym indeksie.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
Indeks od zera pierwszego znaku w `CStringT` obiekcie do usunięcia.

*Ncount*<br/>
Liczba znaków do usunięcia.

### <a name="return-value"></a>Wartość zwracana

Długość zmienionego ciągu.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* jest dłuższy niż ciąg, reszta ciągu zostaną usunięte.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

## <a name="cstringtfind"></a><a name="find"></a>CStringT::Znajdź

Przeszukuje ten ciąg dla pierwszego dopasowania znaku lub podciągów.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parametry

*pszSub*<br/>
Podciąg do wyszukania.

*Istart*<br/>
Indeks znaku w ciągu, aby rozpocząć wyszukiwanie z lub 0, aby rozpocząć od początku.

*Ch*<br/>
Pojedynczy znak do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera pierwszego znaku w `CStringT` tym obiekcie, który pasuje do żądanego podciągu lub znaków; -1, jeśli nie znaleziono podciągu lub znaku.

### <a name="remarks"></a>Uwagi

Funkcja jest przeciążona, aby akceptować zarówno pojedyncze `strchr`znaki (podobne do `strstr`funkcji czasu wykonywania) i ciągi (podobne do ).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

## <a name="cstringtfindoneof"></a><a name="findoneof"></a>CStringT::FindOneOf

Wyszukuje ten ciąg pierwszego znaku, który pasuje do dowolnego znaku zawartego w *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg zawierający znaki do dopasowywania.

### <a name="return-value"></a>Wartość zwracana

Indeks zerowy pierwszego znaku w tym ciągu, który jest również w *pszCharSet*; -1, jeśli nie ma dopasowania.

### <a name="remarks"></a>Uwagi

Znajduje pierwsze wystąpienie dowolnego ze znaków w *pszCharSet*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

## <a name="cstringtformat"></a><a name="format"></a>CStringT::Format

Zapisuje sformatowane `CStringT` dane w taki sam sposób, w jaki [sprintf_s](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formatuje dane w tablicę znaków w stylu C.

```cpp
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identyfikator zasobu ciągu zawierający ciąg kontroli formatu.

*pszFormat*<br/>
Ciąg kontroli formatu.

*Argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Ta funkcja formatuje i przechowuje serię `CStringT`znaków i wartości w pliku . Każdy opcjonalny argument (jeśli istnieje) jest konwertowany i wyprowadzany zgodnie z odpowiednią specyfikacją formatu w *pszFormat* lub z zasobu ciągu identyfikowany przez *nFormatID*.

Wywołanie zakończy się niepowodzeniem, jeśli sam obiekt `Format`ciągu jest oferowany jako parametr do . Na przykład następujący kod spowoduje nieprzewidywalne wyniki:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Aby uzyskać więcej informacji, zobacz [Formatowanie składni specyfikacji: printf i wprintf Functions](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

## <a name="cstringtformatmessage"></a><a name="formatmessage"></a>CStringT::FormatMessage

Formatuje ciąg wiadomości.

```cpp
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identyfikator zasobu ciągu zawierający niesformatowany tekst wiadomości.

*pszFormat*<br/>
Wskazuje ciąg kontroli formatu. Zostanie on zeskanowany w poszukiwaniu wstawek i odpowiednio sformatowany. Ciąg formatu jest podobny do funkcji *printf*-style ciągów w czasie wykonywania, z tą różnicą, że umożliwia wstawienie parametrów w dowolnej kolejności.

*Argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Funkcja wymaga definicji wiadomości jako dane wejściowe. Definicja wiadomości jest określana przez *pszFormat* lub z zasobu ciągu identyfikowane przez *nFormatID*. Funkcja kopiuje sformatowany `CStringT` tekst wiadomości do obiektu, przetwarzając wszystkie osadzone sekwencje wstawiania, jeśli jest to wymagane.

> [!NOTE]
> `FormatMessage`próbuje przydzielić pamięć systemową dla nowo sformatowanego ciągu. Jeśli ta próba nie powiedzie się, wyjątek pamięci jest automatycznie generowany.

Każda płytka musi mieć odpowiedni parametr zgodnie z parametrem *pszFormat* lub *nFormatID.* W tekście wiadomości kilka sekwencji unikowych jest obsługiwanych w celu dynamicznego formatowania wiadomości. Aby uzyskać więcej informacji, zobacz funkcję Format systemu [WindowsMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) w programie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

## <a name="cstringtformatmessagev"></a><a name="formatmessagev"></a>CStringT::FormatMessageV

Formatuje ciąg wiadomości przy użyciu listy argumentów zmiennej.

```cpp
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Wskazuje ciąg kontroli formatu. Zostanie on zeskanowany w poszukiwaniu wstawek i odpowiednio sformatowany. Ciąg formatu jest podobny do `printf`ciągów formatu funkcji w czasie wykonywania, z tą różnicą, że umożliwia wstawienie parametrów w dowolnej kolejności.

*pArgList (Lista PArg)*<br/>
Wskaźnik do listy argumentów.

### <a name="remarks"></a>Uwagi

Funkcja wymaga definicji wiadomości jako danych wejściowych, określonej przez *pszFormat*. Funkcja kopiuje sformatowany tekst wiadomości i `CStringT` zmienną listę argumentów do obiektu, przetwarzając wszystkie osadzone sekwencje wstawiania, jeśli jest to wymagane.

> [!NOTE]
> `FormatMessageV`wywołuje [CStringT::FormatMessage](#formatmessage), który próbuje przydzielić pamięć systemową dla nowo sformatowanego ciągu. Jeśli ta próba nie powiedzie się, wyjątek pamięci jest automatycznie generowany.

Aby uzyskać więcej informacji, zobacz funkcję Format systemu [WindowsMessage](/windows/win32/api/winbase/nf-winbase-formatmessage) w programie Windows SDK.

## <a name="cstringtformatv"></a><a name="formatv"></a>CStringT::FormatV

Formatuje ciąg wiadomości przy użyciu listy argumentów zmiennej.

```cpp
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Wskazuje ciąg kontroli formatu. Zostanie on zeskanowany w poszukiwaniu wstawek i odpowiednio sformatowany. Ciąg formatu jest podobny do `printf`ciągów formatu funkcji w czasie wykonywania, z tą różnicą, że umożliwia wstawienie parametrów w dowolnej kolejności.

*Args*<br/>
Wskaźnik do listy argumentów.

### <a name="remarks"></a>Uwagi

Zapisuje sformatowany ciąg i zmienną `CStringT` listę argumentów `vsprintf_s` do ciągu w taki sam sposób, w jaki formatuje dane w tablicy znaków w stylu C.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

## <a name="cstringtgetenvironmentvariable"></a><a name="getenvironmentvariable"></a>CStringT::GetEnvironmentVariable

Ustawia ciąg na wartość określonej zmiennej środowiskowej.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parametry

*pszVar*<br/>
Wskaźnik do ciągu zakończonego zerem, który określa zmienną środowiskową.

### <a name="return-value"></a>Wartość zwracana

Nonzero jeśli się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobiera wartość określonej zmiennej z bloku środowiska procesu wywołującego. Wartość jest w postaci ciągu znaków zakończonych wartością null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

## <a name="cstringtinsert"></a><a name="insert"></a>CStringT::Wstaw

Wstawia pojedynczy znak lub podciąg w danym indeksie w ciągu.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parametry

*Iindex*<br/>
Indeks znaku, przed którym nastąpi wstawienie.

*Psz*<br/>
Wskaźnik do podciągów, który ma zostać wstawiony.

*Ch*<br/>
Znak, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Długość zmienionego ciągu.

### <a name="remarks"></a>Uwagi

Parametr *iIndex* identyfikuje pierwszy znak, który zostanie przeniesiony, aby zrobić miejsce dla znaku lub podciągu. Jeśli *nIndex* wynosi zero, wstawienie nastąpi przed całym ciągiem. Jeśli *nIndex* jest wyższa niż długość ciągu, funkcja połączy obecny ciąg i nowy materiał dostarczony przez *ch* lub *psz*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

## <a name="cstringtleft"></a><a name="left"></a>CStringT::Po lewej

Wyodrębnia znaki *nCount* po `CStringT` lewej stronie z tego obiektu i zwraca kopię wyodrębnionego podciągu.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parametry

*Ncount*<br/>
Liczba znaków do wyodrębnienia `CStringT` z tego obiektu.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CStringT` zawierający kopię określonego zakresu znaków. Zwrócony `CStringT` obiekt może być pusty.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* przekracza długość ciągu, a następnie cały ciąg jest wyodrębniany. `Left`jest podobny do `Left` funkcji Basic.

W przypadku zestawów znaków wielo-bajtowych (MBCS) *nCount* traktuje każdą sekwencję 8-bitową jako znak, dzięki czemu *nCount* zwraca liczbę znaków wielo bajtowych pomnożoną przez dwa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

## <a name="cstringtloadstring"></a><a name="loadstring"></a>CStringT::LoadString

Odczytuje zasób ciągu systemu Windows, identyfikowany przez *nID,* w istniejący `CStringT` obiekt.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parametry

*hInstance (Nieumieja)*<br/>
Dojście do wystąpienia modułu.

*Nid*<br/>
Identyfikator zasobu ciągu systemu Windows.

*wLanguageID*<br/>
Język zasobu ciągu.

### <a name="return-value"></a>Wartość zwracana

Niezerowe, jeśli obciążenie zasobu zakończyło się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ładuje zasób ciągu *(nID)* z określonego modułu (*hInstance*) przy użyciu określonego języka (*wLanguage*).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

## <a name="cstringtmakelower"></a><a name="makelower"></a>CStringT::MakeLower

Konwertuje `CStringT` obiekt na ciąg małych liter.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowy ciąg małych liter.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

## <a name="cstringtmakereverse"></a><a name="makereverse"></a>CStringT::MakeReverse

Odwraca kolejność znaków w `CStringT` obiekcie.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowy odwrócony ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

## <a name="cstringtmakeupper"></a><a name="makeupper"></a>CStringt::MakeUpper

Konwertuje `CStringT` obiekt na ciąg wielkich liter.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowy ciąg wielkich liter.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

## <a name="cstringtmid"></a><a name="mid"></a>CStringT::Mid

Wyodrębnia podciąg o długości *nCount* znaków z tego `CStringT` obiektu, począwszy od pozycji *iFirst* (zero-based).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parametry

*iPierwsz*<br/>
Indeks oparty na wartości zero pierwszego `CStringT` znaku w tym obiekcie, który ma zostać uwzględniony w wyodrębnianym podciągie.

*Ncount*<br/>
Liczba znaków do wyodrębnienia `CStringT` z tego obiektu. Jeśli ten parametr nie jest dostarczany, a następnie pozostała część ciągu jest wyodrębniana.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CStringT` zawierający kopię określonego zakresu znaków. Należy zauważyć, `CStringT` że zwrócony obiekt może być pusty.

### <a name="remarks"></a>Uwagi

Funkcja zwraca kopię wyodrębnionego podciągu. `Mid`jest podobny do funkcji Basic Mid (z tą różnicą, że indeksy w języku Basic są oparte na jednej).

W przypadku zestawów znaków wielobajtowych (MBCS) *nCount* odnosi się do każdego znaku 8-bitowego; oznacza to, że ołów i bajt szlaku w jednym znaku wielobajtowym są liczone jako dwa znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

## <a name="cstringtoemtoansi"></a><a name="oemtoansi"></a>CStringT::OemToAnsi

Konwertuje wszystkie znaki `CStringT` w tym obiekcie z zestawu znaków OEM na zestaw znaków ANSI.

```cpp
void OemToAnsi();
```

### <a name="remarks"></a>Uwagi

Ta funkcja nie jest dostępna, jeśli zdefiniowano _UNICODE.

### <a name="example"></a>Przykład

Zobacz przykład [CStringT::AnsiToOem](#ansitooem).

## <a name="cstringtoperator-"></a><a name="operator_eq"></a>CStringT::operator =

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

*strSrc ( strSrc )*<br/>
A, `CStringT` aby przypisać do tego ciągu.

*Str*<br/>
Odwołanie do `CThisSimpleString` obiektu.

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteką DLL MFC, czy nie.

*BaseType*<br/>
Typ podstawowy ciągu.

*var*<br/>
Obiekt wariantu do przypisania do tego ciągu.

*Ch*<br/>
Znak ANSI lub Unicode do przypisania do ciągu.

*pszsrc*<br/>
Wskaźnik do przypisanego oryginalnego ciągu.

### <a name="remarks"></a>Uwagi

Operator przypisania akceptuje `CStringT` inny obiekt, wskaźnik znaku lub pojedynczy znak. Należy pamiętać, że wyjątki pamięci może wystąpić za każdym razem, gdy używasz tego operatora, ponieważ można przydzielić nowy magazyn.

Aby uzyskać `CThisSimpleString`informacje na temat , zobacz uwagi sekcji [CStringT::CStringT](#cstringt).

> [!NOTE]
> Chociaż istnieje możliwość `CStringT` tworzenia wystąpień, które zawierają osadzone znaki null, zaleca się przeciwko niemu. Wywoływanie metod `CStringT` i operatorów na obiektach zawierających osadzone znaki null może tworzyć niezamierzone wyniki.

## <a name="cstringtoperator-"></a><a name="operator_add"></a>CStringT::operator +

Łączy dwa ciągi znaków lub znak i ciąg.

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

*ch1*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*ch2*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*str1*<br/>
A `CStringT` do łączenia z ciągiem lub znakiem.

*str2*<br/>
A `CStringT` do łączenia z ciągiem lub znakiem.

*psz1*<br/>
Wskaźnik do ciągu zakończonego z wartością null, aby połączyć je z ciągiem lub znakiem.

*psz2*<br/>
Wskaźnik do ciągu do połączenia z ciągiem lub znakiem.

### <a name="remarks"></a>Uwagi

Istnieje siedem form przeciążenia `CStringT::operator+` funkcji. Pierwsza wersja łączy dwa `CStringT` istniejące obiekty. Następne dwa połączyć `CStringT` obiekt i ciąg zakończony z wartością null. Następne dwa łączy obiekt `CStringT` i znak ANSI. Dwa ostatnie łączyć `CStringT` obiekt i znak Unicode.

> [!NOTE]
> Chociaż istnieje możliwość `CStringT` tworzenia wystąpień, które zawierają osadzone znaki null, zaleca się przeciwko niemu. Wywoływanie metod `CStringT` i operatorów na obiektach zawierających osadzone znaki null może tworzyć niezamierzone wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_add_eq"></a>CStringT::operator +=

Łączy znaki z końcem ciągu.

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

*Str*<br/>
Odwołanie do `CThisSimpleString` obiektu.

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteką DLL MFC, czy nie.

*BaseType*<br/>
Typ podstawowy ciągu.

*var*<br/>
Obiekt wariantu do łączenia z tym ciągiem.

*Ch*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*pszsrc*<br/>
Wskaźnik do oryginalnego ciągu jest łączony.

*strSrc ( strSrc )*<br/>
A, `CStringT` aby połączyć ten ciąg.

### <a name="remarks"></a>Uwagi

Operator akceptuje inny `CStringT` obiekt, wskaźnik znaków lub pojedynczy znak. Należy pamiętać, że wyjątki pamięci mogą wystąpić za każdym razem, gdy używasz tego `CStringT` operatora łączenia, ponieważ nowy magazyn może być przydzielony dla znaków dodanych do tego obiektu.

Aby uzyskać `CThisSimpleString`informacje na temat , zobacz uwagi sekcji [CStringT::CStringT](#cstringt).

> [!NOTE]
> Chociaż istnieje możliwość `CStringT` tworzenia wystąpień, które zawierają osadzone znaki null, zaleca się przeciwko niemu. Wywoływanie metod `CStringT` i operatorów na obiektach zawierających osadzone znaki null może tworzyć niezamierzone wyniki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_eq_eq"></a>CStringT::operator ==

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

*ch1*<br/>
Znak ANSI lub Unicode do porównania.

*ch2*<br/>
Znak ANSI lub Unicode do porównania.

*str1*<br/>
A `CStringT` dla porównania.

*str2*<br/>
A `CStringT` dla porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy ciąg lub znak po lewej stronie jest równa ciąg lub znak po prawej stronie i zwraca prawda lub fałsz odpowiednio.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

## <a name="cstringtoperator-"></a><a name="operator_neq"></a>CStringT::operator !=

Określa, czy dwa ciągi logicznie nie są równe.

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

*ch1*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*ch2*<br/>
Znak ANSI lub Unicode do łączenia z ciągiem.

*str1*<br/>
A `CStringT` dla porównania.

*str2*<br/>
A `CStringT` dla porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy ciąg lub znak po lewej stronie nie jest równy ciąg lub znak po prawej stronie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt"></a>CStringT::operator&lt;

Określa, czy ciąg po lewej stronie operatora jest mniejsza niż ciąg po prawej stronie.

```
friend bool operator<(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` dla porównania.

*str2*<br/>
A `CStringT` dla porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

### <a name="remarks"></a>Uwagi

Leksykograficzne porównanie ciągów, znak po znaku, aż:

- Znajduje dwa odpowiednie znaki nierówne, a wynik ich porównania jest traktowany jako wynik porównania ciągów.

- Nie znajduje żadnych nierówności, ale jeden ciąg ma więcej znaków niż inne, a krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Nie znajduje żadnych nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, a więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt"></a>CStringT::operator&gt;

Określa, czy ciąg po lewej stronie operatora jest większy niż ciąg po prawej stronie.

```
friend bool operator>(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` dla porównania.

*str2*<br/>
A `CStringT` dla porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

### <a name="remarks"></a>Uwagi

Leksykograficzne porównanie ciągów, znak po znaku, aż:

- Znajduje dwa odpowiednie znaki nierówne, a wynik ich porównania jest traktowany jako wynik porównania ciągów.

- Nie znajduje żadnych nierówności, ale jeden ciąg ma więcej znaków niż inne, a krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Nie znajduje żadnych nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

## <a name="cstringtoperator-lt"></a><a name="operator_lt_eq"></a>CStringT::operator&lt;=

Określa, czy ciąg po lewej stronie operatora jest mniejsza lub równa ciąg po prawej stronie.

```
friend bool operator<=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator<=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator<=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` dla porównania.

*str2*<br/>
A `CStringT` dla porównania.

*psz1*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

*psz2*<br/>
Wskaźnik do ciągu zakończonego wartością null do porównania.

### <a name="remarks"></a>Uwagi

Leksykograficzne porównanie ciągów, znak po znaku, aż:

- Znajduje dwa odpowiednie znaki nierówne, a wynik ich porównania jest traktowany jako wynik porównania ciągów.

- Nie znajduje żadnych nierówności, ale jeden ciąg ma więcej znaków niż inne, a krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Nie znajduje żadnych nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

## <a name="cstringtoperator-gt"></a><a name="operator_gt_eq"></a>CStringT::operator&gt;=

Określa, czy ciąg po lewej stronie operatora jest większa lub równa ciąg po prawej stronie.

```
friend bool operator>=(const CStringT& str1, const CStringT& str2) throw();
friend bool operator>=(const CStringT& str1, PCXSTR psz2) throw();
friend bool operator>=(PCXSTR psz1, const CStringT& str2) throw();
```

### <a name="parameters"></a>Parametry

*str1*<br/>
A `CStringT` dla porównania.

*str2*<br/>
A `CStringT` dla porównania.

*psz1*<br/>
Wskaźnik do ciągu do porównania.

*psz2*<br/>
Wskaźnik do ciągu do porównania.

### <a name="remarks"></a>Uwagi

Leksykograficzne porównanie ciągów, znak po znaku, aż:

- Znajduje dwa odpowiednie znaki nierówne, a wynik ich porównania jest traktowany jako wynik porównania ciągów.

- Nie znajduje żadnych nierówności, ale jeden ciąg ma więcej znaków niż inne, a krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Nie znajduje żadnych nierówności i stwierdza, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

## <a name="cstringtremove"></a><a name="remove"></a>CStringT::Usuń

Usuwa wszystkie wystąpienia określonego znaku z ciągu.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parametry

*chUsuj*<br/>
Znak, który ma zostać usunięty z ciągu.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków usuniętych z ciągu. Zero, jeśli ciąg nie zostanie zmieniony.

### <a name="remarks"></a>Uwagi

W porównaniach dla znaku rozróżniana jest wielkość liter.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

## <a name="cstringtreplace"></a><a name="replace"></a>CStringT::Zamień

Istnieją dwie wersje `Replace`programu . Pierwsza wersja zastępuje jedną lub więcej kopii podciągu przy użyciu innego podciągu. Oba podciągi są zakończone z wartością null. Druga wersja zastępuje jedną lub więcej kopii znaku przy użyciu innego znaku. Obie wersje działają na danych `CStringT`znaków przechowywanych w programie .

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parametry

*pszOld*<br/>
Wskaźnik do ciągu zakończonego zerem, który ma zostać zastąpiony przez *pszNew*.

*pszNew*<br/>
Wskaźnik do ciągu zakończonego zerem, który zastępuje *pszOld*.

*chStary*<br/>
Znak, który ma zostać zastąpiony przez *chNew*.

*chNowy*<br/>
Znak *zastępujący chOld*.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę zastąpionych wystąpień znaku lub podciągów lub zero, jeśli ciąg nie zostanie zmieniony.

### <a name="remarks"></a>Uwagi

`Replace`można zmienić długość napisu bo *pszNew* i *pszOld* nie muszą być tej samej długości, a kilka kopii starego podciągu można zmienić na nowy. Funkcja wykonuje dopasowanie z uwzględnieniem wielkości liter.

Przykładami `CStringT` wystąpień `CString`są `CStringA`, `CStringW`i .

Dla `CStringA` `Replace` , współpracuje ze znakami ANSI lub wielobajtowymi (MBCS). For `CStringW` `Replace` , działa z szerokimi znakami.

Dla `CString`, typ danych znaku jest wybierany w czasie kompilacji, na podstawie tego, czy zdefiniowane są stałe w poniższej tabeli.

|Stała zdefiniowana|Typ danych znaków|
|----------------------|-------------------------|
|_unicode|Znaki dwubajtowe|
|_mbcs|Znaki wielo bajtowe|
|Żadna|Znaki jedno bajtowe|
|Obie|Niezdefiniowane|

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

## <a name="cstringtreversefind"></a><a name="reversefind"></a>CStringT::ReverseFind

Przeszukuje ten `CStringT` obiekt pod kątem ostatniego dopasowania znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*Ch*<br/>
Znak do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Indeks od zera ostatniego znaku `CStringT` w tym obiekcie, który pasuje do żądanego znaku, lub -1, jeśli znak nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Funkcja jest podobna do funkcji `strrchr`czasu wykonywania .

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

## <a name="cstringtright"></a><a name="right"></a>CStringT::Prawy

Wyodrębnia ostatnie (czyli prawo) *znaki nCount* `CStringT` z tego obiektu i zwraca kopię wyodrębnione podciąg.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parametry

*Ncount*<br/>
Liczba znaków do wyodrębnienia `CStringT` z tego obiektu.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CStringT` zawierający kopię określonego zakresu znaków. Należy zauważyć, `CStringT` że zwrócony obiekt może być pusty.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* przekracza długość ciągu, a następnie cały ciąg jest wyodrębniany. `Right`jest podobny do `Right` basic funkcji (z tą różnicą, że indeksy w basic są oparte na wartości zero).

W przypadku zestawów znaków wielobajtowych (MBCS) *nCount* odnosi się do każdego znaku 8-bitowego; oznacza to, że ołów i bajt szlaku w jednym znaku wielobajtowym są liczone jako dwa znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

## <a name="cstringtsetsysstring"></a><a name="setsysstring"></a>CStringT::SetSysString

Ponownie przydziela BSTR wskazywala przez *pbstr* `CStringT` i kopiuje do niego zawartość obiektu, w tym znak NULL.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parametry

*pbstr (pbstr)*<br/>
Wskaźnik do ciągu znaków.

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg.

### <a name="remarks"></a>Uwagi

W zależności od `CStringT` zawartości obiektu wartość BSTR, do którego odwołuje się *pbstr,* może ulec zmianie. Funkcja `CMemoryException` zgłasza, jeśli istnieje niewystarczająca ilość pamięci.

Ta funkcja jest zwykle używana do zmiany wartości ciągów przekazywanych przez odwołanie do automatyzacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

## <a name="cstringtspanexcluding"></a><a name="spanexcluding"></a>CStringT::SpanExcluding

Wyodrębnia znaki z ciągu, zaczynając od pierwszego znaku, które nie znajdują się w zestawie znaków zidentyfikowanych przez *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg interpretowany jako zestaw znaków.

### <a name="return-value"></a>Wartość zwracana

Podciąg zawierający znaki w ciągu, które nie znajdują się w *pszCharSet*, począwszy od pierwszego znaku w ciągu, a kończąc na pierwszym znaku znalezionym w ciągu, który jest również w *pszCharSet* (czyli począwszy od pierwszego znaku w ciągu i do, ale z wyłączeniem pierwszego znaku w ciągu, który znajduje się *pszCharSet*). Zwraca cały ciąg, jeśli w ciągu nie znaleziono żadnego znaku w *pszCharSet.*

### <a name="remarks"></a>Uwagi

`SpanExcluding`wyodrębnia i zwraca wszystkie znaki poprzedzające pierwsze wystąpienie znaku z *pszCharSet* (innymi słowy, znak z *pszCharSet* i wszystkie znaki następujące po nim w ciągu, nie są zwracane). Jeśli w ciągu nie zostanie znaleziony żaden znak `SpanExcluding` z *pszCharSet,* zwraca cały ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

## <a name="cstringtspanincluding"></a><a name="spanincluding"></a>CStringT::SpanWcluding

Wyodrębnia znaki z ciągu, począwszy od pierwszego znaku, które znajdują się w zestawie znaków zidentyfikowanych przez *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg interpretowany jako zestaw znaków.

### <a name="return-value"></a>Wartość zwracana

Podciąg zawierający znaki w ciągu, które znajdują się w *pszCharSet*, począwszy od pierwszego znaku w ciągu i kończąc, gdy znak znajduje się w ciągu, który nie znajduje się w *pszCharSet*. `SpanIncluding`zwraca pusty podciąg, jeśli pierwszy znak w ciągu nie znajduje się w określonym zestawie.

### <a name="remarks"></a>Uwagi

Jeśli pierwszy znak ciągu nie znajduje się w `SpanIncluding` zestawie znaków, zwraca pusty ciąg. W przeciwnym razie zwraca sekwencję kolejnych znaków, które znajdują się w zestawie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

## <a name="cstringttokenize"></a><a name="tokenize"></a>CStringT::Tokenize

Znajduje następny token w ciągu docelowym

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parametry

*pszTokens*<br/>
Ciąg zawierający ograniczniki tokenu. Kolejność tych ograniczników nie jest ważna.

*Istart*<br/>
Indeks od zera, aby rozpocząć wyszukiwanie.

### <a name="return-value"></a>Wartość zwracana

Obiekt `CStringT` zawierający bieżącą wartość tokenu.

### <a name="remarks"></a>Uwagi

Funkcja `Tokenize` znajduje następny token w ciągu docelowym. Zestaw znaków w *pszTokens* określa możliwe ograniczniki tokenu, który ma zostać znaleziony. Przy każdym `Tokenize` wywołaniu funkcji rozpoczyna się od *iStart*, pomija `CStringT` wiodących ograniczników i zwraca obiekt zawierający bieżący token, który jest ciąg znaków do następnego znaku ogranicznika. Wartość *iStart* jest aktualizowana jako pozycja po końcowym znaku ogranicznika lub -1, jeśli osiągnięto koniec ciągu. Więcej tokenów można podzielić z pozostałej części ciągu docelowego `Tokenize`przez serię wywołań do , za pomocą *iStart,* aby śledzić, gdzie w ciągu następny token ma być odczytywany. Gdy nie ma więcej tokenów funkcja zwróci pusty ciąg i *iStart* zostanie ustawiona na -1.

W przeciwieństwie do funkcji tokenizacji CRT, takich jak [strtok_s, _strtok_s_l, wcstok_s, _wcstok_s_l, _mbstok_s, _mbstok_s_l](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` nie modyfikuje ciągu docelowego.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu są następujące:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

## <a name="cstringttrim"></a><a name="trim"></a>CStringT::Przytnij

Przycina znaki początkowe i końcowe z ciągu.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowy, który ma zostać przycięty.

*pszTargety*<br/>
Wskaźnik do ciągu zawierającego znaki docelowe, które mają zostać przycięte. Wszystkie wiodące i końcowe wystąpienia znaków w *pszTarget* `CStringT` zostaną przycięte z obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca przycięty ciąg.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie wystąpienia początkowe i końcowe jednego z następujących:

- Znak określony przez *chTarget*.

- Wszystkie znaki znalezione w ciągu określonym przez *pszTargets*.

- Odstępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu są następujące:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

## <a name="cstringttrimleft"></a><a name="trimleft"></a>CStringT::TrimLeft

Przycina znaki wiodące z ciągu.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowy, który ma zostać przycięty.

*pszTargety*<br/>
Wskaźnik do ciągu zawierającego znaki docelowe, które mają zostać przycięte. Wszystkie wiodące wystąpienia znaków w *pszTarget* zostaną `CStringT` przycięte z obiektu.

### <a name="return-value"></a>Wartość zwracana

Wynikowy ciąg przycięty.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie wystąpienia początkowe i końcowe jednego z następujących:

- Znak określony przez *chTarget*.

- Wszystkie znaki znalezione w ciągu określonym przez *pszTargets*.

- Odstępu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

## <a name="cstringttrimright"></a><a name="trimright"></a>CStringT::TrimRight

Przycina końcowe znaki z ciągu.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowy, który ma zostać przycięty.

*pszTargety*<br/>
Wskaźnik do ciągu zawierającego znaki docelowe, które mają zostać przycięte. Wszystkie końcowe wystąpienia znaków w *pszTarget* zostaną przycięte z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CStringT` obiekt zawierający przycięty ciąg.

### <a name="remarks"></a>Uwagi

Usuwa końcowe wystąpienia jednego z następujących objawów:

- Znak określony przez *chTarget*.

- Wszystkie znaki znalezione w ciągu określonym przez *pszTargets*.

- Odstępu.

Wersja `CStringT& TrimRight(XCHAR chTarget)` akceptuje jeden parametr znak i usuwa wszystkie kopie tego `CStringT` znaku z końca danych ciągu. Zaczyna się od końca ciągu i działa w kierunku przodu. Zatrzymuje się, gdy znajdzie inny `CSTringT` znak lub gdy zabraknie danych znakowych.

Wersja `CStringT& TrimRight(PCXSTR pszTargets)` akceptuje ciąg zakończony z wartością null, który zawiera wszystkie różne znaki do wyszukania. Usuwa wszystkie kopie tych znaków w `CStringT` obiekcie. Zaczyna się na końcu ciągu i działa w kierunku przodu. Zatrzymuje się, gdy znajdzie znak, który nie znajduje `CStringT` się w ciągu docelowym lub gdy zabraknie danych znaków. Nie próbuje dopasować całego ciągu docelowego do podciągów na końcu . `CStringT`

Wersja `CStringT& TrimRight()` nie wymaga żadnych parametrów. Przycina wszystkie końcowe znaki odstępu z `CStringT` końca ciągu. Znaki odstępów mogą być podziałami wierszy, spacjami lub kartami.

-

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Zobacz też

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT, klasa](../../atl-mfc-shared/reference/csimplestringt-class.md)
