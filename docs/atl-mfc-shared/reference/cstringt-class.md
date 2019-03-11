---
title: CStringT, klasa
ms.date: 10/18/2018
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
ms.openlocfilehash: 9566830de4d3af8f34e8efa5e5ef468acae1fba5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750874"
---
# <a name="cstringt-class"></a>CStringT, klasa

Ta klasa reprezentuje `CStringT` obiektu.

## <a name="syntax"></a>Składnia

```
template<typename BaseType, class StringTraits>
class CStringT :
    public CSimpleStringT<BaseType,
        _CSTRING_IMPL_::_MFCDLLTraitsCheck<BaseType, StringTraits>::c_bIsMFCDLLTraits>
```

#### <a name="parameters"></a>Parametry

*BaseType*<br/>
Typ znaku klasa string. Może to być jeden z następujących elementów:

- **CHAR** (na ciągi znaków ANSI).

- **wchar_t** (na ciągi znaków Unicode).

- TCHAR (na ciągi znaków ANSI i Unicode).

*StringTraits*<br/>
Określa, czy klasa string konieczne Obsługa bibliotek C Run-Time (CRT) i gdzie znajdują się zasoby w postaci ciągów. Może to być jeden z następujących elementów:

- **StrTraitATL < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **char** &#124;  **TCHAR >>**

   Klasa wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów w moduł określony przez `m_hInstResource` (członek klasy modułu aplikacji).

- **StrTraitATL < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **char** &#124;  **TCHAR >>**

   Klasa nie wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów w moduł określony przez `m_hInstResource` (członek klasy modułu aplikacji).

- **StrTraitMFC < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsCRT < wchar_t** &#124; **char** &#124;  **TCHAR >>**

   Klasa wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów za pomocą standardowego algorytmu wyszukiwania MFC.

- **StrTraitMFC < wchar_t** &#124; **char** &#124; **TCHAR, ChTraitsOS < wchar_t** &#124; **char** &#124;  **TCHAR >>**

   Klasa nie wymaga obsługi CRT i umożliwia wyszukiwanie ciągów zasobów za pomocą standardowego algorytmu wyszukiwania MFC.

## <a name="members"></a>Elementy członkowskie

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringT::CStringT](#cstringt)|Konstruuje `CStringT` obiektu na różne sposoby.|
|[CStringT::~CStringT](#_dtorcstringt)|Niszczy `CStringT` obiektu.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CStringT::AllocSysString](#allocsysstring)|Przydziela ciąg BSTR z `CStringT` danych.|
|[CStringT::AnsiToOem](#ansitooem)|Sprawia, że w miejscu konwersja zestawu na zbiór znaków OEM znaków ANSI.|
|[CStringT::AppendFormat](#appendformat)|Dołącza sformatowane dane do istniejącego `CStringT` obiektu.|
|[CStringT::Collate](#collate)|Porównuje dwa ciągi (wielkość liter, informacje specyficzne dla ustawień regionalnych używa).|
|[CStringT::CollateNoCase](#collatenocase)|Porównuje dwa ciągi (przypadek jest rozróżniana wielkość liter, informacje specyficzne dla ustawień regionalnych używa).|
|[CStringT::Compare](#compare)|Porównuje dwa ciągi (z uwzględnieniem wielkości liter).|
|[CStringT::CompareNoCase](#comparenocase)|Porównuje dwa ciągi (wielkich liter).|
|[CStringT::Delete](#delete)|Usuwa znaku lub znaków z ciągu.|
|[CStringT::Find](#find)|Umożliwia znalezienie znak lub podciąg dłuższym ciągu.|
|[CStringT::FindOneOf](#findoneof)|Wyszukuje pierwszy znak zgodnego z zestawu.|
|[CStringT::Format](#format)|Formaty ciągu jako `sprintf` jest.|
|[CStringT::FormatMessage](#formatmessage)|Formatuje ciąg komunikatu.|
|[CStringT::FormatMessageV](#formatmessagev)|Formatuje komunikat ciągu przy użyciu listy zmiennych argumentów.|
|[CStringT::FormatV](#formatv)|Formaty ciągu przy użyciu listy zmiennych argumentów.|
|[CStringT::GetEnvironmentVariable](#getenvironmentvariable)|Ustawia ciąg na wartość określonej zmiennej środowiskowej.|
|[CStringT::Insert](#insert)|Wstawia pojedynczy znak lub podciąg pod danym indeksem w ciągu.|
|[CStringT::Left](#left)|Wyodrębnia lewy część ciągu.|
|[CStringT::LoadString](#loadstring)|Ładuje istniejące `CStringT` obiekt z zasobem Windows.|
|[CStringT::MakeLower](#makelower)|Konwertuje wszystkie znaki w tym ciągu na małe litery.|
|[CStringT::MakeReverse](#makereverse)|Odwraca ciągu.|
|[CStringT::MakeUpper](#makeupper)|Konwertuje wszystkie znaki w tym ciągu na wielkie litery.|
|[CStringT::Mid](#mid)|Wyodrębnia środkową część ciągu.|
|[CStringT::OemToAnsi](#oemtoansi)|Sprawia, że konwersja w miejscu z zestawu do zestawu znaków ANSI znaków OEM.|
|[CStringT::Remove](#remove)|Usuwa wskazany znaków z ciągu.|
|[CStringT::Replace](#replace)|Zastępuje wskazany znaków z innymi znakami.|
|[CStringT::ReverseFind](#reversefind)|Umożliwia znalezienie znak wewnątrz dłuższym ciągu; rozpoczyna się od końca.|
|[CStringT::Right](#right)|Wyodrębnia prawa część ciągu.|
|[CStringT::SetSysString](#setsysstring)|Ustawia przy użyciu danych z istniejącego obiektu BSTR `CStringT` obiektu.|
|[CStringT::SpanExcluding](#spanexcluding)|Wyodrębnia znaki ciągu, począwszy od pierwszego znaku, które nie znajdują się w zestawie znaków identyfikowane przez `pszCharSet`.|
|[CStringT::SpanIncluding](#spanincluding)|Wyodrębnianie podciągu, który zawiera tylko znaki w zestawie.|
|[CStringT::Tokenize](#tokenize)|Wyodrębnia określone tokenów w ciągu docelowym.|
|[CStringT::Trim](#trim)|Usuwa wszystkie znaki początkowe i końcowe białe znaki z ciągu.|
|[CStringT::TrimLeft](#trimleft)|Przycina początkowe białych znaków z ciągu.|
|[CStringT::TrimRight](#trimright)|Przycina końcowe białych znaków z ciągu.|

### <a name="operators"></a>Operatory

|||
|-|-|
|[operator =](#operator_eq)|Przypisuje nową wartość do `CStringT` obiektu.|
|[CStringT::operator +](#operator_add)|Łączy dwa ciągi lub znak i ciąg.|
|[CStringT::operator +=](#operator_add_eq)|Łączy nowy ciąg na końcu istniejącego ciągu.|
|[CStringT::operator ==](#operator_eq_eq)|Określa, czy dwa ciągi są logicznie równe.|
|[CStringT::operator! =](#operator_neq)|Określa, czy dwa ciągi logicznie nie są równe.|
|[CStringT::operator &lt;](#operator_lt)|Określa, czy ciąg po lewej stronie operatora jest mniejszy niż do ciągu z prawej strony.|
|[CStringT::operator &gt;](#operator_gt)|Określa, jeśli ciąg po lewej stronie operatora jest większy niż ciąg po prawej stronie.|
|[CStringT::operator &lt;=](#operator_lt_eq)|Określa, czy ciąg po lewej stronie operatora jest mniejszy niż lub równe ciągu z prawej strony.|
|[CStringT::operator &gt;=](#operator_gt_eq)|Określa, jeśli ciąg po lewej stronie operatora jest większy lub równy ciągowi po prawej stronie.|

## <a name="remarks"></a>Uwagi

`CStringT` dziedziczy [CSimpleStringT, klasa](../../atl-mfc-shared/reference/csimplestringt-class.md). Zaawansowane funkcje, takie jak manipulowanie znaków, kolejności i wyszukiwania, są implementowane przez `CStringT`.

> [!NOTE]
> `CStringT` obiekty są w stanie zgłaszać wyjątki. Ten problem wystąpi podczas `CStringT` obiektu skończy się pamięć jakiegokolwiek powodu.

A `CStringT` obiekt składa się z sekwencji znaków o zmiennej długości. `CStringT` udostępnia funkcje i operatory przy użyciu składni podobnej do Basic. Łączenie i operatory porównania, wraz z zarządzania pamięci uproszczonej `CStringT` łatwiejszy w obsłudze niż zwykły znak tablice obiektów.

> [!NOTE]
>  Chociaż istnieje możliwość utworzenia `CStringT` wystąpień, które zawierają osadzone znaki o wartości null, zaleca się przed nim. Wywoływanie metody i operatory na `CStringT` obiektów, które zawierają znaki null embedded może wygenerować niepożądanych wyników.

Przy użyciu różnych kombinacji `BaseType` i `StringTraits` parametrów, `CStringT` obiekty można wróć w następujących typów, które są wstępnie zdefiniowanych przez biblioteki ATL.

Jeśli używane w aplikacji ATL:

`CString`, `CStringA`, i `CStringW` są eksportowane z biblioteki MFC DLL (MFC90. Biblioteka DLL), nigdy nie przed użytkownikiem biblioteki dll. W ten sposób zapobiec `CStringT` z jest zdefiniowany wielokrotnie.

> [!NOTE]
>  Jeśli kod zawiera obejście błędy konsolidatora, które jest opisane w [eksportowanie CStringT przy użyciu klas parametrów](../../atl-mfc-shared/exporting-string-classes-using-cstringt.md), należy usunąć ten kod. Nie jest już potrzebny.

Dostępne w aplikacjach MFC są następujące typy parametrów:

|Typ CStringT|Deklaracja|
|-------------------|-----------------|
|`CStringA`|Znak ANSI wpisz ciąg z obsługą CRT.|
|`CStringW`|Znak Unicode, wpisz ciąg z obsługą CRT.|
|`CString`|ANSI i Unicode typy znaków z obsługą CRT.|

Parametry są następujące typy dostępne w projektach, jest definiowana ATL_CSTRING_NO_CRT:

|Typ CStringT|Deklaracja|
|-------------------|-----------------|
|`CAtlStringA`|Znak ANSI wpisz ciąg bez obsługi CRT.|
|`CAtlStringW`|Znak Unicode, wpisz ciąg bez obsługi CRT.|
|`CAtlString`|ANSI i Unicode typy znaków bez obsługi CRT.|

Parametry są następujące typy dostępne w projektach którym nie zdefiniowano ATL_CSTRING_NO_CRT:

|Typ CStringT|Deklaracja|
|-------------------|-----------------|
|`CAtlStringA`|Znak ANSI wpisz ciąg z obsługą CRT.|
|`CAtlStringW`|Znak Unicode, wpisz ciąg z obsługą CRT.|
|`CAtlString`|ANSI i Unicode typy znaków z obsługą CRT.|

`CString` obiekty mają również następujące cechy:

- `CStringT` obiekty można powiększać wyniku operacji łączenia.

- `CStringT` Postępuj zgodnie z obiektów, "wartość semantyki." Traktować `CStringT` obiektu jako ciąg rzeczywiste, a nie jako wskaźnik do ciągu.

- Można łatwo zastąpić `CStringT` obiektów dla `PCXSTR` argumenty funkcji.

- Zarządzanie pamięcią niestandardowe dla buforów ciągu. Aby uzyskać więcej informacji, zobacz [zarządzanie pamięcią i CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

## <a name="cstringt-predefined-types"></a>CStringT wstępnie zdefiniowanych typów

Ponieważ `CStringT` używa argumentu szablonu, aby zdefiniować typ znaku (albo [wchar_t](../../c-runtime-library/standard-types.md) lub [char](../../c-runtime-library/standard-types.md)) obsługiwane typy parametrów metody mogą być skomplikowane w czasie. Aby uprościć ten problem, zestaw wstępnie zdefiniowanych typów zdefiniowane i używane w całym `CStringT` klasy. W poniższej tabeli wymieniono różne typy:

|Nazwa|Opis|
|----------|-----------------|
|`XCHAR`|Pojedynczy znak (albo **wchar_t** lub **char**) przy użyciu tego samego typu znak jako `CStringT` obiektu.|
|`YCHAR`|Pojedynczy znak (albo **wchar_t** lub **char**) z odwrotną typ znaków jako `CStringT` obiektu.|
|`PXSTR`|Wskaźnik do ciągu znaków (albo **wchar_t** lub **char**) przy użyciu tego samego typu znak jako `CStringT` obiektu.|
|`PYSTR`|Wskaźnik do ciągu znaków (albo **wchar_t** lub **char**) z odwrotną typ znaków jako `CStringT` obiektu.|
|`PCXSTR`|Wskaźnik do **const** ciąg znaków (albo **wchar_t** lub **char**) przy użyciu tego samego typu znak jako `CStringT` obiektu.|
|`PCYSTR`|Wskaźnik do **const** ciąg znaków (albo **wchar_t** lub **char**) z odwrotną typ znaków jako `CStringT` obiektu.|

> [!NOTE]
>  Kod, który korzystał wcześniej z metody nieudokumentowane `CString` (takie jak `AssignCopy`) muszą zostać zastąpione przez kod, który korzysta z następujących metod udokumentowane `CStringT` (takie jak `GetBuffer` lub `ReleaseBuffer`). Te metody są dziedziczone z `CSimpleStringT`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

[CSimpleStringT](../../atl-mfc-shared/reference/csimplestringt-class.md)

`CStringT`

## <a name="requirements"></a>Wymagania

|nagłówek|Na użytek|
|------------|-------------|
|cstringt.h|Obiekty ciągu tylko do MFC|
|atlstr.h|Inne niż MFC obiektów w postaci ciągów|

##  <a name="allocsysstring"></a>  CStringT::AllocSysString

Przydziela ciąg automatyzacji typu BSTR i kopiuje zawartość `CStringT` obiekt, w tym kończącego znaku null.

```
BSTR AllocSysString() const;
```

### <a name="return-value"></a>Wartość zwracana

Nowo przydzielone ciąg.

### <a name="remarks"></a>Uwagi

W programach MFC [klasa CMemoryException](../../mfc/reference/cmemoryexception-class.md) jest generowany, jeśli istnieje niewystarczająca ilość pamięci. W programach ATL [CAtlException](../../atl/reference/catlexception-class.md) zgłaszany. Ta funkcja jest zwykle używana do zwracania ciągów dla usługi Automation.

Najczęściej Jeśli ten ciąg jest przekazywany do funkcji COM jako [in] parametru, a następnie ta wymaga obiekt wywołujący zwolnić ciągu. Można to zrobić za pomocą [SysFreeString](/windows/desktop/api/oleauto/nf-oleauto-sysfreestring), zgodnie z opisem w zestawie Windows SDK. Aby uzyskać więcej informacji, zobacz [Allocating i zwalnianie pamięci dla BSTR](../../atl-mfc-shared/allocating-and-releasing-memory-for-a-bstr.md).

Aby uzyskać więcej informacji na temat funkcji alokacji OLE w Windows, zobacz [SysAllocString](/windows/desktop/api/oleauto/nf-oleauto-sysallocstring) w zestawie Windows SDK.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CStringT::AllocSysString`.

[!code-cpp[NVC_ATLMFC_Utilities#105](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_1.cpp)]

##  <a name="ansitooem"></a>  CStringT::AnsiToOem

Konwertuje wszystkie znaki w tym `CStringT` obiekt z zestawu na zbiór znaków OEM znaków ANSI.

```
void AnsiToOem();
```

### <a name="remarks"></a>Uwagi

Funkcja jest niedostępna w przypadku _UNICODE zdefiniowano.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#106](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_2.cpp)]

##  <a name="appendformat"></a>  CStringT::AppendFormat

Dołącza sformatowane dane do istniejącego `CStringT` obiektu.

```
void __cdecl AppendFormat(PCXSTR pszFormat, [, argument] ...);
void __cdecl AppendFormat(UINT nFormatID, [, argument] ...);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Ciąg formantu formatu.

*nFormatID*<br/>
Identyfikatora zasobu ciągu, który zawiera ciąg formantu formatu.

*argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Ta funkcja formatuje i dołącza serie znaków i wartości w `CStringT`. Każdy opcjonalny argument (jeśli istnieje) jest konwertowaya i dołączany według specyfikacji formatu w *pszFormat* lub z zasobu ciągu określonego przez *nFormatID*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#107](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_3.cpp)]

##  <a name="collate"></a>  CStringT::Collate

Porównuje dwa ciągi przy użyciu funkcji zwykłego tekstu `_tcscoll`.

```
int Collate(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Drugi ciąg używana na potrzeby porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0, jeśli `CStringT` obiekt jest mniejszy niż *psz*, lub 0 > Jeśli ten `CStringT` obiekt jest większy niż *psz*.

### <a name="remarks"></a>Uwagi

Funkcja generic tekst `_tcscoll`, który jest zdefiniowany w TCHAR. Godz., mapuje do jednej `strcoll`, `wcscoll`, lub `_mbscoll`, w zależności od zestawu znaków, który jest definiowany w czasie kompilacji. Każda funkcja wykonuje porównania uwzględniającego wielkość liter ciągów zgodnie ze stroną kodową aktualnie w użyciu. Aby uzyskać więcej informacji, zobacz [strcoll —, wcscoll —, _mbscoll —, _strcoll_l —, _wcscoll_l —, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

##  <a name="collatenocase"></a>  CStringT::CollateNoCase

Porównuje dwa ciągi przy użyciu funkcji zwykłego tekstu `_tcscoll`.

```
int CollateNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Drugi ciąg używana na potrzeby porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne (bez uwzględnienia wielkości liter), < 0, jeśli `CStringT` obiekt jest mniejszy niż *psz* (bez uwzględnienia wielkości liter) lub > 0, jeśli ta `CStringT` obiekt jest większy niż *psz* (bez uwzględnienia wielkości liter).

### <a name="remarks"></a>Uwagi

Funkcja generic tekst `_tcscoll`, który jest zdefiniowany w TCHAR. Godz., mapuje do jednej `stricoll`, `wcsicoll`, lub `_mbsicoll`, w zależności od zestawu znaków, który jest definiowany w czasie kompilacji. Każda funkcja wykonuje porównania bez uwzględniania ciągów, zgodnie z aktualnie używaną stroną kodową. Aby uzyskać więcej informacji, zobacz [strcoll —, wcscoll —, _mbscoll —, _strcoll_l —, _wcscoll_l —, _mbscoll_l](../../c-runtime-library/reference/strcoll-wcscoll-mbscoll-strcoll-l-wcscoll-l-mbscoll-l.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#109](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_4.cpp)]

##  <a name="compare"></a>  CStringT::Compare

Porównuje dwa ciągi (z uwzględnieniem wielkości liter).

```
int Compare(PCXSTR psz) const;
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Drugi ciąg używana na potrzeby porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne, < 0, jeśli `CStringT` obiekt jest mniejszy niż *psz*, lub 0 > Jeśli ten `CStringT` obiekt jest większy niż *psz*.

### <a name="remarks"></a>Uwagi

Funkcja generic tekst `_tcscmp`, który jest zdefiniowany w TCHAR. Godz., mapuje do jednej `strcmp`, `wcscmp`, lub `_mbscmp`, w zależności od zestawu znaków, który jest definiowany w czasie kompilacji. Każda funkcja wykonuje porównania uwzględniającego wielkość liter, ciągów i nie występuje w ustawieniach regionalnych. Aby uzyskać więcej informacji, zobacz [strcmp —, wcscmp —, _mbscmp —](../../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md).

Jeśli ciąg zawiera osadzone wartości, na potrzeby porównania ciągu uznaje się być obcięty przy pierwszym znaku null, embedded.

### <a name="example"></a>Przykład

W poniższym przykładzie pokazano użycie `CStringT::Compare`.

[!code-cpp[NVC_ATLMFC_Utilities#110](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_5.cpp)]

##  <a name="comparenocase"></a>  CStringT::CompareNoCase

Porównuje dwa ciągi (wielkich liter).

```
int CompareNoCase(PCXSTR psz) const throw();
```

### <a name="parameters"></a>Parametry

*psz*<br/>
Drugi ciąg używana na potrzeby porównania.

### <a name="return-value"></a>Wartość zwracana

Zero, jeśli ciągi są identyczne (bez uwzględnienia wielkości liter) < 0, jeśli ta `CStringT` obiekt jest mniejszy niż *psz* (bez uwzględnienia wielkości liter) lub > 0, jeśli ta `CStringT` obiekt jest większy niż *psz* (bez uwzględnienia wielkości liter).

### <a name="remarks"></a>Uwagi

Funkcja generic tekst `_tcsicmp`, który jest zdefiniowany w TCHAR. Godz., mapuje do jednej `_stricmp`, `_wcsicmp` lub `_mbsicmp`, w zależności od zestawu znaków, który jest definiowany w czasie kompilacji. Każda funkcja wykonuje porównania bez uwzględniania ciągów. Porównanie zależy od aspekt LC_CTYPE ustawień regionalnych, ale nie LC_COLLATE. Aby uzyskać więcej informacji, zobacz [_stricmp —, _wcsicmp —, _mbsicmp —, _stricmp_l —, _wcsicmp_l —, _mbsicmp_l —](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#111](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_6.cpp)]

##  <a name="cstringt"></a>  CStringT::CStringT

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

*pch*<br/>
Wskaźnik do tablicy znaków o długości *nLength*, nie zakończony znakiem null.

*nLength*<br/>
Liczbę znaków w *pch*.

*ch*<br/>
Pojedynczy znak.

*pszSrc*<br/>
Ciąg zakończony wartością null do skopiowania do tego `CStringT` obiektu.

*pStringMgr*<br/>
Wskaźnik do Menedżera pamięci `CStringT` obiektu. Aby uzyskać więcej informacji na temat `IAtlStringMgr` i zarządzania pamięci dla `CStringT`, zobacz [zarządzanie pamięcią za pomocą CStringT](../../atl-mfc-shared/memory-management-with-cstringt.md).

*strSrc*<br/>
Istniejące `CStringT` obiektu do skopiowania do tego `CStringT` obiektu. Aby uzyskać więcej informacji na temat `CThisString` i `CThisSimpleString`, zobacz sekcję Uwagi.

*varSrc*<br/>
Variant — obiekt ma być skopiowany do tego `CStringT` obiektu.

*BaseType*<br/>
Typ znaku klasa string. Może to być jeden z następujących elementów:

**CHAR** (na ciągi znaków ANSI).

**wchar_t** (na ciągi znaków Unicode).

TCHAR (na ciągi znaków ANSI i Unicode).

*bMFCDLL*<br/>
Wartość logiczna określająca, czy projekt jest biblioteki DLL MFC (TRUE) czy nie (FALSE).

*SystemString*<br/>
Musi być `System::String`, i projektu muszą być skompilowane z/CLR.

*pString*<br/>
Dojście do `CStringT` obiektu.

### <a name="remarks"></a>Uwagi

Konstruktory skopiować dane wejściowe do nowego magazynu przydzielone, dlatego należy pamiętać, że pamięć wyjątków może spowodować. Należy pamiętać, że niektóre z tych konstruktorów pełnią funkcje konwersji. Dzięki temu można na przykład, zastąpić LPTSTR gdzie `CStringT` Oczekiwano obiektu.

- `CStringT`( `LPCSTR` `lpsz` ): Konstruuje Unicode `CStringT` z na ciąg ANSI. Można również użyć tego konstruktora, można załadować zasobu ciągu, jak pokazano w poniższym przykładzie.

- `CStringT(` `LPCWSTR` `lpsz` ): Konstruuje `CStringT` z ciągu Unicode.

- `CStringT`( `const unsigned char*` `psz` ): Służy do konstruowania `CStringT` ze wskaźnika do **unsigned char**.

> [!NOTE]
>  Zdefiniuj makro _CSTRING_DISABLE_NARROW_WIDE_CONVERSION, aby wyłączyć ciągu niejawna konwersja między ciągów ANSI i Unicode. Makro wyklucza z konstruktorów kompilacji, które obsługują konwersję.

Należy pamiętać, że *strSrc* parametru może być `CStringT` lub `CThisSimpleString` obiektu. Dla `CStringT`, użyj jednej z jego wystąpień domyślne (`CString`, `CStringA`, lub `CStringW`); w przypadku `CThisSimpleString`, użyj **to** wskaźnika. `CThisSimpleString` deklaruje wystąpienie [CSimpleStringT, klasa](../../atl-mfc-shared/reference/csimplestringt-class.md), czyli mniejszej klasy ciągu za pomocą funkcji wbudowanych mniej niż `CStringT` klasy.

Przeciążaj operator `CSimpleStringT<>&()` tworzy `CStringT` obiektu z `CSimpleStringT` deklaracji.

> [!NOTE]
>  Chociaż istnieje możliwość utworzenia `CStringT` wystąpień, które zawierają osadzone znaki o wartości null, zaleca się przed nim. Wywoływanie metody i operatory na `CStringT` obiektów, które zawierają znaki null embedded może wygenerować niepożądanych wyników.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#112](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_7.cpp)]

##  <a name="_dtorcstringt"></a>  CStringT:: ~ CStringT

Niszczy `CStringT` obiektu.

```
~CStringT() throw();
```

### <a name="remarks"></a>Uwagi

Niszczy `CStringT` obiektu.

##  <a name="delete"></a>  CStringT::Delete

Usuwa znaku lub znaków z ciągu, począwszy od znaku pod danym indeksem.

```
int Delete(int iIndex, int nCount = 1);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Liczony od zera indeks pierwszego znaku w `CStringT` obiektu do usunięcia.

*nCount*<br/>
Liczba znaków, które mają zostać usunięte.

### <a name="return-value"></a>Wartość zwracana

Długość ciągu zmienione.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* jest dłuższa niż spowoduje usunięcie parametrów, pozostała część ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#113](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_8.cpp)]

```Output
Before: Soccer is best,
    but hockey is quicker!
After: Soccer best,
    but hockey is quicker!
```

##  <a name="find"></a>  CStringT::Find

Przeszukuje ten ciąg pierwszego dopasowania znaku lub podciąg.

```
int Find(PCXSTR pszSub, int iStart=0) const throw();
int Find(XCHAR ch, int iStart=0) const throw();
```

### <a name="parameters"></a>Parametry

*pszSub*<br/>
Ciąg do wyszukania.

*iStart*<br/>
Indeks znaków w ciągu, aby rozpocząć wyszukiwanie z lub 0, aby rozpocząć od samego początku.

*ch*<br/>
Pojedynczy znak do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pierwszego znaku, w tym `CStringT` obiekt, który zastępuje podciąg żądanego lub znaków; -1, jeśli nie zostanie znaleziony podciąg lub znak.

### <a name="remarks"></a>Uwagi

Funkcja jest przeciążona, aby zaakceptować zarówno pojedynczych znaków (podobne do funkcji wykonawczej `strchr`) i ciągi (podobnie jak `strstr`).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#114](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_9.cpp)]

##  <a name="findoneof"></a>  CStringT::FindOneOf

Wyszukuje tego ciągu pierwszy znak, który dopasowuje dowolny znak zawarty w *pszCharSet*.

```
int FindOneOf(PCXSTR pszCharSet) const throw();
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg zawierający znaki do dopasowania.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks pierwszego wystąpienia znaku w tym ciągu, który jest również w *pszCharSet*; -1, jeśli nie ma dopasowania.

### <a name="remarks"></a>Uwagi

Znajduje pierwsze wystąpienie znaków w *pszCharSet*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#115](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_10.cpp)]

##  <a name="format"></a>  CStringT::Format

Zapisuje sformatowane dane do `CStringT` w taki sam sposób [sprintf_s —](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md) formatuje dane w stylu języka C tablicy znaków.

```
void __cdecl Format(UINT nFormatID, [, argument]...);
void __cdecl Format(PCXSTR pszFormat,  [, argument] ...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identyfikatora zasobu ciągu, który zawiera ciąg formantu formatu.

*pszFormat*<br/>
Ciąg formantu formatu.

*argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Ta funkcja formatuje i przechowuje serie znaków i wartości w `CStringT`. Każdy opcjonalny argument (jeśli istnieje) jest konwertowaya i wychodzi według specyfikacji formatu w *pszFormat* lub z zasobu ciągu określonego przez *nFormatID*.

Wywołanie zakończy się niepowodzeniem, jeśli sam obiekt ciągu jest oferowana jako parametr do `Format`. Na przykład poniższy kod będzie powodować nieprzewidywalne skutki:

[!code-cpp[NVC_ATLMFC_Utilities#116](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_11.cpp)]

Aby uzyskać więcej informacji, zobacz [składnia specyfikacji formatu: funkcje printf i wprintf](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#117](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_12.cpp)]

##  <a name="formatmessage"></a>  CStringT::FormatMessage

Formatuje ciąg komunikatu.

```
void __cdecl FormatMessage(UINT nFormatID, [, argument]...);
void __cdecl FormatMessage(PCXSTR pszFormat, [, argument]...);
```

### <a name="parameters"></a>Parametry

*nFormatID*<br/>
Identyfikator zasobu ciągu zawierający tekst sformatowany komunikat.

*pszFormat*<br/>
Wskazuje ciąg formantu formatu. Zostanie ono skanowane pod kątem operacji wstawienia i odpowiednio sformatowane. Ciąg formatu jest podobna do funkcji wykonawczej *printf*-stylu ciągów formatu, z wyjątkiem umożliwia parametry, które ma zostać wstawiony w dowolnej kolejności.

*argument*<br/>
Argumenty opcjonalne.

### <a name="remarks"></a>Uwagi

Funkcja wymaga definicji wiadomość jako dane wejściowe. Definicji komunikatu jest określana przez *pszFormat* lub z zasobu ciągu określonego przez *nFormatID*. Funkcja kopiuje tekst sformatowany komunikat, który ma `CStringT` obiektu, przetwarzanie osadzone Wstaw sekwencje, jeśli jest to wymagane.

> [!NOTE]
> `FormatMessage` próbuje przydzielić pamięci systemowej dla nowo sformatowany ciąg. Jeśli ta próba nie powiedzie się, automatycznie jest zgłaszany wyjątek pamięci.

Każdy insert musi mieć odpowiedni parametr po *pszFormat* lub *nFormatID* parametru. W ramach treści wiadomości kilka sekwencje ucieczki są obsługiwane w przypadku dynamicznie formatowania komunikatu. Aby uzyskać więcej informacji, zobacz Windows [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) funkcji w zestawie Windows SDK.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#118](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_13.cpp)]

##  <a name="formatmessagev"></a>  CStringT::FormatMessageV

Formatuje komunikat ciągu przy użyciu listy zmiennych argumentów.

```
void FormatMessageV(PCXSTR pszFormat, va_list* pArgList);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Wskazuje ciąg formantu formatu. Zostanie ono skanowane pod kątem operacji wstawienia i odpowiednio sformatowane. Ciąg formatu jest podobna do funkcji wykonawczej `printf`-stylu ciągów formatu, z wyjątkiem umożliwia parametry, które ma zostać wstawiony w dowolnej kolejności.

*pArgList*<br/>
Wskaźnik do listy argumentów.

### <a name="remarks"></a>Uwagi

Funkcja wymaga definicji wiadomość jako dane wejściowe, określane przez *pszFormat*. Funkcja kopiuje tekst sformatowany komunikat i listy zmiennych argumentów `CStringT` obiektu, przetwarzanie osadzone Wstaw sekwencje, jeśli jest to wymagane.

> [!NOTE]
> `FormatMessageV` wywołania [CStringT::FormatMessage](#formatmessage), który próbuje przydzielić pamięci systemowej dla nowo sformatowany ciąg. Jeśli ta próba nie powiedzie się, automatycznie jest zgłaszany wyjątek pamięci.

Aby uzyskać więcej informacji, zobacz Windows [FormatMessage](/windows/desktop/api/winbase/nf-winbase-formatmessage) funkcji w zestawie Windows SDK.

##  <a name="formatv"></a>  CStringT::FormatV

Formatuje komunikat ciągu przy użyciu listy zmiennych argumentów.

```
void FormatV(PCXSTR pszFormat, va_list args);
```

### <a name="parameters"></a>Parametry

*pszFormat*<br/>
Wskazuje ciąg formantu formatu. Zostanie ono skanowane pod kątem operacji wstawienia i odpowiednio sformatowane. Ciąg formatu jest podobna do funkcji wykonawczej `printf`-stylu ciągów formatu, z wyjątkiem umożliwia parametry, które ma zostać wstawiony w dowolnej kolejności.

*argumenty*<br/>
Wskaźnik do listy argumentów.

### <a name="remarks"></a>Uwagi

Zapisuje sformatowany ciąg i listy zmiennych argumentów `CStringT` ciągu w taki sam sposób `vsprintf_s` formatuje dane w stylu języka C tablicy znaków.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#119](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_14.cpp)]

[!code-cpp[NVC_ATLMFC_Utilities#120](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_15.cpp)]

##  <a name="getenvironmentvariable"></a>  CStringT::GetEnvironmentVariable

Ustawia ciąg na wartość określonej zmiennej środowiskowej.

```
BOOL GetEnvironmentVariable(PCXSTR pszVar);
```

### <a name="parameters"></a>Parametry

*pszVar*<br/>
Wskaźnik na ciąg zakończony znakiem null, który określa zmienną środowiskową.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli to się powiedzie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Pobiera wartość określonej zmiennej z bloku środowiska procesu wywołującego. Wartość w formie ciąg znaków zakończony znakiem null.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#121](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_16.cpp)]

##  <a name="insert"></a>  CStringT::Insert

Wstawia pojedynczy znak lub podciąg pod danym indeksem w ciągu.

```
int Insert(int iIndex, PCXSTR psz);
int Insert(int iIndex, XCHAR ch);
```

### <a name="parameters"></a>Parametry

*iIndex*<br/>
Indeks znaków, przed którym odbędzie się wstawiania.

*psz*<br/>
Wskaźnik do podciągu, który ma zostać wstawiony.

*ch*<br/>
Znak, który ma zostać wstawiony.

### <a name="return-value"></a>Wartość zwracana

Długość ciągu zmienione.

### <a name="remarks"></a>Uwagi

*IIndex* parametr identyfikuje pierwszy znak, który zostanie przeniesiona do zwolnienia miejsca dla znaku lub podciąg. Jeśli *nIndex* wynosi zero, nastąpi wstawiania przed cały ciąg. Jeśli *nIndex* jest większa niż długość ciągu, funkcja będzie łączyć się ciąg i złożone nowy materiał *ch* lub *psz*.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#122](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_17.cpp)]

##  <a name="left"></a>  CStringT::Left

Wyodrębnia najdalej z lewej strony *nCount* znaków z tego `CStringT` obiektu i zwraca kopię wyodrębnionego ciągu.

```
CStringT Left(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Liczba znaków do wyodrębnienia z tego `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

A `CStringT` obiekt, który zawiera kopię określonego zakresu znaków. Zwrócony `CStringT` obiekt może być pusta.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* przekracza długość ciągu, a następnie wyodrębniany jest cały ciąg. `Left` jest podobny do podstawowego `Left` funkcji.

Dla zestawów znaków wielobajtowych (MBCS) *nCount* traktuje każdy 8-bitową sekwencję jako znak, tak aby *nCount* zwraca liczbę znaków wielobajtowych pomnożoną przez dwa.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#123](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_18.cpp)]

##  <a name="loadstring"></a>  CStringT::LoadString

Odczytuje zasób ciągu Windows identyfikowane przez *nID*, z istniejącymi `CStringT` obiektu.

```
BOOL LoadString(HINSTANCE hInstance, UINT nID, WORD wLanguageID);
BOOL LoadString(HINSTANCE hInstance, UINT nID);
BOOL LoadString(UINT nID);
```

### <a name="parameters"></a>Parametry

*hInstance*<br/>
Dojście do wystąpienia modułu.

*nID*<br/>
Identyfikator Windows ciągu zasobu.

*wLanguageID*<br/>
Język zasobu ciągu.

### <a name="return-value"></a>Wartość zwracana

Wartość różną od zera, jeśli obciążenia zasobu zakończyła się pomyślnie; w przeciwnym razie 0.

### <a name="remarks"></a>Uwagi

Ładuje zasobu ciągu (*nID*) z określonym module (*hInstance*) przy użyciu określonego języka (*wLanguage*).

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#124](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_19.cpp)]

##  <a name="makelower"></a>  CStringT::MakeLower

Konwertuje `CStringT` obiekt na ciąg małych liter.

```
CStringT& MakeLower();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowy ciąg małych liter.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#125](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_20.cpp)]

##  <a name="makereverse"></a>  CStringT::MakeReverse

Odwraca kolejność znaków w `CStringT` obiektu.

```
CStringT& MakeReverse();
```

### <a name="return-value"></a>Wartość zwracana

Wartość wynikowa wycofać ciągu.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#126](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_21.cpp)]

##  <a name="makeupper"></a>  CStringT::MakeUpper

Konwertuje `CStringT` obiekt na ciąg na wielkie litery.

```
CStringT& MakeUpper();
```

### <a name="return-value"></a>Wartość zwracana

Wynikowy ciąg wielkie litery.

### <a name="remarks"></a>Uwagi

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#127](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_22.cpp)]

##  <a name="mid"></a>  CStringT::Mid

Zwraca podciąg o długości *nCount* znaków z tego `CStringT` obiektu, zaczynając od pozycji *iFirst* (liczony od zera).

```
CStringT Mid(int iFirst, int nCount) const;
CStringT Mid(int iFirst) const;
```

### <a name="parameters"></a>Parametry

*iFirst*<br/>
Liczony od zera indeks pierwszego znaku, w tym `CStringT` obiekt, który ma być zawarty w wyodrębnionego ciągu.

*nCount*<br/>
Liczba znaków do wyodrębnienia z tego `CStringT` obiektu. Jeśli ten parametr nie zostanie podany, jest wyodrębniany do końca ciągu.

### <a name="return-value"></a>Wartość zwracana

A `CStringT` obiekt, który zawiera kopię określonego zakresu znaków. Należy pamiętać, że zwrócony `CStringT` obiekt może być pusta.

### <a name="remarks"></a>Uwagi

Funkcja zwraca kopię wyodrębnionego ciągu. `Mid` jest podobna do funkcji podstawowych Mid (z tą różnicą, że indeksy Basic są oparte na jeden).

Dla znaków wielobajtowych zestawów znaków (MBCS) *nCount* odwołuje się do każdego 8-bitowych znaków; oznacza to, potencjalny klienta i szlak bajtów na jeden znak wielobajtowy są liczone jako dwa znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#128](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_23.cpp)]

##  <a name="oemtoansi"></a>  CStringT::OemToAnsi

Konwertuje wszystkie znaki w tym `CStringT` obiekt z zestawu do zestawu znaków ANSI znaków OEM.

```
void OemToAnsi();
```

### <a name="remarks"></a>Uwagi

Ta funkcja jest niedostępna w przypadku _UNICODE zdefiniowano.

### <a name="example"></a>Przykład

Zobacz przykład [CStringT::AnsiToOem](#ansitooem).

##  <a name="operator_add"></a>  CStringT::operator +

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

*ch1*<br/>
ANSI lub Unicode znak do łączenia się z parametrami.

*ch2*<br/>
ANSI lub Unicode znak do łączenia się z parametrami.

*str1*<br/>
A `CStringT` do łączenia z ciąg lub znak.

*str2*<br/>
A `CStringT` do łączenia z ciąg lub znak.

*psz1*<br/>
Wskaźnik na ciąg zakończony wartością null do łączenia z ciąg lub znak.

*psz2*<br/>
Wskaźnik do ciągu do łączenia z ciąg lub znak.

### <a name="remarks"></a>Uwagi

Istnieje siedem form przeciążenia `CStringT::operator+` funkcji. Pierwsza wersja łączy dwa istniejące `CStringT` obiektów. Kolejne dwa ZŁĄCZ.teksty `CStringT` obiektów i ciąg zakończony znakiem null. Kolejne dwa ZŁĄCZ.teksty `CStringT` obiektu i znak ANSI. Ostatnie dwa ZŁĄCZ.teksty `CStringT` obiektu i znak Unicode.

> [!NOTE]
>  Chociaż istnieje możliwość utworzenia `CStringT` wystąpień, które zawierają osadzone znaki o wartości null, zaleca się przed nim. Wywoływanie metody i operatory na `CStringT` obiektów, które zawierają znaki null embedded może wygenerować niepożądanych wyników.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#140](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_24.cpp)]

##  <a name="operator_add_eq"></a>  CStringT::operator +=

Łączy znaki do końca ciągu.

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
Wartość logiczna, określając, czy projekt jest biblioteki MFC DLL.

*BaseType*<br/>
Bazowy typ ciągu.

*var*<br/>
Variant — obiekt do połączenia tego ciągu.

*ch*<br/>
ANSI lub Unicode znak do łączenia się z parametrami.

*pszSrc*<br/>
Wskaźnik do oryginalnego ciągu są łączone.

*strSrc*<br/>
A `CStringT` do łączenia się tego ciągu.

### <a name="remarks"></a>Uwagi

Operator akceptuje innego `CStringT` obiektu, wskaźnik znaku lub jeden znak. Należy pamiętać, że ilość pamięci, które mogą wystąpić wyjątki, zawsze gdy używasz tego operatora łączenia, ponieważ można przydzielić nowego magazynu dla znaków dodane do tego `CStringT` obiektu.

Instrukcje dotyczące `CThisSimpleString`, zobacz sekcję Uwagi [CStringT::CStringT](#cstringt).

> [!NOTE]
>  Chociaż istnieje możliwość utworzenia `CStringT` wystąpień, które zawierają osadzone znaki o wartości null, zaleca się przed nim. Wywoływanie metody i operatory na `CStringT` obiektów, które zawierają znaki null embedded może wygenerować niepożądanych wyników.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#141](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_25.cpp)]

##  <a name="operator_eq_eq"></a>  CStringT::operator ==

Określa, czy dwa ciągi są równe logicznie.

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
ANSI lub Unicode znaków do porównania.

*ch2*<br/>
ANSI lub Unicode znaków do porównania.

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy ciąg lub znak z lewej strony jest równa ciąg lub znak po prawej stronie i zwraca wartość PRAWDA lub FAŁSZ w związku z tym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#142](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_26.cpp)]

##  <a name="operator_neq"></a>  CStringT::operator! =

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

*ch1*<br/>
ANSI lub Unicode znak do łączenia się z parametrami.

*ch2*<br/>
ANSI lub Unicode znak do łączenia się z parametrami.

*str1*<br/>
A `CStringT` do porównania.

*str2*<br/>
A `CStringT` do porównania.

*psz1*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Sprawdza, czy ciąg lub znak po lewej stronie nie jest równa ciąg lub znak po prawej stronie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#143](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_27.cpp)]

##  <a name="operator_lt"></a>  CStringT::operator &lt;

Określa, czy ciąg po lewej stronie operatora jest mniejszy niż ciąg po prawej stronie.

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
Wskaźnik na ciąg zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami, znak po znaku, aż do:

- Znajdzie dwie odpowiadające im znaki nierówne, a wynik porównania ich jest traktowana jako wynik porównania ciągów.

- Znalezione nie nierówności, ale jeden ciąg zawiera więcej znaków niż drugi, krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, a więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#144](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_28.cpp)]

##  <a name="operator_gt"></a>  CStringT::operator &gt;

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
Wskaźnik na ciąg zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami, znak po znaku, aż do:

- Znajdzie dwie odpowiadające im znaki nierówne, a wynik porównania ich jest traktowana jako wynik porównania ciągów.

- Znalezione nie nierówności, ale jeden ciąg zawiera więcej znaków niż drugi, krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#145](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_29.cpp)]

##  <a name="operator_lt_eq"></a>  CStringT::operator &lt;=

Określa, czy ciąg po lewej stronie operatora jest mniejszy niż lub równe ciągu z prawej strony.

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
Wskaźnik na ciąg zakończony wartością null do porównania.

*psz2*<br/>
Wskaźnik na ciąg zakończony wartością null do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami, znak po znaku, aż do:

- Znajdzie dwie odpowiadające im znaki nierówne, a wynik porównania ich jest traktowana jako wynik porównania ciągów.

- Znalezione nie nierówności, ale jeden ciąg zawiera więcej znaków niż drugi, krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#146](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_30.cpp)]

##  <a name="operator_gt_eq"></a>  CStringT::operator &gt;=

Określa, czy ciąg po lewej stronie operatora jest większy lub równy ciągowi po prawej stronie.

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
Wskaźnik na ciąg do porównania.

*psz2*<br/>
Wskaźnik na ciąg do porównania.

### <a name="remarks"></a>Uwagi

Porównanie lexicographical między ciągami, znak po znaku, aż do:

- Znajdzie dwie odpowiadające im znaki nierówne, a wynik porównania ich jest traktowana jako wynik porównania ciągów.

- Znalezione nie nierówności, ale jeden ciąg zawiera więcej znaków niż drugi, krótszy ciąg jest uważany za mniej niż dłuższy ciąg.

- Znalezione nie nierówności i stwierdzi, że ciągi mają taką samą liczbę znaków, więc ciągi są równe.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#147](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_31.cpp)]

##  <a name="remove"></a>  CStringT::Remove

Usuwa wszystkie wystąpienia określonego znaku z ciągu.

```
int Remove(XCHAR chRemove);
```

### <a name="parameters"></a>Parametry

*chRemove*<br/>
Znak, który ma zostać usunięty z ciągu.

### <a name="return-value"></a>Wartość zwracana

Usunięte liczba znaków z ciągu. Zero, jeśli ciąg nie jest zmieniany.

### <a name="remarks"></a>Uwagi

Porównania dla znaku jest uwzględniana wielkość liter.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#129](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_32.cpp)]

##  <a name="replace"></a>  CStringT::Replace

Istnieją dwie wersje `Replace`. Pierwsza wersja zastępuje jedną lub więcej kopii podciągu przy użyciu innego podciąg. Oba podciągi są zakończony znakiem null. Druga wersja zastępuje kopie co najmniej jeden znak, używając innego znaku. Obie wersje operować na danych znakowych przechowywanych w `CStringT`.

```
int Replace(PCXSTR pszOld, PCXSTR pszNew);
int Replace(XCHAR chOld, XCHAR chNew);
```

### <a name="parameters"></a>Parametry

*pszOld*<br/>
Wskaźnik na ciąg zakończony znakiem null, mają zostać zastąpione przez *pszNew*.

*pszNew*<br/>
Wskaźnik na ciąg zakończony znakiem null, który zastępuje *pszOld*.

*chOld*<br/>
Znak, który ma zostać zastąpione przez *chNew*.

*chNew*<br/>
Zastępowanie znaków *chOld*.

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę wystąpień Zamieniono znak lub podciąg lub zero, jeśli ciąg nie jest zmieniany.

### <a name="remarks"></a>Uwagi

`Replace` można zmienić długość ciągu, ponieważ *pszNew* i *pszOld* nie muszą mieć taką samą długość, a kilku kopii stare podciąg można zmienić na nową. Funkcja wykonuje czułym na wielkość liter.

Przykłady `CStringT` wystąpienia są `CString`, `CStringA`, i `CStringW`.

Aby uzyskać `CStringA`, `Replace` współpracuje z ANSI lub znaków wielobajtowych (MBCS). Aby uzyskać `CStringW`, `Replace` współpracuje z szerokich znaków.

Aby uzyskać `CString`, typ danych znakowych wybiera się w czasie kompilacji, na podstawie tego, czy są zdefiniowane stałe w poniższej tabeli.

|Zdefiniowanej stałej|Typ danych znakowych|
|----------------------|-------------------------|
|_UNICODE|Znaki dwubajtowe|
|_MBCS|Znaków wielobajtowych|
|Ani|Znaki jednobajtowe|
|Oba|Niezdefiniowane|

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#200](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_33.cpp)]

##  <a name="reversefind"></a>  CStringT::ReverseFind

Wyszukuje to `CStringT` obiektu dla ostatniego dopasowania znaku.

```
int ReverseFind(XCHAR ch) const throw();
```

### <a name="parameters"></a>Parametry

*ch*<br/>
Znak do wyszukania.

### <a name="return-value"></a>Wartość zwracana

Liczony od zera indeks ostatniego znaku w tym `CStringT` obiekt, który odpowiada żądanej znaków lub wartość -1, jeśli znak nie zostanie znaleziony.

### <a name="remarks"></a>Uwagi

Funkcja jest podobne do funkcji wykonawczej `strrchr`.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#130](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_34.cpp)]

##  <a name="right"></a>  CStringT::Right

Wyodrębnianie ostatnich (czyli po prawej stronie) *nCount* znaków z tego `CStringT` obiektu i zwraca kopię wyodrębnionego ciągu.

```
CStringT Right(int nCount) const;
```

### <a name="parameters"></a>Parametry

*nCount*<br/>
Liczba znaków do wyodrębnienia z tego `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

A `CStringT` obiekt, który zawiera kopię określonego zakresu znaków. Należy pamiętać, że zwrócony `CStringT` obiekt może być pusta.

### <a name="remarks"></a>Uwagi

Jeśli *nCount* przekracza długość ciągu, a następnie wyodrębniany jest cały ciąg. `Right` jest podobny do podstawowego `Right` funkcji (z tą różnicą, że indeksy Basic zaczynają się od zera).

Dla znaków wielobajtowych zestawów znaków (MBCS) *nCount* odwołuje się do każdego 8-bitowych znaków; oznacza to, potencjalny klienta i szlak bajtów na jeden znak wielobajtowy są liczone jako dwa znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#131](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_35.cpp)]

##  <a name="setsysstring"></a>  CStringT::SetSysString

Przydzieli BSTR wskazywany przez *pbstr* i kopiuje zawartość `CStringT` obiekt, w tym znakiem NULL.

```
BSTR SetSysString(BSTR* pbstr) const;
```

### <a name="parameters"></a>Parametry

*pbstr*<br/>
Wskaźnik do ciągu znaków.

### <a name="return-value"></a>Wartość zwracana

Nowy ciąg.

### <a name="remarks"></a>Uwagi

W zależności od zawartości `CStringT` obiekt, wartość BSTR odwołuje się *pbstr* można zmienić. Funkcja zgłasza `CMemoryException` Jeśli istnieje niewystarczająca ilość pamięci.

Ta funkcja jest zwykle używana do zmiany wartości parametrów przekazywany przez odwołanie do automatyzacji.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#132](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_36.cpp)]

##  <a name="spanexcluding"></a>  CStringT::SpanExcluding

Wyodrębnia znaki ciągu, począwszy od pierwszego znaku, które nie znajdują się w zestawie znaków identyfikowane przez *pszCharSet*.

```
CStringT SpanExcluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg jest interpretowany jako zbiór znaków.

### <a name="return-value"></a>Wartość zwracana

Podciąg, który zawiera znaki do ciągu, które nie znajdują się w *pszCharSet*, począwszy od pierwszego znaku w ciągu, a kończąc na pierwszy znak w ciągu, który jest również w *pszCharSet* (oznacza to, rozpoczynając od pierwszego znaku w ciągu i maksymalnie, ale z wyjątkiem pierwszego znaku w ciąg, który znajduje się *pszCharSet*). Zwraca cały ciąg, jeśli żaden znak w *pszCharSet* znajduje się w ciągu.

### <a name="remarks"></a>Uwagi

`SpanExcluding` wyodrębnia i zwraca wszystkie znaki, poprzedzający pierwsze wystąpienie ciągu znaków z *pszCharSet* (innymi słowy, znak z *pszCharSet* i wszystkie znaki w ciągu, nie są zwrócone). Jeśli żaden znak z *pszCharSet* znajduje się w ciągu, następnie `SpanExcluding` zwraca cały ciąg.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#133](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_37.cpp)]

##  <a name="spanincluding"></a>  CStringT::SpanIncluding

Wyodrębnia znaki ciągu, począwszy od pierwszego znaku, które znajdują się w zestawie znaków identyfikowane przez *pszCharSet*.

```
CStringT SpanIncluding(PCXSTR pszCharSet) const;
```

### <a name="parameters"></a>Parametry

*pszCharSet*<br/>
Ciąg jest interpretowany jako zbiór znaków.

### <a name="return-value"></a>Wartość zwracana

Podciąg, który zawiera znaki do ciągu, które znajdują się w *pszCharSet*, zaczynając od pierwszego znaku w ciągu i kończy się po znaku znajduje się w ciąg, który nie znajduje się w *pszCharSet*. `SpanIncluding` Zwraca podciąg puste, jeśli pierwszy znak w ciągu nie jest w określonym zestawie.

### <a name="remarks"></a>Uwagi

Jeśli pierwszym znakiem ciągu nie ma w zestawie znaków następnie `SpanIncluding` zwraca pusty ciąg. W przeciwnym razie zwraca sekwencji następujących po sobie znaków, które znajdują się w zestawie.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#134](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_38.cpp)]

##  <a name="tokenize"></a>  CStringT::Tokenize

Znajduje następny token w ciągu docelowym

```
CStringT Tokenize(PCXSTR pszTokens, int& iStart) const;
```

### <a name="parameters"></a>Parametry

*pszTokens*<br/>
Ciąg zawierający token ograniczników. Kolejność tych ograniczniki nie jest ważna.

*iStart*<br/>
Liczony od zera indeks, aby rozpocząć wyszukiwanie.

### <a name="return-value"></a>Wartość zwracana

A `CStringT` obiekt zawierający bieżącą wartość tokenu.

### <a name="remarks"></a>Uwagi

`Tokenize` Funkcja znajduje następny token w ciągu docelowym. Zestaw znaków *pszTokens* określa ograniczniki możliwe tokenu, który ma zostać odnaleziona. Przy każdym wywołaniu `Tokenize` funkcja rozpoczyna się od *iStart*, pomija wiodących ograniczniki i zwraca `CStringT` obiektu zawierającego bieżącego tokenu, który jest ciąg znaków do następnego znaku ogranicznika. Wartość *iStart* jest zaktualizowane pod kątem pozycji końcowy znak ograniczający lub -1, jeśli osiągnięto koniec ciągu. Kolejnych tokenów można zaburzyć spoza końca ciągu docelowego przez szereg wywołań do `Tokenize`przy użyciu *iStart* do śledzenia, gdzie w ciągu następnego tokenu jest do odczytu. W przypadku żadnych kolejnych tokenów funkcja zwróci ciąg pusty i *iStart* zostanie ustawiona na wartość -1.

W przeciwieństwie do CRT tokenizację funkcji, takich jak [strtok_s —, _strtok_s_l —, wcstok_s —, _wcstok_s_l —, _mbstok_s —, _mbstok_s_l —](../../c-runtime-library/reference/strtok-s-strtok-s-l-wcstok-s-wcstok-s-l-mbstok-s-mbstok-s-l.md), `Tokenize` nie powoduje modyfikacji ciągu docelowym.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#135](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_39.cpp)]

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu jest następująca:

```Output
Resulting Token: First
Resulting Token: Second
Resulting Token: Third
```

##  <a name="trim"></a>  CStringT::Trim

Przycina początkowe i końcowe znaków z ciągu.

```
CStringT& Trim(XCHAR chTarget);
CStringT& Trim(PCXSTR pszTargets);
CStringT& Trim();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowych można przycięcia.

*pszTargets*<br/>
Wskaźnik do ciągu zawierającego znaki docelowych można przycięcia. Wszystkie wiodące i końcowe wystąpienia znaków w *pszTarget* będą usuwane z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg przycięty.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie wystąpienia początkowe i końcowe w jednej z następujących czynności:

- Znak określony przez *chTarget*.

- Wszystkie znaki w ciągu określonego przez *pszTargets*.

- Białe znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#136](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_40.cpp)]

### <a name="remarks"></a>Uwagi

Dane wyjściowe z tego przykładu jest następująca:

```Output
Before: "******Soccer is best, but liquor is quicker!!!!!"
After : "Soccer is best, but liquor is quicker"
```

##  <a name="trimleft"></a>  CStringT::TrimLeft

Przycina początkowe znaki ciągu.

```
CStringT& TrimLeft(XCHAR chTarget);
CStringT& TrimLeft(PCXSTR pszTargets);
CStringT& TrimLeft();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowych można przycięcia.

*pszTargets*<br/>
Wskaźnik do ciągu zawierającego znaki docelowych można przycięcia. Wszystkie wystąpienia wiodących znaków *pszTarget* będą usuwane z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Wynikowy ciąg przycięty.

### <a name="remarks"></a>Uwagi

Usuwa wszystkie wystąpienia początkowe i końcowe w jednej z następujących czynności:

- Znak określony przez *chTarget*.

- Wszystkie znaki w ciągu określonego przez *pszTargets*.

- Białe znaki.

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#137](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_41.cpp)]

##  <a name="trimright"></a>  CStringT::TrimRight

Przycina końcowe znaków z ciągu.

```
CStringT& TrimRight(XCHAR chTarget);
CStringT& TrimRight(PCXSTR pszTargets);
CStringT& TrimRight();
```

### <a name="parameters"></a>Parametry

*chTarget*<br/>
Znak docelowych można przycięcia.

*pszTargets*<br/>
Wskaźnik do ciągu zawierającego znaki docelowych można przycięcia. Końcowe wszystkie wystąpienia znaków w *pszTarget* będą usuwane z `CStringT` obiektu.

### <a name="return-value"></a>Wartość zwracana

Zwraca `CStringT` obiekt, który zawiera ciąg przycięty.

### <a name="remarks"></a>Uwagi

Usuwa końcowe wystąpienia jednego z następujących czynności:

- Znak określony przez *chTarget*.

- Wszystkie znaki w ciągu określonego przez *pszTargets*.

- Białe znaki.

`CStringT& TrimRight(XCHAR chTarget)` Wersji przyjmuje jeden parametr znaku i usuwa wszystkie kopie tego znaku od końca `CStringT` dane ciągu. Rozpoczyna się od końca ciągu i działa w kierunku do przodu. Zatrzymuje się, gdy znajdzie inny znak lub gdy `CSTringT` zabraknie danych znakowych.

`CStringT& TrimRight(PCXSTR pszTargets)` Wersji akceptuje ciąg zakończony wartością null zawierający wszystkie znaki różnych do wyszukania. Usuwa wszystkie kopie tych znaków w `CStringT` obiektu. Rozpoczyna od końca ciągu i działa w kierunku do przodu. Zatrzymuje się, gdy znajdzie znak, który nie znajduje się w ciągu docelowym lub gdy `CStringT` zabraknie danych znakowych. Spróbuj nie pasuje do ciągu docelowego całego do podciągu na końcu `CStringT`.

`CStringT& TrimRight()` Wersji nie wymaga parametrów. Jego przycina końcowe białych znaków od końca `CStringT` ciągu. Podziały wierszy, spacje lub tabulatory, może być białych znaków.

-

### <a name="example"></a>Przykład

[!code-cpp[NVC_ATLMFC_Utilities#138](../../atl-mfc-shared/codesnippet/cpp/cstringt-class_42.cpp)]

## <a name="see-also"></a>Zobacz także

[Wykres hierarchii](../../mfc/hierarchy-chart.md)<br/>
[Klasy współdzielone ATL/MFC](../../atl-mfc-shared/atl-mfc-shared-classes.md)<br/>
[CSimpleStringT, klasa](../../atl-mfc-shared/reference/csimplestringt-class.md)
